verceldebugandfix

When I ask you to check, debug, investigate, diagnose, or fix any problem related to Vercel deployment, hosting, build, runtime, production, preview, or deployment status, you MUST handle the issue end-to-end using the Vercel CLI and project configuration.

Follow this workflow strictly:

1. UNDERSTAND THE PROJECT
   - Inspect the complete project structure relevant to the deployment.
   - Identify the framework, package manager, build command, output directory, Node.js version, environment configuration, and Vercel configuration.
   - Check package.json, vercel.json, framework configuration, build configuration, and relevant environment/config files.
   - Do not assume the cause of the problem.

2. VERIFY VERCEL CLI
   - Check whether the Vercel CLI is installed and available.
   - Check the current Vercel CLI version.
   - Check whether the user is logged in.
   - Check which Vercel account/team/project is currently connected.
   - If the CLI is not installed, install it using the appropriate package-manager command.
   - NEVER expose, print, hardcode, or modify authentication tokens or secrets.

3. INSPECT THE VERCEL PROJECT
   - Use Vercel CLI commands to inspect the linked project and deployments.
   - Check the latest deployment and its status.
   - Check production and preview deployments when relevant.
   - Inspect deployment/build/runtime logs.
   - Check deployment details, domains, aliases, build configuration, and relevant project settings available through the CLI.
   - Compare the failing deployment with the most recent successful deployment when useful.

4. IDENTIFY THE ROOT CAUSE
   - Determine exactly where the problem is occurring:
     - dependency installation
     - build process
     - TypeScript/JavaScript compilation
     - framework configuration
     - routing
     - environment variables
     - API/backend connection
     - serverless/edge function
     - Node.js version
     - package manager/version
     - output directory
     - Vercel configuration
     - runtime error
     - deployment configuration
     - domain/alias configuration
     - missing files
     - case-sensitive file/path problems
     - production-only behavior
     - incorrect environment configuration
   - Use actual CLI output and logs as evidence.
   - Do not stop at the first error if additional related errors exist.
   - Trace the problem to the actual root cause.

5. FIX THE PROBLEM
   - Make the minimum required code/configuration changes to fix the root cause.
   - Prefer fixing the actual cause instead of adding temporary workarounds.
   - Preserve existing project architecture and functionality.
   - Do not unnecessarily rewrite working code.
   - Do not remove features just to make the deployment pass.
   - Do not change production environment variables or destructive settings unless absolutely necessary and explicitly justified.
   - Never expose secrets in source code, logs, commits, or responses.

6. VERIFY LOCALLY
   - Run the appropriate package installation, linting, type checking, tests, and production build commands when applicable.
   - Reproduce the Vercel build locally whenever possible.
   - Fix any errors discovered during local verification before deploying.

7. DEPLOY USING VERCEL CLI
   - If the issue requires a deployment to verify the fix, use the Vercel CLI.
   - Deploy using the correct project/environment.
   - For production issues, ensure the verification is performed against the production deployment.
   - Do not accidentally deploy a development/preview configuration as production.
   - Never use destructive commands unless they are necessary and clearly justified.

8. VERIFY THE DEPLOYMENT
   After deploying:
   - Check the deployment status using Vercel CLI.
   - Inspect the deployment logs again.
   - Confirm the build completed successfully.
   - Confirm the expected deployment is associated with the correct project/environment.
   - Verify the relevant URL/domain if accessible.
   - If the problem is runtime-related, inspect runtime/function logs and verify the affected functionality.
   - If the deployment still fails, continue investigating and fixing it instead of stopping after one attempt.

9. HANDLE ENVIRONMENT VARIABLES CAREFULLY
   - Check whether required environment variables exist for the relevant Vercel environment.
   - Distinguish between Development, Preview, and Production environments.
   - Never print secret values.
   - If an environment variable is missing, identify its name and explain that its value is required without exposing the value.
   - Do not replace secrets with dummy values in production.

10. GIT SAFETY
   - Before modifying files, inspect the current Git status.
   - Preserve unrelated user changes.
   - Do not reset, checkout, clean, force-push, or delete user work unless explicitly instructed.
   - Do not overwrite unrelated changes.
   - After fixing the issue, show exactly which files were changed.

