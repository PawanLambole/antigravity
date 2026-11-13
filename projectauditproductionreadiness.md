---
name: projectauditproductionreadiness
description: Audit the project, find bugs, optimize code, and verify production readiness.
---
# Project Audit & Production Readiness

Your objective is to verify that the project is complete, stable, optimized, and ready for production.

## 1. Feature Verification

Analyze the entire project and verify that every planned feature is:

- Fully implemented
- Working correctly
- Connected to all dependent modules
- Consistent across the application

Report any missing, incomplete, or partially implemented features.

---

## 2. Workflow Verification

Test every user workflow from start to finish.

Verify workflows for:

- Admin
- Agent
- Customer

Ensure every action completes successfully without breaking any dependent functionality.

---

## 3. Functional Testing

Verify that:

- Navigation works correctly
- Buttons perform the correct actions
- Forms validate correctly
- CRUD operations work properly
- APIs return expected results
- Authentication works
- Authorization is correct
- File uploads/downloads work
- Notifications work
- Search, filters, pagination, and sorting work correctly

---

## 4. Cross-Platform Verification

Analyze consistency between:

- Mobile Application
- Admin Web
- Backend/API
- Database

Ensure all dependent changes are implemented across every affected platform.

---

## 5. Database Verification

Check:

- Tables
- Columns
- Relationships
- Foreign Keys
- Constraints
- Indexes
- RLS Policies
- Storage
- Migrations

Verify that the database matches the application requirements.

---

## 6. Find Bugs

Search for:

- Runtime errors
- Logic errors
- Edge cases
- Broken workflows
- Broken UI
- Missing validations
- Broken APIs
- Incorrect permissions
- Performance issues

Fix every issue that can be safely resolved.

---

## 7. Remove Development Code

Remove:

- Dummy data
- Mock APIs
- Test components
- Placeholder implementations
- Console logs
- Debug code
- Temporary comments
- Unused assets
- Unused imports
- Dead code

---

## 8. Code Cleanup & Optimization

Improve the project by:

- Removing duplicate logic
- Refactoring complex code
- Simplifying components
- Optimizing database queries
- Optimizing API calls
- Optimizing rendering
- Improving readability
- Following project coding standards

Do not change application behavior.

---

## 9. Build & Quality Verification

Ensure:

- No build errors
- No lint errors
- No TypeScript errors
- No missing imports
- No unused dependencies
- No compilation errors

---

## 10. Final Report

Provide a summary including:

- Project Completion Status (%)
- Features Verified
- Missing Features
- Bugs Found
- Bugs Fixed
- Remaining Issues
- Files Modified
- Performance Improvements
- Code Cleanup Summary
- Production Readiness Status

Do not mark the project as production-ready until all critical issues have been resolved.