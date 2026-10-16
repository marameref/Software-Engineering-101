# DATABASE DESIGN, DEVELOPMENT & MANAGEMENT WITH POSTGRESQL
## Zero to Hero: A Practical Handbook for Web and Mobile Application Developers

**Author:** **Engr. Amarachi Crystal Omereife**  
**Organisation:** Opsfuxion Technologies Limited  
**Tagline:** *Orchestrate intelligence, deliver with precision.*  
**Edition:** October 2026  
**Audience:** Absolute beginners, software engineering students, web/mobile developers, junior backend engineers and aspiring database administrators.

> **Learning promise:** Starting with no SQL experience, learn to model a real application, implement it in PostgreSQL, connect it securely to a backend, test it, and operate it responsibly. Every major concept includes a demonstration, exercises, and answers. Examples assume a local practice database, never a production system.

## How to use this handbook

1. Read each concept, then type the SQL yourself instead of only copying it.
2. Run the examples in `psql` or pgAdmin Query Tool. SQL blocks are executable unless marked as illustrative.
3. Work through **Try it yourself** before opening the solution immediately below.
4. Keep a `database/` folder with your schema, seed data, migrations, tests, and notes.
5. Never run destructive commands against a database you cannot afford to lose.

**Recommended pace:** 10–14 weeks of part-time practice, or adapt as a reference alongside a software project. SQL examples target modern PostgreSQL (16+); features that depend on versions are identified where relevant. Your PostgreSQL server and client versions may differ.

## Roadmap

| Stage | Chapters | Outcome |
|---|---|---|
| Foundation | 1–4 | Understand databases, install tools, design tables and relationships |
| SQL practitioner | 5–10 | Build schemas; insert, retrieve, join, aggregate, modify and query safely |
| Application engineer | 11–16 | Transactions, performance, migrations, backend integration and security |
| Production readiness | 17–21 | Backups, monitoring, maintenance, concurrency, testing and deployment |
| Capstone | 22–24 | Complete course-enrolment platform database, challenges and answer key |

---

# PART I — THINKING LIKE A DATABASE DESIGNER

## Chapter 1 — What is a database, and why do applications need one?

A **database** stores organised information so it can be found, updated and protected. A **DBMS** (database management system) manages that information. **PostgreSQL** is an open-source relational DBMS. **SQL** (Structured Query Language) is the language used to describe, read and modify relational data.

Imagine a learning application: students create accounts, enrol in courses, pay for access, and mark lessons complete. Without persistent storage, the application forgets everything when the server restarts. PostgreSQL stores durable records and enforces rules such as “an enrolment must belong to an existing student.”

**Basic vocabulary**

| Term | Meaning | Example |
|---|---|---|
| Database | Collection of related data | `academy_dev` |
| Schema | Namespace for objects inside a database | `public` |
| Table | Records about one entity | `students` |
| Row | One record | One student |
| Column | One attribute | `email` |
| Primary key | Unique row identifier | `student_id` |
| Foreign key | Reference to another table | `enrollments.student_id` |
| Constraint | Database-enforced rule | Unique email |
| Query | Request to the DBMS | List enrolled students |
| Transaction | Group of operations that succeed or fail together | Create payment + enrolment |

**Relational vs document vs key–value:** relational databases excel when records have relationships, structured rules, and transactional consistency. Document stores can be useful for flexible nested documents; key–value stores for fast caching. PostgreSQL also supports JSONB, so this is not an either/or choice.

### How a web/mobile app connects

```mermaid
flowchart LR
    A[Web browser or mobile app] -->|HTTPS| B[Backend API]
    B -->|SQL over secure connection| C[(PostgreSQL)]
    B -->|JSON response| A
```

**Critical security rule:** A mobile app or browser should **not** connect directly using a privileged PostgreSQL username and password. The backend handles authorisation and uses restricted DB credentials.

**Try it yourself:** Identify three entities for a food delivery app. **Suggested answer:** `customers`, `restaurants`, `orders` (plus `order_items`, `payments`, etc.).

## Chapter 2 — Install PostgreSQL and your tools

Install the PostgreSQL server and `psql` command-line client from the official PostgreSQL distribution or your operating system's package manager. Optional: pgAdmin, DBeaver, or VS Code SQL extension. On macOS, Postgres.app is a convenient option; on Linux, package-managed PostgreSQL is common; on Windows, the official installer works well.

Check installation:

```bash
psql --version
```

Connect using a role you control (your installation may use another admin role):

```bash
psql -h localhost -U postgres -d postgres
```

Inside `psql` (these are **psql commands**, not SQL):

```text
\conninfo       -- connection information
\l              -- list databases
\du             -- list roles
\dt             -- list tables
\d students     -- describe a table (once created)
\q              -- exit
```

If the server is not running, start it through your OS service manager or Postgres.app. If password authentication fails, verify your actual role, host, port and authentication configuration; do not disable authentication as a shortcut.

Create a **practice-only** database from a role with `CREATEDB` privilege:

```sql
CREATE DATABASE academy_dev;
```

Reconnect: `psql -h localhost -U postgres -d academy_dev`. In pgAdmin, create the database from the Databases context menu, then open Query Tool connected to it.

**Common beginner errors:** `psql: command not found` (client missing or PATH issue); `connection refused` (server stopped or wrong port); `role does not exist` (wrong username); `permission denied to create database` (insufficient privilege).

## Chapter 3 — From product requirements to an ER diagram

### Step 1: Write plain-language requirements

- A learner has an account and can enrol in multiple courses.
- A course has many lessons and an instructor.
- A learner can enrol only once per course.
- Each enrolment records status and enrolment time.
- A learner can complete each lesson at most once.
- A payment belongs to a learner and may be associated with an enrolment.

### Step 2: Find nouns (candidate entities)

`users`, `courses`, `lessons`, `enrollments`, `lesson_progress`, `payments`.

### Step 3: Identify cardinality

- One user → many authored courses (1:N).
- One course → many lessons (1:N).
- Many users ↔ many courses (M:N), implemented using `enrollments`.
- One user → many payments (1:N).

```mermaid
erDiagram
    USERS ||--o{ COURSES : teaches
    USERS ||--o{ ENROLLMENTS : makes
    COURSES ||--o{ ENROLLMENTS : has
    COURSES ||--o{ LESSONS : contains
    USERS ||--o{ LESSON_PROGRESS : records
    LESSONS ||--o{ LESSON_PROGRESS : tracks
    USERS ||--o{ PAYMENTS : makes
    ENROLLMENTS o|--o{ PAYMENTS : associated_with
```