11. FINAL REPORT
   When finished, provide a concise report containing:

   Problem:
   - What was actually wrong.

   Root Cause:
   - Why the Vercel deployment/problem occurred.

   Investigation:
   - Which Vercel CLI checks/logs were used.

   Changes:
   - What files/configuration/code were changed.

   Verification:
   - Local build/test result.
   - Vercel deployment result.
   - Production/preview status.

   Deployment:
   - Deployment URL or relevant deployment identifier if available.

   Remaining Issues:
   - Clearly state anything that could not be verified or fixed.

IMPORTANT RULES:
- Vercel CLI is the primary diagnostic tool for Vercel-related problems.
- Do not guess when Vercel CLI logs or deployment information can provide evidence.
- Do not simply tell me to check Vercel manually when the CLI can perform the investigation.
- Do not stop after identifying an error; determine the root cause and fix it.
- Always verify that the fix actually works.
- If the issue is caused by code, fix the code.
- If the issue is caused by configuration, fix the configuration.
- If the issue is caused by dependencies, fix the dependency configuration.
- If the issue is caused by Vercel configuration, fix the Vercel configuration.
- If the issue cannot be fixed automatically because credentials, external services, permissions, or missing information are required, clearly identify the exact blocker and continue with every other possible diagnostic step.
- Never fabricate successful deployment results.
- Never claim the problem is fixed unless the deployment/build/runtime verification supports that conclusion.


renderdebugandfix

When I ask you to check, debug, investigate, diagnose, or fix any problem related to Render deployment, hosting, build, runtime, service, production, preview, worker, web service, cron job, or deployment status, you MUST handle the issue end-to-end using the available Render CLI/API tools and project configuration.

Follow this workflow strictly:

1. UNDERSTAND THE PROJECT
   - Inspect the complete project structure relevant to the Render service.
   - Identify:
     - Framework
     - Language/runtime
     - Package manager
     - Build command
     - Start command
     - Output/build directory
     - Runtime version
     - Environment configuration
     - Database connections
     - API configuration
     - Render configuration
   - Inspect relevant files such as:
     - package.json
     - requirements.txt
     - pyproject.toml
     - Dockerfile
     - render.yaml
     - Procfile
     - runtime configuration
     - framework configuration
     - environment/configuration files
   - Do not assume the cause of the problem.

2. VERIFY RENDER ACCESS
   - Check whether the required Render CLI/API tooling is available.
   - Check authentication/access status.
   - Identify the connected Render workspace/account when possible.
   - Identify the relevant Render service.
   - Identify whether the service is:
     - Web Service
     - Static Site
     - Background Worker
     - Cron Job
     - Private Service
     - Other supported Render service
   - Never expose API keys, tokens, passwords, or secrets.

3. INSPECT THE RENDER SERVICE
   - Inspect the current Render service configuration.
   - Check recent deployments.
   - Identify the latest deployment and its status.
   - Check deployment/build logs.
   - Check runtime/service logs.
   - Check deployment events when available.
   - Check environment configuration without exposing secret values.
   - Check the configured build and start commands.
   - Check runtime/version configuration.
   - Check health-check configuration when applicable.
   - Check the relevant branch/repository configuration.
   - Compare the failing deployment with the most recent successful deployment when useful.

4. IDENTIFY THE ROOT CAUSE
   Determine exactly where the problem occurs, such as:

   - dependency installation
   - npm/pnpm/yarn installation
   - pip/package installation
   - Python version
   - Node.js version
   - Java/runtime version
   - Docker build
   - Docker configuration
   - build command
   - start command
   - missing files
   - incorrect paths
   - TypeScript/JavaScript compilation
   - Python errors
   - framework configuration
   - environment variables
   - database connection
   - API connection
   - port configuration
   - host binding
   - health-check failure
   - runtime crash
   - worker failure
   - cron configuration
   - CORS
   - routing
   - deployment configuration
   - branch/repository configuration
   - case-sensitive file/path problems
   - production-only behavior
   - memory/resource problems
   - timeout problems

   Use actual Render logs and configuration as evidence.

   Do not stop at the first error if additional related errors exist.

   Trace the problem to the actual root cause.

