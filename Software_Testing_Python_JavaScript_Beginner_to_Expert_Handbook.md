# SOFTWARE TESTING: BEGINNER TO EXPERT
## A practical, self-study handbook for Python and JavaScript applications

**Author:** Engr. Amarachi Crystal Omereife  
**Publisher:** Opsfuxion Technologies Limited  
**Edition:** October 2026  
**Level:** Absolute beginner → professional and expert-level foundations  
**Platforms:** Python, JavaScript/TypeScript, browser, Node.js, APIs, databases and CI/CD

> **How to use this book:** Read chapters in order if you are new to testing. Type the examples rather than copying blindly. Run each test, intentionally break the code, observe the failure, and fix it. Each chapter includes a practical checkpoint; solutions appear in the answer-key sections. Commands assume macOS/Linux shell unless otherwise noted. Tool APIs can evolve: consult current documentation before adopting them in production.

**Important:** This is a learning handbook, not a certification or a guarantee of production readiness. Expert practice requires experience with real systems, requirements, risks and teams.

---

## Contents

1. Testing mindset, terminology and quality
2. Installation and first tests
3. Designing strong test cases
4. Python unit testing with `unittest`
5. Python testing with `pytest`
6. JavaScript testing with Vitest
7. Test doubles: mocks, stubs, spies and fakes
8. Parameterisation, fixtures and test data
9. Testing errors, boundaries and edge cases
10. Integration tests and databases
11. API and HTTP testing in Python and JavaScript
12. Frontend component and accessibility testing
13. End-to-end browser testing with Playwright
14. Async, concurrency and time-dependent tests
15. Property-based and fuzz testing
16. Security, performance and reliability testing
17. Coverage, mutation testing and test effectiveness
18. CI/CD automation, GitHub Actions and quality gates
19. Architecture, contracts, test pyramids and risk-based strategy
20. Debugging flaky tests and test-suite maintenance
21. Advanced testing: state machines, migrations and observability
22. Capstone A: Python student records API
23. Capstone B: JavaScript course enrolment app
24. Exercises, solutions, glossary and mastery roadmap
25. Author biography

---

# PART I — FOUNDATIONS

## 1. Testing mindset, terminology and quality

**Software testing** is the systematic activity of gathering evidence about whether software behaves as expected and where it may fail. Testing can reveal defects; passing tests never proves that a system has no defects.

- **Requirement:** What the system must do (e.g., reject a negative course price).
- **Test case:** Inputs, setup, action and expected outcome.
- **Assertion:** A check comparing actual behaviour with an expected result.
- **Test suite:** A collection of related tests.
- **Defect/bug:** An unwanted difference between expected and actual behaviour.
- **Regression:** A previously working behaviour breaks after a change.
- **Unit test:** Exercises a small piece of behaviour in isolation.
- **Integration test:** Checks that components work together (for example, API + database).
- **End-to-end (E2E) test:** Exercises a user journey across the running application.
- **Acceptance test:** Verifies business requirements from a stakeholder's perspective.
- **Smoke test:** Quick, broad checks that a build is usable.
- **Exploratory test:** Human-guided investigation, learning and testing simultaneously.

### Example: testing a discount calculator

Requirement: A 10% discount on ₦1,000 produces ₦900; discounts must be between 0 and 100 percent.

**Arrange:** Price = 1,000; discount = 10. **Act:** Call the function. **Assert:** Result is 900.

A good test suite also asks: What about 0%, 100%, negative prices, 101%, decimals and malformed input?

### Verification versus validation

- **Verification:** Did we implement the specified behaviour correctly?
- **Validation:** Did we build something that actually meets user needs?

### Testing layers

| Layer | Typical scope | Speed | Main risk |
|---|---|---|---|
| Unit | Pure functions, small classes | Fast | Logic errors |
| Component | UI component in test DOM | Fast–medium | Rendering/interaction |
| Integration | Database, API, service combinations | Medium | Boundary failures |
| E2E | Real browser + running application | Slow | User-journey failures |
| Nonfunctional | Security, performance, accessibility | Varies | Operational/user harm |

**Checkpoint:** Describe one unit, one integration and one E2E test for an online course platform.

## 2. Installation and your first tests

### Python setup

```bash
mkdir testing-lab && cd testing-lab
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install pytest pytest-cov hypothesis
mkdir -p python_app/tests
```

Create `python_app/calculator.py`:

```python
def add(a: float, b: float) -> float:
    return a + b
```

