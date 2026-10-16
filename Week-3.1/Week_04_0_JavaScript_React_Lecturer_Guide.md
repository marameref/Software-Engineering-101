# WEEK 4.0 — JAVASCRIPT FOUNDATIONS & INTRODUCTORY REACT.JS

**Opsfuxion Technologies Limited**  
*Orchestrate Intelligence, Deliver with Precision.*

**Practical Software Engineering Foundation Programme | Lecturer's Complete Teaching Manual**  
**Status:** Supplementary introductory frontend module, distinct from the Python module  
**Level:** Beginner | **Contact time:** 3 × 120 minutes = 6 hours | **Independent practice:** 6–10 hours  
**Prerequisites:** Week 1 HTML, Week 2 CSS, Week 3 Git/GitHub  
**Final product:** Interactive Student Profile Application built with React and Vite

> **Important scope:** This is an *introduction*, not a comprehensive JavaScript/React qualification. Three classes introduce JavaScript, DOM/events, React components, props and state. Do not claim the learner has mastered modern frontend engineering. **STUDENT TASK** must be attempted before showing **INSTRUCTOR SOLUTION**. All code solutions are examples; equivalent correct approaches are acceptable.

---

## Lecturer quick-start: what to prepare

- Verify `node --version`, `npm --version`, `git --version`; use a current supported Node.js LTS version. Vite requirements change, so follow the compatibility message from `npm create vite@latest` if a version mismatch occurs.
- Open VS Code, browser Developer Tools (Console), terminal, and a browser preview of Week 2 portfolio.
- Create `week-04-0-react/` and `javascript-labs/` before class. Have stable internet for `npm install` or a pre-installed starter prepared.
- Explain **HTML = structure**, **CSS = presentation**, **JavaScript = behaviour**, **React = component-based interface library**.
- Use plain JavaScript for initial exercises; JSX is introduced only after the student understands variables, functions, arrays and event handling.
- Check the student can type and explain each example. If JavaScript fundamentals are shaky, assign extra practice rather than racing through hooks.

### End-of-module success criteria

Student can write basic JS expressions/functions, modify text on a page through the DOM, explain a React component, pass a prop, update `useState` via an event handler, render a list with stable keys, handle a form without refreshing the page, and explain that the project stores data **in memory only**.

### Instructor pedagogy

**I do → We do → You do:** First demonstrate, then pair-code, then allow 10–20 minutes of independent work. Ask for predictions *before* running code. Explain every error aloud: what the message says, where it occurs, what was expected, and how to verify the fix. Save completed solutions in an instructor-only folder rather than publishing them beside unfinished student exercises.

---

# SESSION 1 — JAVASCRIPT FUNDAMENTALS & THE DOM (120 MINUTES)

| Time | Topic | Instructor action |
|---|---|---|
| 0–10 | Prior knowledge check | Ask what HTML/CSS can and cannot do |
| 10–30 | JS basics | `let`, `const`, strings, numbers, booleans, `console.log` |
| 30–50 | Operators and conditions | Comparisons, `===`, `if/else`, truthy/falsy |
| 50–70 | Functions, arrays, objects | Write functions and inspect data |
| 70–90 | DOM and events | `querySelector`, `.textContent`, `addEventListener` |
| 90–112 | Guided lab | Interactive greeting and score checker |
| 112–120 | Exit quiz | Explain output and debug one mistake |

## Lecture 1.1 — What JavaScript adds to a website

**Say:** “A contact form written in HTML can collect typed values. JavaScript can react to clicks, validate input, and update the page without loading a new document. It does *not* automatically send data to a server.”

Open browser DevTools → Console. Type:

```js
console.log('Hello, developer!');
console.log(2 + 3);
```

Explain `console.log` as a developer diagnostic, not visible webpage content. Use `//` and `/* ... */` comments. Show that JS is case-sensitive (`studentName` differs from `StudentName`).

## Lecture 1.2 — Variables and data types

```js
const studentName = 'Uzoamaka'; // cannot reassign this binding
let age = 16;                   // can reassign
const isEnrolled = true;
let score = 85.5;

age = age + 1;
console.log(studentName, age, isEnrolled, score);
console.log(typeof studentName); // string
console.log(typeof age);         // number
console.log(typeof isEnrolled);  // boolean
```

**Teach:** `const` does not make objects immutable; it prevents reassigning the variable. Prefer `const` unless reassignment is needed. Explain `undefined` and `null` briefly.