### Step 4: Pick keys and constraints

Each entity needs a stable primary key. Business rules become `UNIQUE`, `NOT NULL`, `CHECK`, and foreign-key constraints. Choose meaningful data types: money as `NUMERIC(12,2)` or integer minor units; timestamps as `TIMESTAMPTZ`; email as `TEXT` with a normalised uniqueness strategy.

**Try it yourself:** Why not put `course1`, `course2`, `course3` columns on `users`? **Solution:** It imposes a fixed limit, duplicates structure, complicates querying and violates sound relational design. Use `enrollments(user_id, course_id)`.

## Chapter 4 — Normalisation without the jargon overload

**First normal form (1NF):** values are atomic for the application's purpose; do not store comma-separated course IDs in a single cell. **Second normal form (2NF):** non-key attributes depend on the whole candidate key, not part of a composite key. **Third normal form (3NF):** non-key attributes should not depend transitively on other non-key attributes.

**Bad design:**

| student_id | student_name | course_id | course_title | instructor_email |
|---|---|---|---|---|
| 1 | Ada | 10 | Python | teacher@example.com |
| 1 | Ada | 11 | SQL | teacher2@example.com |

Student name repeats; course titles repeat. Changing a title in one row but not another creates an update anomaly.

**Better design:** `users`, `courses`, `enrollments`. Each fact has one primary home, and keys link related facts.

**When denormalisation is justified:** measured performance needs, analytics, or carefully maintained summary tables. First design for correctness; optimise from evidence.

**Challenge:** A shopping cart table stores `product_name`, `unit_price`, `quantity`, `customer_address`. Which values should be snapshots? **Answer:** Order items commonly snapshot product name and charged price at purchase time because historical receipts must remain accurate; customer delivery address is commonly captured on the order, not read live from the user's current address.

---

# PART II — POSTGRESQL SQL FROM FIRST PRINCIPLES

## Chapter 5 — SQL grammar, data types, and schema creation

SQL statements normally end with `;`. Keywords are case-insensitive, but use uppercase for readability. PostgreSQL folds unquoted identifiers to lowercase; prefer `snake_case` names without spaces.

**Frequently used types:** `BIGINT`, `INTEGER`, `NUMERIC(p,s)`, `TEXT`, `VARCHAR(n)`, `BOOLEAN`, `DATE`, `TIMESTAMPTZ`, `UUID`, `JSONB`. Prefer `GENERATED ... AS IDENTITY` for numeric auto-generated keys. Use `TIMESTAMPTZ` for real instants; display in the user's timezone in your app.

### Our main schema — run in a fresh `academy_dev` database

```sql
CREATE TABLE users (
    user_id BIGINT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    full_name TEXT NOT NULL CHECK (length(trim(full_name)) >= 2),
    email TEXT NOT NULL,
    role TEXT NOT NULL DEFAULT 'student'
         CHECK (role IN ('student', 'instructor', 'admin')),
    created_at TIMESTAMPTZ NOT NULL DEFAULT now(),
    CONSTRAINT users_email_not_blank CHECK (length(trim(email)) > 3)
);

CREATE UNIQUE INDEX users_email_ci_uq ON users (lower(email));

CREATE TABLE courses (
    course_id BIGINT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    instructor_id BIGINT NOT NULL REFERENCES users(user_id),
    title TEXT NOT NULL,
    price NUMERIC(12,2) NOT NULL DEFAULT 0 CHECK (price >= 0),
    published BOOLEAN NOT NULL DEFAULT FALSE,
    created_at TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE lessons (
    lesson_id BIGINT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    course_id BIGINT NOT NULL REFERENCES courses(course_id) ON DELETE CASCADE,
    title TEXT NOT NULL,
    position INTEGER NOT NULL CHECK (position > 0),
    UNIQUE (course_id, position),
    UNIQUE (lesson_id, course_id)
);

CREATE TABLE enrollments (
    enrollment_id BIGINT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    user_id BIGINT NOT NULL REFERENCES users(user_id),
    course_id BIGINT NOT NULL REFERENCES courses(course_id),
    status TEXT NOT NULL DEFAULT 'active'
           CHECK (status IN ('active', 'completed', 'cancelled')),
    enrolled_at TIMESTAMPTZ NOT NULL DEFAULT now(),
    UNIQUE (user_id, course_id),
    UNIQUE (enrollment_id, user_id, course_id)
);

CREATE TABLE lesson_progress (
    user_id BIGINT NOT NULL,
    course_id BIGINT NOT NULL,
    lesson_id BIGINT NOT NULL,
    completed_at TIMESTAMPTZ NOT NULL DEFAULT now(),
    PRIMARY KEY (user_id, lesson_id),
    FOREIGN KEY (user_id, course_id)
        REFERENCES enrollments(user_id, course_id),
    FOREIGN KEY (lesson_id, course_id)
        REFERENCES lessons(lesson_id, course_id)
);

CREATE TABLE payments (
    payment_id BIGINT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    user_id BIGINT NOT NULL REFERENCES users(user_id),
    enrollment_id BIGINT,
    amount NUMERIC(12,2) NOT NULL CHECK (amount >= 0),
    currency CHAR(3) NOT NULL DEFAULT 'NGN',
    provider_reference TEXT UNIQUE,
    status TEXT NOT NULL CHECK (status IN ('pending', 'paid', 'failed', 'refunded')),
    paid_at TIMESTAMPTZ,
    created_at TIMESTAMPTZ NOT NULL DEFAULT now(),
    FOREIGN KEY (enrollment_id, user_id)
        REFERENCES enrollments(enrollment_id, user_id)
);
```

**Why composite foreign keys?** They prevent a progress record from pointing to a lesson in a different course, and prevent a payment from being linked to another user's enrolment. Constraints are not just documentation: PostgreSQL enforces them.

**Instructor-role caveat:** The schema does not yet enforce that `courses.instructor_id` refers to a user whose `role = 'instructor'`. That is a cross-row business rule; enforce it in a controlled application workflow or a carefully designed trigger/role model.

**Try it yourself:** Add a non-negative estimated duration to `lessons`.

**Solution:**

