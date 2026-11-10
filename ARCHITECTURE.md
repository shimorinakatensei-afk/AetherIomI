# Architecture and data model

## Overview

Aether is currently delivered as one static `index.html` file containing:

- Semantic HTML for the application layout and overlays.
- CSS custom properties, responsive rules, and component styling.
- Vanilla JavaScript for timer behavior, study tracking, rendering, and persistence.

There is no server-side application, database service, authentication layer, or build pipeline in this repository.

## Main application areas

1. **Navigation and modes** — timer, stopwatch, and clock selection, plus sound, theme, records, and fullscreen controls.
2. **Focus workspace** — duration presets, custom-duration slider, progress indicator, and start/pause/reset actions.
3. **Subject selection** — current subject and quick-select subject list.
4. **Personal summary** — scholar name, streak, last subject, and last-study information.
5. **Records archive** — saved study sessions and archive actions.
6. **Daily summary** — today's accumulated focus time and subject breakdown.

## Persistence

The current storage key is `aether_study_state_v2`. The application attempts to read `aether_study_state_v1` as a legacy fallback.

The persisted object contains these main properties:

| Property | Purpose |
|---|---|
| `scholarName` | Display name for the local profile |
| `currentSubject` | Selected study subject |
| `soundEnabled` | Sound preference |
| `theme`, `themeName` | Selected appearance theme |
| `customSubjects` | User's quick-select subject list |
| `streakCount` | Current study streak |
| `lastStudyDateKey` | Local date key used for streak calculation |
| `lastSubject` | Most recently tracked subject |
| `lastStudyTimestamp` | Timestamp of most recent study activity |
| `lastStudyDurationSec` | Duration metadata for the latest activity |
| `savedRecords` | Saved session archive (maximum 100 entries) |
| `todayKey` | Local date associated with today's totals |
| `subjectSecondsToday` | Today’s accumulated seconds grouped by subject |

A saved session record includes `id`, `name`, `subject`, `durationSec`, `streak`, `timestamp`, and `mode`.

## Tracking semantics

- The timer, stopwatch, and clock/logging mode use the same focus-time tracking path while active.
- Daily subject totals are attributed on each timer tick. A saved session archive record uses the subject selected at save time; changing subjects mid-session can therefore cause the archive's single subject label to differ from the daily subject breakdown.
- Study time is accumulated against the currently selected subject.
- Timer completion saves the actual tracked duration for the session.
- Manual save requires at least five seconds of tracked time.
- The study streak advances when study activity is registered for a local calendar day.
- The daily subject totals reset when a new local day is encountered during tracking.

## Important design constraints

- Do not introduce fake study data or pretend a local leaderboard is a real shared service.
- Do not transmit the stored profile or session records to an external service without explicit owner approval and a clear privacy update.
- If the storage schema changes, add a migration path and update this document.
- In-progress timer state is not stored as a resumable timer across page reloads.