Create `python_app/tests/test_calculator.py`:

```python
from python_app.calculator import add

def test_adds_two_numbers():
    assert add(2, 3) == 5
```

From the repository root, run `python -m pytest -q`. Add empty `__init__.py` files in `python_app/` and `python_app/tests/` if your import configuration needs them.

### JavaScript setup (Node.js + npm)

```bash
mkdir js-testing-lab && cd js-testing-lab
npm init -y
npm install --save-dev vitest
mkdir -p src
```

Create `src/calculator.js`:

```javascript
export function add(a, b) {
  return a + b;
}
```

Create `src/calculator.test.js`:

```javascript
import { test, expect } from 'vitest';
import { add } from './calculator.js';

test('adds two numbers', () => {
  expect(add(2, 3)).toBe(5);
});
```

Run `npx vitest run`. For ESM consistency, set `"type": "module"` in `package.json`.

### Read the red-green-refactor cycle

1. **Red:** Write a test for missing behaviour; verify it fails for the expected reason.
2. **Green:** Implement the smallest correct change.
3. **Refactor:** Improve the code while keeping tests green.

**Exercise:** Change `add` to subtract, run the test, explain the failure, then restore it.

## 3. Designing strong test cases

### Equivalence partitions

Group inputs expected to behave similarly. For age-based eligibility (18–65 inclusive), partitions include below 18, 18–65 and above 65; also consider non-integer and missing values.

### Boundary-value analysis

Test just below, at and just above boundaries: 17, 18, 19, 64, 65, 66.

### Decision tables

For login with valid credentials and active account:

| Credentials valid? | Account active? | Expected |
|---|---|---|
| Yes | Yes | Allow |
| Yes | No | Deny |
| No | Yes | Deny |
| No | No | Deny |

### State transitions

An enrolment might transition `pending → active → completed`, with cancellation from pending or active. Tests must reject impossible transitions such as `cancelled → completed` unless explicitly supported.

### Traceability

Assign IDs to requirements and tests: `REQ-LOGIN-01` maps to `TEST-LOGIN-VALID`, `TEST-LOGIN-INACTIVE`, etc. This makes gaps visible.

### A reusable test-case template

```text
Test ID: TC-ENROL-004
Requirement: REQ-ENROL-002
Preconditions: Student exists; course has one remaining seat
Steps: Enrol student; attempt a second enrolment
Expected: First succeeds; second is rejected without duplicate record
Priority: High
Evidence: Test output / screenshot / database query
```

**Exercise:** Write six cases for a registration form: valid email, missing email, duplicate email, short password, weak password and successful submission.

---

# PART II — PYTHON AND JAVASCRIPT TESTING

## 4. Python unit testing with `unittest`

Python ships with `unittest`; no third-party installation is required.

```python
# pricing.py
def final_price(price, discount):
    if price < 0 or not 0 <= discount <= 100:
        raise ValueError('Invalid price or discount')
    return round(price * (1 - discount / 100), 2)
```

```python
# test_pricing_unittest.py
import unittest
from pricing import final_price

class PricingTests(unittest.TestCase):
    def test_regular_discount(self):
        self.assertEqual(final_price(1000, 10), 900)

    def test_rejects_negative_price(self):
        with self.assertRaises(ValueError):
            final_price(-1, 10)

    def test_full_discount(self):
        self.assertEqual(final_price(1000, 100), 0)

if __name__ == '__main__':
    unittest.main()
```

Run `python -m unittest discover -v`. Learn `setUp`, `tearDown`, `subTest`, `assertAlmostEqual`, `assertIn`, and `assertRaises`.

**Common mistake:** Using `assertEqual` for approximate floating-point results without considering rounding. Prefer integer cents or `Decimal` for financial values.

## 5. Python testing with `pytest`

`pytest` uses ordinary `assert` statements, fixtures and rich failure messages.

```python
# test_pricing_pytest.py
import pytest
from pricing import final_price

@pytest.mark.parametrize('price,discount,expected', [
    (1000, 10, 900),
    (200, 0, 200),
    (500, 100, 0),
])
def test_valid_discounts(price, discount, expected):
    assert final_price(price, discount) == expected

@pytest.mark.parametrize('price,discount', [(-1, 10), (100, -1), (100, 101)])
def test_invalid_discounts(price, discount):
    with pytest.raises(ValueError):
        final_price(price, discount)
```

Run `python -m pytest -v`; coverage: `python -m pytest --cov=python_app --cov-report=term-missing` (adjust the module path to your project).