```sql
ALTER TABLE lessons
ADD COLUMN duration_minutes INTEGER CHECK (duration_minutes >= 0);
```

## Chapter 6 — INSERT, SELECT, UPDATE and DELETE (CRUD)

**C**reate, **R**ead, **U**pdate, **D**elete are the basic operations of most apps.

```sql
INSERT INTO users (full_name, email, role) VALUES
('Ada Okafor', 'ada@example.com', 'student'),
('Tunde Bello', 'tunde@example.com', 'student'),
('Nneka Obi', 'nneka@example.com', 'instructor')
RETURNING user_id, full_name;

INSERT INTO courses (instructor_id, title, price, published)
SELECT user_id, 'Practical PostgreSQL', 25000.00, TRUE
FROM users WHERE email = 'nneka@example.com'
RETURNING course_id, title;

INSERT INTO lessons (course_id, title, position)
SELECT course_id, 'Getting Started', 1 FROM courses
WHERE title = 'Practical PostgreSQL';

INSERT INTO lessons (course_id, title, position)
SELECT course_id, 'SQL Basics', 2 FROM courses
WHERE title = 'Practical PostgreSQL';

INSERT INTO enrollments (user_id, course_id)
SELECT u.user_id, c.course_id
FROM users u CROSS JOIN courses c
WHERE u.email = 'ada@example.com'
  AND c.title = 'Practical PostgreSQL';

SELECT user_id, full_name, email FROM users ORDER BY user_id;

UPDATE users SET full_name = 'Ada C. Okafor'
WHERE email = 'ada@example.com'
RETURNING user_id, full_name;

-- Safe DELETE demonstration: run in a transaction and undo it.
BEGIN;
DELETE FROM users WHERE email = 'tunde@example.com' RETURNING *;
ROLLBACK;
```

**Golden rule:** Always inspect your `WHERE` clause before `UPDATE` or `DELETE`. Without `WHERE`, every row may be affected. A `DELETE` can also fail if foreign keys protect referenced rows; this is a feature, not a bug.

**Try it yourself:** List only published courses costing less than ₦30,000.

```sql
SELECT title, price FROM courses
WHERE published = TRUE AND price < 30000
ORDER BY price ASC;
```

## Chapter 7 — Filtering, sorting, NULL, patterns and pagination

```sql
SELECT * FROM courses WHERE price BETWEEN 10000 AND 50000;
SELECT * FROM users WHERE role IN ('student', 'instructor');
SELECT * FROM users WHERE email ILIKE '%@example.com';
SELECT * FROM payments WHERE paid_at IS NULL;
SELECT title, price FROM courses ORDER BY price DESC, course_id ASC;
SELECT course_id, title FROM courses ORDER BY course_id LIMIT 10 OFFSET 20;
```

**NULL** means unknown/missing, not zero or an empty string. `= NULL` does not work; use `IS NULL`. `COALESCE(x, fallback)` supplies a default in query results.

For large datasets, prefer **keyset pagination** over huge offsets:

```sql
SELECT course_id, title FROM courses
WHERE course_id > 100
ORDER BY course_id
LIMIT 20;
```

**Try it yourself:** Find users whose email contains `gmail`.

```sql
SELECT full_name, email FROM users WHERE email ILIKE '%gmail%';
```

## Chapter 8 — JOINs: connecting related tables

A `JOIN` matches rows based on keys. `INNER JOIN` returns matches; `LEFT JOIN` preserves all rows from the left table even if there is no match. Avoid accidental Cartesian products by writing explicit join conditions.

```sql
SELECT u.full_name AS learner, c.title AS course, e.enrolled_at
FROM enrollments e
JOIN users u ON u.user_id = e.user_id
JOIN courses c ON c.course_id = e.course_id
ORDER BY e.enrolled_at DESC;

-- Include courses even if nobody has enrolled yet.
SELECT c.title, COUNT(e.enrollment_id) AS total_enrollments
FROM courses c
LEFT JOIN enrollments e ON e.course_id = c.course_id
GROUP BY c.course_id, c.title
ORDER BY total_enrollments DESC;
```

**Important:** With a `LEFT JOIN`, `COUNT(*)` counts the preserved course row even if no enrolment exists; `COUNT(e.enrollment_id)` correctly counts only matching enrolments.

**Try it yourself:** Show course titles and instructor names.

```sql
SELECT c.title, u.full_name AS instructor
FROM courses c JOIN users u ON c.instructor_id = u.user_id;
```

## Chapter 9 — Aggregation, GROUP BY, HAVING and subqueries

```sql
SELECT status, COUNT(*) AS count, SUM(amount) AS total
FROM payments GROUP BY status;

SELECT c.title, COUNT(e.enrollment_id) AS students
FROM courses c LEFT JOIN enrollments e ON e.course_id = c.course_id
GROUP BY c.course_id, c.title
HAVING COUNT(e.enrollment_id) >= 1;

-- Courses above the average course price.
SELECT title, price FROM courses
WHERE price > (SELECT AVG(price) FROM courses);

-- Students with at least one enrolment.
SELECT u.full_name FROM users u
WHERE EXISTS (SELECT 1 FROM enrollments e WHERE e.user_id = u.user_id);
```

`WHERE` filters rows **before** grouping; `HAVING` filters groups **after** aggregation.

## Chapter 10 — CTEs, window functions, CASE and JSONB

A common table expression (`WITH`) names a temporary query result. Window functions compute values across related rows without collapsing each row into one group.

```sql
WITH course_counts AS (
  SELECT course_id, COUNT(*) AS learner_count
  FROM enrollments GROUP BY course_id
)
SELECT c.title, COALESCE(cc.learner_count, 0) AS learners
FROM courses c LEFT JOIN course_counts cc USING (course_id);

SELECT title, price,
       DENSE_RANK() OVER (ORDER BY price DESC) AS price_rank
FROM courses;

SELECT title, price,
       CASE WHEN price = 0 THEN 'Free' ELSE 'Paid' END AS category
FROM courses;
```

**JSONB:** useful for flexible supplemental metadata, but not a replacement for proper tables and foreign keys.

```sql
ALTER TABLE courses ADD COLUMN metadata JSONB NOT NULL DEFAULT '{}'::jsonb;
UPDATE courses SET metadata = '{"level":"beginner","language":"English"}'::jsonb
WHERE title = 'Practical PostgreSQL';
SELECT title FROM courses WHERE metadata @> '{"level":"beginner"}'::jsonb;
```