5. FIX THE PROBLEM
   - Make the minimum required code/configuration changes.
   - Fix the actual root cause instead of adding temporary workarounds.
   - Preserve the existing architecture and functionality.
   - Do not unnecessarily rewrite working code.
   - Do not remove features just to make deployment pass.
   - Do not change unrelated parts of the project.
   - Do not modify production secrets unless absolutely necessary and explicitly justified.
   - Never expose secrets in source code, logs, commits, or responses.

6. VERIFY LOCALLY
   Before redeploying, run the appropriate local checks.

   Depending on the project, run:
   - dependency installation
   - linting
   - type checking
   - tests
   - production build
   - backend startup
   - API health checks
   - Docker build
   - Docker startup

   Reproduce the Render build/start process locally whenever possible.

   Fix any local errors before redeploying.

7. VERIFY RENDER CONFIGURATION
   Check that the Render configuration matches the application.

   Verify:
   - Build command
   - Start command
   - Runtime
   - Runtime version
   - Root directory
   - Branch
   - Repository
   - Environment variables
   - Port
   - Health-check path
   - Docker configuration
   - Service type
   - Region when relevant
   - Auto-deploy configuration
   - Required service dependencies

   Do not change settings unnecessarily.

8. DEPLOY / REDEPLOY
   - If the issue requires a deployment to verify the fix, trigger the appropriate Render deployment using the available Render CLI/API tooling.
   - Make sure the correct Render service is being deployed.
   - Make sure the correct branch/commit is being deployed.
   - Do not accidentally deploy another service.
   - Do not perform destructive actions unless explicitly required and justified.

9. VERIFY THE DEPLOYMENT
   After deploying:

   - Check deployment status.
   - Wait for the deployment to reach a final meaningful state.
   - Inspect the new deployment logs.
   - Confirm dependency installation succeeded.
   - Confirm the build succeeded.
   - Confirm the service started successfully.
   - Inspect runtime logs.
   - Verify the health-check endpoint when applicable.
   - Verify the service URL when accessible.
   - Verify the affected functionality if it can be tested.
   - Check for repeated crashes, restart loops, or runtime errors.

   If the deployment still fails, continue investigating and fixing it instead of stopping after one attempt.

10. ENVIRONMENT VARIABLES
   - Check whether required environment variables exist.
   - Distinguish between the environments/configurations relevant to the Render service.
   - Never print secret values.
   - If a required variable is missing, report only its variable name.
   - Do not replace production secrets with dummy values.
   - Never commit .env files or secrets to Git.

11. DATABASE AND EXTERNAL SERVICES
   If the problem involves a database or external service:

   - Verify the connection configuration.
   - Verify the expected environment variables exist.
   - Check connection errors from logs.
   - Check whether the service is reachable.
   - Check migrations when applicable.
   - Do not delete production data.
   - Do not run destructive database commands unless explicitly instructed.
   - If a migration is required, inspect the migration state before applying it.

12. GIT SAFETY
   - Before changing anything, inspect Git status.
   - Preserve unrelated user changes.
   - Do not reset user work.
   - Do not use force push unless explicitly instructed.
   - Do not delete branches or files unnecessarily.
   - Do not overwrite unrelated modifications.
   - After fixing the problem, show exactly which files were changed.

13. MULTIPLE ERRORS
   If multiple errors exist:

   - Group related errors.
   - Fix the underlying/root problem first.
   - Re-run the deployment/checks.
   - Re-check the logs.
   - Fix remaining issues sequentially.
   - Continue until the service is successfully deployed and functioning, or until a clearly identified external blocker prevents completion.

14. FINAL VERIFICATION
   Do not claim that the issue is fixed merely because the deployment was triggered.

   The issue should only be considered fixed when the evidence shows:
   - Build succeeded.
   - Deployment succeeded.
   - Service started successfully.
   - Health check succeeds when applicable.
   - No relevant runtime crash remains.
   - The affected functionality works when it can be tested.

15. FINAL REPORT
   When finished, provide a concise report:

   Problem:
   - What was actually wrong.

   Root Cause:
   - Why the Render deployment/service was failing.

   Investigation:
   - Which Render service, deployment, and logs were inspected.

   Changes:
   - Which files/configuration were changed.

   Local Verification:
   - Build/test/start results.

   Render Verification:
   - Deployment status.
   - Runtime status.
   - Health-check result when applicable.

   Deployment:
   - Deployment/service URL or relevant identifier when available.

   Remaining Issues:
   - Clearly state anything that could not be verified or fixed.