### Fixtures

```python
import pytest

@pytest.fixture
def sample_student():
    return {'id': 1, 'name': 'Ada', 'scores': [80, 90]}

def test_student_average(sample_student):
    assert sum(sample_student['scores']) / len(sample_student['scores']) == 85
```

Fixtures can manage setup/cleanup using `yield`. Keep fixture scopes as narrow as practical to prevent test interference.

## 6. JavaScript unit testing with Vitest

```javascript
// src/pricing.js
export function finalPrice(price, discount) {
  if (!Number.isFinite(price) || !Number.isFinite(discount) ||
      price < 0 || discount < 0 || discount > 100) {
    throw new RangeError('Invalid price or discount');
  }
  return Math.round((price * (1 - discount / 100) + Number.EPSILON) * 100) / 100;
}
```

```javascript
// src/pricing.test.js
import { describe, it, expect } from 'vitest';
import { finalPrice } from './pricing.js';

describe('finalPrice', () => {
  it.each([
    [1000, 10, 900],
    [200, 0, 200],
    [500, 100, 0],
  ])('discounts %i by %i%% to %i', (price, discount, expected) => {
    expect(finalPrice(price, discount)).toBe(expected);
  });

  it('rejects invalid discounts', () => {
    expect(() => finalPrice(100, 101)).toThrow(RangeError);
  });
});
```

Run `npx vitest run`. Learn `toBe`, `toEqual`, `toThrow`, `toMatchObject`, `toHaveBeenCalledWith` and `toBeCloseTo`.

### JavaScript-specific hazards

- `===` differs from loose `==`; avoid coercion surprises.
- `NaN`, `Infinity`, `null`, `undefined`, `''` and `0` are different cases.
- Dates and time zones can make tests machine-dependent.
- Floating-point numbers can produce rounding surprises; for money, use integer minor units or a decimal library.

## 7. Test doubles: mocks, stubs, spies and fakes

A **stub** supplies predetermined responses; a **spy** records calls; a **mock** verifies interactions; a **fake** provides a simplified working substitute (for example, an in-memory repository).

### Python: patch a dependency

```python
# notifier.py
def welcome_user(email, send_email):
    send_email(email, 'Welcome!')
    return True
```

```python
from unittest.mock import Mock
from notifier import welcome_user

def test_welcome_email():
    sender = Mock()
    assert welcome_user('ada@example.com', sender) is True
    sender.assert_called_once_with('ada@example.com', 'Welcome!')
```

### JavaScript: spy on a callback

```javascript
import { it, expect, vi } from 'vitest';

function welcomeUser(email, sendEmail) {
  sendEmail(email, 'Welcome!');
}

it('sends a welcome email', () => {
  const sendEmail = vi.fn();
  welcomeUser('ada@example.com', sendEmail);
  expect(sendEmail).toHaveBeenCalledWith('ada@example.com', 'Welcome!');
});
```

**Rule:** Mock slow or nondeterministic external boundaries, not every internal function. Excessive mocking tests implementation details rather than behaviour.

## 8. Parameterisation, fixtures and test data

Good test data should be **representative, minimal, deterministic, independent and privacy-safe**. Never copy real passwords, payment cards or confidential customer records into test repositories.

Python fixture cleanup:

```python
import tempfile
from pathlib import Path
import pytest

@pytest.fixture
def temp_report():
    with tempfile.TemporaryDirectory() as directory:
        yield Path(directory) / 'report.txt'
```

JavaScript temporary directory:

```javascript
import { mkdtemp, rm } from 'node:fs/promises';
import { tmpdir } from 'node:os';
import { join } from 'node:path';

export async function withTempDir(callback) {
  const directory = await mkdtemp(join(tmpdir(), 'test-'));
  try { return await callback(directory); }
  finally { await rm(directory, { recursive: true, force: true }); }
}
```

**Exercise:** Parameterise five password lengths and classify them as valid/invalid using a documented policy.

## 9. Errors, boundaries and edge cases

For each function, test the **happy path**, boundaries, invalid input, unexpected types, empty input, duplicates and failure of dependencies.

```python
def average(scores):
    if not scores:
        raise ValueError('At least one score is required')
    if any(not isinstance(s, (int, float)) or isinstance(s, bool) for s in scores):
        raise TypeError('Scores must be numeric')
    return sum(scores) / len(scores)
```