---

# PART III — DESIGNING RELIABLE APPLICATION DATABASES

## Chapter 11 — Transactions and ACID

A transaction groups related changes. **Atomicity:** all-or-nothing. **Consistency:** rules remain valid. **Isolation:** concurrent operations are controlled. **Durability:** committed changes survive according to PostgreSQL's durability guarantees.

```sql
BEGIN;
INSERT INTO payments (user_id, amount, currency, status, provider_reference)
SELECT user_id, 25000, 'NGN', 'pending', 'demo-payment-001'
FROM users WHERE email = 'ada@example.com';
-- Inspect results before committing a real transaction.
ROLLBACK;
```

`COMMIT` persists; `ROLLBACK` undoes changes in the transaction. Use `SAVEPOINT` for partial rollback inside a transaction.

**Real payment safety:** A payment provider's successful webhook must be verified server-side; payment events must be idempotent; never mark payment as successful because a client says so. An enrolment grant and verified payment state should be updated together where practical. Never keep a DB transaction open while waiting for a remote payment provider.

## Chapter 12 — Constraints, UPSERT, views and generated values

```sql
-- Safe retry: do not create duplicate enrolments.
INSERT INTO enrollments (user_id, course_id)
SELECT u.user_id, c.course_id
FROM users u CROSS JOIN courses c
WHERE u.email = 'ada@example.com'
  AND c.title = 'Practical PostgreSQL'
ON CONFLICT (user_id, course_id) DO NOTHING;

CREATE VIEW published_course_catalog AS
SELECT course_id, title, price
FROM courses WHERE published = TRUE;

SELECT * FROM published_course_catalog;
```

`ON CONFLICT` handles specified uniqueness conflicts, not every possible error. A view simplifies reuse but does not automatically provide security isolation; consider permissions and PostgreSQL view security behaviour carefully.

**Challenge:** Prevent duplicate lesson positions within a course. **Answer:** `UNIQUE (course_id, position)` in the schema already enforces this.

## Chapter 13 — Indexes and query performance

An index is like a book index: it speeds up certain lookups at the cost of disk space and write overhead. PostgreSQL automatically creates indexes for primary-key and unique constraints, **but not generally for referencing foreign-key columns**.

```sql
CREATE INDEX enrollments_course_id_idx ON enrollments (course_id);
CREATE INDEX enrollments_user_id_idx ON enrollments (user_id);
CREATE INDEX lessons_course_position_idx ON lessons (course_id, position);
CREATE INDEX payments_user_created_idx ON payments (user_id, created_at DESC);

EXPLAIN (ANALYZE, BUFFERS)
SELECT * FROM enrollments WHERE course_id = 1;
```

**Read an execution plan:** look for sequential scans vs index scans, estimated vs actual row counts, expensive sorts, and total execution time. A sequential scan can be optimal for tiny tables; index usage is not automatically better.

`EXPLAIN ANALYZE` **executes** the query. On data-changing statements, it can change data unless you explicitly wrap it in a transaction and roll back. Use care.

**Try it yourself:** Why not index every column? **Answer:** indexes consume storage, slow writes, and require maintenance; create them for real query patterns supported by measurement.

## Chapter 14 — Concurrency, locking and isolation

Two requests may attempt to reserve the last seat simultaneously. A naïve “read available seats, then update” can oversell. Use a single conditional `UPDATE` or appropriate row locks inside a transaction.

```sql
CREATE TABLE workshop_seats (
    workshop_id BIGINT PRIMARY KEY,
    available_seats INTEGER NOT NULL CHECK (available_seats >= 0)
);
INSERT INTO workshop_seats VALUES (1, 2);

-- Atomic reservation: succeeds only when seats remain.
UPDATE workshop_seats
SET available_seats = available_seats - 1
WHERE workshop_id = 1 AND available_seats > 0
RETURNING available_seats;
```

If zero rows return, no seat was reserved. This conditional update avoids the common lost-update pattern for this use case. Other workflows may require `SELECT ... FOR UPDATE`, optimistic version columns, or stronger transaction isolation. Know deadlocks, lock timeouts, and retryable errors (`40001` serialization failure, `40P01` deadlock detected).

## Chapter 15 — Schema migrations and version control

A migration is a reproducible change to database structure. Never rely on manually clicking through production database changes with no record.

Suggested structure:

```text
academy-platform/
├── backend/
├── database/
│   ├── migrations/
│   │   ├── 001_initial_schema.sql
│   │   ├── 002_course_metadata.sql
│   │   └── 003_indexes.sql
│   ├── seeds/
│   │   └── development_seed.sql
│   └── README.md
└── .env.example
```

**Expand–migrate–contract strategy:** (1) add a new nullable column; (2) deploy code that writes old and new formats if necessary; (3) backfill; (4) switch readers; (5) enforce constraints; (6) remove the old column in a later deployment. Avoid destructive changes in the same release as code that still depends on the old schema.

Example migration:

```sql
ALTER TABLE users ADD COLUMN display_name TEXT;
UPDATE users SET display_name = full_name WHERE display_name IS NULL;
```

For production, use a migration framework (e.g. Alembic for SQLAlchemy or a framework-native tool), code review, backups, and a staging rehearsal. PostgreSQL supports transactional DDL for many changes, but not all operations can run inside a transaction (e.g. `CREATE INDEX CONCURRENTLY`).

## Chapter 16 — Backend integration: FastAPI + psycopg

The browser/mobile app calls your API; the API queries PostgreSQL. Use a dedicated least-privilege DB role and environment-based secrets. Install in a Python virtual environment:

```bash
python -m venv .venv
source .venv/bin/activate       # Windows PowerShell: .venv\Scripts\Activate.ps1
pip install fastapi uvicorn 'psycopg[binary]' python-dotenv
```

Local `.env` (never commit real credentials):

```dotenv
DATABASE_URL=postgresql://academy_app:YOUR_LOCAL_PASSWORD@localhost:5432/academy_dev
```

A minimal **read-only demonstration** (`main.py`):