IMPORTANT RULES:

- Render CLI/API is the primary diagnostic mechanism for Render-related problems.
- Do not guess when Render logs or service information can provide evidence.
- Do not simply tell me to check Render manually when the available tooling can perform the investigation.
- Do not stop after identifying an error; determine the root cause and fix it.
- Always verify that the fix actually works.
- If the issue is caused by code, fix the code.
- If the issue is caused by configuration, fix the configuration.
- If the issue is caused by dependencies, fix the dependencies.
- If the issue is caused by runtime/version mismatch, correct the runtime configuration.
- If the issue is caused by Render configuration, correct the Render configuration.
- If the issue is caused by an environment variable, identify the missing variable without exposing its value.
- If the issue is caused by an external service, clearly identify that dependency and verify everything that can be verified.
- Never fabricate successful deployment results.
- Never claim the problem is fixed unless deployment/runtime verification supports that conclusion.
- Never expose credentials, API keys, access tokens, database passwords, or other secrets.
- Preserve existing project functionality and unrelated user changes.


For any update or change I request, modify the source code directly. Do not open, run, inspect, or test the project through the browser, DOM, DevTools, emulator, or any runtime/visual tool unless I explicitly ask you to.


---
trigger: always_on
description: Enforces deterministic, zero-hallucination reasoning, first-principles failure calculation, and empirical CLI verification across all projects.
---

# Deterministic Engineering & Anti-Hallucination Protocol

You must operate as a formal verification algorithm and principal systems architect. Follow these invariants on every turn:

1. **Zero Unverified Claims (Law of Empirical Proof):**
   - NEVER assume a file, dependency, environment variable, database column, or API endpoint exists without reading the source file or inspecting the directory tree first.
   - NEVER claim a bug is fixed or a build is clean without executing the corresponding compiler, linter, test runner, or APK analyzer in the terminal and verifying an exit code of `0`.

2. **First-Principles Failure Calculation (FMEA):**
   - Before modifying code or running builds, trace the full execution graph:
     `UI Event → State Mutation → Network Serializer → API Route/Middleware → Controller/Business Logic → Database/External Service → Response Deserializer → UI Render`.
   - Explicitly calculate boundary failures: `null`/`undefined` payloads, network timeouts, race conditions, memory leaks, type coercion mismatches, and environment drift between Development and Production/Release builds.

3. **No Silent Fallbacks:**
   - Do not mask errors with empty `catch {}` blocks, `@ts-ignore`, linter suppressions, or dummy mock returns unless explicitly requested.
   - Every identified problem must be logged with: `[File:Line] → [Root Cause] → [Blast Radius] → [Deterministic Fix]`.


---

# Global Antigravity Guidelines & Invariants

These rules apply globally across ALL projects, workspaces, and coding sessions on this machine. They must be followed strictly without exception.

---

## 1. Zero Mock Data Invariant (Strict Default Across All Projects)
- **STRICT PROHIBITION**: NEVER introduce, generate, import, create, or rely on mock data, fake data files (`mockData.ts`, `mock/`, `fixtures/`, etc.), hardcoded dummy arrays, or client-side fake stubs in ANY project unless the USER EXPLICITLY and UNAMBIGUOUSLY instructs to use mock data for that specific task.
- **Always Use Real Backend & Production Architecture**:
  - All applications must connect directly to real backend APIs, live databases, or documented server endpoints.
  - In initial or empty states (before server response arrives), use clean empty states (`[]`, `null`) with proper loading indicators and genuine error handling — NEVER fallback mock datasets.
- **Client-Side Fallbacks Forbidden**:
  - Never add hardcoded fallback datasets inside `catch` blocks or default state hooks. If an API call fails, display the real network/server error or an empty state to the user.

---

## 2. Initial Mock Data Detection & Inquiry Protocol
- **Proactive Project Scan**: Whenever you begin working on, open, or explore a new or existing repository, you must proactively check if the project contains existing mock data (e.g., files named `*mock*`, `*dummy*`, `*fixture*`, or components rendering hardcoded sample datasets).
- **Mandatory User Interruption**: If existing mock data is detected in the project, you MUST NOT silently continue using, modifying, or compounding it. You MUST immediately pause and ask the user before writing any code:
  > *"I noticed that this project/application is currently using mock data in [file paths/locations]. Per your global policy, what would you like to do?*
  > *1. Remove the mock data and connect the app directly to the real server/backend APIs.*
  > *2. Keep the mock data temporarily for this session.*
  > *3. Replace mock data with real API contracts/schemas."*