**Predict before running:** What prints for `2 + '3'`? Answer: `'23'`, due to string concatenation. Use `Number('3')` for explicit conversion.

## Lecture 1.3 — Conditions, operators and comparison

```js
const score = 72;
if (score >= 50) {
  console.log('PASS');
} else {
  console.log('FAIL');
}

console.log(5 === '5'); // false: strict equality checks type
console.log(5 == '5');  // true: coercion; avoid in beginner projects
```

Explain `>`, `<`, `>=`, `<=`, `===`, `!==`, `&&`, `||`, `!`. Highlight boundary testing: score 49, 50, 100. Show why `=` is assignment, not equality.

## Lecture 1.4 — Functions, arrays, objects

```js
function calculateAverage(scores) {
  if (scores.length === 0) return null;
  const total = scores.reduce((sum, score) => sum + score, 0);
  return total / scores.length;
}

const scores = [70, 85, 90];
const student = { id: 1, name: 'Uzoamaka', course: 'Software Engineering' };
console.log(student.name);
console.log(scores.map((score) => score + 5));
console.log(calculateAverage(scores));
```

Explain `return` vs `console.log`; zero-based indexing; `map` creates a new array; `reduce` accumulates a value. If these methods overwhelm the learner, teach the equivalent `for...of` loop first:

```js
let total = 0;
for (const score of scores) total += score;
console.log(total / scores.length);
```

## Lecture 1.5 — DOM: JavaScript meets HTML

**Say:** “The DOM is the browser's object representation of the HTML page. JavaScript can select elements and update them.”

Create `javascript-labs/greeting.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Interactive Greeting</title>
</head>
<body>
  <label for="student-name">Your name</label>
  <input id="student-name" type="text">
  <button id="greet-button" type="button">Greet me</button>
  <p id="output" aria-live="polite"></p>

  <script>
    const input = document.querySelector('#student-name');
    const button = document.querySelector('#greet-button');
    const output = document.querySelector('#output');

    button.addEventListener('click', () => {
      const name = input.value.trim();
      output.textContent = name ? `Hello, ${name}!` : 'Please enter your name.';
    });
  </script>
</body>
</html>
```

**Walk through line by line:** `querySelector` finds the element; `.value` reads input; `.trim()` removes surrounding whitespace; click handler runs only on click; `.textContent` updates text safely; `aria-live` announces dynamic output to some assistive technologies. Explain why the script is placed after the elements here.

### STUDENT TASK 1A — Predict the output (8 minutes)

```js
const student = { name: 'Ada', scores: [40, 60, 80] };
const result = student.scores.filter((score) => score >= 50);
console.log(result.length);
```

**INSTRUCTOR SOLUTION:** `2`; `filter` keeps 60 and 80. Have learner explain why 40 is excluded.

### STUDENT TASK 1B — Interactive score checker (14 minutes)

Create an HTML page with number input, a Check button, and result paragraph. Display `PASS` if 50–100, `FAIL` if 0–49, and `Enter a score between 0 and 100` otherwise. Empty input must be rejected.

**INSTRUCTOR SOLUTION:**

```html
<label for="score">Score</label>
<input id="score" type="number" min="0" max="100">
<button id="check" type="button">Check</button>
<p id="result" aria-live="polite"></p>
<script>
  const scoreInput = document.querySelector('#score');
  document.querySelector('#check').addEventListener('click', () => {
    const raw = scoreInput.value.trim();
    const score = Number(raw);
    const message = raw === '' || !Number.isFinite(score) || score < 0 || score > 100
      ? 'Enter a score between 0 and 100'
      : score >= 50 ? 'PASS' : 'FAIL';
    document.querySelector('#result').textContent = message;
  });
</script>
```

**Checkpoints:** blank, -1, 0, 49, 50, 100, 101. Ask why `Number('') === 0` makes the empty check necessary.

### Independent assignment — Session 1

**Build a Mini Student Profile (plain JavaScript):** HTML input for name, course and score; button generates a summary below the form. Reject blank name/course and invalid score; show PASS/FAIL. Write `README.md` describing the interaction.

**Instructor reference algorithm:** Read `.value`, trim text, validate, convert score with `Number`, construct output using `.textContent`, never use user-supplied strings in `innerHTML`. **Suggested rubric:** correctness 40%, validation 25%, clear code 20%, explanation 15%.

### Exit questions (with answers)