```python
import os
from contextlib import asynccontextmanager
from fastapi import FastAPI, HTTPException
from psycopg_pool import ConnectionPool
from psycopg.rows import dict_row

pool = None

@asynccontextmanager
async def lifespan(app: FastAPI):
    global pool
    pool = ConnectionPool(
        conninfo=os.environ['DATABASE_URL'],
        min_size=1, max_size=5,
        kwargs={'row_factory': dict_row},
        open=True,
    )
    yield
    pool.close()

app = FastAPI(lifespan=lifespan)

@app.get('/courses')
def list_courses():
    with pool.connection() as conn:
        with conn.cursor() as cur:
            cur.execute("""
                SELECT course_id, title, price
                FROM published_course_catalog
                ORDER BY course_id
            """)
            return cur.fetchall()

@app.get('/courses/{course_id}')
def get_course(course_id: int):
    with pool.connection() as conn:
        with conn.cursor() as cur:
            cur.execute("""
                SELECT course_id, title, price
                FROM published_course_catalog
                WHERE course_id = %s
            """, (course_id,))
            result = cur.fetchone()
    if result is None:
        raise HTTPException(status_code=404, detail='Course not found')
    return result
```

Install the pool dependency too:

```bash
pip install 'psycopg[pool]'
# Load .env into the environment using your preferred method before running.
uvicorn main:app --reload
```

**Important:** This snippet is an instructional starting point, not a production-ready service. Production apps require authentication, authorisation, structured error handling, migrations, timeouts, health checks, deployment configuration, and tests. Use bound parameters (`%s`, values tuple) to prevent SQL injection; never build SQL by concatenating untrusted user input. The sample `academy_app` role must be created and granted permissions separately.

**Example role setup (run as an authorised DB administrator; adapt to your environment):**

```sql
CREATE ROLE academy_app LOGIN PASSWORD 'REPLACE_WITH_STRONG_SECRET';
GRANT CONNECT ON DATABASE academy_dev TO academy_app;
GRANT USAGE ON SCHEMA public TO academy_app;
GRANT SELECT ON published_course_catalog TO academy_app;
```

Use your operating system's secret store or deployment secrets in real environments. For a read-only endpoint, do **not** grant write permissions unnecessarily. The sample role may need view access to underlying tables depending on view ownership and security configuration; test actual permissions.

---

# PART IV — DATABASE SECURITY, OPERATIONS & QUALITY

## Chapter 17 — Authentication, authorisation and least privilege

Separate PostgreSQL **roles** from application **users**. A DB role authenticates your backend to PostgreSQL; app users authenticate to your API. The API decides which student can view which records.

**Security checklist:** strong secrets; TLS for remote DB connections; no credentials in Git; restrict network access; separate dev/staging/prod; minimal privileges; patch PostgreSQL; audit sensitive access; validate inputs; use parameterised SQL; apply rate limits and API auth; never trust a `user_id` supplied by a client as proof of identity.

### Row-level security (advanced introduction)

```sql
-- Illustrative policy; DO NOT apply until you have designed role/session identity handling.
-- ALTER TABLE enrollments ENABLE ROW LEVEL SECURITY;
-- CREATE POLICY learner_own_enrollments ON enrollments
-- FOR SELECT USING (user_id = current_setting('app.current_user_id', true)::bigint);
```

RLS is powerful but easy to misuse. Session identity must be set by trusted server code, scoped to a transaction, and cleared reliably with connection pooling. Table owners and privileged roles can bypass RLS under certain conditions. Treat RLS as an additional layer, not a replacement for API authorisation.

## Chapter 18 — Backups, restoration and disaster recovery

**A backup is only useful if you have tested restoration.**

```bash
# Custom-format logical backup
pg_dump -h localhost -U postgres -Fc -d academy_dev -f academy_dev.backup

# Create an empty restore target (requires suitable privileges)
createdb -h localhost -U postgres academy_restore_test

# Restore into a DIFFERENT practice database
pg_restore -h localhost -U postgres -d academy_restore_test academy_dev.backup

# Inspect restored tables
psql -h localhost -U postgres -d academy_restore_test -c '\dt'
```

`pg_dump` is useful for logical backups. For larger production deployments and point-in-time recovery (PITR), plan physical base backups and WAL archiving or use a managed service with tested PITR. Decide recovery point objective (RPO: acceptable data loss) and recovery time objective (RTO: acceptable outage). Store encrypted backups separately, restrict access, rotate them, and test restoration regularly.

**Safety:** Restoring can overwrite or duplicate data depending on flags and target. Always inspect target DB and restore options; this example uses a separate test database intentionally.

## Chapter 19 — Monitoring and routine maintenance

Monitor connection usage, query latency, lock waits, storage growth, dead tuples, replication lag (if applicable), and backup success. PostgreSQL has internal statistics views:

```sql
SELECT datname, numbackends, xact_commit, xact_rollback
FROM pg_stat_database
WHERE datname = current_database();

SELECT pid, state, wait_event_type, wait_event,
       now() - query_start AS running_for
FROM pg_stat_activity
WHERE datname = current_database()
ORDER BY running_for DESC NULLS LAST;

SELECT relname, n_live_tup, n_dead_tup
FROM pg_stat_user_tables
ORDER BY n_dead_tup DESC;
```

Autovacuum prevents table bloat and supports transaction ID maintenance. Do not disable it casually. `VACUUM (ANALYZE)` may help in particular situations; `VACUUM FULL` takes an exclusive lock and rewrites a table, so plan downtime if you truly need it. Use `ANALYZE` to refresh planner statistics after unusual bulk loads.

## Chapter 20 — Testing database behaviour

Test constraints, queries, transactions, migrations, and permissions—not only application screens.

**Constraint test (should fail; isolate in a transaction):**

```sql
BEGIN;
INSERT INTO users (full_name, email) VALUES ('Test User', 'ada@example.com');
-- Expect unique violation because case-insensitive email index already exists.
ROLLBACK;
```

**Caution:** Once a statement errors inside a transaction, PostgreSQL marks that transaction aborted; issue `ROLLBACK` before continuing. The test assumes the seed row exists.

**Testing layers:** unit tests for business logic; integration tests against a disposable PostgreSQL DB; migration tests; performance tests with representative data; authorisation tests; backup restore drills. Do not run integration tests against live customer records.

## Chapter 21 — Production deployment patterns

Typical environments: local developer DB → CI test DB → staging DB → production DB. Use infrastructure-managed secrets and private networking. Prefer managed PostgreSQL when operational capacity is limited; understand backups, failover, patching, maintenance windows and cost.

