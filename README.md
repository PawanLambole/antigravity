# Antigravity Rules & Workflows

A centralized repository containing global rules, guidelines, invariants, and operational workflows for **Google Antigravity (AGY)** agents.

---

## 📋 Overview

This repository standardizes agent behavior across projects and workspaces. It contains:
- **Global Rules (`GEMINI.md`)**: Enforced invariants ensuring production readiness, zero mock data contamination, living project analysis, environment template sanitization, and pre-execution previews.
- **Workflows (`*.md`)**: Reusable procedural runbooks for comprehensive architecture audits, functional verification, and project onboarding.

---

## 🛡️ Global Rules (`GEMINI.md`)

The `GEMINI.md` file defines the core global invariants governing every session:

1. **Zero Mock Data Invariant**:
   - Strict prohibition against introducing or relying on fake data or mock stubs.
   - All code must integrate with real production APIs and databases, using clean empty states with loading indicators.
2. **Initial Mock Data Detection & Inquiry Protocol**:
   - Proactive scanning of new repositories for existing mock data, immediately prompting the user before writing code.
3. **Strict Dummy Values in Environment Templates (`.env.example`)**:
   - Sanitized generic dummy values only; zero real secrets, live project URLs, or production keys.
4. **Living Project Analysis & Fast-Context Execution Protocol**:
   - Mandatory maintenance of `PROJECT_ANALYSIS.md` at the root of every project.
5. **Pre-Execution Change Preview Protocol**:
   - Mandatory concise summary (Target Files, What Will Change, Purpose) before modifying any disk files.

---

## 🚀 Workflows Catalog

| File | Purpose | Description |
| :--- | :--- | :--- |
| **`projectinformation.md`** | Project Onboarding | Step-by-step workflow to inspect a project and produce a consolidated `PROJECT_CONTEXT.md`. |
| **`projectinformationarchitecture.md`** | Architecture Blueprint | Deep dive into architecture, tech stack, folder structure, key modules, and user roles. |
| **`projectknowledgearchitectureanalysis.md`** | Architecture Discovery | Complete codebase scan prior to feature development or refactoring. |
| **`projectknowledgeandarchitectureanalysis.md`** | Architecture Analysis (v1) | Alternate analysis prompt for comprehensive system comprehension. |
| **`projectauditproductionreadiness.md`** | Production Audit | Verifies feature completeness, tests end-to-end workflows, validates CRUD/APIs, and checks production readiness. |
| **`projectauditandproductionreadiness.md`** | Production Audit (v1) | Feature and workflow audit guidelines for multi-role platforms. |
| **`projectfunctionalverification.md`** | Functional Verification | Exhaustive verification across Admin, Agent, and Customer workflows to identify broken or missing functionality. |

---

## ⚙️ Installation & Usage

### 1. Global Rules
Copy `GEMINI.md` to your home Antigravity configuration directory:
```bash
# Windows (PowerShell)
Copy-Item .\GEMINI.md "$HOME\.gemini\GEMINI.md"

# Linux / macOS
cp GEMINI.md ~/.gemini/GEMINI.md
```

### 2. Global Workflows
Copy the workflow files to your global workflows directory:
```bash
# Windows (PowerShell)
New-Item -ItemType Directory -Force "$HOME\.gemini\config\global_workflows"
Copy-Item .\project*.md "$HOME\.gemini\config\global_workflows\"

# Linux / macOS
mkdir -p ~/.gemini/config/global_workflows
cp project*.md ~/.gemini/config/global_workflows/
```
