---
description: Verify every project feature, workflow, user role, and integration to ensure all functionality is fully implemented, working correctly, and no required functionality is missing or broken.
---

# Project Functional Verification

Your objective is to verify that the application is fully functional and that every planned feature has been correctly implemented.

Do not assume anything. Analyze and verify every workflow from start to finish.

---

## 1. Feature Verification

Analyze the project requirements and compare them with the implementation.

Identify features that are:

- Fully Implemented
- Partially Implemented
- Missing
- Broken
- Incomplete

Report every missing or incomplete functionality.

---

## 2. Workflow Verification

Verify every application workflow from start to finish.

Ensure every workflow completes successfully without interruptions or unexpected behavior.

Identify any missing implementation within the workflow.

---

## 3. User Role Verification

Verify the complete workflow for every user role.

Examples:

- Admin
- Agent
- Customer

For each role verify:

- Dashboard
- Navigation
- Permissions
- Available Features
- CRUD Operations
- Notifications
- Reports
- Settings

Ensure every role can complete its intended workflow successfully.

---

## 4. Screen Verification

Verify every screen.

Check:

- Navigation
- Buttons
- Forms
- Validation
- Loading States
- Empty States
- Error States
- Success Messages

Identify any missing functionality.

---

## 5. API Verification

Verify that:

- Every API endpoint exists.
- APIs return expected data.
- Validation works.
- Error handling works.
- Authentication works.
- Authorization works.

Identify broken or missing APIs.

---

## 6. Database Verification

Verify:

- Database operations
- CRUD functionality
- Relationships
- Data consistency

Ensure application functionality matches the database implementation.

---

## 7. Cross Platform Verification

If the project contains multiple platforms:

- Mobile
- Web
- Admin Panel
- Backend

Verify that dependent functionality is implemented across every affected platform.

Report inconsistencies.

---

## 8. Dependency Verification

Analyze dependent functionality.

If one feature depends on another:

Verify that both are implemented correctly.

Ensure no workflow breaks because of missing dependent functionality.

---

## 9. Integration Verification

Verify every integration.

Examples:

- Authentication
- Storage
- Notifications
- Payment Gateway
- Third-party APIs
- Email
- SMS
- Maps

Ensure integrations work correctly.

---

## 10. Identify Missing Functionality

Search the project for:

- TODOs
- Placeholder implementations
- Mock functionality
- Disabled features
- Unfinished screens
- Incomplete APIs
- Missing validations

Determine whether they prevent the application from being considered complete.

---

## 11. Final Verification

Determine whether the project is functionally complete.

If not, provide a detailed implementation checklist.

For every issue include:

- Problem
- Location
- Impact
- Suggested Fix
- Priority

---

## 12. Final Report

Generate a report including:

- Overall Completion Percentage
- Fully Implemented Features
- Missing Features
- Broken Features
- Partially Implemented Features
- Workflow Issues
- User Role Issues
- API Issues
- Database Issues
- Cross Platform Issues
- Integration Issues
- Remaining Tasks

Only consider the project functionally complete if every required feature and workflow has been successfully verified.