1. `let` vs `const`? **Reassignable binding vs non-reassignable binding.**
2. What does `===` check? **Value and type without coercion.**
3. What is an event listener? **A callback registered for an event.**
4. Does DOM manipulation save data permanently? **No.**
5. Why `textContent`? **It displays text rather than parsing it as HTML.**

---

# SESSION 2 — REACT, VITE, JSX, COMPONENTS & PROPS (120 MINUTES)

| Time | Topic | Instructor action |
|---|---|---|
| 0–15 | Review JS assignment | Run and discuss learner's code |
| 15–30 | React mental model | Components and declarative UI |
| 30–55 | Create Vite project | CLI commands, files, dev server |
| 55–75 | JSX rules | Expressions, className, one parent |
| 75–95 | Components and props | Reusable StudentCard |
| 95–115 | Guided lab | Render multiple student cards |
| 115–120 | Exit quiz | Component vs prop |

## Lecture 2.1 — Why React?

**Say:** “In the DOM lab, we manually selected and updated HTML elements. React lets us describe the UI for a given set of data. When data changes, React updates the rendered interface.”

**Clarify:** React is a UI library, not a database, backend, or full application framework. Vite is a development/build tool. JSX looks like HTML but is JavaScript syntax transformed by the build tool.

## Lecture 2.2 — Vite setup, explained command by command

```bash
node --version
npm --version
npm create vite@latest student-profile-react -- --template react
cd student-profile-react
npm install
npm run dev
```

Open the local URL printed by Vite (often `http://localhost:5173/`). Do not hard-code that URL as a guarantee. If prompted to install `create-vite`, approve it. Explain `package.json` (scripts/dependencies), `node_modules/` (installed packages), `src/` (application source), `public/` (static files), `index.html` (entry HTML), `src/main.jsx` (React mount), `src/App.jsx` (root component). `npm run dev` starts a local server; it does not publish a website.

**Troubleshooting:** `node: command not found` → install Node.js LTS; unsupported engine → use compatible LTS; port busy → use URL shown; missing modules → run `npm install` from folder with `package.json`; blank page → inspect browser console and terminal.

## Lecture 2.3 — JSX rules

Replace `src/App.jsx`:

```jsx
function App() {
  const course = 'Software Engineering';
  return (
    <main>
      <h1>Welcome to React</h1>
      <p>Course: {course}</p>
      <p className="intro">This is JSX.</p>
    </main>
  );
}
export default App;
```

**Explain:** component names begin with uppercase; JSX expressions use `{}`; return one enclosing parent (or fragment `<>...</>`); `className` instead of `class`; tags such as `<input />` must be closed. JSX event props use camelCase (`onClick`).

**Live debugging exercise:** Intentionally change `className` to `class`, omit a closing tag, then restore. Discuss warnings/errors rather than asking student to memorise them.

## Lecture 2.4 — Reusable components and props

Create `src/components/StudentCard.jsx`:

```jsx
export default function StudentCard({ name, course, score }) {
  return (
    <article className="student-card">
      <h2>{name}</h2>
      <p>Course: {course}</p>
      <p>Score: {score}</p>
      <p>Status: {score >= 50 ? 'PASS' : 'FAIL'}</p>
    </article>
  );
}
```

In `src/App.jsx`:

```jsx
import StudentCard from './components/StudentCard.jsx';

export default function App() {
  return (
    <main>
      <h1>Student Profiles</h1>
      <StudentCard name="Uzoamaka" course="Software Engineering" score={85} />
      <StudentCard name="Ada" course="Data Science" score={46} />
    </main>
  );
}
```

**Explain:** props are values passed *from parent to child*. The child reads them but should not mutate them. A component is a reusable function returning JSX. Numeric props use `{85}` instead of the string `'85'`.

### STUDENT TASK 2A — Modify a component (10 minutes)

Add a `school` prop and show it in each card. Then render a third student.

**INSTRUCTOR SOLUTION:** Add `school` to destructuring; insert `<p>School: {school}</p>`; supply `school="Example College"` on each component. Discuss why missing props render no meaningful text.

### STUDENT TASK 2B — Render a list (10 minutes)

Replace repeated card markup with an array and `.map()`.

**INSTRUCTOR SOLUTION:**

```jsx
import StudentCard from './components/StudentCard.jsx';
const students = [
  { id: 'ST001', name: 'Uzoamaka', course: 'Software Engineering', score: 85 },
  { id: 'ST002', name: 'Ada', course: 'Data Science', score: 46 },
  { id: 'ST003', name: 'Chidi', course: 'Cybersecurity', score: 73 },
];
export default function App() {
  return (
    <main>
      <h1>Student Profiles</h1>
      {students.map((student) => (
        <StudentCard key={student.id} {...student} />
      ))}
    </main>
  );
}
```

