---
description: Analyze and document an existing project before starting development work
---

# Project Understanding & Documentation Workflow

## Objective

When starting work on an existing project, first understand the complete project before making any changes.

The goal is to:
1. Read and analyze the complete project.
2. Understand how every major part works and connects.
3. Identify how the project is installed, configured, run, built, tested, and deployed.
4. Identify database, API, authentication, roles, integrations, dependencies, and environment configuration.
5. Document the complete understanding in a single `PROJECT_CONTEXT.md` file.
6. Use `PROJECT_CONTEXT.md` as the primary reference for future development work.

---

## Step 1 — Inspect the Project

Start by inspecting the complete project structure.

Analyze:
- Root folders and files
- Frontend/mobile applications
- Backend/API
- Database and migrations
- Configuration files
- Environment files and environment variable usage
- Authentication and authorization
- API routes/services
- Components/screens/pages
- State management
- Utilities/helpers
- Models/types/interfaces
- External services and integrations
- Build and deployment configuration
- Scripts and package managers
- Documentation and README files

Do NOT modify code during this analysis phase.

---

## Step 2 — Understand the Architecture

Determine and explain:

- Overall project purpose
- Application architecture
- Technology stack
- Main applications/modules
- Frontend → backend → database flow
- Authentication flow
- Authorization and user roles
- Important business logic
- API communication
- Database structure and relationships
- Third-party integrations
- File/storage handling
- Important dependencies
- Important configuration

Trace important functionality from:
`User Action → UI/Screen → Logic → API/Service → Database/External Service → Response → UI`

---

## Step 3 — Understand How to Run It

Determine the actual commands and requirements needed to:

- Install dependencies
- Configure environment variables
- Start development server
- Start frontend/mobile app
- Start backend
- Start database/services if required
- Run migrations
- Seed/setup data if required
- Run tests/linting
- Build production version
- Deploy the project

Only document commands that are supported by the project files/configuration.

If something cannot be confirmed, mark it as:
`UNKNOWN / NEEDS VERIFICATION`

Never invent commands, credentials, environment variables, APIs, or project behavior.

---

## Step 4 — Identify Important Development Context

Identify:

- Current project state
- Main entry points
- Important files
- Important folders
- Core features
- User roles and permissions
- Database tables/schema
- API endpoints
- Environment variables
- External services
- Known TODOs
- Known bugs/errors
- Technical risks
- Incomplete features
- Deployment requirements
- Anything a developer must know before changing the project

Also identify which parts are affected when a feature is changed.

---

## Step 5 — Create / Update `PROJECT_CONTEXT.md`

Create a single root-level file:

`PROJECT_CONTEXT.md`

Use this structure:

# Project Context

## 1. Project Overview
- Purpose
- Current status
- Main features

## 2. Technology Stack
- Frontend
- Backend
- Database
- Mobile
- Libraries
- Services
- Deployment

## 3. Project Structure
Important folders/files and their responsibilities.

## 4. Architecture
Explain the complete application flow and module relationships.

## 5. Application Flow
Explain important user/business flows step-by-step.

## 6. Authentication & Authorization
- Login/signup
- Sessions/tokens
- Roles
- Permissions
- Protected routes

## 7. Database
- Database technology
- Important tables
- Relationships
- Migrations
- Important queries/business rules

## 8. APIs & Services
Document important endpoints/services and what they do.

## 9. Environment Configuration
List required environment variables and their purpose.
Never store secret values.

## 10. Running the Project

### Installation
Commands required.

### Development
Commands required.

### Database Setup
Commands required.

### Testing
Commands required.

### Production Build
Commands required.

### Deployment
Actual deployment process.

## 11. Important Files
List critical files and why they matter.

## 12. Feature Map
Map major features to their relevant files/modules.

## 13. Dependencies & Integrations
External APIs, SDKs, services, storage, payments, authentication providers, etc.

## 14. Known Issues / TODOs
Only confirmed issues or TODOs.

## 15. Development Rules
Important project-specific conventions and constraints discovered from the codebase.

## 16. Change Impact Guide
For each major module, explain what other modules may be affected when it changes.

## 17. Current Understanding
Summarize the complete understanding of how the project works.

## 18. Unknowns
Clearly list anything that could not be verified.

---

## Step 6 — Validate the Documentation

Before finishing:

- Cross-check `PROJECT_CONTEXT.md` against the actual codebase.
- Remove assumptions.
- Correct outdated information.
- Ensure commands match package/config files.
- Ensure important modules are included.
- Ensure no secrets/passwords/API keys are written.
- Ensure the documentation is concise but sufficiently complete.

---

## Step 7 — Future Development Behavior

After `PROJECT_CONTEXT.md` exists:

Before making any future change:
1. Read `PROJECT_CONTEXT.md`.
2. Inspect the relevant source files.
3. Understand the impact of the requested change.
4. Identify affected frontend/mobile/backend/database modules.
5. Check whether a migration, environment change, API change, or deployment change is required.
6. Then implement the change.
7. Update `PROJECT_CONTEXT.md` if the architecture, setup, feature flow, dependencies, or project behavior changes.

Do not blindly modify code without understanding its existing architecture.

---

## Final Output

At the end of the analysis:

1. Create/update `PROJECT_CONTEXT.md`.
2. Give a short summary of:
   - What the project does
   - How it works
   - How to run it
   - Important modules
   - Important unknowns/issues
3. Do not modify application code unless explicitly requested.