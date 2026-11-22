# ASCEND — Offline Anime Fitness RPG (build 1.4)

ASCEND is an original anime-inspired fitness RPG combined with a private personal execution system. It is designed to run locally in a browser/PWA and keep user records on the device.

## Non-negotiable product scope

- **Offline runtime:** no backend, account server, cloud database, remote API, analytics beacon, social server or network leaderboard.
- **No AI Coach:** intentionally excluded at the user's request.
- **Original IP:** ASCEND's Aster setting, characters, writing and SVG assets are original project material; do not add third-party copyrighted game assets.
- **User agency:** no punitive streak resets, guilt copy, forced daily login, fake scarcity or paid recovery.
- **Local ownership:** workout, RPG, learning and Part 27 records remain in the current browser profile/origin until the user exports or deletes them.

GitHub Pages may be used to distribute the static app. It is not a runtime backend. The first download/visit requires access to the hosted files (or a local copy); after the service worker has cached the app shell and assets, normal use can continue offline. A fully disconnected device must receive the app files by a local transfer/install method first.

## Included in build 1.4

- Responsive dark anime-inspired UI with desktop navigation and mobile bottom navigation.
- Local profile, onboarding, XP/levels/ranks, achievements, cosmetics and optional measurements.
- **105 exercise entries** with movement group, equipment, level, cues and available easier/harder substitutions.
- Offline rule-based weekly program builder for goal, experience, equipment, training days and session length; editable days, movements, sets and reps.
- Guided workout player with set completion, load tracking, pause/resume, rest timer, saved history and synchronization to the same day's Part 27 workout record.
- Daily quests, custom quests, habits with editable day-of-week schedules (unscheduled days are neutral), recovery check-ins and private solo weekly challenges.
- Four skill branches with nine unlock nodes; three boss trials; six original story chapters; three original SVG character portraits and an original Aster map.
- Offline Spellbook / Academy with **12 text lessons and quizzes**.
- **24 starter flashcards**, custom cards and spaced review without an internet connection.
- Local analytics, workout history, optional body measurements and career milestones.
- Part 27 single daily record: wake-up, phone-free start, safe commute learning, detailed two-question DSA log/revision, DBMS → OS → CN rotation, build sprint/commit reference, English listen-back record, workout/recovery, night review/top three, Exam Crunch Mode, recovery flow, Sunday weekly review and career milestones.
- JSON backup/restore and password-encrypted portable backups (AES-GCM-256; PBKDF2-SHA-256 key derivation).
- Unit conversion, larger text, high contrast, reduced motion, in-app reminders and optional browser notification permission/test.
- PWA manifest with SVG and raster 180/192/512px icons, locally bundled assets and versioned service-worker cache.

## Run locally

Requirements: a current desktop browser and Python 3 (for a local static HTTP server).

**Windows:** double-click `run-local.bat`, then open `http://localhost:8000`.

**Linux / macOS:** run `./run-local.sh`, then open `http://localhost:8000`.

**Manual alternative:** from this folder run `python -m http.server 8000` and open `http://localhost:8000`.

Use HTTP localhost rather than opening `index.html` directly so that the service worker/PWA features can register. The app itself makes no runtime requests to external domains. Its service worker only handles same-origin static app files for caching and updates.

## GitHub Pages distribution

1. Extract the ZIP.
2. Open the `ascend-rpg` folder.
3. Upload the *contents* of that folder to the repository root so `index.html` is at the root.
4. In GitHub, open **Settings → Pages** and select deployment from the `main` branch and `/(root)`.
5. Open the published static site once while online so the browser can download/cache the PWA shell and assets. Then test airplane mode.

GitHub Pages is only a static distribution host. No app data is sent to GitHub by ASCEND.

## Data, privacy and backup

- Data is stored locally in the browser profile for this site/origin. It does not automatically move to another browser or device.
- Export a normal JSON backup for portability, or use **Export encrypted backup** and set a strong password. The encrypted backup uses AES-GCM-256 with a PBKDF2-SHA-256-derived key (250,000 iterations), a random salt and a random IV.
- Import validates the backup before applying it; wrong-password/decryption failures should leave the current profile unchanged.
- Browser local storage/IndexedDB is **not itself an encrypted vault**. The encrypted option protects the exported backup file, not the live browser database. Do not use a shared/untrusted device for sensitive records.
- Clearing browser site data, uninstalling a browser profile or losing the device can remove local records. Make backups regularly and before a reset/device change.
- No telemetry, remote analytics, login, sync, payments, ads, cloud storage or social network are included.

## Offline boundaries and practical alternatives

- Closed-app reminders vary by browser/OS; use the phone's built-in alarm/calendar as a dependable local fallback. App-open reminders are available.
- Audio is not recorded by ASCEND. Use the device's local voice recorder and enter a private file reference/listen-back confirmation.
- DSA solutions and Git commits are user-entered evidence; the app does not execute code or independently verify GitHub.
- Solo challenges replace server-based guilds/leaderboards.
- Rule-based templates replace AI workout generation. They are transparent, editable starting points, not medical prescriptions or automatic injury detection.
- Original SVG portraits/map and text story/lessons provide a bundled visual/content foundation. Commissioned full animation, voice acting and large illustration packs are not included.

See [`ALTERNATIVES.md`](ALTERNATIVES.md), [`IMPLEMENTATION_STATUS.md`](IMPLEMENTATION_STATUS.md) and [`REMAINING_VALIDATION.md`](REMAINING_VALIDATION.md) for exact scope and limitations.

## Tests

From this folder, run:

```sh
node --check app.js
node --check tests/smoke.js
node tests/smoke.js
```

The Node smoke suite uses a test DOM/VM harness. It tests data rules, 135 program combinations, page render functions, migration/backup behavior, encrypted backup wrong/correct password paths, challenge reward duplication, DSA revision, weekly review, exam rules, offline asset inventory and corruption recovery. It is **not** a full graphical browser test or a substitute for real Android/iOS testing.

## Safety and limitations

ASCEND is a general activity organizer, not a medical assessment, diagnosis, rehabilitation protocol or individualized prescription. Exercise catalogue instructions are general cues and have not been professionally reviewed. Select movements appropriate to your current abilities and equipment; keep movements comfortable; stop if pain or concerning symptoms occur. Seek qualified professional advice where needed.

The current build has not undergone a formal WCAG/screen-reader audit, independent security audit, professional exercise review, user research study or full real-device QA. Do not interpret a passing smoke test as production certification.