**Connection pooling:** use application-side pooling (or PgBouncer where appropriate). Too many open connections can exhaust server resources. **Read replicas** help some read-heavy workloads but can lag; do not assume a just-written record is immediately visible on a replica. **Caching** reduces repeat reads but creates invalidation challenges. **Multi-tenancy:** choose shared tables with tenant IDs, schemas per tenant, or DB per tenant based on isolation, cost, and operational requirements.

**Production release checklist:** reviewed migration; tested rollback/forward-fix strategy; recent verified backup; monitoring and alerts; performance plan; least-privilege role; TLS; API auth; staging smoke tests; restore procedure; on-call ownership.

---

# PART V — COMPLETE CAPSTONE AND PROGRESSIVE WORKED EXAMPLES

## Chapter 22 — Build the Academy platform database step by step

**Goal:** Support learner registration, course catalogue, enrolment, lessons, progress and payment records. Use the Chapter 5 schema as the starting point.

**Acceptance criteria:**

1. No duplicate emails ignoring case.
2. No duplicate enrolments for the same user/course.
3. Lessons cannot have duplicate positions within a course.
4. A learner cannot complete a lesson belonging to a different course than their enrolment.
5. A payment cannot be attached to someone else's enrolment.
6. Published course listing excludes unpublished courses.
7. Queries are parameterised in backend code.
8. Backup can be restored to a fresh test DB.

### Step A — Add realistic seed data

```sql
INSERT INTO users (full_name, email, role) VALUES
('Chidi Nwosu', 'chidi@example.com', 'student'),
('Fatima Musa', 'fatima@example.com', 'student')
ON CONFLICT DO NOTHING;

INSERT INTO enrollments (user_id, course_id)
SELECT u.user_id, c.course_id
FROM users u CROSS JOIN courses c
WHERE u.email = 'chidi@example.com'
  AND c.title = 'Practical PostgreSQL'
ON CONFLICT (user_id, course_id) DO NOTHING;
```

### Step B — Record progress correctly

```sql
INSERT INTO lesson_progress (user_id, course_id, lesson_id)
SELECT e.user_id, e.course_id, l.lesson_id
FROM enrollments e
JOIN users u ON u.user_id = e.user_id
JOIN courses c ON c.course_id = e.course_id
JOIN lessons l ON l.course_id = e.course_id
WHERE u.email = 'ada@example.com'
  AND c.title = 'Practical PostgreSQL'
  AND l.position = 1
ON CONFLICT (user_id, lesson_id) DO NOTHING;
```

### Step C — Calculate completion percentage

```sql
SELECT u.full_name, c.title,
       COUNT(DISTINCT lp.lesson_id) AS lessons_done,
       COUNT(DISTINCT l.lesson_id) AS total_lessons,
       ROUND(100.0 * COUNT(DISTINCT lp.lesson_id)
             / NULLIF(COUNT(DISTINCT l.lesson_id), 0), 1) AS completion_pct
FROM enrollments e
JOIN users u ON u.user_id = e.user_id
JOIN courses c ON c.course_id = e.course_id
LEFT JOIN lessons l ON l.course_id = c.course_id
LEFT JOIN lesson_progress lp
       ON lp.user_id = e.user_id AND lp.lesson_id = l.lesson_id
WHERE u.email = 'ada@example.com'
GROUP BY u.user_id, u.full_name, c.course_id, c.title;
```

**Why `NULLIF`?** Prevents division by zero when a course has no lessons. `COUNT(DISTINCT ...)` avoids duplicate counts if joins multiply rows.

### Step D — Test failure cases

Attempt a duplicate email, a duplicate enrolment, a negative course price, and a lesson position of zero. Record the exact PostgreSQL error and explain which constraint caught it. Run each failing statement separately; if testing inside `BEGIN`, `ROLLBACK` before the next one.

### Step E — Deliverables

`schema.sql`, `seed.sql`, `queries.sql`, `README.md`, ER diagram, 5 API endpoints (at least read-only), screenshots of successful queries, tests, and a restore-test log. Include sample environment variables but **never** commit actual passwords.

## Chapter 23 — 18 worked examples from beginner to advanced

Every example below is a small standalone challenge. Unless otherwise stated, run it against the Chapter 5 schema after inserting the sample data.


### Worked example 01 · List every student

**Problem:** Read all students alphabetically.

**Solution (SQL):**

```sql
SELECT user_id, full_name FROM users WHERE role = 'student' ORDER BY full_name;
```

**Why it works:** Filter on `role`, then sort.

**Practice extension:** Add a second sort key for ties.


### Worked example 02 · Find free courses

**Problem:** Return courses with a zero price.

**Solution (SQL):**

```sql
SELECT course_id, title FROM courses WHERE price = 0;
```

**Why it works:** A numeric comparison is clearer than comparing formatted currency strings.

**Practice extension:** Return only published free courses.


### Worked example 03 · Find an email case-insensitively

**Problem:** Find the account even if input case differs.

**Solution (SQL):**

```sql
SELECT user_id, full_name FROM users WHERE lower(email) = lower('ADA@EXAMPLE.COM');
```

**Why it works:** Matches the normalised unique index expression.

**Practice extension:** Explain why `lower(email)` index matters.


### Worked example 04 · Insert a new course

**Problem:** Add a course by looking up its instructor.

**Solution (SQL):**

```sql
INSERT INTO courses (instructor_id, title, price) SELECT user_id, 'Intro to APIs', 15000 FROM users WHERE email = 'nneka@example.com' RETURNING course_id;
```

**Why it works:** Uses `INSERT ... SELECT` rather than assuming an instructor ID.

**Practice extension:** Publish it using `UPDATE`.


### Worked example 05 · List all lessons in order

**Problem:** Fetch a course curriculum.

**Solution (SQL):**

```sql
SELECT l.position, l.title FROM lessons l JOIN courses c USING (course_id) WHERE c.title = 'Practical PostgreSQL' ORDER BY l.position;
```

**Why it works:** The position column determines display order.

**Practice extension:** Add `duration_minutes` to the output.


### Worked example 06 · Count learners per course

**Problem:** Include courses with zero learners.

**Solution (SQL):**

```sql
SELECT c.title, COUNT(e.enrollment_id) AS learner_count FROM courses c LEFT JOIN enrollments e USING (course_id) GROUP BY c.course_id, c.title;
```

**Why it works:** A `LEFT JOIN` preserves empty courses.

**Practice extension:** Sort by highest count.


