# Contributing

Thank you for your interest in improving Aether.

## Before making changes

- Keep the interface focused, calm, and accessible.
- Prefer native browser capabilities and small dependencies.
- Do not add a backend, account system, analytics, or data transmission without explicit project-owner approval.
- Preserve the existing local-storage key and data compatibility unless a migration is deliberately designed and documented.
- Never add fabricated study statistics or fake social profiles.

## Development

Aether is currently a static HTML/CSS/JavaScript application. Run it locally with:

```bash
python -m http.server 8000
```

Open `http://localhost:8000` in a browser.

## Pull request checklist

- [ ] Existing timer, stopwatch, and clock behavior still works.
- [ ] Session saving and record management still work.
- [ ] Daily statistics and streak calculations are not silently changed.
- [ ] Existing `localStorage` data remains compatible.
- [ ] Desktop, tablet, and mobile layouts are checked.
- [ ] Keyboard navigation and visible focus states are preserved.
- [ ] No fake users, fake metrics, or unrequested tracking were introduced.
- [ ] Changes and any known limitations are documented.

Please describe the user problem addressed, the implementation, and how the change was tested.
