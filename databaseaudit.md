---
description: Comprehensive audit workflow to verify that a project's database adheres to industry standards, ACID properties, relational integrity, optimal indexing and performance, schema necessity, correct hierarchy, and security best practices across any project stack.
---

# Universal Database Architecture, Standards & Performance Audit

When asked to check, audit, verify, or review a database, execute this comprehensive end-to-end audit. This workflow applies universally to any relational or non-relational database stack (PostgreSQL, Supabase, MySQL, MariaDB, SQLite, SQL Server, Oracle, MongoDB, DynamoDB, Firebase) and any ORM/query layer (Prisma, Drizzle, TypeORM, SQLAlchemy, Django ORM, Eloquent, Hibernate, or raw SQL migrations).

---

## 1. Discovery & Database Stack Identification

Inspect the codebase and configuration to identify the database architecture:
- **Engine & Version**: Identify the database engine (e.g., PostgreSQL 15+, MySQL 8+, SQLite 3, Supabase, MongoDB).
- **ORM / Schema Tooling**: Detect Prisma, Drizzle, TypeORM, Sequelize, SQLAlchemy, Django ORM, Alembic, Flyway, Supabase migrations, or manual SQL scripts.
- **Environment & Connection**: Locate connection definitions, connection pooling settings (PgBouncer, Prisma Accelerate, connection limits, SSL enforcement). Never print secret values or credentials.
- **Active Schemas**: Identify all relevant schemas (e.g., `public`, `auth`, multi-tenant schemas).

---

## 2. Schema Necessity & Zero-Dead-Weight Audit

Ensure every table and parameter serves a concrete business or technical requirement:
- **Zero Obsolete Tables**: Scan for deprecated, test, dummy, abandoned, or temporary tables (e.g., `temp_*`, `*_backup`, `test_*`, unused mock entities).
- **Zero Zombie Columns**: Identify columns that are never queried, written to, or mapped in application models.
- **Redundant Data Storage**: Identify accidental duplicate storage where identical data is replicated across multiple tables without a clear caching/denormalization justification.
- **Purged Test & Dummy Data**: Verify that demo data, mock accounts, placeholder seeding, and fixture rows are separated from production schemas.

---

## 3. Relational Hierarchy & Dependency Integrity

Verify that table relationships form a clean, well-structured Directed Acyclic Graph (DAG):
- **Hierarchy & Directionality**: Confirm clear parent-to-child ownership without circular dependencies (Table A -> Table B -> Table A).
- **Foreign Key Coverage**: Ensure every relational reference has an explicit foreign key constraint rather than relying solely on application-level enforcement.
- **Cascade Behavior Appropriateness**:
  - `ON DELETE RESTRICT` / `NO ACTION`: Default for critical financial, audit, or core master data to prevent accidental data loss.
  - `ON DELETE CASCADE`: Reserved for strictly owned dependent records (e.g., order items owned by an order).
  - `ON DELETE SET NULL`: For optional associations (e.g., assigned supervisor or optional category).
- **Junction / Pivot Tables**: Verify Many-to-Many relationships are handled via dedicated junction tables with compound primary keys or unique constraints preventing duplicate links.

---

## 4. Database Characteristics & ACID Compliance

Audit compliance with foundational database principles:
- **Atomicity**: Critical multi-step workflows (e.g., payment deductions, balance transfers, multi-entity submissions) must run within explicit transactions (`BEGIN ... COMMIT`) or stored procedures.
- **Consistency**:
  - **Entity Integrity**: Every table must have a distinct, immutable primary key (`UUID` v4/v7 or `BIGINT / BIGSERIAL`).
  - **Domain Integrity**: Appropriate data types, strict `NOT NULL` constraints where data is mandatory, and explicit `CHECK` constraints (e.g., `balance >= 0`, `status IN (...)`, format validation).
  - **Referential Integrity**: No orphaned foreign keys or dangling pointers.
- **Isolation & Concurrency**:
  - Race condition protection on mutable numerical or ledger balances (e.g., `SELECT ... FOR UPDATE`, optimistic concurrency with version columns, or atomic SQL increments).
  - No dirty reads or non-repeatable read vulnerabilities in financial/critical transactions.
- **Durability**: Write-Ahead Logging (WAL) configuration, automated snapshot/backup policies, and persistence guarantees.

---

## 5. Performance, Indexing & Query Efficiency

