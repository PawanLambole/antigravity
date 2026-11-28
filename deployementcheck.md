---
description: Check whether the project is fully ready for the final GitHub push and production deployment. Verify Git status, secrets, environment variables, fallback or dummy APIs, dummy data, migrations, production configuration, build, tests, and deployment readiness. Fix safe issues and report any remaining blockers before allowing the final push.
---

# githubdeployreadiness

When I ask you to check whether the project is ready for the final GitHub push and deployment, perform this pre-deployment audit.

## 1. Git & Project
- Check Git status, branch, remote, and uncommitted changes.
- Verify `.gitignore`.
- Ensure no `node_modules`, build files, logs, `.env`, secrets, or temporary files will be pushed.
- Check for merge conflicts and accidental files.

## 2. Environment & APIs
- Find all API URLs, backend URLs, database URLs, and external services.
- Verify production values use environment variables correctly.
- Detect localhost URLs, hardcoded URLs, fallback APIs, mock APIs, test endpoints, and hardcoded secrets.
- Verify frontend/backend environment variable names are consistent.
- Never expose secret values.

## 3. Dummy & Development Data
- Search for dummy, mock, fake, sample, placeholder, test, and hardcoded production data.
- Remove or flag development-only data.
- Ensure production uses the real database and APIs.

## 4. Database & Migrations
- Check all migration files.
- Verify migrations are complete, ordered, and consistent.
- Check for schema changes without migrations.
- Run migrations against a clean/test database when possible.
- Ensure all required migrations are committed.
- Never delete existing migrations just to make the check pass.

## 5. Build & Code
- Install dependencies.
- Run lint, type-check, tests, and production build when available.
- Fix deployment-blocking errors.
- Check broken imports, missing files, incorrect case-sensitive paths, and runtime errors.

## 6. Deployment Configuration
Check relevant files such as:
- `vercel.json`
- `render.yaml`
- `Dockerfile`
- `Procfile`
- `package.json`
- `requirements.txt`
- runtime/framework configuration

Verify build command, start command, output directory, runtime version, and production configuration.

## 7. Security
- Search for API keys, tokens, passwords, service-role keys, and credentials.
- Ensure secrets are not committed.
- Ensure server-only secrets are not exposed to frontend code.
- Check for authentication or security bypasses intended only for development.

## 8. Production Check
- Disable debug/development-only configuration where required.
- Check error handling.
- Check critical API, authentication, database, and routing flows.
- Check missing assets and broken production routes.
- Check that no fallback/mock system can silently replace the real production service.

## 9. Final Gate

Before declaring the project ready, verify:

✓ Git structure is clean  
✓ No secrets are being committed  
✓ No `.env` files are being committed  
✓ No fallback/dummy APIs remain  
✓ No unwanted dummy/test data remains  
✓ Environment variables are correctly configured  
✓ Migrations pass  
✓ Production build passes  
✓ Tests/type-check/lint pass when available  
✓ Deployment configuration is valid  
✓ No known deployment-blocking issue remains  

If a safe issue can be fixed automatically, fix it and rerun the relevant check.

Do not push to GitHub automatically unless I explicitly ask you to.

## Final Response

Return:

**READY FOR GITHUB PUSH**

or

**NOT READY FOR GITHUB PUSH**

Then provide only:

- ✓ Passed
- ✗ Failed
- ⚠ Warnings
- 📁 Files requiring changes

Never declare the project ready without actually verifying the important checks.