Explain that `key` helps React identify list items; use stable IDs, not array indices for mutable lists. `...student` passes object properties as props. For a beginner, also show explicit `name={student.name}` etc.

### Independent assignment — Session 2

**Student Directory:** Render at least four StudentCard components from an array; each card shows ID, name, course, score, pass/fail. Use external CSS to style cards using Flexbox or Grid. Add a short README with a screenshot. **Rubric:** JSX/components 30%, props 25%, `.map()` and keys 20%, CSS 15%, explanation 10%.

### Exit questions (with answers)

1. React vs Vite? **UI library vs dev/build tool.**
2. What is JSX? **JavaScript syntax for describing UI elements.**
3. What are props? **Read-only values passed into a component.**
4. Why a `key`? **Stable identity for list items.**
5. Why uppercase `StudentCard`? **React distinguishes components from built-in tags.**

---

# SESSION 3 — STATE, EVENTS, FORMS & FINAL MINI-PROJECT (120 MINUTES)

| Time | Topic | Instructor action |
|---|---|---|
| 0–15 | Review directory | Run, inspect, ask questions |
| 15–35 | State and re-render | `useState`, immutable updates |
| 35–55 | Event handlers | Buttons and controlled inputs |
| 55–75 | Conditional rendering | Empty states, validation |
| 75–105 | Guided final project | Build interactive directory |
| 105–115 | Test and debug | Test cases |
| 115–120 | Exit reflection | Explain data flow |

## Lecture 3.1 — Why React state?

**Say:** “A normal variable does not tell React to re-render when it changes. State is data React tracks across renders. Call its setter to request an update.”

```jsx
import { useState } from 'react';
export default function Counter() {
  const [count, setCount] = useState(0);
  return (
    <section>
      <p>Count: {count}</p>
      <button onClick={() => setCount((previous) => previous + 1)}>Add one</button>
    </section>
  );
}
```

Explain destructuring `[value, setter]`, initial state `0`, functional updater, `onClick` receives a function rather than invoking it immediately. State is not persisted after a page reload in this project.

## Lecture 3.2 — Controlled inputs

```jsx
import { useState } from 'react';
export default function NameForm() {
  const [name, setName] = useState('');
  return (
    <div>
      <label htmlFor="name">Name</label>
      <input id="name" value={name} onChange={(event) => setName(event.target.value)} />
      <p>Hello, {name || 'visitor'}!</p>
    </div>
  );
}
```

**Explain:** `htmlFor` replaces HTML `for` in JSX; `value` binds the input to state; `onChange` updates it. Avoid direct DOM editing with `querySelector` inside React components for ordinary input updates.

## Lecture 3.3 — Conditional rendering and immutable arrays

```jsx
{students.length === 0 ? <p>No students registered.</p> : <p>{students.length} students</p>}
```

For arrays in state, do not call `students.push(newStudent)` and expect React to detect a new reference. Instead:

```jsx
setStudents((previous) => [...previous, newStudent]);
```

## Guided capstone — Interactive Student Profile Application

### Requirements (student-facing)

- Display at least two initial students.
- Show name, course, score and PASS/FAIL on each card.
- Provide controlled fields for name, course and score.
- Validate nonempty name/course and integer score from 0 to 100.
- Add new student on form submit without reloading.
- Show total student count and a friendly empty-state message.
- Use a stable ID for each new card.
- Style with CSS; explain the difference between state and props.

### INSTRUCTOR SOLUTION — `src/App.jsx` (complete)

