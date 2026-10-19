# JavaScript Zero to Hero — The Complete Practical Handbook

> **From your first console statement to reliable, tested browser applications**  
> **Format:** comprehensive, self-paced Markdown handbook, beginner → expert  
> **Method:** understand → type → predict → run → modify → test → build  
> **Tools:** VS Code, a modern browser, Git and a terminal

## How to use this handbook

1. Work through the chapters in order. Re-type code rather than only reading it.
2. Complete each challenge before opening its suggested solution.
3. Keep a Git repository with one folder per chapter or lab.
4. After every project, write a README explaining decisions and trade-offs.
5. Return to the mastery checklist until you can explain and build without copying.

## Table of contents
- [1. JavaScript and the Runtime](#1.-javascript-and-the-runtime)
- [2. Variables, Types and Operators](#2.-variables,-types-and-operators)
- [3. Strings, Numbers and Conversion](#3.-strings,-numbers-and-conversion)
- [4. Conditions and Logical Reasoning](#4.-conditions-and-logical-reasoning)
- [5. Loops and Iteration](#5.-loops-and-iteration)
- [6. Functions, Scope and Closures](#6.-functions,-scope-and-closures)
- [7. Arrays and Collection Methods](#7.-arrays-and-collection-methods)
- [8. Objects, Destructuring and Spread](#8.-objects,-destructuring-and-spread)
- [9. Equality, Truthiness and Edge Cases](#9.-equality,-truthiness-and-edge-cases)
- [10. DOM Selection and Updates](#10.-dom-selection-and-updates)
- [11. Events, Forms and Validation](#11.-events,-forms-and-validation)
- [12. Modules and Project Structure](#12.-modules-and-project-structure)
- [13. Errors, Debugging and Defensive Code](#13.-errors,-debugging-and-defensive-code)
- [14. Asynchronous JavaScript and Promises](#14.-asynchronous-javascript-and-promises)
- [15. Fetch, APIs and JSON](#15.-fetch,-apis-and-json)
- [16. Timers, Debouncing and the Event Loop](#16.-timers,-debouncing-and-the-event-loop)
- [17. Classes, Prototypes and this](#17.-classes,-prototypes-and-this)
- [18. Functional Patterns and Immutability](#18.-functional-patterns-and-immutability)
- [19. Browser Storage and Security](#19.-browser-storage-and-security)
- [20. Testing JavaScript](#20.-testing-javascript)
- [21. Performance, Accessibility and Maintainability](#21.-performance,-accessibility-and-maintainability)
- [22. Advanced Patterns and Architecture](#22.-advanced-patterns-and-architecture)
- [Guided labs](#guided-labs)
- [Portfolio projects](#portfolio-projects)
- [Final capstone](#final-capstone)
- [Knowledge checks and answers](#knowledge-checks-and-answers)
- [Glossary](#glossary)
- [Learning roadmap and mastery checklist](#learning-roadmap-and-mastery-checklist)

---

# Part I — Language Foundations

## 1. JavaScript and the Runtime

### Core idea
JavaScript is the language of browser behaviour and also runs outside browsers (for example in Node.js). HTML creates elements; CSS styles them; JavaScript responds to events, updates data, and changes the DOM. Browser APIs such as `document` are not part of the language itself.

### Runnable example
```javascript
console.log('Hello, JavaScript!');
console.log(typeof window === 'undefined' ? 'Non-browser runtime' : 'Browser');
```

### Walkthrough
Run the first line in browser DevTools and in a Node.js terminal. The second line illustrates that environments expose different global objects.

### Practice challenge
Write three console messages: your goal, your current skill level, and today’s date.

<details><summary>Suggested solution / checkpoint</summary>

Use `console.log("Goal: build accessible web apps")`; obtain a date with `new Date().toLocaleDateString()`.

</details>

### Production insight
Use the browser console for experiments and `.js` modules for reproducible code.

**Common mistake:** Assuming `document` exists in Node.js.

---

## 2. Variables, Types and Operators

### Core idea
Use `const` for bindings that will not be reassigned and `let` for those that will. Primitives include string, number, boolean, bigint, symbol, undefined and null; objects are reference values. `typeof null` returning `"object"` is a historic quirk.

### Runnable example
```javascript
const price = 2500;
let quantity = 3;
const total = price * quantity;
console.log(`${quantity} seats cost ₦${total}`);
console.log(typeof price, Number.isFinite(total));
```

### Walkthrough
`const` prevents reassignment, not object mutation. `===` compares without coercing different types. `+` concatenates if a string operand is involved.

### Practice challenge
Calculate discounted tuition for 4 students at ₦15,000 each with a 10% discount.

<details><summary>Suggested solution / checkpoint</summary>

`const total = 4 * 15000 * (1 - 0.10); // 54000`

</details>

### Production insight
Use `Number.isNaN()` and `Number.isFinite()` to validate numeric inputs.

**Common mistake:** Using `var`, accidental globals or `==` without understanding coercion.

---

## 3. Strings, Numbers and Conversion

### Core idea
Strings are immutable sequences of UTF-16 code units. Numbers use floating-point arithmetic; financial calculations may need integer minor units or a decimal library. Template literals support interpolation.

### Runnable example
```javascript
const input = '  Abuja  ';
const city = input.trim().toLowerCase();
const amount = Number('1200');
console.log(city, amount.toFixed(2));
console.log(0.1 + 0.2 === 0.3); // false
```

### Walkthrough
`.trim()` removes surrounding whitespace; `Number()` parses numeric text, but invalid input becomes `NaN`. `toFixed()` returns a string.

### Practice challenge
Create a `formatPrice` function that formats a numeric naira value.

<details><summary>Suggested solution / checkpoint</summary>

`const formatPrice = n => new Intl.NumberFormat("en-NG", {style:"currency",currency:"NGN"}).format(n);`

</details>

### Production insight
For user-facing dates and numbers prefer `Intl` formatting over manual string concatenation.

**Common mistake:** Treating `toFixed()` as a number or assuming decimal floating-point is exact.

---

## 4. Conditions and Logical Reasoning

### Core idea
`if`, `else`, `switch`, ternary expressions, `&&`, `||` and `??` express decisions. `??` substitutes only for null or undefined; `||` substitutes for all falsy values, including 0.

### Runnable example
```javascript
function feeLabel(fee) {
  if (fee == null) return 'Contact admissions';
  return fee === 0 ? 'Free' : `₦${fee}`;
}
console.log(feeLabel(0), feeLabel(null));
```

### Walkthrough
Notice why `fee || "Ask"` would incorrectly hide a legitimate zero fee. Keep conditions simple and make boundary cases explicit.

### Practice challenge
Write a function that assigns `Beginner`, `Intermediate`, or `Advanced` for scores below 40, 40–79, and 80+.

<details><summary>Suggested solution / checkpoint</summary>

`function level(n){return n < 40 ? "Beginner" : n < 80 ? "Intermediate" : "Advanced";}`

</details>

### Production insight
Use guard clauses to keep nesting shallow.

**Common mistake:** Confusing assignment `=` with equality `===`.

---

## 5. Loops and Iteration

### Core idea
`for`, `while`, `for...of` and array iteration methods repeat work. Prefer `for...of` for values and `Object.entries()` for object pairs. Use `break` and `continue` deliberately.

### Runnable example
```javascript
const scores = [72, 88, 91];
let sum = 0;
for (const score of scores) sum += score;
console.log(sum / scores.length);
```

### Walkthrough
The accumulator begins at zero, adds each score, then divides by the number of scores. An empty array needs special handling.

### Practice challenge
Print numbers 1–30, replacing multiples of 3 with `Fizz` and multiples of 5 with `Buzz`.

<details><summary>Suggested solution / checkpoint</summary>

Use `for (let i=1;i<=30;i++)` and test divisibility with `%`; test multiples of both first.

</details>

### Production insight
Avoid unnecessary nested loops on large collections.

**Common mistake:** Off-by-one loop boundaries and infinite `while` loops.

---

## 6. Functions, Scope and Closures

### Core idea
Functions encapsulate reusable behaviour. Function declarations are hoisted; arrow functions have lexical `this`. A closure retains access to variables in its surrounding lexical environment.

### Runnable example
```javascript
function makeCounter(start = 0) {
  let count = start;
  return () => ++count;
}
const next = makeCounter(5);
console.log(next(), next()); // 6 7
```

### Walkthrough
`count` remains available to the returned function even after `makeCounter` has returned. Each invocation creates a distinct enclosed state.

### Practice challenge
Create a function factory `makeMultiplier(n)` that returns a function multiplying by `n`.

<details><summary>Suggested solution / checkpoint</summary>

`const makeMultiplier = n => value => n * value;`

</details>

### Production insight
Prefer pure functions for business logic and isolate side effects.

**Common mistake:** Assuming closures copy values rather than retaining bindings.

---

## 7. Arrays and Collection Methods

### Core idea
Arrays store ordered collections. `map` transforms, `filter` selects, `find` retrieves, `some` tests, and `reduce` accumulates. Non-mutating methods are easier to reason about than `sort`, `splice` or `push` when state must stay immutable.

### Runnable example
```javascript
const courses = [{name:'JS',fee:30000},{name:'CSS',fee:20000}];
const affordable = courses.filter(c => c.fee <= 25000).map(c => c.name);
console.log(affordable); // ['CSS']
```

### Walkthrough
Each method creates a new array. Chaining is readable when each step has a clear purpose.

### Practice challenge
Compute the sum of all course fees with `reduce`.

<details><summary>Suggested solution / checkpoint</summary>

`const sum = courses.reduce((total, c) => total + c.fee, 0);`

</details>

### Production insight
Use `.toSorted()` where supported, or `[...items].sort(...)` to avoid mutation.

**Common mistake:** Forgetting to return from a `map` callback with braces.

---

## 8. Objects, Destructuring and Spread

### Core idea
Objects group named values and methods. Destructuring extracts properties; spread creates shallow copies; optional chaining safely accesses missing paths. Objects compare by identity, not structural equality.

### Runnable example
```javascript
const learner = {name:'Ada', profile:{city:'Abuja'}};
const {name, profile:{city}} = learner;
const updated = {...learner, name:'Adaeze'};
console.log(name, city, updated.name);
```

### Walkthrough
Spreading copies only the outer object. Nested objects still reference the original unless copied separately.

### Practice challenge
Create a student object and update one nested property without mutating the original.

<details><summary>Suggested solution / checkpoint</summary>

`const changed = {...learner, profile:{...learner.profile, city:"Lagos"}};`

</details>

### Production insight
Use `structuredClone` for suitable structured data; it cannot clone functions.

**Common mistake:** Believing `{...object}` performs a deep copy.

---

## 9. Equality, Truthiness and Edge Cases

### Core idea
JavaScript has coercion rules. Falsy values include `false`, `0`, `-0`, `0n`, `""`, `null`, `undefined` and `NaN`. Arrays and objects are truthy even when empty.

### Runnable example
```javascript
console.log(Boolean([])); // true
console.log('5' === 5); // false
console.log(null ?? 'fallback'); // fallback
console.log(0 ?? 99); // 0
```

### Walkthrough
Use strict equality for most comparisons and explicit validation for user input.

### Practice challenge
Explain the result of `[] == false` and why you should not rely on it.

<details><summary>Suggested solution / checkpoint</summary>

Loose equality coerces operands and yields `true`; use explicit conversion or strict equality.

</details>

### Production insight
When an input may be empty, check its length or content rather than only truthiness.

**Common mistake:** Assuming `[]` is falsy.

---


# Part II — Browser and Application Development

## 10. DOM Selection and Updates

### Core idea
The DOM is a browser-maintained object tree. Use `querySelector`, `textContent`, `classList`, and element creation to change the page. Treat user text as text, not HTML.

### Runnable example
```javascript
const output = document.querySelector('#output');
const button = document.querySelector('#show');
button.addEventListener('click', () => {
  output.textContent = 'Welcome to JavaScript!';
});
```

### Walkthrough
Create HTML with `<button id="show">Show</button><p id="output"></p>` and load your script with `defer` or as a module so elements exist when queried.

### Practice challenge
Build a counter with increment, decrement and reset buttons.

<details><summary>Suggested solution / checkpoint</summary>

Keep a `let count = 0`, update `textContent`, and attach three click listeners.

</details>

### Production insight
Use `textContent` for untrusted content; avoid unsafe `innerHTML`.

**Common mistake:** Calling `.addEventListener` on `null` because the element is missing.

---

## 11. Events, Forms and Validation

### Core idea
Events connect user actions to logic. `submit` events are better than button clicks for forms because keyboard submission works. Use built-in HTML constraints and add clear, accessible feedback.

### Runnable example
```javascript
const form = document.querySelector('#signup');
form.addEventListener('submit', event => {
  event.preventDefault();
  const data = new FormData(form);
  const email = String(data.get('email') ?? '').trim();
  console.log(email.includes('@') ? 'Received' : 'Check email');
});
```

### Walkthrough
Add `<form id="signup"><input name="email" type="email" required><button>Join</button></form>`. HTML validation runs before a valid submit event.

### Practice challenge
Build a registration form with name, email and programme; show errors without alerts.

<details><summary>Suggested solution / checkpoint</summary>

Read values with `FormData`, validate required fields, and write messages into an `aria-live="polite"` region.

</details>

### Production insight
Validate again on the server; browser validation is not a security boundary.

**Common mistake:** Relying on front-end checks to protect a backend.

---

## 12. Modules and Project Structure

### Core idea
ES modules let files import and export named functionality. Modules use strict mode and have their own scope. In browsers, serve modules over HTTP instead of opening local files directly.

### Runnable example
```javascript
// math.js
export const add = (a, b) => a + b;
// main.js
import {add} from './math.js';
console.log(add(2, 3));
```

### Walkthrough
In HTML use `<script type="module" src="./main.js"></script>`. For a simple dev server run `python3 -m http.server 8000` and visit localhost.

### Practice challenge
Separate tuition calculations from DOM event handling into two modules.

<details><summary>Suggested solution / checkpoint</summary>

Export a pure `calculateTotal` function; import it in the UI module.

</details>

### Production insight
Keep modules cohesive and avoid circular imports.

**Common mistake:** Forgetting relative paths and `.js` in browser module imports.

---

## 13. Errors, Debugging and Defensive Code

### Core idea
Errors can be syntax, runtime or logic errors. Use `try/catch` for operations that may throw; do not use it to conceal bugs. Debug with breakpoints and readable stack traces.

### Runnable example
```javascript
function parseStudent(json) {
  try {
    const value = JSON.parse(json);
    if (!value || typeof value.name !== 'string') throw new Error('Missing name');
    return {ok:true, value};
  } catch (error) { return {ok:false, message:error.message}; }
}
console.log(parseStudent('{"name":"Ada"}'));
```

### Walkthrough
`JSON.parse` can throw. The function returns an explicit success/failure result instead of crashing the caller.

### Practice challenge
Handle invalid JSON and missing properties in a profile importer.

<details><summary>Suggested solution / checkpoint</summary>

Use `try/catch` for parsing, validate fields, and display actionable error messages.

</details>

### Production insight
Log useful context without exposing secrets or private data.

**Common mistake:** Swallowing errors with an empty catch block.

---

## 14. Asynchronous JavaScript and Promises

### Core idea
JavaScript can start I/O work without blocking all further execution. Promises represent eventual fulfilment or rejection; `async` functions always return promises. Microtasks generally run before the next timer task.

### Runnable example
```javascript
async function getMessage() {
  const value = await Promise.resolve('Ready');
  return value;
}
getMessage().then(console.log);
console.log('This prints first');
```

### Walkthrough
`await` suspends only the async function, not the entire runtime. The synchronous log runs before the resolved promise handler.

### Practice challenge
Write an async function that waits for two independent promises.

<details><summary>Suggested solution / checkpoint</summary>

Use `const [a,b] = await Promise.all([first(),second()]);` for independent work.

</details>

### Production insight
Use `Promise.allSettled` when you need every outcome even if one fails.

**Common mistake:** Forgetting to `await` a promise or handle rejection.

---

## 15. Fetch, APIs and JSON

### Core idea
`fetch()` requests resources and returns a Response. HTTP 404/500 do not automatically reject `fetch`; check `response.ok`. Parse JSON only when appropriate and handle loading/error states.

### Runnable example
```javascript
async function loadPosts() {
  const response = await fetch('https://jsonplaceholder.typicode.com/posts?_limit=2');
  if (!response.ok) throw new Error(`HTTP ${response.status}`);
  return response.json();
}
loadPosts().then(console.log).catch(console.error);
```

### Walkthrough
Run this in a browser with internet access. The endpoint is a demonstration service, not a production dependency.

### Practice challenge
Fetch course data from a local JSON file and render titles into a list.

<details><summary>Suggested solution / checkpoint</summary>

Use `fetch("./courses.json")`, check `ok`, await `.json()`, and create `li` nodes with `textContent`.

</details>

### Production insight
Abort obsolete requests with `AbortController` and avoid exposing API secrets in client code.

**Common mistake:** Assuming a fulfilled fetch means the server returned success.

---

## 16. Timers, Debouncing and the Event Loop

### Core idea
`setTimeout` schedules later work; it does not pause JavaScript. Debouncing waits for input to settle before running expensive work. Understand call stack, task queue and microtask queue.

### Runnable example
```javascript
function debounce(fn, delay) {
  let timer;
  return (...args) => {
    clearTimeout(timer);
    timer = setTimeout(() => fn(...args), delay);
  };
}
const search = debounce(term => console.log('Search:', term), 300);
```

### Walkthrough
Call `search("r")`, `search("re")`, `search("rea")` rapidly: only the final value logs after the delay.

### Practice challenge
Add debounced filtering to a course search field.

<details><summary>Suggested solution / checkpoint</summary>

Attach an `input` listener that calls a debounced filter function.

</details>

### Production insight
Throttle high-frequency scroll handlers when a steady update cadence is required.

**Common mistake:** Assuming timeout duration guarantees exact execution time.

---


# Part III — Advanced and Production JavaScript

## 17. Classes, Prototypes and this

### Core idea
JavaScript uses prototype-based inheritance. `class` syntax is convenient sugar over prototype behaviour. `this` depends on how ordinary functions are called; arrow functions capture lexical `this`.

### Runnable example
```javascript
class Course {
  constructor(title, fee) { this.title = title; this.fee = fee; }
  describe() { return `${this.title}: ₦${this.fee}`; }
}
const course = new Course('React', 45000);
console.log(course.describe());
```

### Walkthrough
Methods live on the prototype and are shared. Private class fields begin with `#` when encapsulation is needed.

### Practice challenge
Create a `Student` class with `enrol(course)` and `listCourses()` methods.

<details><summary>Suggested solution / checkpoint</summary>

Store courses in an array, push only valid courses, and return a copy with `[...this.courses]`.

</details>

### Production insight
Prefer composition when inheritance hierarchies become complex.

**Common mistake:** Passing an unbound method as a callback and losing `this`.

---

## 18. Functional Patterns and Immutability

### Core idea
Pure functions return the same output for the same inputs without observable side effects. Higher-order functions accept or return functions. Immutable updates help with predictable state and testing.

### Runnable example
```javascript
const addCourse = (courses, course) => [...courses, course];
const before = ['HTML'];
const after = addCourse(before, 'JavaScript');
console.log(before, after);
```

### Walkthrough
The original array remains unchanged. The new array can be passed to a UI renderer or state manager.

### Practice challenge
Write `removeCourse(courses, title)` without mutating its input.

<details><summary>Suggested solution / checkpoint</summary>

`const removeCourse = (items,title) => items.filter(x => x !== title);`

</details>

### Production insight
Avoid premature abstraction; use functional patterns where they reduce complexity.

**Common mistake:** Mutating an object inside a supposedly pure function.

---

## 19. Browser Storage and Security

### Core idea
`localStorage` stores strings persistently per origin, but is accessible to scripts on that origin. It is not appropriate for access tokens or secrets. Validate and encode data at trust boundaries.

### Runnable example
```javascript
const settings = {theme:'dark'};
localStorage.setItem('settings', JSON.stringify(settings));
const saved = JSON.parse(localStorage.getItem('settings') ?? '{}');
console.log(saved.theme);
```

### Walkthrough
Run in a browser. Storage may be unavailable or restricted in some contexts; production apps should handle storage errors.

### Practice challenge
Save a non-sensitive theme preference and restore it after refresh.

<details><summary>Suggested solution / checkpoint</summary>

Store `"light"` or `"dark"` only, validate the retrieved value, and update the document class.

</details>

### Production insight
Prevent XSS with safe DOM APIs, avoid `eval`, and use secure server-side authentication.

**Common mistake:** Putting passwords, private API keys or session tokens into localStorage.

---

## 20. Testing JavaScript

### Core idea
Tests express expected behaviour and protect against regressions. Unit tests focus on pure functions; integration tests exercise interactions. Node includes a built-in `node:test` runner in current releases.

### Runnable example
```javascript
// fees.test.mjs
import test from 'node:test';
import assert from 'node:assert/strict';
test('applies discount', () => {
  const total = 10000 * (1 - 0.2);
  assert.equal(total, 8000);
});
```

### Walkthrough
Save the snippet and run `node --test fees.test.mjs`. Check success, boundary and invalid cases.

### Practice challenge
Write three tests for a score classifier including 39, 40 and 80.

<details><summary>Suggested solution / checkpoint</summary>

Assert that 39 is Beginner, 40 Intermediate, and 80 Advanced.

</details>

### Production insight
Test observable behaviour rather than implementation details.

**Common mistake:** Testing only the happy path.

---

## 21. Performance, Accessibility and Maintainability

### Core idea
Efficient JavaScript avoids unnecessary DOM work, oversized bundles and blocking tasks. Accessibility requires semantic HTML, keyboard operation and clear focus states; JavaScript should enhance rather than replace these foundations.

### Runnable example
```javascript
const list = document.querySelector('#results');
const fragment = document.createDocumentFragment();
for (const title of ['HTML','CSS','JavaScript']) {
  const li = document.createElement('li');
  li.textContent = title;
  fragment.append(li);
}
list.append(fragment);
```

### Walkthrough
Build nodes off-screen and append them together. Profile before optimising and consider rendering fewer items for very long lists.

### Practice challenge
Make a keyboard-operable disclosure widget using a native `<details>` element.

<details><summary>Suggested solution / checkpoint</summary>

Use `<details><summary>Course details</summary><p>...</p></details>`; native semantics reduce custom JS.

</details>

### Production insight
Use Lighthouse and DevTools Performance to measure real bottlenecks.

**Common mistake:** Optimising code without measuring or ignoring keyboard navigation.

---

## 22. Advanced Patterns and Architecture

### Core idea
Advanced JS includes iterators/generators, `Map`, `Set`, typed arrays, event delegation and structured concurrency patterns. Use the simplest structure that satisfies requirements.

### Runnable example
```javascript
const unique = [...new Set(['JS','CSS','JS'])];
const byId = new Map([[1,{name:'Ada'}]]);
function* ids() { let id=1; while(true) yield id++; }
console.log(unique, byId.get(1), ids().next().value);
```

### Walkthrough
`Set` deduplicates values; `Map` accepts keys of any type; generators yield values lazily.

### Practice challenge
Build an event-delegated list with one click handler on the parent.

<details><summary>Suggested solution / checkpoint</summary>

Attach a listener to the `<ul>` and inspect `event.target.closest("button[data-id]")`.

</details>

### Production insight
Prefer explicit module boundaries over creating a large global singleton.

**Common mistake:** Introducing elaborate patterns to solve simple problems.

---


# Guided labs

Complete each lab in its own directory with `README.md`, working code and screenshots where relevant.

| Lab | Deliverable | Acceptance test |
|---|---|---|
| 1 | Tip and tax calculator | Handles zero, invalid input and rounding |
| 2 | Grade classifier | Tests all score boundaries |
| 3 | Array analytics | Correct sum, mean, min and max |
| 4 | Student record manager | Add, edit, search and delete without duplicate IDs |
| 5 | Accessible counter | Mouse and keyboard controls work |
| 6 | Registration form | Inline errors and success message |
| 7 | Filterable course catalogue | Search is case-insensitive |
| 8 | Theme switcher | Theme persists on refresh |
| 9 | Async loading widget | Loading, success and failure states |
| 10 | API-powered list | Checks `response.ok` and handles offline state |
| 11 | Debounced search | Rapid input does not trigger repeated heavy work |
| 12 | Tested tuition calculator | Automated tests pass for boundary cases |

**Lab review method:** predict output, implement, test manually, add at least one automated test, then explain one improvement you would make.

# Portfolio projects

### Project A — Personal expense tracker (foundation)
**Requirements:** add income/expenses, category filters, totals, validation and browser persistence. **Stretch:** CSV export and accessible chart summary. **Proof:** demonstrate correct totals after reload.

### Project B — Student registration dashboard (intermediate)
**Requirements:** add/search/edit/remove students, programme selection, form validation, pagination or filtering, modular architecture and tests. **Stretch:** import/export JSON and duplicate detection. **Proof:** document at least five edge cases.

### Project C — API-powered course explorer (advanced)
**Requirements:** fetch course data, show loading/empty/error states, filter and sort, cancel stale requests, and use semantic markup. **Stretch:** caching and optimistic favourites. **Proof:** simulate network failures and explain recovery.

# Final capstone

## Training Academy Admissions App — Final assessment
Build a responsive, accessible multi-page or single-page web application using **vanilla JavaScript** (no UI framework required). Features: course catalogue; programme details; enquiry/registration form; client-side validation; saved preferences; accessible navigation; an API-backed or local JSON data source; robust loading/empty/error states; and testable tuition calculations.

**Suggested structure:** `index.html`, `src/main.js`, `src/data/courses.js`, `src/lib/fees.js`, `src/ui/render.js`, `src/styles.css`, `tests/`, `README.md`.

**Milestones:** (1) sketch data and UI; (2) implement core logic; (3) connect DOM and events; (4) integrate async data; (5) test and audit; (6) deploy and document.

**100-point rubric:** functionality 30; code quality/modules 20; accessibility 15; tests/error handling 15; responsiveness 10; documentation/deployment 10. **Pass target:** 75+ with no critical accessibility or security issue.

**Oral defence:** explain event propagation, why you used `textContent`, your async error strategy, one boundary test, and a performance trade-off.

# Knowledge checks and answers

1. **`let` versus `const`?** `let` permits reassignment; `const` does not, but referenced objects can still mutate.
2. **`===` versus `==`?** Strict equality avoids cross-type coercion; loose equality may coerce.
3. **Why is `0.1 + 0.2 !== 0.3`?** Binary floating-point representation.
4. **What is a closure?** A function retaining access to its lexical environment.
5. **`map` versus `forEach`?** `map` produces a transformed array; `forEach` is for side effects.
6. **Why check `response.ok`?** HTTP error statuses usually fulfil the fetch promise.
7. **What does `await` do?** Suspends execution inside an async function until a promise settles.
8. **What is event delegation?** Handling descendant events via a common ancestor.
9. **What is XSS?** Untrusted content executing as script in a trusted origin.
10. **Why avoid DOM `innerHTML` for user text?** It can interpret markup and introduce injection vulnerabilities.
11. **What is a pure function?** No observable side effects and stable output for the same input.
12. **When use `Map`?** Key-value associations where non-string keys or iteration semantics are useful.
13. **What is the event loop?** The runtime mechanism coordinating synchronous execution, tasks and microtasks.
14. **How do you debug?** Reproduce, inspect inputs, use breakpoints, isolate cause, fix and test regression.
15. **What makes code production-ready?** Correctness, security, accessibility, tests, performance, monitoring and documentation.

# Glossary

- **API:** interface for interacting with a service or library.
- **Callback:** function supplied to another function.
- **Closure:** function plus its retained lexical bindings.
- **DOM:** browser representation of document nodes.
- **Event bubbling:** propagation from target toward ancestors.
- **Hoisting:** declaration processing before execution of a scope.
- **Immutable update:** producing a new value rather than mutating the old one.
- **JSON:** text data interchange format.
- **Microtask:** high-priority queued job such as a promise reaction.
- **Module:** file with explicit imports/exports.
- **Promise:** eventual success/failure of asynchronous work.
- **Prototype:** object used for property delegation.
- **Side effect:** observable change beyond returning a value.
- **XSS:** cross-site scripting vulnerability.

# Learning roadmap and mastery checklist

| Week | Focus | Evidence |
|---|---|---|
| 1 | Runtime, variables, operators, conditions | Calculator |
| 2 | Loops, functions, arrays | Data-analysis exercises |
| 3 | Objects, coercion, edge cases | Student records |
| 4 | DOM, events, forms | Accessible registration form |
| 5 | Modules, debugging, errors | Modular refactor |
| 6 | Promises, fetch, timers | API course explorer |
| 7 | Classes, functional patterns, storage | Expense tracker |
| 8 | Security, testing, performance | Tested application |
| 9–10 | Capstone and deployment | Demo + README + oral defence |

**Mastery checklist:** I can explain value vs reference; choose `const`/`let`; implement and test functions; transform arrays; avoid accidental mutation; manipulate DOM safely; validate forms; handle async failures; separate modules; write automated tests; explain XSS risks; and deploy an accessible app.

**Further reading:** [MDN JavaScript Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide), [JavaScript language reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference), [Node.js documentation](https://nodejs.org/en/learn), [web.dev Learn JavaScript](https://web.dev/learn/javascript).
