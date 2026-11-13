# Project Analysis & Architecture Memory Map: Antigravity Rules & Workflows

## 1. Project Overview
- **Repository**: `PawanLambole/antigravity`
- **Purpose**: Centralized version-controlled repository containing Antigravity agent global rules, guidelines, invariants, and standard operational workflows.
- **Owner**: Pawan Lambole (`pavanlambole6@gmail.com`)
- **Integration Target**: Google Antigravity Agent Configuration (`~/.gemini/` and `~/.gemini/config/global_workflows/`).

---

## 2. Tech Stack & Environment
- **Platform**: Google Antigravity (AGY) / Gemini Agent Ecosystem
- **File Format**: Markdown (`.md`) with YAML frontmatter where applicable
- **Version Control**: Git & GitHub (`main` branch)

---

## 3. Architecture Layer Map (File Paths & Manifest)

```
antigravity/
├── GEMINI.md                                  # Active Global Guidelines & Invariants for all workspaces
├── projectauditandproductionreadiness.md      # Workflow: Audit and production readiness check (v1)
├── projectauditproductionreadiness.md         # Workflow: Audit and production readiness check (v2 with frontmatter)
├── projectfunctionalverification.md           # Workflow: Exhaustive functional and role-based verification
├── projectinformation.md                      # Workflow: Comprehensive project understanding & documentation workflow
├── projectinformationarchitecture.md          # Workflow: Project information & architecture deep analysis
├── projectknowledgeandarchitectureanalysis.md # Workflow: Project knowledge & architecture pre-modification analysis (v1)
├── projectknowledgearchitectureanalysis.md    # Workflow: Project knowledge & architecture analysis (v2 with frontmatter)
├── abc.md                                     # Workflow stub template
├── README.md                                  # Repository documentation & installation guide
└── PROJECT_ANALYSIS.md                        # Living architecture memory map and invariants tracker
```

---

## 4. Active Rules & Workflows Matrix

| Identifier / File | Type | Description |
| :--- | :--- | :--- |
| `GEMINI.md` | Global Rule | 5 Core Antigravity Invariants: Zero Mock Data, Detection & Inquiry, Strict Dummy Values in Env Templates, Living Project Analysis, and Pre-Execution Change Preview. |
| `projectauditproductionreadiness.md` | Workflow | Comprehensive audit to verify features, test workflows, validate CRUD, API, and production stability. |
| `projectauditandproductionreadiness.md` | Workflow | Complementary / alternative prompt structure for production readiness audits. |
| `projectfunctionalverification.md` | Workflow | Validates every feature, user role (Admin, Agent, Customer), and integration without assumptions. |
| `projectinformation.md` | Workflow | Standard workflow to inspect an existing project and compile comprehensive `PROJECT_CONTEXT.md`. |
| `projectinformationarchitecture.md` | Workflow | Analysis workflow detailing architecture, tech stack, directory structure, modules, and user roles. |
| `projectknowledgearchitectureanalysis.md` | Workflow | Scans repository before modifications to grasp folder structure, environment, dependencies, and DB/API layout. |
| `projectknowledgeandarchitectureanalysis.md` | Workflow | Standard prompt structure for architecture understanding. |
| `abc.md` | Workflow | Minimal template stub for creating new workflows. |

---

## 5. Invariants & Security Rules
- **Zero Mock Data Invariant**: Mandatory real backend/production architecture; never introduce mock/dummy files unless explicitly requested.
- **Initial Mock Data Detection**: Scan projects proactively and pause for user decision if mock data is found.
- **Strict Dummy Values in `.env.example`**: Never leak real API keys, credentials, live URLs, or secrets in templates.
- **Living Project Analysis Protocol**: Maintain `PROJECT_ANALYSIS.md` in every project and update continuously.
- **Pre-Execution Change Preview Protocol**: Provide target files, changes, and purpose before touching any disk files.

---

## 6. Recent Changes Changelog
- **2026-11-13**:
  - Initialized repository with full suite of local Antigravity global rules (`GEMINI.md`).
  - Added all global workflows (`projectauditproductionreadiness.md`, `projectfunctionalverification.md`, `projectknowledgearchitectureanalysis.md`, etc.).
  - Added `PROJECT_ANALYSIS.md` living memory map.
  - Added comprehensive `README.md` documentation and setup instructions.
