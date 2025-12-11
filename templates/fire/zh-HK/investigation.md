# {{ EVENT_NAME }} - 深入案件分析報告

## 案件概覽

| 項目         | 資料              |
| ------------ | ----------------- |
| **案件編號** | {{ INCIDENT_ID }} |
| **調查狀態** | 進行中 / 已結案   |
| **主責部門** | {{ DEPARTMENTS }} |
| **起火位置** | {{ LOCATION }}    |
| **關鍵證物** | {{ EVIDENCE }}    |

---

## 1. 起火原因深入分析

### 1.1 物理起火點

<!-- ANALYSIS_START -->

{{ ANALYSIS_CONTENT }}

- **發火源:** {{ IGNITION_SOURCE }}
- **助燃物:** {{ FUEL_SOURCE }}
- **火勢蔓延路徑:** {{ SPREAD_PATTERN }}

<!-- ANALYSIS_END -->

### 1.2 工程違規與監管缺失

<!-- REGULATORY_START -->

{{ REGULATORY_CONTENT }}

<!-- REGULATORY_END -->

---

## 2. 刑事調查進展

### 2.1 被捕人士

| DATE       | IDENTITY       | OFFENSE       | STATUS       |
| ---------- | -------------- | ------------- | ------------ |
| YYYY-MM-DD | {{ IDENTITY }} | {{ OFFENSE }} | {{ STATUS }} |

### 2.2 搜證工作

- {{ EVIDENCE_WORK }}

---

## 3. 建築結構與安全評估

### 3.1 {{ BUILDING_NAME }}

- **損毀程度：** {{ DAMAGE_LEVEL }}
- **結構完整性：** {{ STRUCTURAL_INTEGRITY }}
- **居住狀態：** {{ OCCUPANCY_STATUS }}

---

## 4. 責任歸屬與法律訴訟

- **民事索償：** {{ CIVIL_CLAIMS }}
- **保險理賠：** {{ INSURANCE }}

<!-- NOTES_START -->

- {{ NOTES }}

<!-- NOTES_END -->