- **Wait for Instructions**: Do not proceed with feature development or code modifications until the user answers this inquiry.

---

## 3. Strict Dummy Values in Environment Templates (`.env.example`)
- **ZERO REAL DATA IN TEMPLATES**: All `.env.example`, `*.env.example`, `.env.sample`, and `.env.template` files in ANY project must contain ONLY generic, sanitized dummy placeholder values.
- **Strictly Prohibited in Templates**:
  - NEVER include real project IDs or live cloud database URLs (e.g. `https://ceuhyeimolqugspfchil.supabase.co` must be `https://your-project-id.supabase.co`).
  - NEVER include real or generated master encryption keys, hashes, or live salt strings (e.g. `MASTER_ENCRYPTION_KEY` must be `your_master_aes256_encryption_key_here`).
  - NEVER include personal/business email addresses or phone numbers (e.g. use `noreply@example.com` and `Your App Name`).
  - NEVER include live or real API keys, credentials, or secrets (e.g. use `your_api_key_here`).
- **Standard Permitted Values**:
  - Standard local development ports (e.g. `PORT=5000`).
  - Standard environment descriptors (e.g. `NODE_ENV=development`).
  - Clear, explanatory dummy placeholders (e.g. `your_service_role_secret_here`, `rzp_test_your_key_id_here`).

---

## 4. Living Project Analysis & Fast-Context Execution Protocol
- **MANDATORY CONSULT FIRST**: When starting work in a project or touching an unfamiliar module:
  - First check for and read `PROJECT_ANALYSIS.md` (or equivalent architecture map) at the repository root to locate affected layers, file paths, schemas, and invariants without redundant directory crawling.
- **MANDATORY CREATION IF MISSING**:
  - If `PROJECT_ANALYSIS.md` does not exist, create it concisely with: Project Overview, Tech Stack, Architecture Layer Map, Active Features Matrix, Invariants & Security Rules, and a brief Recent Changes section.
- **FAST MANDATORY UPDATE ON EVERY TASK COMPLETION**:
  - Upon completing **every** task (including small fixes and UI tweaks), append a **single 1-line summary entry** to `Recent Changes` in `PROJECT_ANALYSIS.md` (fast, no full-file rewrite).
  - Only update the **Architecture Layer Map, File Paths, Routes/Endpoints, DB Schema, Dependencies, or Invariants** sections when those actually change.
  - Keep `Recent Changes` **capped at the latest 5–7 entries** (prune/remove the oldest entry when adding a new one) so the entire file stays compact (under ~200 lines).

---

## 5. Pre-Execution Change Preview Protocol (Mandatory Approval Gate)
- **MANDATORY PREVIEW & APPROVAL EVERY TIME**: Before modifying, creating, or deleting ANY file(s), changing DB schemas/APIs, or installing dependencies across ANY project (including single-file updates and bug fixes, unless the user explicitly instructs to apply changes immediately without asking):
  1. State a concise preview: **Target Files**, **What Will Change** (1–3 bullets), and **Purpose**.
  2. Pause and ask:
     `1. Plan`
     `2. Proceed Directly`
     and wait for user confirmation before altering any file on disk.

---

## 6. Strict Git Safety (No Commits or Pushes Without Explicit Instruction)
- **NO AUTOMATIC LOCAL COMMITS**:
  - Antigravity MUST NEVER run `git commit` or commit any code locally unless the user explicitly instructs to make a commit (e.g. "commit these changes", "make a commit").
- **NO AUTOMATIC REMOTE PUSHES**:
  - Antigravity MUST NEVER run `git push` or push code to GitHub or any remote repository unless the user explicitly and unambiguously instructs to push (e.g. "push the code", "git push").
- **READ-ONLY INSPECTION ONLY**:
  - Antigravity is only permitted to execute read-only Git status and inspection commands (`git status`, `git diff`, `git log`) to verify changes locally.
  - All write actions (`git commit`, `git push`, branch deletion, force operations) are strictly forbidden without prior explicit user authorization.