```python
import pytest
from scores import average

def test_average():
    assert average([60, 80]) == 70

def test_empty_scores():
    with pytest.raises(ValueError):
        average([])

def test_boolean_rejected():
    with pytest.raises(TypeError):
        average([True, 80])
```

**Exercise:** Decide whether scores outside 0–100 should be rejected; implement and test that business rule.

---

# PART III — SYSTEMS, WEB APPS AND APIS

## 10. Integration tests and databases

Unit tests can pass while database constraints, SQL queries and migrations fail. Integration tests verify actual interaction with a database.

### Python SQLite integration example

```python
import sqlite3

def create_schema(db):
    db.execute('CREATE TABLE students (id INTEGER PRIMARY KEY, email TEXT UNIQUE NOT NULL)')

def register_student(db, email):
    db.execute('INSERT INTO students (email) VALUES (?)', (email,))
    db.commit()


def test_unique_student_emails():
    db = sqlite3.connect(':memory:')
    try:
        create_schema(db)
        register_student(db, 'ada@example.com')
        import pytest
        with pytest.raises(sqlite3.IntegrityError):
            register_student(db, 'ada@example.com')
    finally:
        db.close()
```

**PostgreSQL-specific advice:** Use a disposable PostgreSQL test database/container for real integration testing. SQLite differs in typing, constraints, SQL dialect and concurrency. Run migrations on the disposable database and reset state between tests. Never point test fixtures at production.

### What to verify

- Primary/foreign keys and uniqueness.
- Transactions and rollback after partial failure.
- Migration up/down strategy and data preservation.
- Pagination and deterministic ordering.
- SQL injection resistance through parameterised queries.
- Concurrent updates and race conditions.

## 11. API and HTTP testing

An API test checks method, path, headers, status code, response body, authentication and side effects.

### Python FastAPI with TestClient

Install `fastapi`, `httpx`, `pytest`.

```python
# api.py
from fastapi import FastAPI, HTTPException
from pydantic import BaseModel

app = FastAPI()

class Student(BaseModel):
    name: str
    age: int

@app.post('/students', status_code=201)
def create_student(student: Student):
    if student.age < 0:
        raise HTTPException(status_code=422, detail='Age cannot be negative')
    return {'id': 1, **student.model_dump()}
```

```python
# test_api.py
from fastapi.testclient import TestClient
from api import app

client = TestClient(app)

def test_create_student():
    response = client.post('/students', json={'name': 'Ada', 'age': 20})
    assert response.status_code == 201
    assert response.json()['name'] == 'Ada'

def test_reject_negative_age():
    response = client.post('/students', json={'name': 'Ada', 'age': -2})
    assert response.status_code == 422
```

### JavaScript Express with Supertest

Install `express`, `supertest`, `vitest`.

```javascript
// app.js
import express from 'express';
export const app = express();
app.use(express.json());
app.post('/students', (req, res) => {
  const { name, age } = req.body;
  if (typeof name !== 'string' || !Number.isInteger(age) || age < 0) {
    return res.status(422).json({ error: 'Invalid student' });
  }
  return res.status(201).json({ id: 1, name, age });
});
```

```javascript
// app.test.js
import { test, expect } from 'vitest';
import request from 'supertest';
import { app } from './app.js';

test('POST /students creates a student', async () => {
  const response = await request(app).post('/students').send({ name: 'Ada', age: 20 });
  expect(response.status).toBe(201);
  expect(response.body.name).toBe('Ada');
});
```

**Exercise:** Add tests for missing name, string age, unauthorised access (once authentication is implemented) and duplicate email.

## 12. Frontend component and accessibility testing

Use React Testing Library to verify what users see and do. Prefer semantic queries (`getByRole`, `getByLabelText`) over implementation-specific CSS selectors.

Install in a React/Vite project:

```bash
npm install --save-dev vitest jsdom @testing-library/react @testing-library/jest-dom @testing-library/user-event
```

Configure Vitest to use `jsdom` and load a setup file importing `@testing-library/jest-dom/vitest`.

```jsx
// Greeting.jsx
export function Greeting() {
  return <><label htmlFor="name">Your name</label><input id="name" />
    <button type="button">Greet</button></>;
}
```

```jsx
// Greeting.test.jsx
import { test, expect } from 'vitest';
import { render, screen } from '@testing-library/react';
import { Greeting } from './Greeting.jsx';

test('shows an accessible name field and button', () => {
  render(<Greeting />);
  expect(screen.getByRole('textbox', { name: /your name/i })).toBeInTheDocument();
  expect(screen.getByRole('button', { name: /greet/i })).toBeInTheDocument();
});
```

