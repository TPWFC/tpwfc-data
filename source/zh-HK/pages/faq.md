---
slug: faq
title: 常見問題
excerpt: 關於TPWFC項目架構、技術堆疊及開發流程的常見問題解答。
---

# 常見問題 (FAQ)

歡迎來到 **TPWFC (大埔宏福苑大火文檔計劃)**。本文檔旨在解答關於本項目架構、技術堆疊及開發流程的常見問題。

## 📌 項目概覽

### 這個項目的目標是什麼？

我們的主要目標是為 **2025 年大埔宏福苑大火** 建立一個永久、客觀且透明的歷史檔案。我們致力於保存真相，透過數據分析推動公眾安全，並提供一個數位紀念空間。

此外，本項目亦旨在成為一個高品質的全端開發範本 (Full-stack Template)，供開發者在進行 "Vibe Coding" 時參考，以建立更安全且易於維護的應用程式。

### 這是政府官方網站嗎？

**不是。** 這是一個由民間發起的開源計劃，與香港特區政府、消防處或警務處無關。

---

## 🛠️ 技術堆疊 (Tech Stack)

### 為什麼選擇 Next.js 16？

我們使用 Next.js 16 (App Router) 是因為其強大的伺服器端渲染 (SSR) 能力，這對搜尋引擎優化 (SEO) 和首屏載入效能至關重要。同時，它與我們選用的 Payload CMS 3 完美整合。

### 為什麼選擇 Payload CMS 3？

Payload CMS 3 是一款無頭 (Headless) 內容管理系統，提供靈活的後台介面與強大的 GraphQL API。第 3 版是 Next.js 原生的，允許我們將 CMS 與前端網站運行在同一個應用實例中，大大簡化了部署流程。

### 為什麼選擇 SQLite？

我們使用 `@payloadcms/db-sqlite` 是為了簡化架構與提高可移植性。由於這是一個「讀多寫少」的文檔網站，SQLite 能在無需維護獨立資料庫伺服器 (如 PostgreSQL 或 MongoDB) 的情況下提供優異效能。此外，使用 SQLite 讓資料庫檔案可以直接被提交或在本地開發環境中輕鬆同步。

### 為什麼 Worker Service 使用 Go 語言？

Worker Service 涉及高併發任務，例如同時爬取多個網路來源及處理大量文本數據。Go (Golang) 因其高效能、強型別系統及優秀的併發模型 (Goroutines) 而被選用。

### 為什麼使用 Biome 而非 ESLint/Prettier？

我們選用 [Biome](https://biomejs.dev/) 進行程式碼檢查與格式化。它比傳統的 ESLint + Prettier 組合快得多，並為網頁開發提供了統一的工具鏈。

---

## 🚀 快速開始與開發

### 如何啟動開發伺服器？

1. 安裝依賴：`bun install`
2. 設定環境變數：`cp .env.example .env`
3. 初始化並填充資料庫：`bun run db:reset-seed`
4. 啟動伺服器：`bun dev`

### 如何登入管理後台 (Admin Panel)？

執行 `bun run db:reset-seed` 或 `bun run seed:admin` 後，您可以訪問 `http://localhost:3000/admin` 並使用以下資訊登入：

- **電郵：** `admin@example.com`
- **密碼：** `changeme123`

### 如何運行 Go Worker？

請進入 `worker/` 目錄並使用 `Makefile`：

- 編譯所有執行檔：`make build`
- 運行完整管線：`make run-worker ...` (詳見 `worker/README.md` 中的參數說明)

### 應該使用哪個套件管理器？

我們統一使用 **Bun** (`bun`) 來安裝依賴及運行腳本。雖然 `package.json` 中的部分內部腳本可能提及 `pnpm`，但 `bun` 會處理執行過程。

---

## 📝 內容管理

### 內容是如何儲存的？

- **結構化數據 (事件、時間軸)：** 透過 Payload CMS 儲存在 SQLite 資料庫中。
- **敘事內容 (頁面、文章)：** 通常源自 `data/source/` 目錄下的 **Markdown** 檔案。這些檔案被視為「單一事實來源 (Single Source of Truth)」，並會被同步至 CMS。

### 如何編輯內容？

1. **CMS:** 您可以直接在管理後台 (`/admin`) 進行編輯。
2. **Markdown:** 您可以編輯 `data/source/` 中的 Markdown 檔案，然後運行 `Normalizer` + `Uploader` Worker 組件將變更同步至 CMS。

### 「同步 (Sync)」是如何運作的？

Go Worker 管線 (`Crawler` -> `Normalizer` -> `Uploader`) 負責讀取原始數據 (網路來源或本地 Markdown)，將其轉換為標準 JSON 格式，最後透過 GraphQL API 上傳至 Payload CMS。

---

## ⚠️ 疑難排解

### 出現 `Error: P1001: Can't reach database server`？

由於我們使用 SQLite，這通常代表檔案權限錯誤或路徑不正確。請確認根目錄下是否存在 `payload.db` 檔案，或嘗試重新運行 Seed 腳本。

### 提交 (Commit) 時出現 `Biome` 錯誤？

我們強制執行嚴格的程式碼風格。請運行 `bun run format` 來自動修復格式問題。

### 測試失敗？

- **E2E 測試:** 請確保開發伺服器正在運行，或讓 Playwright 自動啟動它。
- **整合測試:** 請檢查測試資料庫是否乾淨。

---

## 🤝 參與貢獻

### 我該如何貢獻？

- **程式碼:** 請查看我們的 [GitHub Repository](https://github.com/TPWFC)。
- **資料/內容:** 加入我們的 Discord 伺服器提交更正或新資訊。

### 設計系統在哪裡？

我們使用 **Tailwind CSS 4** 搭配 **Shadcn UI**。元件位於 `src/app/(frontend)/components/` 目錄下。

<!-- METADATA_START
VALIDATION: TRUE
LAST_MODIFY: 2025-12-25T13:21:09Z
HASH: 3d164a5eca7330cb31346b472f49aeb71b39519c97f5b1a2ad0bc4e9cf3945a5
METADATA_END -->
