# [事件名称]完整时间线

## 事件概述

### 基本资料

<!-- BASIC_INFO_START -->

| 项目               | 资料                           |
| ------------------ | ------------------------------ |
| INCIDENT_ID        | [EVENT_ID]                     |
| DATE_RANGE         | [YYYY-MM-DD]/[YYYY-MM-DD]      |
| LOCATION           | [地点]                         |
| INCIDENT_NAME      | [事件名称]                     |
| MAP                | [地图](URL)                    |
| DISASTER_LEVEL     | [LEVEL]                        |
| DURATION           | [DD:HH:MM:SS]                  |
| AFFECTED_BUILDINGS | [数量]                         |
| SOURCES            | [Source1](URL), [Source2](URL) |

<!-- BASIC_INFO_END -->

### 起火原因

<!-- FIRE_CAUSE_START -->

[在此输入起火原因]

<!-- FIRE_CAUSE_END -->

### 灾情严重性

<!-- SEVERITY_START -->

[在此输入灾情严重性描述]

<!-- SEVERITY_END -->

---

## 详细时间线

<!-- TIMELINE_TABLE_START -->

| 日期         | 时间    | 事件       | 类别       | 死伤状况 | 来源     | 影片        | 图片        |
| ------------ | ------- | ---------- | ---------- | -------- | -------- | ----------- | ----------- |
| [YYYY-MM-DD] | [HH:MM] | [事件描述] | [CATEGORY] | [STATUS] | [Source] | [影片](URL) | [图片](URL) |

<!-- TIMELINE_TABLE_END -->

---

## 死伤状况状态代码标准

### 标准格式

```bash
CATEGORY:数量(子类别:数量),CATEGORY:数量
```

### 状况代码定义

| 代码                    | 意义            | 范例                     |
| ----------------------- | --------------- | ------------------------ |
| `STATUS_NONE`           | 无人员伤亡      | `STATUS_NONE`            |
| `DEAD:X`                | 死亡X人         | `DEAD:13`                |
| `INJURED:X`             | 受伤X人         | `INJURED:7`              |
| `MISSING:X`             | 失踪X人         | `MISSING:279`            |
| `FIREFIGHTER_DEAD:X`    | 消防员殉职X人   | `FIREFIGHTER_DEAD:1`     |
| `FIREFIGHTER_INJURED:X` | 消防员受伤X人   | `FIREFIGHTER_INJURED:12` |
| `REMAINING_CASES:X`     | 余下救援个案X宗 | `REMAINING_CASES:25`     |
| `UNIDENTIFIED:X`        | 未能辨认遗体X具 | `UNIDENTIFIED:89`        |

### 子类别格式

```bash
DEAD:13(ON_SITE:9,TRANSIT:4)
```

- `ON_SITE:X` = 现场死亡X人
- `TRANSIT:X` = 送院途中死亡X人

---

## 关键统计数据

<!-- KEY_STATISTICS_START -->

| 项目                   | 数据          |
| ---------------------- | ------------- |
| FIRE_DURATION          | [DD:HH:MM:SS] |
| FIRE_LEVEL             | [LEVEL]       |
| FINAL_DEATHS           | [数量]        |
| FIREFIGHTER_CASUALTIES | [描述]        |
| FIREFIGHTERS_DEPLOYED  | [数量]        |
| FIRE_VEHICLES          | [数量]        |
| HELP_CASES             | [数量]        |
| HELP_CASES_PROCESSED   | [数量]        |
| AFFECTED_BUILDINGS     | [数量]        |
| SHELTER_USERS          | [数量]        |
| MISSING_PERSONS        | [数量]        |
| UNIDENTIFIED_BODIES    | [数量]        |

<!-- KEY_STATISTICS_END -->

---

## 📝 新增事件指南

### 表格格式说明

#### 1. 基本表格格式

时间线事件必须以单一表格形式组织，使用以下栏位：

```bash
| 日期 | 时间 | 事件 | 类别 | 死伤状况 | 来源 | 影片 |
|------|------|------|------|----------|------|------|
```

#### 2. 表格边界标记

- **开始标记：** `<!-- TIMELINE_TABLE_START -->`
- **结束标记：** `<!-- TIMELINE_TABLE_END -->`

这些HTML注释标记用于帮助自动化工具识别时间线数据范围，不会影响人类阅读体验。

#### 3. 日期格式

- 使用ISO 8601标准格式：`YYYY-MM-DD`
- 例如：`2025-11-26`、`2025-11-27`、`2025-11-28`
- 日期必须包含在表格中作为第一栏，便于机器解析

#### 4. 类别格式

- 使用全大写英文单词，以下划线分隔：`INITIAL_REPORT`
- 类别用于分类事件类型，便于数据分析和筛选
- 常见类别：
  - `INITIAL_REPORT` - 火警初报
  - `FIRE_ESCALATION` - 火警升级
  - `FIREFIGHTING` - 消防灭火行动
  - `SEARCH_RECOVERY` - 搜索救援行动
  - `CASUALTY_UPDATE` - 伤亡统计更新
  - `RELIEF_ASSISTANCE` - 救灾援助
  - `OTHER` - 其他类型事件

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

| SOURCE_ID | SOURCE_NAME | SOURCE_TITLE | SOURCE_URL |
| --------- | ----------- | ------------ | ---------- |
| [ID]      | [Name]      | [Title]      | [URL]      |

<!-- SOURCES_END -->

---

## 註釋

<!-- NOTES_START -->

- [註釋1]

<!-- NOTES_END -->