The example intentionally checks accessible structure, not an unimplemented greeting action. Extend it with state and test the button interaction.

**Accessibility checklist:** labels, keyboard navigation, focus order, visible errors, contrast, alternative text, screen-reader semantics. Automated checks are helpful but cannot replace manual accessibility testing.

## 13. End-to-end browser testing with Playwright

Install into a JavaScript web app:

```bash
npm install --save-dev @playwright/test
npx playwright install
```

Create `playwright.config.js`:

```javascript
import { defineConfig } from '@playwright/test';
export default defineConfig({
  testDir: './e2e',
  use: { baseURL: 'http://127.0.0.1:4173', trace: 'on-first-retry' },
  webServer: {
    command: 'npm run dev -- --host 127.0.0.1 --port 4173',
    url: 'http://127.0.0.1:4173',
    reuseExistingServer: !process.env.CI,
  },
});
```

```javascript
// e2e/home.spec.js
import { test, expect } from '@playwright/test';

test('home page displays its heading', async ({ page }) => {
  await page.goto('/');
  await expect(page.getByRole('heading', { level: 1 })).toBeVisible();
});
```

Run `npx playwright test`. Configure the app's actual server command and port; the sample assumes a Vite dev server. Avoid fixed sleeps such as `waitForTimeout(5000)`; use Playwright's locator assertions and auto-waiting.

**Critical E2E practices:** use isolated test accounts, seeded data, stable semantic locators, traces/screenshots on failure and cleanup after each test. Do not use production payment services or send real notifications.

## 14. Async, concurrency and time-dependent tests

### Python async example

Install `pytest-asyncio`.

```python
import asyncio
import pytest

async def get_status():
    await asyncio.sleep(0)
    return 'ready'

@pytest.mark.asyncio
async def test_status():
    assert await get_status() == 'ready'
```

### JavaScript async example

```javascript
import { test, expect } from 'vitest';

async function fetchStatus() { return 'ready'; }

test('returns ready', async () => {
  await expect(fetchStatus()).resolves.toBe('ready');
});
```

Test failures and timeouts as well as success. Inject a clock into business logic instead of relying on wall-clock time. For concurrent booking or inventory logic, check atomic updates, transaction isolation and duplicate requests.

## 15. Property-based and fuzz testing

Example-based tests check selected inputs. Property-based testing generates many inputs to check an invariant.

```python
from hypothesis import given, strategies as st

@given(st.lists(st.integers()))
def test_sort_preserves_length_and_order(values):
    result = sorted(values)
    assert len(result) == len(values)
    assert all(a <= b for a, b in zip(result, result[1:]))
    assert sorted(result) == sorted(values)
```

The last assertion is deliberately weak/redundant: improve the property by comparing `collections.Counter(result)` with `Counter(values)` to verify no elements are lost or duplicated.

For JavaScript, explore `fast-check`:

```javascript
import { test, expect } from 'vitest';
import fc from 'fast-check';

test('reversing twice restores an array', () => {
  fc.assert(fc.property(fc.array(fc.integer()), values => {
    const twice = [...values].reverse().reverse();
    expect(twice).toEqual(values);
  }));
});
```

**Fuzz testing** sends diverse, sometimes malformed inputs to find crashes and unexpected behaviour. Keep fuzzing in an authorised local/test environment.

## 16. Security, performance and reliability testing

### Security test categories

- Authentication: missing/expired credentials, brute-force protections.
- Authorisation: users cannot read or edit other users' records.
- Input handling: injection, XSS, unsafe file uploads, path traversal.
- Session/cookie security: expiry, secure flags, CSRF where applicable.
- Secrets: no API keys or passwords in source control or test logs.
- Dependencies: vulnerability scans and updates.

**Safe local test example:** Confirm a query parameter is handled as data, not concatenated into SQL. Always use parameterised queries. Do not run offensive security tests against systems without authorisation.

### Performance

Define a service-level target such as “p95 API latency below 300 ms at 50 concurrent virtual users under stated test conditions.” Measure latency distribution, throughput, errors, CPU/memory and database queries. Avoid claiming a performance threshold is universally appropriate.

### Reliability

Test retries, duplicate requests, unavailable services, network timeouts, partial writes and graceful degradation. Retrying a payment requires idempotency controls to avoid duplicate charges.

## 17. Coverage, mutation testing and effectiveness

