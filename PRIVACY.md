# Privacy

## Summary

Aether is a client-side study timer and tracker. In this version, study records are saved in the browser's local storage. The application does not include a project-owned backend, account registration, cloud synchronization, or analytics integration.

## Information stored locally

The application writes data to the browser's `localStorage` key:

```text
aether_study_state_v2
```

It can also read the legacy key `aether_study_state_v1`.

The stored application state can include:

- Scholar display name.
- Current subject and custom subject list.
- Theme and sound preferences.
- Current streak and the date of the last study activity.
- Last subject and last-study timestamp/duration.
- Saved session records, up to 100 entries.
- Today's study time, grouped by subject.

The saved session record fields include an identifier, scholar name, subject, duration in seconds, streak value, timestamp, and session mode.

## Network requests

The current HTML loads two third-party frontend resources:

- Tailwind CSS from `cdn.tailwindcss.com`.
- Lucide icons from `unpkg.com`.

The application source contains no `fetch`, `XMLHttpRequest`, WebSocket, `sendBeacon`, project API, or analytics integration for transmitting study records. The third-party CDNs still receive normal browser requests for their assets and may process request metadata according to their own policies.

## User control

- Data stays in the browser profile and site origin where Aether is used.
- Data is not automatically synchronized across browsers or devices.
- Clearing site data/local storage in the browser can permanently remove the saved data.
- The application provides record-level deletion and archive-clearing controls, but does not yet provide a complete export/restore or one-click erase-all-data feature.

## Important limitation

Aether measures time while a tracking mode is running. It cannot determine whether a person is genuinely focused or studying. Study records are self-reported activity measurements, not verified behavioral or academic outcomes.

This document describes the current repository implementation. Review it again whenever new dependencies, network integrations, or storage behavior are introduced.
