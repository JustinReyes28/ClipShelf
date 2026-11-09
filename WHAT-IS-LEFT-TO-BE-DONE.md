# SourceSpool — What is Left to be Done

*Last updated: 9 November 2026. Workspace: `JustinReyes28/sourcespool`.*

This document provides a comprehensive inventory of completed milestones, in-progress items, owner-specific actions, and planned future phases.

---

## 1. Executive Summary & Status Overview

| Phase / Area | Scope | Current Status | Next Action |
| :--- | :--- | :--- | :--- |
| **Phase 1: Product & Differentiation** | Job definition, product brief, provenance register, user stories | **Complete** (solo-validation gate) | User interviews (5 creators/students) remain deferred. |
| **Phase 2: Design, Architecture & GitHub** | React/Ink terminal UI scaffold, architecture spec, GitHub repo & issues #1–#4 | **Complete** | Baseline scaffold checks and design simulator intact. |
| **Phase 3: Production Implementation** | Real yt-dlp & FFmpeg saves, SHA-256 hashing, atomic locking, crash journals, duplicate choices, metadata import/export | **Complete** | Production features implemented and verified. |
| **Phase 4: Validation & v0.1.0 GitHub Release** | Windows CI, terminal ANSI verification, production captures, v0.1.0 tag & release | **Complete** | [v0.1.0 GitHub Release](https://github.com/JustinReyes28/sourcespool/releases/tag/v0.1.0) published. |
| **Phase 5: Owner Posting Kit** | v0.1.0 captions, 7 PNG renders, 30s video, posting-kit ZIP | **Complete** (kit delivered) | Actual social posting is owner's responsibility. |
| **Phase 5.5: Easy Installation & npm Release** | Distributable CLI package, `%LOCALAPPDATA%` managed tools, zero-source launch (`npx sourcespool`), Node 22+ support | **Complete (Published & Verified)** | [npm sourcespool@0.2.1](https://www.npmjs.com/package/sourcespool) & [GitHub Release v0.2.1](https://github.com/JustinReyes28/sourcespool/releases/tag/v0.2.1) are live. |
| **Phase 6: Android APK Support** | Standalone arm64 APK, Jetpack Compose UI, Room DB, background download engine, Windows interchange | **Planned (Not Started)** | Milestone 6.1 (engine spike, licensing, 16 KB page-size proof). |

---

## 2. Release Status (Phase 5.5 Wrap-Up)

### 2.1 Public npm Release (`sourcespool@0.2.1`)
* **Status**: **Live on npm**
  - Registry URL: [https://www.npmjs.com/package/sourcespool](https://www.npmjs.com/package/sourcespool)
  - Dist-tag: `latest` -> `0.2.1`
  - Tarball: 36,479 bytes, SHA-256: `20b9ca489f40994258268cee862eacd721a0e4ddd947c61572cdf3f9d294aa61`
  - Install commands:
    ```powershell
    npx sourcespool@latest
    # or
    npm install -g sourcespool@latest
    ```

### 2.2 GitHub Release (`v0.2.1`)
* **Status**: **Published on GitHub**
  - Release URL: [https://github.com/JustinReyes28/sourcespool/releases/tag/v0.2.1](https://github.com/JustinReyes28/sourcespool/releases/tag/v0.2.1)
  - Tag: `v0.2.1` synced to local Git repository.
  - Attached assets: `sourcespool-0.2.1.tgz`, `runtime-fix-SHA256SUMS.txt`.

### 2.3 Social Captions and Launch Kit
* **Status**: **Refreshed and Ready**
  - Updated [`docs/launch-kit/README.md`](docs/launch-kit/README.md)
  - Updated [`docs/launch-kit/general.txt`](docs/launch-kit/general.txt)
  - Updated [`docs/launch-kit/x.txt`](docs/launch-kit/x.txt)
  - Updated [`docs/launch-kit/reddit.txt`](docs/launch-kit/reddit.txt)
  - Updated [`docs/launch-kit/linkedin.txt`](docs/launch-kit/linkedin.txt)
  All captions reflect `v0.2.1` and `Node 22 or newer (Node 24 LTS recommended)`.

---

## 3. What is Left to be Done

### 3.1 Owner Actions (Manual / External)
1. **Social Media Announcement**:
   - Posting the prepared launch captions and images/video to Reddit (e.g., r/commandline, r/selfhosted), X, and LinkedIn.
   - Text files and alt text instructions are ready in `docs/launch-kit/`.

### 3.2 Commit Documentation Updates to GitHub (Optional)
- Uncommitted local documentation changes:
  - Updated captions in `docs/launch-kit/`.
  - Pass `safe.directory` in `scripts/package-release.mjs`.
  - Added roadmap tracker `WHAT-IS-LEFT-TO-BE-DONE.md`.

### 3.3 Phase 6: Android APK Support (Major Upcoming Phase)

*Plan Reference: [PLAN-06-Android-Support.md](PLAN-06-Android-Support.md)*  
*Status: **Planned; Implementation Not Started***

Phase 6 delivers an installable, standalone phone app saving video/audio references with offline search and Windows metadata interchange.

#### Milestone 6.1 — Engine Proof & Dependency Selection
- [ ] Choose and prove the Android yt-dlp/Python + FFmpeg engine (e.g., `youtubedl-android` wrapper).
- [ ] Resolve GPL-3.0 licensing, notices, and corresponding-source obligations (do not represent a GPL bundle as MIT-only).
- [ ] Package an Android-compatible JavaScript runtime for yt-dlp EJS requirements.
- [ ] Verify 16 KB page-size compatibility on arm64 devices.
- [ ] Prove inspection, download, audio/video merge, hashing, and clean cancellation on a physical phone.

#### Milestone 6.2 — Native Library & Android Sharing
- [ ] Initialize `android/` Gradle project with Kotlin & Jetpack Compose.
- [ ] Build touch UI: Library/Search, Add/Review, Collections, Details, Settings.
- [ ] Implement `ACTION_SEND` intent receiver to accept shared URLs into a review draft.
- [ ] Integrate Room database for catalogue persistence.

#### Milestone 6.3 — Reliable Downloads, Storage & Data Controls
- [ ] App-private storage for live media, staging, and atomic commit journals.
- [ ] Storage Access Framework (SAF) pickers for metadata and media backup/export.
- [ ] `FileProvider` integration for opening saved media.
- [ ] User-initiated background transfer jobs (API 34+) and foreground service.
- [ ] Data controls: unmetered-only default, per-job cellular toggle, payload ceilings, duplicate warnings.

#### Milestone 6.4 — Collection Parity & Windows Interchange
- [ ] Validate shared domain logic (naming, tagging, duplicate detection) against `schemaVersion: 1`.
- [ ] Implement "Restore Media" action for re-linking media to imported catalogues.
- [ ] Round-trip validation: Windows → Android → Windows metadata interchange without corruption.

#### Milestone 6.5 — Qualification & Signed APK Release
- [ ] Device testing on physical arm64 hardware (Android 10+ minimum).
- [ ] Live-site smoke verification under a strict 10 MB payload budget.
- [ ] Build and sign release arm64-v8a APK.
- [ ] Publish GitHub release with tag `android-v0.1.0-alpha.1` with accurate compatibility notes.

---

## 4. Deferred Work & Long-Term Items

1. **User Problem Validation Interviews**:
   - 5 structured 20-minute interviews with creators/students as outlined in `docs/research/problem-validation.md`.
   - *Status*: Explicitly deferred under the owner-approved solo-validation gate.
2. **Issue Triage & Feedback Collection**:
   - Tracking incoming GitHub issues, community reports, and feature requests on `JustinReyes28/sourcespool`.
3. **Cross-Platform CLI**:
   - macOS / Linux / Windows ARM64 support is currently out of scope and would require separate qualification.