### Worked example 07 · Enrol a learner safely

**Problem:** Avoid duplicate records.

**Solution (SQL):**

```sql
INSERT INTO enrollments (user_id, course_id) SELECT u.user_id, c.course_id FROM users u CROSS JOIN courses c WHERE u.email = 'fatima@example.com' AND c.title = 'Practical PostgreSQL' ON CONFLICT (user_id, course_id) DO NOTHING;
```

**Why it works:** The unique constraint makes retries idempotent.

**Practice extension:** Return the created row on the first attempt.


### Worked example 08 · Find learners not enrolled

**Problem:** Use an anti-join.

**Solution (SQL):**

```sql
SELECT u.full_name FROM users u WHERE u.role = 'student' AND NOT EXISTS (SELECT 1 FROM enrollments e WHERE e.user_id = u.user_id);
```

**Why it works:** `NOT EXISTS` expresses the absence of related rows.

**Practice extension:** Restrict to learners not enrolled in one particular course.


### Worked example 09 · Compute average course price

**Problem:** Use an aggregate.

**Solution (SQL):**

```sql
SELECT ROUND(AVG(price), 2) AS average_price FROM courses;
```

**Why it works:** `AVG` ignores NULL values; our price column is non-null.

**Practice extension:** Compute only published courses.


### Worked example 10 · Categorise prices

**Problem:** Use CASE expressions.

**Solution (SQL):**

```sql
SELECT title, CASE WHEN price = 0 THEN 'Free' WHEN price < 20000 THEN 'Budget' ELSE 'Premium' END AS tier FROM courses;
```

**Why it works:** CASE branches are tested in order.

**Practice extension:** Introduce a middle tier.


### Worked example 11 · Show enrolment timeline

**Problem:** Combine tables and sort timestamps.

**Solution (SQL):**

```sql
SELECT u.full_name, c.title, e.enrolled_at FROM enrollments e JOIN users u USING (user_id) JOIN courses c USING (course_id) ORDER BY e.enrolled_at DESC;
```

**Why it works:** Useful for admin activity feeds.

**Practice extension:** Limit to the most recent five.


### Worked example 12 · Rank courses by price

**Problem:** Use a window function.

**Solution (SQL):**

```sql
SELECT title, price, DENSE_RANK() OVER (ORDER BY price DESC) AS rank FROM courses;
```

**Why it works:** Equal prices receive equal ranks.

**Practice extension:** Rank only published courses.


### Worked example 13 · Find duplicate business data

**Problem:** Audit case-insensitive emails.

**Solution (SQL):**

```sql
SELECT lower(email) AS normalized_email, COUNT(*) FROM users GROUP BY lower(email) HAVING COUNT(*) > 1;
```

**Why it works:** Expected no rows because a unique index prevents duplicates.

**Practice extension:** Try on a deliberately unconstrained scratch table.


### Worked example 14 · Upsert a preference

**Problem:** Use an isolated demonstration table.

**Solution (SQL):**

```sql
CREATE TEMP TABLE preferences (user_id BIGINT PRIMARY KEY, theme TEXT NOT NULL); INSERT INTO preferences VALUES (1, 'light') ON CONFLICT (user_id) DO UPDATE SET theme = EXCLUDED.theme;
```

**Why it works:** A temporary table exists only for the current session.

**Practice extension:** Repeat with theme `dark`.


### Worked example 15 · Reserve limited inventory

**Problem:** Make an atomic conditional update.

**Solution (SQL):**

```sql
UPDATE workshop_seats SET available_seats = available_seats - 1 WHERE workshop_id = 1 AND available_seats > 0 RETURNING available_seats;
```

**Why it works:** Requires the Chapter 14 workshop demo setup.

**Practice extension:** Run until no rows return.


### Worked example 16 · Diagnose a slow lookup

**Problem:** Examine the query plan.

**Solution (SQL):**

```sql
EXPLAIN (ANALYZE, BUFFERS) SELECT * FROM enrollments WHERE course_id = 1;
```

**Why it works:** Plan choices depend on table size and statistics.

**Practice extension:** Compare before and after adding an index.


### Worked example 17 · Find students with progress

**Problem:** Use EXISTS and two relationships.

**Solution (SQL):**

```sql
SELECT u.full_name FROM users u WHERE EXISTS (SELECT 1 FROM lesson_progress lp WHERE lp.user_id = u.user_id);
```

**Why it works:** EXISTS stops at existence rather than counting all rows.

**Practice extension:** Find students with no progress.


### Worked example 18 · Build a course progress report

**Problem:** Aggregate completed lessons.

**Solution (SQL):**

```sql
SELECT e.enrollment_id, c.title, COUNT(DISTINCT lp.lesson_id) AS completed FROM enrollments e JOIN courses c USING (course_id) LEFT JOIN lesson_progress lp ON lp.user_id = e.user_id AND lp.course_id = e.course_id GROUP BY e.enrollment_id, c.title ORDER BY completed DESC;
```

**Why it works:** Grouping by enrolment makes one result row per enrolment.

**Practice extension:** Extend it with total lessons and percentage.


## Chapter 24 — Exercises, worked answers and mastery checklist

### Beginner exercises

**B1.** Add a `bio` column to users, optional text.  
**B2.** List courses sorted by newest first.  
**B3.** Find learners with email domains ending in `example.com`.  
**B4.** Change one course price safely.  
**B5.** Explain the difference between a primary key and a unique index.

**Model solutions:**

```sql
-- B1
ALTER TABLE users ADD COLUMN bio TEXT;
-- B2
SELECT * FROM courses ORDER BY created_at DESC, course_id DESC;
-- B3
SELECT * FROM users WHERE email ILIKE '%@example.com';
-- B4 (inspect first, then update)
SELECT course_id, title, price FROM courses WHERE title = 'Practical PostgreSQL';
UPDATE courses SET price = 27000 WHERE title = 'Practical PostgreSQL'
RETURNING course_id, price;
```

