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
- **TARGETED UPDATING (KEEP COMPACT, NO BLOAT)**:
  - Update `PROJECT_ANALYSIS.md` **only when architecture, file paths, routes/endpoints, DB schema, dependencies, or invariants change** — skip editing it for minor UI/copy tweaks or small bug fixes.
  - Keep `Recent Changes` **capped at the latest 5–7 milestone entries** (prune/summarize older entries instead of appending indefinitely; full history lives in `git log`) so the entire file stays under ~200 lines.

---

## 5. Pre-Execution Change Preview Protocol (Mandatory Approval Gate)
- **MANDATORY PREVIEW & APPROVAL EVERY TIME**: Before modifying, creating, or deleting ANY file(s), changing DB schemas/APIs, or installing dependencies across ANY project (including single-file updates and bug fixes, unless the user explicitly instructs to apply changes immediately without asking):
  1. State a concise preview: **Target Files**, **What Will Change** (1–3 bullets), and **Purpose**.
  2. Pause and ask: *"Would you like me to create a detailed plan first, or proceed directly with these changes?"* and wait for user confirmation before altering any file on disk.
