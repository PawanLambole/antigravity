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
- **MANDATORY CONSULT FIRST**: Whenever the user requests any change, new feature, bug fix, or code update in ANY project:
  - You MUST first check for and read `PROJECT_ANALYSIS.md` (or equivalent architecture memory map) at the root of the project.
  - Use this document to instantly identify the affected architectural layers, exact file paths, schemas, API contracts, and dependencies.
  - Do NOT spend multiple turns blindly searching, grepping, or crawling unrelated directories.
- **MANDATORY CREATION IF MISSING**:
  - If `PROJECT_ANALYSIS.md` does not exist in the project, you MUST create it immediately during the first interaction.
  - It must contain: Project Overview, Tech Stack, Architecture Layer Map (with exact file paths), Active Services / Features Matrix, Invariants & Security Rules, and Recent Changes Changelog.
- **MANDATORY CONTINUOUS UPDATING**:
  - Whenever you modify code, add new endpoints, introduce migrations, configure new services, or alter UI components:
  - You MUST update `PROJECT_ANALYSIS.md` before finishing the turn so it always mirrors the real-time project state and keeps future tasks ultra-fast.

---

## 5. Pre-Execution Change Preview Protocol (Short Summary First)
- **MANDATORY SHORT PREVIEW**: Before modifying, creating, or deleting ANY file(s) across ANY project:
  - Antigravity MUST first explicitly state a concise, short preview of what changes it is about to make:
    1. **Target Files**: Exact file paths to be modified or created.
    2. **What Will Change**: A brief 1–3 bullet-point summary of the edits or additions.
    3. **Purpose**: The expected outcome or behavior of the changes.
  - This guarantees the user has immediate visibility and clarity before any file on disk is altered.