**B5 answer:** A primary key uniquely identifies each row and is inherently non-null. A unique index enforces uniqueness for indexed expressions/columns (with PostgreSQL's NULL semantics) and may be used for case-insensitive email uniqueness.

### Intermediate exercises

**I1.** List all courses with their instructor names.  
**I2.** Count enrolments for each learner, including zero.  
**I3.** Find courses with at least two enrolments.  
**I4.** Insert a lesson at position 3 for a named course.  
**I5.** Find courses with no lessons.

**Model solutions:**

```sql
-- I1
SELECT c.title, u.full_name FROM courses c JOIN users u ON u.user_id = c.instructor_id;
-- I2
SELECT u.full_name, COUNT(e.enrollment_id) AS total
FROM users u LEFT JOIN enrollments e USING (user_id)
WHERE u.role = 'student'
GROUP BY u.user_id, u.full_name;
-- I3
SELECT c.title FROM courses c JOIN enrollments e USING (course_id)
GROUP BY c.course_id, c.title HAVING COUNT(*) >= 2;
-- I4
INSERT INTO lessons (course_id, title, position)
SELECT course_id, 'Building Queries', 3 FROM courses
WHERE title = 'Practical PostgreSQL';
-- I5
SELECT c.title FROM courses c
WHERE NOT EXISTS (SELECT 1 FROM lessons l WHERE l.course_id = c.course_id);
```

### Advanced exercises

**A1.** Explain why a composite foreign key is useful for lesson progress.  
**A2.** Propose an index for “all payments for a user, newest first.”  
**A3.** Describe how to handle duplicate payment-provider webhooks.  
**A4.** Design a safe release that renames `full_name` to `display_name`.  
**A5.** Outline a backup verification procedure.

**Model answers:**

- **A1:** It enforces that completed lessons belong to a course in which the user is enrolled; single-column foreign keys alone would not ensure the cross-table relationship.
- **A2:** `CREATE INDEX payments_user_created_idx ON payments (user_id, created_at DESC);` Measure with `EXPLAIN`.
- **A3:** Verify webhook signature; persist unique provider event/reference; apply an idempotent transaction; ignore already-processed events; never trust client-side payment success.
- **A4:** Add `display_name`, backfill, update writes and reads in stages, monitor, then remove old column only after old code is retired.
- **A5:** Create encrypted backup, restore into isolated test database, run integrity/smoke queries, record restore duration, check RPO/RTO, and retain the log.

### Common SQL mistakes and their corrections

| Mistake | Why it fails | Correct approach |
|---|---|---|
| `WHERE paid_at = NULL` | NULL is not compared with `=` | `IS NULL` |
| `UPDATE users SET role='admin';` | Affects all rows | Target a verified `WHERE` clause |
| `COUNT(*)` on a left join | Counts unmatched preserved rows | `COUNT(right_table.id)` |
| Storing prices as text | Breaks arithmetic and ordering | `NUMERIC` or minor units |
| String-building SQL | SQL injection risk | Parameterised queries |
| Committing `.env` | Exposes secrets | `.gitignore` + secret manager |
| Treating a DB as an API | Exposes credentials | Backend service/API |
| Only testing backups | Backup may be unusable | Regular restore drills |
| Indexing every column | Write/storage cost | Index measured query patterns |
| No unique enrolment rule | Duplicate relationships | `UNIQUE (user_id, course_id)` |

### Final capstone assessment rubric (100 points)

| Area | Points |
|---|---:|
| Requirements and ER diagram | 15 |
| Normalised schema and suitable types | 15 |
| Keys, constraints and referential integrity | 15 |
| CRUD, joins, reporting queries | 15 |
| Backend integration and SQL injection safety | 15 |
| Migration, testing and documentation | 10 |
| Backup/restore demonstration | 10 |
| Clear presentation and explanation | 5 |
| **Total** | **100** |

### Zero-to-hero mastery checklist

- [ ] I can explain tables, rows, keys, constraints and transactions.
- [ ] I can draw an ER diagram from plain-English requirements.
- [ ] I can normalise common one-to-many and many-to-many relationships.
- [ ] I can create tables and enforce data integrity.
- [ ] I can write CRUD, joins, aggregates, subqueries and window functions.
- [ ] I can use parameterised SQL through a backend API.
- [ ] I can explain indexes and inspect an execution plan.
- [ ] I can handle transactions and common concurrency hazards.
- [ ] I can apply migrations and use separate environments.
- [ ] I can create a backup and successfully restore it.
- [ ] I can describe least privilege, secrets handling and API authorisation.
- [ ] I can defend my design decisions and show a working capstone.

## Further learning and official documentation

- PostgreSQL documentation: https://www.postgresql.org/docs/
- PostgreSQL tutorial: https://www.postgresql.org/docs/current/tutorial.html
- PostgreSQL SQL reference: https://www.postgresql.org/docs/current/sql.html
- PostgreSQL backup and restore: https://www.postgresql.org/docs/current/backup.html
- PostgreSQL performance tips: https://www.postgresql.org/docs/current/performance-tips.html
- psycopg documentation: https://www.psycopg.org/psycopg3/docs/
- FastAPI documentation: https://fastapi.tiangolo.com/

---

# ABOUT THE AUTHOR

## Engr. Amarachi Crystal Omereife

**Software Engineer | Chief Technology Officer, Opsfuxion Technologies Limited**

Engr. Amarachi Crystal Omereife is a software engineer and Chief Technology Officer of **Opsfuxion Technologies Limited**, with professional expertise spanning DevOps, DevSecOps, cloud and AI infrastructure, software engineering, technical programme management, software documentation, MLOps/AIOps, and AI-assisted software development.

She holds a **Master's degree in Software Engineering** and has professional training and certifications across cloud computing, software development, project management, DevOps and IT operations, including Kubernetes, Microsoft Azure, AWS, Python backend development, Google IT and Project Management, and Six Sigma.

Her work sits at the intersection of technology, automation, secure software delivery and digital transformation, helping organisations design and implement practical technology solutions. She also develops structured technical learning resources and translates complex engineering concepts into accessible, hands-on training.

She is passionate about capacity building and workforce development, particularly equipping emerging professionals and organisations with practical, industry-relevant skills in modern software engineering, cloud technologies, DevOps, cybersecurity and AI.

**Organisation:** Opsfuxion Technologies Limited  
**Website:** https://www.opsfuxiontech.com  
**Tagline:** *Orchestrate intelligence, deliver with precision.*

*Author biography adapted from the ECOWAS Startup Awards Master Class speaker profile supplied by the author. Professional credentials and designations are reproduced as supplied; no independent credential verification is implied.*

---

**End of handbook.**  
*Copyright © 2026 Engr. Amarachi Crystal Omereife / Opsfuxion Technologies Limited. All rights reserved.*