**Coverage** measures which code was executed, not whether tests were meaningful.

Python:

```bash
python -m pytest --cov=python_app --cov-branch --cov-report=term-missing
```

JavaScript with Vitest (install the matching coverage provider):

```bash
npm install --save-dev @vitest/coverage-v8
npx vitest run --coverage
```

**Mutation testing** deliberately changes code (for example `>` to `>=`) and checks whether tests detect it. Python: `mutmut` or `cosmic-ray`; JavaScript: `@stryker-mutator/core` with a supported test runner. Review compatibility before installation.

A 100% coverage score can coexist with poor assertions. Prioritise high-risk behaviours, meaningful assertions and mutation resistance over arbitrary percentages.

## 18. CI/CD and GitHub Actions

A minimal multi-language workflow (adjust paths and versions for your repository):

```yaml
name: Tests
on:
  push:
  pull_request:

jobs:
  python:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with:
          python-version: '3.12'
      - run: python -m pip install pytest pytest-cov
      - run: python -m pytest -q

  javascript:
    runs-on: ubuntu-latest
    defaults:
      run:
        working-directory: js-testing-lab
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '22'
          cache: npm
          cache-dependency-path: js-testing-lab/package-lock.json
      - run: npm ci
      - run: npx vitest run
```

**Prerequisites:** The Python tests and the JavaScript project must exist at the specified paths; `npm ci` requires a committed lockfile. Pin actions to reviewed commit SHAs in security-sensitive production repositories. Configure branch protection, required checks, least-privilege token permissions and secret handling.

## 19. Architecture, contracts and risk-based strategy

### Testing pyramid and alternatives

A common starting point is many fast unit tests, fewer integration tests and a smaller set of E2E tests. The ideal mix depends on architecture and risk; avoid rigid percentages.

### Contract tests

Verify an API consumer's expectations (fields, status codes, types) against a provider. This reduces mismatches between frontend and backend. Schema validation (OpenAPI/JSON Schema) is helpful but does not cover all behavioural contracts.

### Risk matrix

| Feature | Likelihood of failure | Impact | Suggested focus |
|---|---|---|---|
| Login/access control | Medium | Critical | Unit + integration + security |
| Payment capture | Medium | Critical | Integration + idempotency + E2E sandbox |
| Search filters | Medium | Medium | Unit + API |
| Decorative animation | Low | Low | Visual/manual smoke |

### Test strategy template

```text
Project:
Release and scope:
Critical user journeys:
In-scope and out-of-scope:
Risk ranking:
Test levels and tools:
Environments and test data:
Entry/exit criteria:
CI quality gates:
Defect triage and ownership:
Reporting and evidence:
```

## 20. Flaky tests and suite maintenance

A **flaky test** passes and fails without a relevant code change. Common causes: timing, shared state, test order, external networks, race conditions, random data, time zones and uncleaned databases.

**Diagnosis sequence:** reproduce repeatedly → inspect logs/trace → isolate test → inspect state/time dependencies → fix root cause → rerun full suite. Do not hide persistent flakes by adding arbitrary sleeps or unlimited retries.

**Good suite habits:** descriptive names, deterministic setup, short feedback cycles, clear ownership, regular pruning of redundant tests, and visible CI failures.

## 21. Advanced topics: state machines, migrations and observability

- **Model-based/state-machine tests:** Generate sequences of actions and check legal transitions.
- **Migration tests:** Upgrade from realistic older schemas; validate data integrity and rollback/recovery plans.
- **Contract compatibility:** Detect breaking changes between API versions.
- **Observability checks:** Verify meaningful structured logs, metrics and trace context without exposing sensitive data.
- **Chaos/failure injection:** In controlled staging, simulate dependency outages and resource constraints.
- **Release techniques:** Feature flags, canary deployments and post-deployment smoke tests.

### State-machine example

A course enrolment may have `PENDING`, `ACTIVE`, `COMPLETED`, `CANCELLED` states. Write tests for all allowed transitions, forbidden transitions, repeated requests and concurrent updates. A state transition table often catches gaps before code is written.

---

# PART IV — CAPSTONE PROJECTS

## 22. Capstone A: Python Student Records API

**Goal:** Build a FastAPI + PostgreSQL student records service with create/list/detail/update/delete endpoints, unique email constraint, validation, authentication/authorisation appropriate to scope, pagination and automated tests.

### Suggested project structure

