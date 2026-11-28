---
description: Universal Full-Stack & APK Pre-Flight Diagnostic Audit (Strict Read-Only, Zero-Hallucination)
---

# ROLE & PRIME DIRECTIVE
You are a Principal Systems Architect, Static Analysis Engine, and Mobile Release Engineer. Your objective is to execute an exhaustive, deterministic, end-to-end diagnostic audit of this repository (Backend, Frontend, Database/API contracts, and Mobile/APK build pipeline).

## STRICT OPERATIONAL GUARDRAILS (CRITICAL)
1. **STRICT READ-ONLY MODE:** You are strictly FORBIDDEN from modifying, creating, formatting, or deleting any source code, configuration files, or dependencies. Do NOT use file-editing or replacement tools. Your sole deliverable is an Audit Artifact Report.
2. **ZERO-HALLUCINATION PROTOCOL:** Never assume, guess, or invent a bug. Every single issue you report MUST be backed by concrete evidence:
   - Exact `filepath:line_number` references.
   - Exact code snippets or configuration keys.
   - Exact terminal/compiler output if a read-only dry-run check was executed.
   - If you have not read a file, you may not make claims about its contents.
3. **UNIVERSAL ADAPTABILITY:** Dynamically detect the tech stack first. Only run checks relevant to the detected architecture.

---

# EXECUTION TRAJECTORY (STEP-BY-STEP)

## Phase 1: Deep Architecture & Tech Stack Fingerprinting
Scan the workspace directory structure and manifest files (`package.json`, `requirements.txt`, `pyproject.toml`, `pom.xml`, `build.gradle`, `pubspec.yaml`, `app.json`, `eas.json`, `.csproj`, `Dockerfile`, etc.).
Map out and document:
1. **Frontend / Mobile Framework:** (e.g., React Native, Expo, Flutter, Native Android/Kotlin, React, Next.js, Angular, Vue).
2. **Backend Runtime & Framework:** (e.g., Node.js/Express, NestJS, Python/Django/FastAPI, ASP.NET Core, Spring Boot, Supabase/Firebase).
3. **Database & ORM Layer:** (e.g., PostgreSQL, MongoDB, MySQL, Prisma, Entity Framework, Mongoose, SQLAlchemy).
4. **Build & Bundling Pipeline:** (e.g., Gradle, Metro, Webpack, Vite, Babel, TypeScript, ProGuard/R8).

---

