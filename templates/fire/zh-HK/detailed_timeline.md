# {{ EVENT_NAME }} - 詳細行動與調查時間線

本文件記錄由火警發生首日至今的詳細行動日誌。

## YYYY年MM月

### YYYY-MM-DD (星期X) - {{ DAY_DESCRIPTION }}

<!-- PHASE_START -->

#### 階段概述

<!-- PHASE_INFO_START -->

| 項目     | 資料                 |
| -------- | -------------------- |
| 階段名稱 | {{ PHASE_NAME }}     |
| 階段類別 | {{ PHASE_CATEGORY }} |
| 日期範圍 | {{ DATE_RANGE }}     |
| 狀態     | {{ STATUS }}         |

<!-- PHASE_INFO_END -->

<!-- PHASE_DESCRIPTION_START -->

**主要階段：** {{ PHASE_MAIN_STAGE }}

{{ PHASE_DESCRIPTION }}

<!-- PHASE_DESCRIPTION_END -->

<!-- TIMELINE_TABLE_START -->

| 日期       | 時間  | 事件        | 類別           | 狀態/備註  | 來源            | 影片        | 圖片        |
| ---------- | ----- | ----------- | -------------- | ---------- | --------------- | ----------- | ----------- |
| YYYY-MM-DD | HH:MM | {{ EVENT }} | {{ CATEGORY }} | {{ NOTE }} | [來源名稱](URL) | [影片](URL) | [圖片](URL) |

<!-- TIMELINE_TABLE_END -->
<!-- PHASE_END -->

---

## 📅 長期事件追蹤

<!-- LONG_TERM_TRACKING_START -->

| 預計日期   | 類別           | 事件        | 狀態         | 備註       |
| ---------- | -------------- | ----------- | ------------ | ---------- |
| YYYY-MM-DD | {{ CATEGORY }} | {{ EVENT }} | {{ STATUS }} | {{ NOTE }} |

<!-- LONG_TERM_TRACKING_END -->

<!-- NOTES_START -->

- {{ NOTES }}

<!-- NOTES_END -->

## 建議 ID 與類別參考 (ID & Category Reference)

### 階段類別 (Phase Categories)

- `PHASE_OUTBREAK` (爆發)
- `PHASE_ESCALATION` (升級)
- `PHASE_RESCUE` (救援)
- `PHASE_CASUALTY_COUNT` (傷亡統計)
- `PHASE_EXTINGUISHMENT` (撲滅)
- `PHASE_INVESTIGATION` (調查)
- `PHASE_AFTERMATH` (善後)
- `PHASE_MOURNING` (哀悼)
- `PHASE_RECOVERY` (復原)
- `PHASE_LEGAL` (法律程序)

### 事件類別 (Event Categories)

- `INITIAL_REPORT` (初報)
- `FIREFIGHTING` (滅火)
- `FIRE_ESCALATION` (升級)
- `SEARCH_RECOVERY` (搜救)
- `CASUALTY_UPDATE` (傷亡更新)
- `GOV_ANNOUNCEMENT` (政府公佈)
- `POLICE_ACTION` (警方行動)
- `INVESTIGATION` (調查)
- `MOURNING` (哀悼)
- `INQUIRY` (研訊)
- `INSPECTION` (巡查)
- `LEGAL` (法律)
- `RELIEF` (賑災)
- `EVACUATION` (疏散)
- `MEDIA_BRIEFING` (簡報會)

### 時間格式參考 (Time Format Reference)

- `HH:MM` (標準時間 24小時制)
- `TIME_ALL_DAY` (全日/整天)
- `TIME_ONGOING` (持續進行中)

### 長期追蹤類別 (Long-term Categories)

- `LEGAL_PROCEEDINGS` (法律訴訟)
- `RECONSTRUCTION` (重建與維修)
- `POLICY_REVIEW` (政策檢討)
- `MEMORIAL` (紀念活動)
- `COMPENSATION` (賠償)
