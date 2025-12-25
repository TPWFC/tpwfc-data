---
slug: faq
title: 常见问题
excerpt: 关于TPWFC项目架构、技术栈及开发流程的常见问题解答。
---

# 常见问题 (FAQ)

欢迎来到 **TPWFC (大埔宏福苑大火文档计划)**。本文档旨在解答关于本项目架构、技术栈及开发流程的常见问题。

## 📌 项目概览

### 这个项目的目标是什么？

我们的主要目标是为 **2025 年大埔宏福苑大火** 建立一个永久、客观且透明的历史档案。我们致力于保存真相，透过数据分析推动公众安全，并提供一个数字纪念空间。

此外，本项目亦旨在成为一个高质量的全栈开发范本 (Full-stack Template)，供开发者在进行 "Vibe Coding" 时参考，以建立更安全且易于维护的应用程序。

### 这是政府官方网站吗？

**不是。** 这是一个由民间发起的开源计划，与香港特区政府、消防处或警务处无关。

---

## 🛠️ 技术栈 (Tech Stack)

### 为什么选择 Next.js 16？

我们使用 Next.js 16 (App Router) 是因为其强大的服务器端渲染 (SSR) 能力，这对搜索引擎优化 (SEO) 和首屏加载性能至关重要。同时，它与我们选用的 Payload CMS 3 完美整合。

### 为什么选择 Payload CMS 3？

Payload CMS 3 是一款无头 (Headless) 内容管理系统，提供灵活的后台界面与强大的 GraphQL API。第 3 版是 Next.js 原生的，允许我们将 CMS 与前端网站运行在同一个应用实例中，大大简化了部署流程。

### 为什么选择 SQLite？

我们使用 `@payloadcms/db-sqlite` 是为了简化架构与提高可移植性。由于这是一个“读多写少”的文档网站，SQLite 能在无需维护独立数据库服务器 (如 PostgreSQL 或 MongoDB) 的情况下提供优异性能。此外，使用 SQLite 让数据库文件可以直接被提交或在本地开发环境中轻松同步。

### 为什么 Worker Service 使用 Go 语言？

Worker Service 涉及高并发任务，例如同时爬取多个网络来源及处理大量文本数据。Go (Golang) 因其高性能、强类型系统及优秀的并发模型 (Goroutines) 而被选用。

### 为什么使用 Biome 而非 ESLint/Prettier？

我们选用 [Biome](https://biomejs.dev/) 进行代码检查与格式化。它比传统的 ESLint + Prettier 组合快得多，并为网页开发提供了统一的工具链。

---

## 🚀 快速开始与开发

### 如何启动开发服务器？

1. 安装依赖：`bun install`
2. 设定环境变量：`cp .env.example .env`
3. 初始化并填充数据库：`bun run db:reset-seed`
4. 启动服务器：`bun dev`

### 如何登录管理后台 (Admin Panel)？

执行 `bun run db:reset-seed` 或 `bun run seed:admin` 后，您可以访问 `http://localhost:3000/admin` 并使用以下信息登录：

- **电邮：** `admin@example.com`
- **密码：** `changeme123`

### 如何运行 Go Worker？

请进入 `worker/` 目录并使用 `Makefile`：

- 编译所有执行档：`make build`
- 运行完整管线：`make run-worker ...` (详见 `worker/README.md` 中的参数说明)

### 应该使用哪个包管理器？

我们统一使用 **Bun** (`bun`) 来安装依赖及运行脚本。虽然 `package.json` 中的部分内部脚本可能提及 `pnpm`，但 `bun` 会处理执行过程。

---

## 📝 内容管理

### 内容是如何存储的？

- **结构化数据 (事件、时间轴)：** 透过 Payload CMS 存储在 SQLite 数据库中。
- **叙事内容 (页面、文章)：** 通常源自 `data/source/` 目录下的 **Markdown** 文件。这些文件被视为“单一事实来源 (Single Source of Truth)”，并会被同步至 CMS。

### 如何编辑内容？

1. **CMS:** 您可以直接在管理后台 (`/admin`) 进行编辑。
2. **Markdown:** 您可以编辑 `data/source/` 中的 Markdown 文件，然后运行 `Normalizer` + `Uploader` Worker 组件将变更同步至 CMS。

### “同步 (Sync)”是如何运作的？

Go Worker 管线 (`Crawler` -> `Normalizer` -> `Uploader`) 负责读取原始数据 (网络来源或本地 Markdown)，将其转换为标准 JSON 格式，最后透过 GraphQL API 上传至 Payload CMS。

---

## ⚠️ 疑难排解

### 出现 `Error: P1001: Can't reach database server`？

由于我们使用 SQLite，这通常代表文件权限错误或路径不正确。请确认根目录下是否存在 `payload.db` 文件，或尝试重新运行 Seed 脚本。

### 提交 (Commit) 时出现 `Biome` 错误？

我们强制执行严格的代码风格。请运行 `bun run format` 来自动修复格式问题。

### 测试失败？

- **E2E 测试:** 请确保开发服务器正在运行，或让 Playwright 自动启动它。
- **整合测试:** 请检查测试数据库是否干净。

---

## 🤝 参与贡献

### 我该如何贡献？

- **代码:** 请查看我们的 [GitHub Repository](https://github.com/TPWFC)。
- **资料/内容:** 加入我们的 Discord 服务器提交更正或新信息。

### 设计系统在哪里？

我们使用 **Tailwind CSS 4** 搭配 **Shadcn UI**。组件位于 `src/app/(frontend)/components/` 目录下。

<!-- METADATA_START
VALIDATION: TRUE
LAST_MODIFY: 2025-12-25T13:21:09Z
HASH: c889205f37d8d0c371ea51e7722f47e1888fbcc7d5bffd79de665a0ecca92f77
METADATA_END -->
