# [事件名稱]完整時間線

## 事件概述

### 基本資料

<!-- BASIC_INFO_START -->

| 項目               | 資料                           |
| ------------------ | ------------------------------ |
| INCIDENT_ID        | [EVENT_ID]                     |
| DATE_RANGE         | [YYYY-MM-DD]/[YYYY-MM-DD]      |
| LOCATION           | [地點]                         |
| INCIDENT_NAME      | [事件名稱]                     |
| MAP                | [地圖](URL)                    |
| DISASTER_LEVEL     | [LEVEL]                        |
| DURATION           | [DD:HH:MM:SS]                  |
| AFFECTED_BUILDINGS | [數量]                         |
| SOURCES            | [Source1](URL), [Source2](URL) |

<!-- BASIC_INFO_END -->

### 起火原因

<!-- FIRE_CAUSE_START -->

[在此輸入起火原因]

<!-- FIRE_CAUSE_END -->

### 災情嚴重性

<!-- SEVERITY_START -->

[在此輸入災情嚴重性描述]

<!-- SEVERITY_END -->

---

## 詳細時間線

<!-- TIMELINE_TABLE_START -->

| 日期         | 時間    | 事件       | 類別       | 死傷狀況 | 來源     | 影片        | 圖片        |
| ------------ | ------- | ---------- | ---------- | -------- | -------- | ----------- | ----------- |
| [YYYY-MM-DD] | [HH:MM] | [事件描述] | [CATEGORY] | [STATUS] | [Source] | [影片](URL) | [圖片](URL) |

<!-- TIMELINE_TABLE_END -->

---

## 死傷狀況狀態代碼標準

### 標準格式

```bash
CATEGORY:數量(子類別:數量),CATEGORY:數量
```

### 狀況代碼定義

| 代碼                    | 意義            | 範例                     |
| ----------------------- | --------------- | ------------------------ |
| `STATUS_NONE`           | 無人員傷亡      | `STATUS_NONE`            |
| `DEAD:X`                | 死亡X人         | `DEAD:13`                |
| `INJURED:X`             | 受傷X人         | `INJURED:7`              |
| `MISSING:X`             | 失蹤X人         | `MISSING:279`            |
| `FIREFIGHTER_DEAD:X`    | 消防員殉職X人   | `FIREFIGHTER_DEAD:1`     |
| `FIREFIGHTER_INJURED:X` | 消防員受傷X人   | `FIREFIGHTER_INJURED:12` |
| `REMAINING_CASES:X`     | 餘下救援個案X宗 | `REMAINING_CASES:25`     |
| `UNIDENTIFIED:X`        | 未能辨認遺體X具 | `UNIDENTIFIED:89`        |

### 子類別格式

```bash
DEAD:13(ON_SITE:9,TRANSIT:4)
```

- `ON_SITE:X` = 現場死亡X人
- `TRANSIT:X` = 送院途中死亡X人

---

## 關鍵統計數據

<!-- KEY_STATISTICS_START -->

| 項目                   | 數據          |
| ---------------------- | ------------- |
| FIRE_DURATION          | [DD:HH:MM:SS] |
| FIRE_LEVEL             | [LEVEL]       |
| FINAL_DEATHS           | [數量]        |
| FIREFIGHTER_CASUALTIES | [描述]        |
| FIREFIGHTERS_DEPLOYED  | [數量]        |
| FIRE_VEHICLES          | [數量]        |
| HELP_CASES             | [數量]        |
| HELP_CASES_PROCESSED   | [數量]        |
| AFFECTED_BUILDINGS     | [數量]        |
| SHELTER_USERS          | [數量]        |
| MISSING_PERSONS        | [數量]        |
| UNIDENTIFIED_BODIES    | [數量]        |

<!-- KEY_STATISTICS_END -->

---

## 📝 新增事件指南

### 表格格式說明

#### 1. 基本表格格式

時間線事件必須以單一表格形式組織，使用以下欄位：

```bash
| 日期 | 時間 | 事件 | 類別 | 死傷狀況 | 來源 | 影片 |
|------|------|------|------|----------|------|------|
```

#### 2. 表格邊界標記

- **開始標記：** `<!-- TIMELINE_TABLE_START -->`
- **結束標記：** `<!-- TIMELINE_TABLE_END -->`

這些HTML註釋標記用於幫助自動化工具識別時間線數據範圍，不會影響人類閱讀體驗。

#### 3. 日期格式

- 使用ISO 8601標準格式：`YYYY-MM-DD`
- 例如：`2025-11-26`、`2025-11-27`、`2025-11-28`
- 日期必須包含在表格中作為第一欄，便於機器解析

#### 4. 類別格式

- 使用全大寫英文單詞，以下劃線分隔：`INITIAL_REPORT`
- 類別用於分類事件類型，便於數據分析和篩選
- 常見類別：
  - `INITIAL_REPORT` - 火警初報
  - `FIRE_ESCALATION` - 火警升級
  - `FIREFIGHTING` - 消防滅火行動
  - `SEARCH_RECOVERY` - 搜索救援行動
  - `CASUALTY_UPDATE` - 傷亡統計更新
  - `RELIEF_ASSISTANCE` - 救災援助
  - `OTHER` - 其他類型事件

#### 5. 時間格式

- 使用24小時制：`HH:MM`
- 如：`14:51`、`23:15`
- 時間必須與日期結合使用，形成完整的時間戳

#### 6. 事件描述

- 簡潔明確地描述事件
- 避免重複性資訊
- 專注於與火警直接相關的事件

#### 7. 死傷狀況格式

**單一類別：**

```bash
DEAD:13
INJURED:7
STATUS_NONE
```

**多個類別（用逗號分隔）：**

```bash
DEAD:13,INJURED:30
DEAD:94,INJURED:76,FIREFIGHTER_INJURED:12
```

**含子類別：**

```bash
DEAD:13(ON_SITE:9,TRANSIT:4)
```

#### 8. 來源標註

- **兩來源確認：** `HK01, SBS Australia`
- **單一來源：** `HK01` 或 `SBS Australia`

#### 9. 影片格式

- 使用Markdown連結格式：`[顯示文字](URL)`
- 如：`[影片](https://www.youtube.com/watch?v=VIDEO_ID&t=300s)`
- 留空表示該事件沒有對應的影片片段
- URL應包含完整的YouTube連結，可包含時間參數 `&t=秒數s`

#### 10. 圖片格式

- 使用Markdown連結格式：`[顯示文字](URL)`
- 可使用逗號分隔多張圖片：`[圖1](URL1), [圖2](URL2)`
- 接受純URL或Markdown連結
- 留空表示無圖片

#### 11. 添加新狀況代碼

如需新的狀況類型，請：

1. 使用大寫英文和下劃線：`NEW_STATUS:X`
2. 在「死傷狀況狀態代碼標準」表格中添加定義
3. 提供清楚的中文說明和範例

---

## 資料來源

<!-- SOURCES_START -->

| SOURCE_NAME | SOURCE_TITLE | SOURCE_URL |
| ----------- | ------------ | ---------- |
| [Name]      | [Title]      | [URL]      |

<!-- SOURCES_END -->

---

## 註釋

<!-- NOTES_START -->

- [註釋1]

<!-- NOTES_END -->
