---
description: Complete UI, Screenshot, and Implementation Audit for any page, component, route, or feature (Strict Read-Only Audit -> Ask to Plan or Fix)
---

# UI & Implementation Audit (`ui-audit`)

When the user provides **any page, component name, route, feature, or screenshot**, perform an exhaustive, deterministic, read-only audit of the complete UI and its supporting implementation.

## Strict Guardrails
1. **READ-ONLY AUDIT FIRST:** Do NOT modify, create, or delete any project files during the audit phase. Present all findings first, then ask the user whether to plan or proceed directly with the fixes.
2. **NO UNVERIFIED CLAIMS:** Every issue must cite exact `filepath:line_number` evidence and the actual code/style/config observed. Never guess or invent bugs in files you have not read.
3. **RESPECT BROWSER RULES:** Do NOT open, run, or inspect the project in a browser, DOM, DevTools, or emulator unless the user explicitly asks you to. Rely on static code inspection, terminal typecheck/lint checks, and any screenshots provided by the user.

---

## Step 1: Resolve Target Scope & Dependency Graph
Given the user's input (page name, component name, route, or screenshot):
1. Locate the primary page/component file(s) and route definition.
2. Trace all connected layers used by that UI:
   - Parent layout / wrapper / navigation shell
   - Child components, modals, drawers, tables, forms
   - Custom hooks, state management (Context, Redux, Zustand, etc.), and local state
   - Styles (CSS/SCSS, Tailwind classes, CSS modules, styled-components, theme tokens)
   - API/service calls, request/response types, DTOs, and backend route handlers (if in the same repo)
   - Validation schemas (Zod, Yup, Formik, React Hook Form, etc.)

---

## Step 2: Screenshot-to-Code Visual Verification (If Screenshot Provided)
If the user attached or referenced a screenshot:
1. Inspect every visible region of the screenshot (header, sidebar, cards, tables, forms, buttons, badges, icons, spacing, alignment, colors, text, empty/error states).
2. Identify every visual defect:
   - Misalignment, uneven padding/margin, broken grid/flex wrapping, overlapping elements, z-index clipping
   - Text overflow, unintended wrapping, truncation issues, missing contrast (dark/light mode)
   - Wrong labels, wrong numbers/formatting, stale/placeholder/mock text, missing or broken images/icons
   - Missing or wrongly styled states (active tab, disabled button, validation error, loading spinner, empty state)
   - Responsive/viewport breakage
3. Trace **each visual defect** to its exact `filepath:line_number` (JSX/HTML/template + CSS/Tailwind classes + data source).

---

## Step 3: Deep Implementation & Logic Audit
Check the resolved UI files against all of the following categories:

### A. Rendering, Props & React/Framework Bugs
- Missing or unstable `key` props in `.map()` loops (e.g., array index on mutable lists).
- Conditional rendering traps (e.g., `{count && <Component />}` rendering `0`).
- Unguarded `null` / `undefined` nested property access (`user.profile.name` without optional chaining or fallback).
- Stale closures, missing `useEffect` dependencies, infinite re-render loops, or missing cleanup (timers, listeners, subscriptions, AbortController).
- Props passed but ignored, wrong prop types, or mismatched default values.

### B. Forms, State & Interactive Flows
- Controlled vs. uncontrolled input bugs (`value={undefined}`).
- Missing client-side validation, missing inline error display, or broken reset/clear logic.
- Async submit buttons missing `disabled` / loading state (allowing duplicate submissions).
- Broken or no-op event handlers (`onClick`, `onChange`, `onSubmit`), or missing `e.preventDefault()` / `e.stopPropagation()`.
- Missing **Loading**, **Empty**, and **Error** UI states.
- Modals/drawers/dropdowns/tabs that fail to open, close, reset, or sync with URL/state.

### C. API, Data Contracts & Error Handling
- Endpoint URL, HTTP method, query params, request body, or response field mismatches between frontend and backend/types.
- Unhandled promise rejections, silent `catch {}` blocks swallowing errors, or missing user-facing error feedback.
- Missing refetch / cache invalidation / optimistic state update after create, update, or delete actions.
- Hardcoded mock/dummy data or hardcoded `localhost` URLs violating environment configuration.

### D. Routing, Auth & Permissions
- Broken `<Link>` / `navigate()` / `router.push()` paths or missing route parameters.
- Missing authentication or role-based access guards on protected pages/actions.

### E. Layout, Styling & Accessibility (a11y)
- Conflicting or invalid CSS / Tailwind classes, broken responsive breakpoints, fixed widths causing horizontal overflow.
- Icon-only buttons missing `aria-label`, images missing `alt`, form inputs missing `<label>`, clickable `<div>` elements without keyboard/button semantics.

### F. Static Type, Lint & Build Checks (Read-Only)
- Run non-destructive checks relevant to the project (e.g., `npx tsc --noEmit`, `npx eslint <target-files>`) if available in the workspace, and report any errors affecting the target UI.

---

## Step 4: Present Categorized Findings Report
Output a clear, structured report grouping all verified issues by severity:
- **[CRITICAL - Crash / Broken Flow / Wrong Implementation]**
- **[HIGH - Screenshot Mismatch / Visual Defect / API Contract Bug]**
- **[MEDIUM - State / Validation / Missing Loading-Empty-Error State]**
- **[LOW - Styling Polish / Responsiveness / Accessibility]**

For **every** issue, include:
1. **Location:** `filepath:line_number` (and Screenshot Region if applicable)
2. **What Is Wrong:** Exact observed code/visual evidence
3. **Root Cause:** Why it fails or renders incorrectly
4. **Proposed Fix:** Concise description of the exact change needed

If no issues are found in a category, state that it passed verification cleanly.

---

## Step 5: Mandatory Decision Gate
After presenting the complete audit report, **STOP without editing any files** and ask the user:

> **"I have listed all visual, functional, and implementation issues found in this page/component. Reply `1` to create a detailed plan to fix these issues, or `2` to proceed directly with the fixes."**