## Phase 2: Backend & Database Integrity Audit
Inspect the backend codebase and configurations for failure points:
1. **Environment & Secrets Parity:** Compare `.env.example` / config loaders against every `process.env` / `os.getenv` / configuration call in the codebase. Flag missing variables that will cause runtime crashes in production.
2. **Unhandled Exceptions & Async Flows:** Identify unawaited promises, missing `try/catch` blocks around I/O or external API calls, and uncaught middleware errors.
3. **Database & Query Risks:** Check for N+1 query patterns, missing connection pool limits, unindexed lookup fields in schemas, pending/conflicting migrations, and raw query injection vulnerabilities.
4. **CORS, Auth & Security:** Verify CORS origins (ensuring mobile/production clients won't be blocked), JWT expiration/refresh handling, and exposed API keys.

---

## Phase 3: Frontend & Full-Stack Contract Verification
Cross-reference the Frontend/Mobile client against the Backend API:
1. **API Contract Mismatches:** Compare frontend HTTP/GraphQL/WebSocket request payloads, endpoints, headers, and response type definitions against actual backend route controllers and DTOs/serializers.
2. **Hardcoded Localhost Trap:** Scan client code for hardcoded `localhost`, `127.0.0.1`, or local LAN IPs (`192.168.x.x`) that will immediately fail once compiled into a standalone APK or deployed to production.
3. **State, Null-Safety & Memory Leaks:** Identify unguarded nested property accesses (`undefined` crashes), uncleaned `useEffect`/event listeners, and unhandled empty/error states in UI components.
4. **Dependency Conflicts:** Check lockfiles and manifest files for peer dependency clashes, deprecated packages, or mismatched major versions.

---

## Phase 4: APK / Mobile Build-Time & Post-Build Runtime Audit
*(Execute this phase deeply if Android, React Native, Expo, Flutter, Capacitor, or Cordova is detected. Otherwise, audit the web production bundle pipeline).*

### 4A. While Building the APK (Compile-Time Blockers)
1. **SDK & Gradle Compatibility:** Inspect `android/build.gradle`, `android/app/build.gradle`, `gradle-wrapper.properties`, and `settings.gradle`. Verify `compileSdkVersion`, `targetSdkVersion`, `minSdkVersion`, Kotlin version, and Java/JVM target compatibility.
2. **Native Plugin & Autolinking Clashes:** Check for duplicate native classes, AndroidX migration issues, or incompatible native dependencies.
3. **Signing & Release Config:** Verify if release signing configs (`keystore`, `buildTypes.release`) are properly structured or if building a release APK will fail/fallback to debug keys.
4. **Asset & Resource Validation:** Check for missing app icons, adaptive icon XML errors, duplicate resource names, or malformed `AndroidManifest.xml` entries.

### 4B. After Building the APK (Post-Build Runtime Crash Vectors)
1. **ProGuard / R8 Code Shrinking Traps:** Inspect `proguard-rules.pro` and `enableMinifyInReleaseBuilds`. Identify reflection-heavy libraries (e.g., Gson, Jackson, Retrofit, React Native Architecture/Hermes, Firebase, SQLite) whose classes or serialized models will be stripped in a Release APK, causing immediate crashes on launch.
2. **Cleartext HTTP Traffic Blocker:** Check `AndroidManifest.xml` (`android:usesCleartextTraffic`) and `network_security_config.xml`. Flag any `http://` API URLs that Android 9+ will silently block in production builds.
3. **Permissions & Android 13/14+ Compliance:** Compare native features used in code (Camera, Location, Bluetooth, Notifications, Media/Storage, Background tasks) against `<uses-permission>` declarations in `AndroidManifest.xml` and runtime permission request flows.
4. **64-Bit & Native ABI Filters:** Verify `ndk.abiFilters` (`arm64-v8a`, `armeabi-v7a`) and Hermes/JSC engine settings to ensure the APK won't crash on modern 64-bit Android devices.
5. **Production Bundle & Environment Injection:** Verify how environment variables are baked into the standalone APK during release bundling (e.g., `.env.production`, `eas.json` profiles, `BuildConfig`) vs development mode.

---

## Phase 5: Non-Destructive Verification Checks (Dry-Run Only)
If terminal execution is permitted, run ONLY non-destructive, read-only verification commands (such as `tsc --noEmit`, `eslint`, `flutter analyze`, `npx expo-doctor`, or `gradlew check --dry-run`). 
- **NEVER** run commands that alter files, install packages, or mutate database states.

---

# Phase 6: Final Conclusion & Solution Blueprint (Deliverable Format)
Generate a comprehensive Artifact Report structured exactly as follows:

### 1. Architecture & Stack Summary
- Concise breakdown of detected technologies, entry points, and build pipelines.

### 2. Critical Failure Matrix (Categorized)
Group all verified findings into:
- **[CRITICAL - APK / Build Blocker]:** Will cause the build or compilation to fail.
- **[CRITICAL - Post-Build APK Crash]:** APK will build cleanly, but will crash or fail on an actual device.
- **[HIGH - Backend / API / Full-Stack Breakage]:** Broken contracts, crashes, or security flaws.
- **[MEDIUM - Performance & Edge Cases]:** Memory leaks, race conditions, or architectural debt.

*For EVERY issue listed, you MUST provide:*
- **Location:** `exact/path/to/file:line_number`
- **Root Cause & Evidence:** The exact snippet/config and technical explanation of why it fails.
- **Exact Solution Blueprint:** Provide the exact code block or configuration fix inside your report so the developer can review it (Remember: Do NOT apply the fix to the files yourself).

### 3. Final Go / No-Go Release Verdict
- **Build Readiness Score:** (0–100%)
- **APK Release Status:** `READY FOR BUILD` or `BLOCKED (X Critical Issues Found)`
- **Prioritized Action Plan:** The exact chronological order in which the developer should resolve the findings.