```text
python-student-api/
├── app/
│   ├── main.py
│   ├── models.py
│   ├── schemas.py
│   ├── database.py
│   └── services.py
├── tests/
│   ├── conftest.py
│   ├── test_services.py
│   ├── test_api.py
│   └── test_database.py
├── migrations/
├── pyproject.toml
└── README.md
```

### Acceptance criteria

1. Valid registration returns 201 and generated ID.
2. Duplicate email returns 409 (or another documented, consistent status).
3. Invalid email and age return 422.
4. Unknown ID returns 404.
5. An unauthorised user cannot modify another user's record.
6. List results are paginated and deterministically ordered.
7. Tests use a disposable database and leave no residual records.
8. CI executes unit and integration tests.

### Recommended implementation sequence

**Stage 1:** Write pure validation and unit tests. **Stage 2:** Define schema/migration. **Stage 3:** Implement repository and database integration tests. **Stage 4:** Add API and HTTP tests. **Stage 5:** Add authentication/authorisation tests. **Stage 6:** Run coverage and CI. **Stage 7:** Document setup, known limitations and evidence.

### Example service-layer starter

```python
class DuplicateEmailError(Exception):
    pass

class StudentService:
    def __init__(self, repository):
        self.repository = repository

    def register(self, email):
        normalised = email.strip().lower()
        if '@' not in normalised:
            raise ValueError('Invalid email')
        if self.repository.exists(normalised):
            raise DuplicateEmailError(normalised)
        return self.repository.create(normalised)
```

**Instructor note:** The email check is deliberately simplified for this exercise. Production code needs appropriate validation and must rely on a database uniqueness constraint to handle concurrency safely.

## 23. Capstone B: JavaScript Course Enrolment App

**Goal:** Build a React frontend and Express API with course listing, enrolment form, user-visible validation, seat limits and an automated test suite.

### Suggested structure

```text
course-enrolment/
├── client/
│   ├── src/components/
│   ├── src/pages/
│   └── src/**/*.test.jsx
├── server/
│   ├── src/app.js
│   ├── src/services/
│   └── tests/
├── e2e/
│   └── enrolment.spec.js
└── .github/workflows/tests.yml
```

### Acceptance criteria

1. Courses are visible with title, capacity and available seats.
2. An enrolment is rejected if the course is full.
3. Duplicate enrolments are prevented.
4. Form errors are visible and accessible to assistive technologies.
5. An API error is shown as a recoverable user-facing message.
6. Unit, component, API and at least one E2E test run in CI.
7. Concurrent requests cannot oversell course capacity.

### Test-first challenge

Write tests before implementing the `canEnrol(course, studentId)` function. Cases: capacity available, capacity full, already enrolled, missing student, and malformed course object. Then test the API and React UI separately.

### E2E scenario

1. Start with a seeded student and course with one free seat.
2. Open the course page.
3. Select Enrol.
4. Confirm success message and updated seat count.
5. Attempt enrolment again.
6. Confirm a clear duplicate-enrolment error.

**Note:** The full capstones are intentionally open-ended engineering projects. Earlier chapters provide complete runnable examples; the capstones require learners to assemble them, make design decisions and justify trade-offs.

---

# PART V — PRACTICE AND REFERENCE

## 24. Independent practice challenges

Try these without looking at the answer key:

1. Write a test for a `square(n)` function in Python.
2. Test a Python `divide(a,b)` function for zero division.
3. Parameterise a grading function at 49, 50, 69 and 70.
4. Write a Vitest test for a JavaScript `isAdult(age)` function.
5. Spy on a notification callback.
6. Test a Python function that raises on empty input.
7. Add a SQLite uniqueness integration test.
8. Add a 400/422 test for malformed API JSON.
9. Write a React test asserting a form label is accessible.
10. Write a Playwright test for page navigation.
11. Write a property-based test for reversing a list twice.
12. Explain why 100% statement coverage does not prove correctness.
13. Design tests for a course that has one remaining seat.
14. Create a GitHub Actions workflow for a Python project.
15. Diagnose a test that only fails in CI.
16. Write a test strategy for a small banking transfer feature.
17. Specify how to test a database migration preserving 10,000 records.
18. Create a traceability matrix for registration requirements.

### Model answers and solution sketches

**1.** `assert square(4) == 16`; also test `0` and negative inputs.

**2.** `with pytest.raises(ZeroDivisionError): divide(10, 0)` if that is the documented contract.

**3.** Use `@pytest.mark.parametrize` and explicit grade thresholds; test both sides of each boundary.

