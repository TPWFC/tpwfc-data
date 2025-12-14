# [Event Name] Complete Timeline

## Event Overview

### Basic Information

<!-- BASIC_INFO_START -->

| Item               | Data                           |
| ------------------ | ------------------------------ |
| INCIDENT_ID        | [EVENT_ID]                     |
| DATE_RANGE         | [YYYY-MM-DD]/[YYYY-MM-DD]      |
| LOCATION           | [Location]                     |
| INCIDENT_NAME      | [Event Name]                   |
| MAP                | [Map](URL)                     |
| DISASTER_LEVEL     | [LEVEL]                        |
| DURATION           | [DD:HH:MM:SS]                  |
| AFFECTED_BUILDINGS | [Count]                        |
| SOURCES            | [Source1](URL), [Source2](URL) |

<!-- BASIC_INFO_END -->

### Fire Cause

<!-- FIRE_CAUSE_START -->

[Enter fire cause here]

<!-- FIRE_CAUSE_END -->

### Severity

<!-- SEVERITY_START -->

[Enter severity description here]

<!-- SEVERITY_END -->

---

## Detailed Timeline

<!-- TIMELINE_TABLE_START -->

| Date         | Time    | Event               | Category   | Casualties | Source   | Video        | Photos       |
| ------------ | ------- | ------------------- | ---------- | ---------- | -------- | ------------ | ------------ |
| [YYYY-MM-DD] | [HH:MM] | [Event Description] | [CATEGORY] | [STATUS]   | [Source] | [Video](URL) | [Photo](URL) |

<!-- TIMELINE_TABLE_END -->

---

## Casualty Status Code Standard

### Standard Format

```bash
CATEGORY:Count(SUBCATEGORY:Count),CATEGORY:Count
```

### Status Code Definitions

| Code                    | Meaning                  | Example                  |
| ----------------------- | ------------------------ | ------------------------ |
| `STATUS_NONE`           | No casualties            | `STATUS_NONE`            |
| `DEAD:X`                | X deaths                 | `DEAD:13`                |
| `INJURED:X`             | X injured                | `INJURED:7`              |
| `MISSING:X`             | X missing                | `MISSING:279`            |
| `FIREFIGHTER_DEAD:X`    | X firefighters deceased  | `FIREFIGHTER_DEAD:1`     |
| `FIREFIGHTER_INJURED:X` | X firefighters injured   | `FIREFIGHTER_INJURED:12` |
| `REMAINING_CASES:X`     | X remaining rescue cases | `REMAINING_CASES:25`     |
| `UNIDENTIFIED:X`        | X unidentified bodies    | `UNIDENTIFIED:89`        |

### Subcategory Format

```bash
DEAD:13(ON_SITE:9,TRANSIT:4)
```

- `ON_SITE:X` = X died at scene
- `TRANSIT:X` = X died during transport

---

## Key Statistics

<!-- KEY_STATISTICS_START -->

| Item                   | Data          |
| ---------------------- | ------------- |
| FIRE_DURATION          | [DD:HH:MM:SS] |
| FIRE_LEVEL             | [LEVEL]       |
| FINAL_DEATHS           | [Count]       |
| FIREFIGHTER_CASUALTIES | [Description] |
| FIREFIGHTERS_DEPLOYED  | [Count]       |
| FIRE_VEHICLES          | [Count]       |
| HELP_CASES             | [Count]       |
| HELP_CASES_PROCESSED   | [Count]       |
| AFFECTED_BUILDINGS     | [Count]       |
| SHELTER_USERS          | [Count]       |
| MISSING_PERSONS        | [Count]       |
| UNIDENTIFIED_BODIES    | [Count]       |

<!-- KEY_STATISTICS_END -->

---

## 📝 New Event Guidelines

### Table Format Description

#### 1. Basic Table Format

Timeline events must be organized in a single table using the following columns:

```bash
| Date | Time | Event | Category | Casualties | Source | Video |
|------|------|------|------|----------|------|------|
```

#### 2. Table Boundary Markers

- **Start Marker:** `<!-- TIMELINE_TABLE_START -->`
- **End Marker:** `<!-- TIMELINE_TABLE_END -->`

These HTML comment markers are used to help automation tools identify the
timeline data range and will not affect the human reading experience.

#### 3. Date Format

- Use ISO 8601 standard format: `YYYY-MM-DD`
- Example: `2025-11-26`, `2025-11-27`, `2025-11-28`
- The date must be included in the table as the first column for easy machine
  parsing

#### 4. Category Format

- Use all uppercase English words separated by underscores: `INITIAL_REPORT`
- Categories are used to classify event types for easy data analysis and
  filtering
- Common categories:
  - `INITIAL_REPORT` - Initial fire report
  - `FIRE_ESCALATION` - Fire escalation
  - `FIREFIGHTING` - Firefighting operations
  - `SEARCH_RECOVERY` - Search and recovery operations
  - `CASUALTY_UPDATE` - Casualty statistics update
  - `RELIEF_ASSISTANCE` - Relief assistance
  - `OTHER` - Other types of events

#### 5. Time Format

- Use 24-hour format: `HH:MM`
- Example: `14:51`, `23:15`
- Time must be combined with the date to form a complete timestamp

#### 6. Event Description

- Describe the event concisely and clearly
- Avoid repetitive information
- Focus on events directly related to the fire

#### 7. Casualty Status Format

**Single Category:**

```bash
DEAD:13
INJURED:7
STATUS_NONE
```

**Multiple Categories (separated by commas):**

```bash
DEAD:13,INJURED:30
DEAD:94,INJURED:76,FIREFIGHTER_INJURED:12
```

**With Subcategories:**

```bash
DEAD:13(ON_SITE:9,TRANSIT:4)
```

#### 8. Source Citation

- **Two sources confirmed:** `HK01, SBS Australia`
- **Single source:** `HK01` or `SBS Australia`

#### 9. Video Format

- Use Markdown link format: `[Display Text](URL)`
- Example: `[Video](https://www.youtube.com/watch?v=VIDEO_ID&t=300s)`
- Leave blank to indicate no corresponding video clip for the event
- The URL should contain the complete YouTube link, optionally including the
  time parameter `&t=seconds`

#### 10. Photo Format

- Use Markdown link format: `[Display Text](URL)`
- Can separate multiple images with commas: `[Image 1](URL1), [Image 2](URL2)`
- Accepts plain URL or Markdown link
- Leave blank to indicate no images

#### 11. Adding New Status Codes

If a new status type is needed, please:

1. Use uppercase English and underscores: `NEW_STATUS:X`
2. Add definition to the "Casualty Status Code Standard" table
3. Provide clear English explanation and examples

---

## Sources

<!-- SOURCES_START -->

| SOURCE_NAME | SOURCE_TITLE | SOURCE_URL |
| ----------- | ------------ | ---------- |
| [Name]      | [Title]      | [URL]      |

<!-- SOURCES_END -->

---

## Notes

<!-- NOTES_START -->

- [Note 1]

<!-- NOTES_END -->
