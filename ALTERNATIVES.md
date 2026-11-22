# ASCEND — Offline-only implementation boundaries (build 1.4)

ASCEND is intentionally a **100% offline runtime** app. The features below are either implemented locally or have an explicit local alternative. No backend or online services are planned as part of this product specification.

| Need | Local implementation in v1.4 | Boundary / honest limitation |
|---|---|---|
| User identity/profile | Local player profile and onboarding | One browser profile/origin; no account recovery service |
| Save data | Local browser storage and schema normalization | Browser storage can be cleared by the user/OS; it is not an encrypted vault |
| Portable backup | JSON export/import and password-encrypted AES-GCM-256 backup | User must store the exported file/password safely; no automatic cross-device sync |
| Workout planning | Editable deterministic rule-based weekly templates | Not AI, not medical advice and not automatic injury-risk prediction |
| Adaptive safety | Transparent recent-session/recovery notes and user-controlled edits | Does not diagnose or prescribe loads; user decides to reduce, replace or rest |
| Exercise instruction | 105 local catalogue entries with cues and substitutions where available | No full motion-capture/video library; no professional review yet |
| Workout player | Set tracking, pause/resume, rest timer, elapsed session and local history | Browser/OS may suspend a tab; timer cannot be guaranteed while the app is closed |
| Habit/quest progression | Local quests/habits, bounded rewards and duplicate-claim protections | No guilt, streak punishment or paid recovery; custom entries remain self-reported |
| Social/guild experience | Private solo weekly challenges and local achievements | No remote friends, chat, moderation, guild server or online leaderboard by design |
| AI workout generation | Editable offline planner | No AI model or network dependency |
| AI Coach | Explicitly excluded | No Coach screen, chat, simulation or API |
| Reminders | In-app reminders and optional browser notification permission/test | Closed-app notification support varies; built-in phone alarm/calendar is the reliable fallback |
| English recording | Local audio file reference and listen-back confirmation | ASCEND does not capture microphone audio or host recordings; use the phone's recorder |
| DSA evidence | Problem IDs, topic, difficulty, time, hints, solution notes, explanation and revision tracking | Code is not executed/judged; completion is self-reported |
| GitHub/project evidence | Feature, sprint duration, commit URL/hash and manual push confirmation | No GitHub token/API; app cannot inspect the repository or verify a push |
| Flashcards/revision | 24 bundled starter cards, custom local cards and spaced review | User maintains their own decks; no cloud deck catalogue |
| Learning courses | 12 bundled text lessons with quizzes | No streaming videos, external learning content or remote content feed |
| Story/characters | Six original chapters, three original SVG portraits and Aster SVG map | No commissioned animation, voice acting or full production art pipeline |
| Analytics | Local charts/history and Part 27 totals | No telemetry or cross-device aggregation; health metrics are descriptive, not clinical |
| Support/feedback | Local feedback notes included in backup for user-controlled sharing | No ticket inbox or live support service; avoid putting secrets/medical details in notes |
| Payments/ads | None | No premium tier, ads, subscriptions or purchases in this offline build |
| Initial install | Static PWA assets and raster/SVG app icons can be cached by the service worker | First download/install requires a local file transfer or one-time access to the static host |
| App updates | Versioned same-origin service-worker cache | New versions must be downloaded while connected to the static host or transferred locally |
| Security | No remote collection; validated imports; encrypted portable backup | Live browser storage is not encrypted at rest; no independent security audit |
| Accessibility | Responsive layout, keyboard focus, larger text, high contrast and reduced motion | Full WCAG and screen-reader review plus assistive-device testing remain external QA tasks |

## Out-of-scope by design

- Backend, database server, authentication server, account service and cloud sync.
- Runtime internet APIs, remote analytics/telemetry, ads, payments or subscriptions.
- Online social, multiplayer, moderation, guild servers or leaderboards.
- AI Coach or online AI workout planner.
- Punitive streaks, guilt messaging, artificial scarcity and coercive retention.

## External tasks that code alone cannot honestly complete

These require a real person/device or qualified reviewer; the app includes practical safeguards but does not pretend to have performed them:

1. Test install, refresh, offline launch, storage persistence and backup restore on the target Android/desktop browsers and devices.
2. Obtain qualified fitness-professional review of exercise instructions, program templates, contraindications and substitutions.
3. Conduct a full screen-reader/WCAG and assistive-technology review.
4. Conduct an independent security/privacy review, including browser storage and backup handling.
5. Run usability sessions with real users and validate whether progress supports sustainable real-world fitness.
6. Commission additional original animation, illustration and voice assets if the user wants production-level anime presentation. Current bundled SVG/text assets are the functional offline alternative.

No online replacement is suggested for any of these; they are manual review/quality tasks, not missing server features.