**4.** `expect(isAdult(18)).toBe(true); expect(isAdult(17)).toBe(false)`; define how non-integers are handled.

**5.** `const spy = vi.fn(); notify(spy); expect(spy).toHaveBeenCalledOnce()`; assert arguments as well.

**6.** `with pytest.raises(ValueError): function([])` and a separate valid-input case.

**7.** Insert the same unique email twice and assert `sqlite3.IntegrityError`; use a fresh in-memory database per test.

**8.** Send a missing required field and assert the application's documented validation status and response shape.

**9.** `expect(screen.getByRole('textbox', {name:/email/i})).toBeInTheDocument()` after rendering.

**10.** `await page.goto('/'); await page.getByRole('link', {name:/courses/i}).click(); await expect(page).toHaveURL(/courses/)`.

**11.** For all lists, `reverse(reverse(values)) == values`; use Hypothesis or fast-check.

**12.** Executing a line says nothing about checking the right output or edge cases; mutation testing reveals weak assertions.

**13.** Test first enrolment succeeds, second independent enrolment fails, duplicate requests fail, and simultaneous enrolments cannot exceed capacity.

**14.** Checkout, setup-python, install dependencies, `python -m pytest`; make checks required on pull requests.

**15.** Check environment versions, time zones, parallel execution, missing secrets, file paths, shared state and network assumptions.

**16.** Include idempotency, authorisation, insufficient funds, atomic debit/credit, rollback, audit logging and concurrent transfers.

**17.** Seed representative old data, run migration on disposable database, compare row counts and invariants, verify indexes/constraints and test recovery plan.

**18.** Create columns `Requirement ID | Description | Test ID | Level | Status | Evidence` and map each requirement to one or more tests.

### Suggested scoring rubric (100 points)

| Category | Points |
|---|---:|
| Requirements and risk analysis | 15 |
| Unit and boundary tests | 20 |
| Integration and API tests | 20 |
| UI/E2E or relevant user-journey tests | 15 |
| Test data, isolation and reliability | 10 |
| CI, coverage and reporting | 10 |
| Documentation and communication | 10 |

### Glossary

**Assertion:** Expected-vs-actual check. **Fixture:** Reusable test setup. **Mock:** Controlled substitute that can verify calls. **Regression:** Reintroduced failure. **Flaky:** Nondeterministic test. **Coverage:** Execution measurement. **Mutation:** Deliberate code change to measure test sensitivity. **Contract:** Interface expectations between components. **Idempotency:** Repeated operation has no additional unintended effect. **p95 latency:** Response time at or below which 95% of measured requests fall.

### Mastery roadmap

- **Beginner:** Write assertions; run `unittest`, `pytest`, Vitest; identify boundary cases.
- **Intermediate:** Use fixtures, parameterisation, mocks, API tests and database integration tests.
- **Advanced:** Build component/E2E suites, CI pipelines, risk-based strategies and reliable test data.
- **Expert foundations:** Apply property-based/mutation/contract testing, analyse concurrency and failure modes, design test architecture and use operational evidence to improve quality.

### Further reading (official project documentation)

- Python `unittest`: https://docs.python.org/3/library/unittest.html
- pytest: https://docs.pytest.org/
- Hypothesis: https://hypothesis.readthedocs.io/
- Vitest: https://vitest.dev/
- Testing Library: https://testing-library.com/
- Playwright: https://playwright.dev/
- FastAPI testing: https://fastapi.tiangolo.com/tutorial/testing/
- GitHub Actions: https://docs.github.com/en/actions
- OWASP Web Security Testing Guide: https://owasp.org/www-project-web-security-testing-guide/

---

## 25. About the author

**Engr. Amarachi Crystal Omereife** is a software engineer and technology educator with experience spanning software development, cloud computing, DevOps, DevSecOps and technical project delivery. She holds a Master's degree in Computer Science with a Software Engineering specialisation and has worked with Python backend development, cloud infrastructure, automation and engineering mentorship. She leads **Opsfuxion Technologies Limited**, a technology company focused on software solutions, cloud and DevOps services, technical training, documentation and digital technology services. Her teaching materials emphasise practical, accessible learning and real-world engineering skills.

**Opsfuxion Technologies Limited**  
*Orchestrate intelligence, deliver with precision.*

© 2026 Engr. Amarachi Crystal Omereife. All rights reserved. Educational examples are illustrative; review security, compatibility and licensing before production use.