```jsx
import { useState } from 'react';
import './App.css';

function StudentCard({ student }) {
  return (
    <article className="student-card">
      <h2>{student.name}</h2>
      <p>ID: {student.id}</p>
      <p>Course: {student.course}</p>
      <p>Score: {student.score}</p>
      <strong>{student.score >= 50 ? 'PASS' : 'FAIL'}</strong>
    </article>
  );
}

const starterStudents = [
  { id: 'ST001', name: 'Uzoamaka', course: 'Software Engineering', score: 85 },
  { id: 'ST002', name: 'Ada', course: 'Data Science', score: 45 },
];

export default function App() {
  const [students, setStudents] = useState(starterStudents);
  const [name, setName] = useState('');
  const [course, setCourse] = useState('');
  const [score, setScore] = useState('');
  const [error, setError] = useState('');
  const [nextId, setNextId] = useState(3);

  function handleSubmit(event) {
    event.preventDefault();
    const numericScore = Number(score);
    if (!name.trim() || !course.trim() || score.trim() === '' ||
        !Number.isInteger(numericScore) || numericScore < 0 || numericScore > 100) {
      setError('Enter a name, course and whole-number score from 0 to 100.');
      return;
    }
    const student = {
      id: `ST${String(nextId).padStart(3, '0')}`,
      name: name.trim(), course: course.trim(), score: numericScore,
    };
    setStudents((previous) => [...previous, student]);
    setNextId((previous) => previous + 1);
    setName(''); setCourse(''); setScore(''); setError('');
  }

  return (
    <main className="app">
      <h1>Student Profile Directory</h1>
      <p>Total students: {students.length}</p>
      <form onSubmit={handleSubmit} className="profile-form">
        <label htmlFor="student-name">Name</label>
        <input id="student-name" value={name} onChange={(e) => setName(e.target.value)} required />
        <label htmlFor="student-course">Course</label>
        <input id="student-course" value={course} onChange={(e) => setCourse(e.target.value)} required />
        <label htmlFor="student-score">Score</label>
        <input id="student-score" type="number" min="0" max="100" step="1"
          value={score} onChange={(e) => setScore(e.target.value)} required />
        <button type="submit">Add student</button>
        {error && <p role="alert">{error}</p>}
      </form>
      <section className="cards" aria-label="Student profiles">
        {students.length === 0 ? <p>No students registered.</p> :
          students.map((student) => <StudentCard key={student.id} student={student} />)}
      </section>
    </main>
  );
}
```

### INSTRUCTOR SOLUTION — `src/App.css`

```css
* { box-sizing: border-box; }
body { margin: 0; font-family: system-ui, sans-serif; background: #f3f6fb; color: #18233b; }
.app { max-width: 960px; margin: 0 auto; padding: 2rem 1rem; }
.profile-form { display: grid; gap: .6rem; padding: 1rem; background: white; border-radius: .7rem; margin-bottom: 1.5rem; }
input { width: 100%; padding: .65rem; border: 1px solid #a5aec0; border-radius: .35rem; }
button { background: #183b70; color: white; border: 0; border-radius: .35rem; padding: .8rem; cursor: pointer; }
button:focus-visible, input:focus-visible { outline: 3px solid #d2a43c; outline-offset: 2px; }
.cards { display: grid; grid-template-columns: repeat(auto-fit, minmax(min(100%, 240px), 1fr)); gap: 1rem; }
.student-card { background: white; padding: 1rem; border-radius: .7rem; box-shadow: 0 2px 8px #14223a12; }
.student-card h2 { margin-top: 0; }
[role="alert"] { color: #a21d2b; }
```

**Important:** Vite's default `src/index.css` may style `body`, buttons, etc. Remove starter rules or replace that file with a minimal reset to avoid conflicts. This application does **not** send data to a server or preserve records across refreshes.

### Testing matrix

| Input/action | Expected |
|---|---|
| Load page | Two starter students, total 2 |
| Add valid name/course/85 | New card, total 3 |
| Blank name | Browser blocks submission or custom validation |
| Score -1, 101, 75.5 | Rejected |
| Score 0 | Accepted, FAIL |
| Score 50 | Accepted, PASS |
| Click Add | No full-page reload |
| Refresh | Starter records return (no persistence) |

### STUDENT TASK 3A — Enhancement

Add a **Show passing students only** checkbox. When selected, display only students with score >= 50, but keep total registered count unchanged.

**INSTRUCTOR SOLUTION:**

```jsx
const [passingOnly, setPassingOnly] = useState(false);
const visibleStudents = passingOnly ? students.filter((student) => student.score >= 50) : students;
// In JSX:
<label><input type="checkbox" checked={passingOnly}
  onChange={(e) => setPassingOnly(e.target.checked)} /> Passing students only</label>
{visibleStudents.map((student) => <StudentCard key={student.id} student={student} />)}
```

**Explain:** derived `visibleStudents` should not usually be a separate state variable; calculate it from source state. Replace the original `students.map` rendering with `visibleStudents.map`, and adapt empty-state messaging as needed.

### Independent assignment — Session 3