Evaluate index coverage and execution overhead to ensure maximum query throughput:
- **Foreign Key Indexes**: Ensure all foreign key columns are indexed. (Most relational engines do NOT index FKs automatically, leading to full-table scans during joins and parent row deletions).
- **High-Frequency Query Indexes**: Check filters (`WHERE`), joins (`JOIN`), and sorting (`ORDER BY`) fields in active queries for matching indexes.
- **Composite Index Order**: Verify composite indexes follow the Leftmost Prefix Rule (equality filters first, high cardinality first, range filters last).
- **Unique Indexes**: Ensure business uniqueness (e.g., username, email, invoice number, reference code) is enforced by unique indexes/constraints.
- **Redundant Index Elimination**: Remove duplicate or overlapping indexes (e.g., an index on `(a)` is redundant if an index on `(a, b)` already exists).
- **Pagination Strategy**: Flag inefficient large-offset queries (`OFFSET 100000`) and recommend keyset/cursor-based pagination.
- **Data Types for Performance**:
  - Use `BIGINT` or `UUID` over arbitrary strings for IDs.
  - Use `NUMERIC / DECIMAL` for money and currency (never `FLOAT` or `DOUBLE` which cause floating-point rounding errors).
  - Use `TIMESTAMPTZ` (UTC) for all timestamps.
  - Use `BOOLEAN` instead of integer flags (`0/1`).

---

## 6. Industry Naming & Design Standards

Verify that the schema follows clean, readable, professional conventions:
- **Casing & Identifiers**: Consistent casing throughout (standard: `snake_case` for tables and columns in PostgreSQL/MySQL).
- **Singular vs. Plural Consistency**: Maintain uniform convention across the entire database (e.g., all plural: `users`, `orders`, `products`, or all singular).
- **Standard Primary Keys**: Use `id` as the primary key name for simplicity and consistency.
- **Standard Foreign Keys**: Follow `<singular_parent_table>_id` naming (e.g., `user_id`, `organization_id`).
- **Standard Audit Timestamps**: Every mutable entity should contain `created_at` (`DEFAULT NOW()`) and `updated_at` (auto-updated via trigger or ORM).
- **Boolean Naming**: Prefix booleans with status verbs (e.g., `is_active`, `is_verified`, `has_access`, `can_edit`).

---

## 7. Security, Access Control & Data Protection

Verify defense-in-depth security at the data layer:
- **Row Level Security (RLS)**: If using Supabase / PostgreSQL RLS, ensure RLS is enabled on all tables, with explicit policies for SELECT, INSERT, UPDATE, DELETE.
- **Principle of Least Privilege**: Verify app roles (e.g., `anon`, `authenticated`, `service_role`) have only the minimum required grants.
- **PII & Sensitive Data Protection**: Ensure passwords are never stored in plaintext (use Argon2, bcrypt, or platform auth like Supabase/Firebase Auth). Ensure sensitive tokens, API secrets, or confidential government identifiers are masked or encrypted.
- **Injection Prevention**: Verify all queries use parameterized inputs or ORM abstraction—zero string concatenation in SQL queries.

---

## 8. Migrations, Drift & Version Control Health

Check migration discipline:
- **Idempotency & Reversibility**: Migrations should be repeatable and safe (`IF EXISTS`, `IF NOT EXISTS`, `ON CONFLICT`).
- **Sequential Integrity**: Migration files must have strict timestamped or ordered numbering without gaps or branch collisions.
- **Schema Drift Check**: Verify code models (TypeScript interfaces, Prisma schema, SQLAlchemy models) match the actual live database schema.
- **No Untracked Schema Edits**: Ensure all changes are committed in migration files rather than applied ad-hoc to production.

---

## 9. Final Audit Report

Structure the audit response clearly:

### 1. Executive Summary
- Overall database health rating (e.g., Excellent, Good, Needs Improvement, Critical Issues).
- Total tables reviewed, total indexes, total foreign keys.

### 2. Standards Compliance Checklist
| Criterion | Status | Findings / Details |
|---|---|---|
| ACID Properties & Transactions | Passed / Warning / Failed | ... |
| Normalization & Hierarchy | Passed / Warning / Failed | ... |
| Schema Necessity (Zero Deadweight) | Passed / Warning / Failed | ... |
| Indexing & Performance | Passed / Warning / Failed | ... |
| Constraints & Data Types | Passed / Warning / Failed | ... |
| Naming Conventions | Passed / Warning / Failed | ... |
| Security & RLS / Access Control | Passed / Warning / Failed | ... |
| Migration & Drift Integrity | Passed / Warning / Failed | ... |

### 3. Detailed Findings & Root Causes
- Detail any anti-patterns, missing indexes, unconstrained foreign keys, or redundant tables.

### 4. Actionable Remediation Plan
- Provide exact, non-destructive SQL migration or ORM schema fixes for every identified issue, ordered by priority (Critical -> High -> Medium -> Low).

---
