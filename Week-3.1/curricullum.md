
# ⚛️ Week 4 — Part 2: Introduction to React.js

## Practical Software Engineering Foundation Programme

![Module](https://img.shields.io/badge/Module-Frontend_Development-2563EB?style=for-the-badge)
![Technology](https://img.shields.io/badge/Technology-React.js-149ECA?style=for-the-badge&logo=react&logoColor=white)
![Level](https://img.shields.io/badge/Level-Beginner-16A085?style=for-the-badge)
![Duration](https://img.shields.io/badge/Duration-6_Hours-7C3AED?style=for-the-badge)

**Training Provider:** Opsfuxion Technologies Limited  
**Programme:** 12-Week Practical Software Engineering Foundation Programme  
**Module:** Week 4 — Part 2  
**Duration:** 3 Sessions  
**Session Duration:** 2 Hours  
**Total Instructor-Led Time:** 6 Hours  
**Prerequisites:** HTML, CSS, basic VS Code usage and Git/GitHub  
**Primary Technologies:** JavaScript, React.js, Vite  
**Weekly Project:** Interactive Student Profile Application

---

# 📖 Module Overview

This supplementary module introduces the student to modern frontend development using React.js.

Building on the HTML and CSS knowledge acquired in Weeks 1 and 2, the student will explore how JavaScript makes webpages interactive and how React enables developers to build user interfaces using reusable components.

The module introduces essential JavaScript concepts before progressing to JSX, components, props, state and event handling.

**Important:** This is an introductory exposure module, not a complete React course. JavaScript proficiency requires additional practice, and the student is not expected to master React within three sessions.

---

# 🎯 Learning Objectives

By the end of this module, the student should be able to:

- Explain the difference between HTML, CSS and JavaScript.
- Describe what React.js is.
- Understand the purpose of JavaScript in frontend development.
- Recognise JavaScript variables, functions, arrays and objects.
- Explain the concept of the Document Object Model (DOM).
- Understand what a React component is.
- Explain JSX.
- Create a basic React application using Vite.
- Understand the purpose of `package.json`.
- Create simple functional components.
- Pass information using props.
- Introduce interactivity using React state.
- Respond to button clicks using event handlers.
- Apply basic CSS styling to React components.
- Run and test a React application locally.

---

# 🗓️ Session 1 — JavaScript Foundations & Introduction to React

**Duration:** 2 Hours

## Session Objectives

The student will:

1. Understand JavaScript's role in web development.
2. Learn essential JavaScript syntax.
3. Understand the DOM at a conceptual level.
4. Understand what React is and why developers use it.
5. Prepare the development environment for React.

---

## 1. Review of HTML & CSS — 10 Minutes

Discuss the technologies previously introduced.

| Technology | Purpose |
|---|---|
| HTML | Structures webpage content |
| CSS | Controls appearance and layout |
| JavaScript | Adds logic and interactivity |
| React | Helps build interactive interfaces using components |

### Discussion

Consider a webpage containing a button.

HTML can create the button.

CSS can style the button.

JavaScript can define what happens when the button is clicked.

React helps organise interactive interfaces into reusable components.

---

## 2. Introduction to JavaScript — 25 Minutes

### What is JavaScript?

JavaScript is a programming language commonly used to make webpages interactive.

Examples include:

- Responding to button clicks
- Validating forms
- Updating displayed information
- Showing and hiding content
- Handling user interactions
- Communicating with backend services

### JavaScript Variables

```javascript
const studentName = "Uzoamaka";
let age = 16;

console.log(studentName);
console.log(age);
```

Explain the difference between `const` and `let`.

### JavaScript Data Types

```javascript
const name = "Uzoamaka";
const age = 16;
const isStudent = true;
```

Introduce:

- Strings
- Numbers
- Booleans

### JavaScript Functions

```javascript
function greetStudent(name) {
  return `Hello, ${name}!`;
}

console.log(greetStudent("Uzoamaka"));
```

### Arrow Functions

```javascript
const greet = (name) => {
  return `Welcome, ${name}!`;
};
```

Explain that arrow functions are common in modern React code.

---

## 3. JavaScript Arrays & Objects — 15 Minutes

### Arrays

```javascript
const subjects = [
  "Mathematics",
  "English",
  "Computer Science"
];

console.log(subjects[0]);
```

### Objects

```javascript
const student = {
  name: "Uzoamaka",
  age: 16,
  course: "Software Engineering"
};

console.log(student.name);
```

Explain that objects group related information.

---

## 4. Introduction to the DOM — 15 Minutes

The Document Object Model (DOM) represents a webpage as a structure that JavaScript can interact with.

### Example

HTML:

```html
<h1 id="greeting">Hello!</h1>
<button id="changeButton">Change Greeting</button>
```

JavaScript:

```javascript
const heading = document.getElementById("greeting");

document.getElementById("changeButton")
  .addEventListener("click", () => {
    heading.textContent = "Welcome to JavaScript!";
  });
```

### Discussion

JavaScript can change webpage content without reloading the entire page.

React provides a component-based approach to managing interface updates.

---

## 5. What is React.js? — 15 Minutes

React is a JavaScript library used to build user interfaces.

It was originally developed at Facebook and is widely used for interactive web applications.

### Why React?

- Reusable components
- Declarative user interfaces
- State-driven updates
- Easier organisation of complex interfaces
- Large development ecosystem

### Traditional HTML vs React

Traditional HTML:

```html
<h1>Welcome, Uzoamaka!</h1>
```

React:

```jsx
function Welcome() {
  return <h1>Welcome, Uzoamaka!</h1>;
}
```

Explain that React components are JavaScript functions that return UI descriptions.

---

## 6. Setting Up a React Project — 30 Minutes

### Prerequisites

Ensure the following are installed:

- VS Code
- Node.js (a supported LTS version)
- npm
- Git

### Verify Node.js

```bash
node --version
```

### Verify npm

```bash
npm --version
```

### Create a React Project

```bash
npm create vite@latest student-react-app -- --template react
```

Navigate into the project:

```bash
cd student-react-app
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

Open the local URL displayed in the terminal.

### Understanding the Project Structure

```text
student-react-app/
│
├── public/
├── src/
│   ├── assets/
│   ├── App.jsx
│   ├── App.css
│   ├── index.css
│   └── main.jsx
│
├── index.html
├── package.json
└── vite.config.js
```

Explain:

- `src/` — application source code
- `App.jsx` — main application component
- `main.jsx` — application entry point
- `package.json` — project configuration and dependencies
- `index.html` — HTML entry document

---

## 7. Session Review — 10 Minutes

### Knowledge Check

1. What is JavaScript?
2. What is the difference between HTML, CSS and JavaScript?
3. What is a function?
4. What is an array?
5. What is an object?
6. What is React?
7. What is a component?
8. What does Vite do?
9. What is npm?
10. What does `npm run dev` do?

---

# 📝 Session 1 Assignment

## JavaScript Student Information Exercise

Create a file named:

```text
student-info.js
```

Requirements:

1. Create a variable containing the student's name.
2. Create a variable containing the student's age.
3. Create an array of favourite subjects.
4. Create an object containing student information.
5. Write a function that displays a greeting.
6. Print the information using `console.log()`.

### Deliverable

A JavaScript file demonstrating basic syntax, variables, arrays, objects and functions.

---

# 🗓️ Session 2 — JSX, Components & Props

**Duration:** 2 Hours

## Session Objectives

The student will:

- Understand JSX.
- Create React components.
- Understand component reusability.
- Pass data using props.
- Style React components.
- Build a basic student profile interface.

---

## 1. Review of Session 1 — 15 Minutes

Review:

- JavaScript variables
- Arrays and objects
- Functions
- React project setup
- React project structure

Ask the student to explain how to start the React development server.

---

## 2. Introduction to JSX — 20 Minutes

JSX is a syntax extension commonly used with React that allows developers to describe user interfaces using HTML-like syntax inside JavaScript.

### Example

```jsx
function App() {
  return (
    <div>
      <h1>Hello, React!</h1>
      <p>Welcome to frontend development.</p>
    </div>
  );
}

export default App;
```

### Important JSX Rules

1. Components must return a single parent element or fragment.
2. Use `className` instead of `class`.
3. JavaScript expressions can be placed inside `{}`.
4. Tags must be properly closed.

### Example

```jsx
function App() {
  const studentName = "Uzoamaka";

  return (
    <div>
      <h1>Welcome, {studentName}!</h1>
    </div>
  );
}
```

---

## 3. Understanding Components — 25 Minutes

A component is a reusable part of a user interface.

### Example

Create:

```text
src/components/Header.jsx
```

```jsx
function Header() {
  return (
    <header>
      <h1>Student Portfolio</h1>
      <p>My First React Application</p>
    </header>
  );
}

export default Header;
```

Import the component into `App.jsx`.

```jsx
import Header from "./components/Header";

function App() {
  return (
    <div>
      <Header />
      <main>
        <p>Welcome to my portfolio.</p>
      </main>
    </div>
  );
}

export default App;
```

### Discussion

Why are reusable components useful?

Examples:

- Navigation bars
- Headers
- Footers
- Buttons
- Profile cards
- Forms

---

## 4. Introduction to Props — 25 Minutes

Props allow parent components to pass information to child components.

### Example

Create:

```text
src/components/StudentCard.jsx
```

```jsx
function StudentCard({ name, age, course }) {
  return (
    <article className="student-card">
      <h2>{name}</h2>
      <p>Age: {age}</p>
      <p>Course: {course}</p>
    </article>
  );
}

export default StudentCard;
```

Use it in `App.jsx`:

```jsx
import StudentCard from "./components/StudentCard";

function App() {
  return (
    <main>
      <StudentCard
        name="Uzoamaka"
        age={16}
        course="Software Engineering"
      />
    </main>
  );
}

export default App;
```

### Discussion

What happens when different information is passed to the same component?

---

## 5. Guided Practical — 25 Minutes

### Practical Exercise: Student Profile Page

Create a React interface containing:

- Header component
- Student profile component
- Subjects component
- Footer component

### Suggested Structure

```text
src/
│
├── components/
│   ├── Header.jsx
│   ├── StudentCard.jsx
│   ├── Subjects.jsx
│   └── Footer.jsx
│
├── App.jsx
├── App.css
└── main.jsx
```

Apply CSS styling using an external stylesheet.

---

## 6. Session Review — 10 Minutes

### Knowledge Check

1. What is JSX?
2. Why do React components start with capital letters?
3. What is a functional component?
4. What are props?
5. How do components communicate through props?
6. Why are reusable components important?
7. What is the purpose of `export default`?
8. What is the purpose of `import`?

---

# 📝 Session 2 Assignment

## Reusable Student Profile Components

Improve the Student Profile application.

Requirements:

1. Create at least four components.
2. Use props to display student information.
3. Add a list of favourite subjects.
4. Apply CSS styling.
5. Ensure the interface is readable on mobile screens.

### Deliverable

A React application displaying a styled student profile using reusable components.

---

# 🗓️ Session 3 — React State, Events & Interactive Applications

**Duration:** 2 Hours

## Session Objectives

The student will:

- Understand state.
- Learn the purpose of `useState`.
- Handle button clicks.
- Update information dynamically.
- Build an interactive React application.
- Review and test the weekly project.

---

## 1. Review of Session 2 — 15 Minutes

Review:

- JSX
- Components
- Props
- Imports and exports
- CSS styling
- Student Profile application

---

## 2. Introduction to State — 25 Minutes

State allows a React component to remember information between renders.

React provides the `useState` Hook for managing local component state.

### Example

```jsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h2>Counter: {count}</h2>

      <button onClick={() => setCount(count + 1)}>
        Increase
      </button>
    </div>
  );
}

export default Counter;
```

### Explain

- `useState(0)` creates state with an initial value of zero.
- `count` contains the current state.
- `setCount` updates the state.
- Updating state causes React to render the updated interface.

---

## 3. Event Handling — 20 Minutes

React can respond to user interactions.

### Example

```jsx
function WelcomeButton() {
  function showMessage() {
    alert("Welcome to React!");
  }

  return (
    <button onClick={showMessage}>
      Click Me
    </button>
  );
}

export default WelcomeButton;
```

Explain:

- `onClick`
- Event handlers
- Function references
- User interactions

---

## 4. Conditional Rendering — 20 Minutes

React can display different content depending on a condition.

### Example

```jsx
import { useState } from "react";

function StudentStatus() {
  const [isEnrolled, setIsEnrolled] = useState(false);

  return (
    <div>
      <p>
        Status: {isEnrolled ? "Enrolled" : "Not Enrolled"}
      </p>

      <button onClick={() => setIsEnrolled(!isEnrolled)}>
        Change Status
      </button>
    </div>
  );
}

export default StudentStatus;
```

### Discussion

How does the interface change when state changes?

---

# 🏆 Week 4 Part 2 — Final Project

## Interactive Student Profile Application

**Project Type:** React.js Frontend Application

### Project Description

Build an interactive student profile application using React.

The application should display student information, educational interests and learning goals while allowing basic user interaction.

### Functional Requirements

The application must include:

1. A header component.
2. A student profile component.
3. A subjects or interests section.
4. A learning goals section.
5. A footer component.
6. At least one component using props.
7. At least one interactive button.
8. State management using `useState`.
9. Conditional rendering.
10. Responsive CSS styling.

### Suggested Interactive Features

Choose at least two:

- Show or hide student details.
- Increase a learning progress counter.
- Toggle enrolment status.
- Display a welcome message.
- Expand or collapse learning goals.

---

## Suggested Project Structure

```text
Week-04-Part-02/
│
├── javascript-exercises/
│   └── student-info.js
│
└── student-react-app/
    │
    ├── public/
    │
    ├── src/
    │   ├── components/
    │   │   ├── Header.jsx
    │   │   ├── StudentCard.jsx
    │   │   ├── Subjects.jsx
    │   │   ├── LearningGoals.jsx
    │   │   └── Footer.jsx
    │   │
    │   ├── App.jsx
    │   ├── App.css
    │   └── main.jsx
    │
    ├── index.html
    ├── package.json
    └── vite.config.js
```

---

## Guided Project Development — 30 Minutes

The instructor will support the student in:

1. Reviewing the application structure.
2. Identifying reusable components.
3. Adding student information.
4. Implementing props.
5. Adding state and event handlers.
6. Applying CSS.
7. Testing the application.

The student should write and explain the code independently.

---

## Independent Project Work — 20 Minutes

The student will complete the remaining project requirements.

Encourage:

- Reading error messages
- Using browser developer tools
- Testing buttons
- Reviewing component imports
- Checking JSX syntax
- Researching unfamiliar concepts

---

## Final Project Review — 10 Minutes

Assess:

- React application runs successfully.
- Components are organised correctly.
- Props are used appropriately.
- State updates work.
- Buttons respond to clicks.
- Styling is readable.
- Student can explain the implementation.

---

# 📂 Final Deliverables

By the end of the module, the student should submit:

- JavaScript fundamentals exercise
- React development environment
- Reusable React components
- Styled Student Profile interface
- Interactive Student Profile application
- Project README
- GitHub repository or committed project folder

---

# 🧠 Module Knowledge Check

1. What is JavaScript?
2. What is React?
3. Is React a programming language or a library?
4. What is JSX?
5. What is a React component?
6. What is the difference between HTML and JSX?
7. What are props?
8. What is state?
9. What does `useState` do?
10. What is an event handler?
11. What does `onClick` do?
12. What is conditional rendering?
13. Why should components be reusable?
14. What is the purpose of `package.json`?
15. What does Vite do?
16. How do you start a React development server?
17. What is the difference between props and state?
18. Why is JavaScript important for React?
19. What happens when React state changes?
20. Why is testing user interactions important?

---

# 📊 Module Assessment

| Assessment Area | Weight |
|---|---:|
| JavaScript fundamentals | 20% |
| Understanding React concepts | 20% |
| Components and JSX | 20% |
| Props and state | 15% |
| Event handling and interactivity | 10% |
| Code organisation and styling | 5% |
| Independent problem-solving | 10% |
| **Total** | **100%** |

---

# 🎓 Expected Learning Outcomes

By the end of this introductory React module, the student should be able to:

- Explain how JavaScript supports frontend development.
- Recognise fundamental JavaScript syntax.
- Explain the purpose of React.
- Create and run a React application.
- Write simple functional components.
- Use JSX.
- Pass information through props.
- Introduce state with `useState`.
- Respond to user interactions.
- Build a basic interactive student profile interface.

The student is expected to continue practising JavaScript and React beyond this introductory module.

---

# 🔗 Recommended Learning Resources

### Official Documentation

- [JavaScript Guide — MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)
- [JavaScript First Steps — MDN](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Scripting)
- [React Documentation](https://react.dev/learn)
- [React Quick Start](https://react.dev/learn)
- [Vite Documentation](https://vite.dev/guide/)

---

<div align="center">

### 🚀 Learn. Build. Experiment. Improve.

**Opsfuxion Technologies Limited**

*Orchestrate Intelligence, Deliver with Precision.*

**© 2026 Opsfuxion Technologies Limited. All Rights Reserved.**

</div>