**Extend the Student Profile Application:** add a Delete button per student, add a course filter, and display average score. Document which features are completed and which are future improvements.

**INSTRUCTOR SOLUTION snippets:**

```jsx
// In App:
function removeStudent(id) {
  setStudents((previous) => previous.filter((student) => student.id !== id));
}
const average = students.length
  ? (students.reduce((sum, student) => sum + student.score, 0) / students.length).toFixed(2)
  : 'N/A';
// Pass onDelete={removeStudent} to StudentCard and render inside it:
<button type="button" onClick={() => onDelete(student.id)}>Delete</button>
// Update signature to StudentCard({ student, onDelete }).
```

For course filtering, create `const [courseFilter, setCourseFilter] = useState('all')`, render a `<select>` from unique courses, and filter displayed records using `student.course === courseFilter` (or `all`). Ensure deleting a student updates the displayed average.

---

# Lecturer troubleshooting playbook

| Symptom | Likely cause | Check/fix |
|---|---|---|
| `npm` not found | Node missing | Install supported Node LTS, restart terminal |
| `package.json` not found | Wrong folder | `pwd`, `ls`, `cd student-profile-react` |
| Blank page | Syntax/import error | Browser console and Vite terminal |
| Component not rendered | Wrong import/export or lowercase tag | Check path, default export, capitalization |
| React warning about keys | Missing/unstable `key` | Use student ID |
| Typing doesn't work | `value` without `onChange` | Add controlled handler |
| Click causes full reload | Form default submission | `event.preventDefault()` |
| UI does not update | Mutating array directly | Use setter and new array |
| CSS appears odd | Starter Vite styles | Inspect `index.css` and specificity |
| Data disappears on refresh | State is in memory | Explain persistence is a later topic |

# Assessment and instructor answer key

## Oral questions (ask without notes)

1. Difference between HTML/CSS/JS? **Structure/presentation/behaviour.**
2. `const` vs `let`? **Binding reassignment.**
3. `===` vs `==`? **Strict vs coercive comparison.**
4. What is DOM? **Document Object Model.**
5. What is an event handler? **Function called when an event occurs.**
6. What is React? **Component-based UI library.**
7. What is Vite? **Development server/build tool.**
8. What is JSX? **JavaScript syntax for UI elements.**
9. What is a component? **Reusable unit of UI.**
10. What is a prop? **Input passed to a component.**
11. What is state? **React-managed component data that triggers updates.**
12. Why call state setter? **To schedule React re-render with new data.**
13. Why `preventDefault`? **Stop default form navigation.**
14. Why a list key? **Identify elements across renders.**
15. Does this project persist to database? **No.**

## Final rubric (100 marks)

| Category | Marks | Evidence |
|---|---:|---|
| JS foundations | 20 | Variables, conditions, functions |
| JSX and component structure | 20 | Valid components and reusable cards |
| Props and list rendering | 15 | Correct data flow, stable keys |
| State, forms and events | 20 | Controlled inputs, updates, no reload |
| Validation and testing | 10 | Boundaries, blank fields, helpful errors |
| CSS and accessibility basics | 5 | Labels, responsive cards, keyboard focus |
| GitHub and documentation | 10 | Commits, README, runnable instructions |
| **Total** | **100** | |

## Submission checklist

- [ ] `javascript-labs/` DOM exercises
- [ ] Vite React project runs with `npm install` and `npm run dev`
- [ ] At least two reusable components or a clear rationale for the component split
- [ ] Props and `useState` demonstrated
- [ ] Add-student form with validation
- [ ] Responsive CSS
- [ ] Tests recorded in README
- [ ] No `node_modules/` committed; `.gitignore` includes it
- [ ] At least three meaningful Git commits
- [ ] Student can explain every file and the limitations of in-memory data

## Homework stretch (optional, not assessed as mastery)

Explore `localStorage` persistence, then explain why browser storage is not a secure database and why user accounts/backend APIs require more learning. Do not teach Next.js as part of this six-hour introduction.

## Bridge to Week 4.1

React uses JavaScript; the next scheduled module returns to **Python fundamentals**, a separate language. Explicitly compare `const student = 'Ada'` in JS with `student = 'Ada'` in Python. Explain that `print()` replaces `console.log()` for beginner terminal examples and indentation defines Python blocks.

---

**Opsfuxion Technologies Limited** · *Orchestrate Intelligence, Deliver with Precision.*  
**Instructor edition — Week 4.0** · © 2026 Opsfuxion Technologies Limited.
