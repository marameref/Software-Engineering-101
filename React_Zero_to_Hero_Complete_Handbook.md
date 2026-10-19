# React Zero to Hero — The Complete Practical Handbook

> **From your first component to accessible, tested and deployable React applications**  
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
- [1. What React Is and When to Use It](#1.-what-react-is-and-when-to-use-it)
- [2. Tooling, Vite and Project Setup](#2.-tooling,-vite-and-project-setup)
- [3. JSX and Rendering Rules](#3.-jsx-and-rendering-rules)
- [4. Components, Props and Composition](#4.-components,-props-and-composition)
- [5. Lists, Keys and Conditional UI](#5.-lists,-keys-and-conditional-ui)
- [6. Events and useState](#6.-events-and-usestate)
- [7. State Structure and Immutable Updates](#7.-state-structure-and-immutable-updates)
- [8. Controlled Forms and Validation](#8.-controlled-forms-and-validation)
- [9. Lifting State and Data Flow](#9.-lifting-state-and-data-flow)
- [10. Effects and External Systems](#10.-effects-and-external-systems)
- [11. Fetching Data and Handling Races](#11.-fetching-data-and-handling-races)
- [12. Refs and DOM Integration](#12.-refs-and-dom-integration)
- [13. Context and useReducer](#13.-context-and-usereducer)
- [14. Custom Hooks and Reuse](#14.-custom-hooks-and-reuse)
- [15. Routing and Navigation](#15.-routing-and-navigation)
- [16. Styling React Interfaces](#16.-styling-react-interfaces)
- [17. Testing Components and User Behaviour](#17.-testing-components-and-user-behaviour)
- [18. Accessibility in React](#18.-accessibility-in-react)
- [19. Performance and React Rendering](#19.-performance-and-react-rendering)
- [20. Error Boundaries, Suspense and Resilience](#20.-error-boundaries,-suspense-and-resilience)
- [21. Architecture, Security and Deployment](#21.-architecture,-security-and-deployment)
- [22. Advanced React and Engineering Trade-offs](#22.-advanced-react-and-engineering-trade-offs)
- [Guided labs](#guided-labs)
- [Portfolio projects](#portfolio-projects)
- [Final capstone](#final-capstone)
- [Knowledge checks and answers](#knowledge-checks-and-answers)
- [Glossary](#glossary)
- [Learning roadmap and mastery checklist](#learning-roadmap-and-mastery-checklist)

---

# Part I — React Foundations

## 1. What React Is and When to Use It

### Core idea
React is a library for building interfaces from reusable components. It describes the UI as a function of state and props. React does not prescribe routing, data fetching or backend infrastructure; choose those separately.

### Runnable example
```jsx
function Welcome() {
  return <h1>Welcome to the academy</h1>;
}
export default Welcome;
```

### Walkthrough
A component is a JavaScript function returning React elements. Capitalised component names distinguish them from intrinsic HTML tags.

### Practice challenge
List three UI regions that would make good components in a course website.

<details><summary>Suggested solution / checkpoint</summary>

Examples: `Header`, `CourseCard`, `EnquiryForm`; choose components based on cohesive responsibilities.

</details>

### Production insight
Use React when UI state and reusable interactions justify its abstraction.

**Common mistake:** Assuming React automatically provides a backend or a database.

---

## 2. Tooling, Vite and Project Setup

### Core idea
A modern React workflow uses a development server, JSX transform, package manager and bundler. Vite is a straightforward choice for client-side learning. Node.js and npm must be installed first.

### Runnable example
```javascript
# terminal commands (not JavaScript)
npm create vite@latest academy-ui -- --template react
cd academy-ui
npm install
npm run dev
```

### Walkthrough
Run these commands in a terminal. Inspect `src/main.jsx`, `src/App.jsx`, `index.html` and `package.json`. Use `npm run build` to verify production compilation.

### Practice challenge
Create a new Vite React project, change the heading and verify a production build.

<details><summary>Suggested solution / checkpoint</summary>

Run `npm run build` and fix any errors; commit the starter project.

</details>

### Production insight
Commit the lockfile; never commit `node_modules` or secrets.

**Common mistake:** Running terminal commands in the browser console.

---

## 3. JSX and Rendering Rules

### Core idea
JSX resembles HTML but is JavaScript syntax. Return one root element (or fragment), use `className`, pass expressions in `{}`, and close tags. JSX expressions cannot directly contain statements such as `if`.

### Runnable example
```jsx
const course = {title:'React Fundamentals', seats:12};
export default function App() {
  return <main className="container">
    <h1>{course.title}</h1>
    <p>{course.seats} seats remaining</p>
  </main>;
}
```

### Walkthrough
JSX compiles into React element creation. Text is escaped by default, which is safer than interpolating raw HTML.

### Practice challenge
Render a course title, duration and price from an object.

<details><summary>Suggested solution / checkpoint</summary>

Use an object literal and reference its properties with `{course.title}`, etc.

</details>

### Production insight
Avoid `dangerouslySetInnerHTML` unless HTML is trusted and sanitised.

**Common mistake:** Writing `class=` or attempting to return sibling elements without a wrapper.

---

## 4. Components, Props and Composition

### Core idea
Props pass information from parent to child. Components should be pure during render. Composition (children and small components) is usually preferable to inheritance.

### Runnable example
```jsx
function CourseCard({title, children}) {
  return <article><h2>{title}</h2><div>{children}</div></article>;
}
export default function App() {
  return <CourseCard title="JavaScript"><p>Beginner friendly</p></CourseCard>;
}
```

### Walkthrough
The parent supplies props and nested children. The child displays them but should not mutate them.

### Practice challenge
Create reusable `CourseCard` components for three courses.

<details><summary>Suggested solution / checkpoint</summary>

Store course objects in an array and pass `title`, `duration` and `fee` as props.

</details>

### Production insight
Use descriptive props and keep presentation separate from data loading when helpful.

**Common mistake:** Mutating props or calling components as ordinary functions.

---

## 5. Lists, Keys and Conditional UI

### Core idea
Render arrays with `.map()`. Stable keys let React match items across updates. Conditional rendering uses ternaries, `&&` or early returns; beware rendering numeric zero with `&&`.

### Runnable example
```javascript
const courses = [{id:'js',title:'JavaScript'},{id:'react',title:'React'}];
export default function List() {
  return <ul>{courses.map(c => <li key={c.id}>{c.title}</li>)}</ul>;
}
```

### Walkthrough
Keys belong on the outermost element returned by each map iteration. IDs are more reliable than array indexes for reorderable lists.

### Practice challenge
Show “No courses” for an empty array, otherwise render course cards.

<details><summary>Suggested solution / checkpoint</summary>

Use `courses.length === 0 ? <p>No courses</p> : courses.map(...)`.

</details>

### Production insight
Stable keys prevent confusing component state when items move.

**Common mistake:** Using `Math.random()` as a key or array indexes for editable lists.

---

## 6. Events and useState

### Core idea
`useState` gives a component memory across renders. Event handlers are passed as functions, not invoked during render. State updates schedule renders; do not expect the old closure value to change immediately.

### Runnable example
```javascript
import {useState} from 'react';
export default function Counter() {
  const [count,setCount] = useState(0);
  return <button onClick={() => setCount(c => c + 1)}>Count: {count}</button>;
}
```

### Walkthrough
The functional updater receives the latest queued state. It is preferable when the next value depends on the previous value.

### Practice challenge
Create plus, minus and reset buttons, and prevent negative counts.

<details><summary>Suggested solution / checkpoint</summary>

`setCount(c => Math.max(0,c-1))`; reset with `setCount(0)`.

</details>

### Production insight
Keep state minimal; derive values that can be calculated from existing state.

**Common mistake:** Calling `setCount(count+1)` repeatedly and expecting synchronous increments.

---

## 7. State Structure and Immutable Updates

### Core idea
React relies on state identity changes to recognise updates. Never mutate state arrays or objects directly. Model related values together when they update as one unit; avoid redundant or contradictory state.

### Runnable example
```javascript
import {useState} from 'react';
function Enrolments() {
  const [names,setNames] = useState(['Ada']);
  const add = () => setNames(prev => [...prev,'Tomi']);
  return <><button onClick={add}>Add</button><p>{names.join(', ')}</p></>;
}
```

### Walkthrough
`[...prev]` creates a new array. For nested objects, copy each modified layer.

### Practice challenge
Build add/remove course favourites using immutable updates.

<details><summary>Suggested solution / checkpoint</summary>

Add with `[...prev,id]` after checking duplicates; remove with `prev.filter(x => x !== id)`.

</details>

### Production insight
Normalise complex nested state or use a reducer for complicated transitions.

**Common mistake:** Using `.push()` directly on a state array.

---

## 8. Controlled Forms and Validation

### Core idea
A controlled input receives its displayed value from state and updates state through `onChange`. HTML constraints remain useful. Validate on submit and give users clear, accessible feedback.

### Runnable example
```javascript
import {useState} from 'react';
export default function Signup() {
  const [email,setEmail] = useState('');
  const [message,setMessage] = useState('');
  function submit(e){e.preventDefault();setMessage(email.includes('@')?'Received':'Check email');}
  return <form onSubmit={submit}><label>Email <input type="email" required value={email} onChange={e=>setEmail(e.target.value)}/></label><button>Submit</button><p role="status">{message}</p></form>;
}
```

### Walkthrough
The form submit handler prevents navigation and reports a result. Server-side validation is still mandatory for real registration.

### Practice challenge
Build a name/email/course form with field-specific error messages.

<details><summary>Suggested solution / checkpoint</summary>

Use one state object or independent states, validate trimmed fields, and associate errors with inputs via `aria-describedby`.

</details>

### Production insight
For large forms consider a suitable form library after understanding controlled inputs.

**Common mistake:** Using `value` without `onChange`, making the input read-only.

---

## 9. Lifting State and Data Flow

### Core idea
When siblings need shared information, move state to their closest common ancestor and pass data and callbacks down. This keeps a single source of truth.

### Runnable example
```javascript
import {useState} from 'react';
function SearchBox({query,onQueryChange}) {return <input aria-label="Search courses" value={query} onChange={e=>onQueryChange(e.target.value)}/>;}
export default function App(){const [query,setQuery]=useState('');return <><SearchBox query={query} onQueryChange={setQuery}/><p>Searching for: {query}</p></>;}
```

### Walkthrough
`App` owns the value; `SearchBox` is controlled by props. The parent can use the same value to filter results.

### Practice challenge
Connect a search input and course list as sibling components.

<details><summary>Suggested solution / checkpoint</summary>

Lift `query` to the parent and derive filtered courses with `.filter()`.

</details>

### Production insight
Avoid duplicating the same state in multiple children.

**Common mistake:** Copying props into state without a reason.

---


# Part II — Hooks, Data and Application Development

## 10. Effects and External Systems

### Core idea
`useEffect` synchronises a component with systems outside React: subscriptions, browser APIs, network connections or timers. You usually do not need an effect for derived values or event-specific logic. Effects can return cleanup functions.

### Runnable example
```javascript
import {useEffect,useState} from 'react';
export default function Clock(){
  const [time,setTime]=useState(new Date().toLocaleTimeString());
  useEffect(()=>{const id=setInterval(()=>setTime(new Date().toLocaleTimeString()),1000);return ()=>clearInterval(id);},[]);
  return <time>{time}</time>;
}
```

### Walkthrough
The interval starts after render and is cleared when the effect is cleaned up. Development Strict Mode may run setup/cleanup more than once to expose bugs.

### Practice challenge
Subscribe to `resize` and display window width, with cleanup.

<details><summary>Suggested solution / checkpoint</summary>

Use `addEventListener` in an effect, remove it in cleanup, and update state in the handler.

</details>

### Production insight
Read the official “You Might Not Need an Effect” guidance before adding effects.

**Common mistake:** Using effects to calculate values that could be computed during render.

---

## 11. Fetching Data and Handling Races

### Core idea
Remote data needs loading, success, empty and error states. For simple learning projects, fetch in an effect with cleanup; larger apps benefit from router loaders or data-fetching libraries. Abort stale requests when dependencies change.

### Runnable example
```javascript
import {useEffect,useState} from 'react';
export default function Posts(){
  const [state,setState]=useState({status:'loading',items:[],error:''});
  useEffect(()=>{const controller=new AbortController();
    (async()=>{try{const r=await fetch('https://jsonplaceholder.typicode.com/posts?_limit=3',{signal:controller.signal});if(!r.ok)throw Error(`HTTP ${r.status}`);const items=await r.json();setState({status:'success',items,error:''});}catch(e){if(e.name!=='AbortError')setState({status:'error',items:[],error:e.message});}})();
    return ()=>controller.abort();
  },[]);
  if(state.status==='loading')return <p>Loading…</p>;
  if(state.status==='error')return <p role="alert">{state.error}</p>;
  return <ul>{state.items.map(x=><li key={x.id}>{x.title}</li>)}</ul>;
}
```

### Walkthrough
This demonstration endpoint requires network access. Aborting prevents an obsolete request from continuing after cleanup.

### Practice challenge
Fetch a local `courses.json` and display an empty-state message if it has no items.

<details><summary>Suggested solution / checkpoint</summary>

Check `response.ok`, parse JSON, and branch on `items.length`.

</details>

### Production insight
Never embed private API keys in client-side React code.

**Common mistake:** Assuming every request succeeds or ignoring effect cleanup.

---

## 12. Refs and DOM Integration

### Core idea
`useRef` holds a mutable value across renders without triggering rerenders. Use refs for focusing inputs, measuring elements or holding imperative handles. Prefer declarative state for content that affects the UI.

### Runnable example
```javascript
import {useRef} from 'react';
export default function FocusSearch(){
  const inputRef=useRef(null);
  return <><input ref={inputRef} aria-label="Course search"/><button onClick={()=>inputRef.current?.focus()}>Focus search</button></>;
}
```

### Walkthrough
React assigns the DOM node to `current` after mounting. Calling `.focus()` is an appropriate imperative DOM operation.

### Practice challenge
Focus the first invalid form field after submit.

<details><summary>Suggested solution / checkpoint</summary>

Attach refs to inputs and call `.focus()` on the invalid one inside the submit handler.

</details>

### Production insight
Do not read or write `ref.current` during render except for predictable initialization.

**Common mistake:** Using refs to bypass React state updates.

---

## 13. Context and useReducer

### Core idea
Context makes values available to a component subtree without passing props at every level. `useReducer` centralises state transitions, especially when multiple actions affect related state. Neither is automatically a replacement for server-state tools.

### Runnable example
```javascript
import {createContext,useContext,useReducer} from 'react';
const ThemeContext=createContext(null);
function reducer(state,action){return action.type==='toggle'?{dark:!state.dark}:state;}
export function ThemeProvider({children}){const [state,dispatch]=useReducer(reducer,{dark:false});return <ThemeContext.Provider value={{state,dispatch}}>{children}</ThemeContext.Provider>;}
export function ThemeButton(){const theme=useContext(ThemeContext);return <button onClick={()=>theme.dispatch({type:'toggle'})}>{theme.state.dark?'Dark':'Light'}</button>;}
```

### Walkthrough
Wrap the application in `ThemeProvider`, then render `ThemeButton` inside it. Context consumers rerender when their provider value changes.

### Practice challenge
Build a cart reducer with `add`, `remove` and `clear` actions.

<details><summary>Suggested solution / checkpoint</summary>

Return a new state for every action and leave the old state untouched.

</details>

### Production insight
Split contexts by responsibility when updates are frequent.

**Common mistake:** Using one global context for every piece of state.

---

## 14. Custom Hooks and Reuse

### Core idea
Custom hooks encapsulate reusable stateful logic. Their names begin with `use`, and they must follow the Rules of Hooks: call hooks at the top level of components or other hooks, never inside conditions or loops.

### Runnable example
```jsx
import {useState} from 'react';
function useToggle(initial=false){const [value,setValue]=useState(initial);return [value,()=>setValue(v=>!v)];}
export default function FAQ(){const [open,toggle]=useToggle();return <><button aria-expanded={open} onClick={toggle}>Details</button>{open&&<p>Evening classes available.</p>}</>;}
```

### Walkthrough
`useToggle` can be reused by several components. Each call receives independent state.

### Practice challenge
Extract a reusable `useLocalStorage` hook for a non-sensitive theme preference.

<details><summary>Suggested solution / checkpoint</summary>

Initialize state from storage safely and persist changes in an effect; handle unavailable storage.

</details>

### Production insight
A custom hook shares logic, not one shared state instance.

**Common mistake:** Calling a hook conditionally.

---

## 15. Routing and Navigation

### Core idea
A multi-page experience can use client-side routing. React itself does not ship a router. Choose a supported router and consult its current docs because APIs change between major versions. Navigation should remain accessible and deep links should work on the host.

### Runnable example
```javascript
// Conceptual example: with an installed, compatible router
// Define routes for /, /courses and /contact.
// Render links as navigation elements, not buttons that manually change location.
const routes = ['/', '/courses', '/contact'];
console.log(routes);
```

### Walkthrough
First create three page components. Then follow your selected router’s official installation and route-configuration instructions. Configure the hosting provider to serve the SPA entry point for client routes when appropriate.

### Practice challenge
Implement Home, Courses and Contact routes with a not-found page.

<details><summary>Suggested solution / checkpoint</summary>

Use the router’s route configuration and link component; verify direct refresh of `/courses`.

</details>

### Production insight
Consider server rendering or framework routing for SEO-sensitive public sites.

**Common mistake:** Deploying an SPA without configuring fallback routing.

---

## 16. Styling React Interfaces

### Core idea
React supports regular CSS, CSS Modules and utility-based approaches. Choose based on team needs; accessible, responsive CSS principles still apply. Use meaningful HTML rather than styling generic divs for everything.

### Runnable example
```jsx
// CourseCard.jsx
import './CourseCard.css';
export function CourseCard({title}){return <article className="course-card"><h2>{title}</h2></article>;}
// CourseCard.css (separate file)
// .course-card { padding: 1rem; border: 1px solid #ccc; border-radius: .75rem; }
```

### Walkthrough
Keep the CSS rule in its own file. In a real project use consistent tokens and visible focus styles.

### Practice challenge
Style a responsive grid of cards with CSS Grid and a mobile-first breakpoint.

<details><summary>Suggested solution / checkpoint</summary>

Use `grid-template-columns: repeat(auto-fit,minmax(min(100%,16rem),1fr))`.

</details>

### Production insight
Use CSS Modules when component-level naming isolation is useful.

**Common mistake:** Relying only on colour to communicate validation errors.

---


# Part III — Production React and Architecture

## 17. Testing Components and User Behaviour

### Core idea
Test user-visible behaviour rather than internal state. A common setup uses Vitest, Testing Library and a DOM environment; verify compatible package versions and current setup instructions.

### Runnable example
```jsx
// Counter.test.jsx (after configuring Vitest and Testing Library)
import {render,screen,fireEvent} from '@testing-library/react';
import {test,expect} from 'vitest';
import Counter from './Counter';
test('increments on click',()=>{
  render(<Counter/>);
  fireEvent.click(screen.getByRole('button',{name:/count/i}));
  expect(screen.getByRole('button',{name:/count: 1/i})).toBeTruthy();
});
```

### Walkthrough
The test expects a `Counter` component like the one in chapter 6. Tests should assert the rendered output after an interaction.

### Practice challenge
Test a registration form: required fields, valid submission and error feedback.

<details><summary>Suggested solution / checkpoint</summary>

Query by role/label; simulate user input; assert the status message.

</details>

### Production insight
Prefer `user-event` for realistic interaction tests once the test environment is configured.

**Common mistake:** Testing implementation details instead of accessible behaviour.

---

## 18. Accessibility in React

### Core idea
Accessible React begins with semantic HTML, proper labels, keyboard support, focus management and feedback. Component abstractions must preserve browser behaviour. Use `aria-*` only when native semantics are insufficient.

### Runnable example
```jsx
export default function Status({message}){
  return <p role="status" aria-live="polite">{message}</p>;
}
// Pair each form input with a visible <label>.
```

### Walkthrough
A live region announces asynchronous updates to assistive technology without forcibly moving focus.

### Practice challenge
Audit a modal design for focus trapping, Escape closing and focus return.

<details><summary>Suggested solution / checkpoint</summary>

Prefer a tested accessible dialog component or native `<dialog>` where suitable; test keyboard flows.

</details>

### Production insight
Test with keyboard only and a screen reader when possible.

**Common mistake:** Using clickable `div` elements instead of buttons.

---

## 19. Performance and React Rendering

### Core idea
React rerenders when props, state or context change. Profile before optimising. `memo`, `useMemo` and `useCallback` can reduce unnecessary work but add complexity and do not fix poor state architecture.

### Runnable example
```jsx
import {useMemo,useState} from 'react';
export default function Filter({courses}){
  const [query,setQuery]=useState('');
  const visible=useMemo(()=>courses.filter(c=>c.title.toLowerCase().includes(query.toLowerCase())),[courses,query]);
  return <><input aria-label="Search" value={query} onChange={e=>setQuery(e.target.value)}/><p>{visible.length} results</p></>;
}
```

### Walkthrough
Memoisation caches the computed array until dependencies change; it is not needed for every small filter.

### Practice challenge
Profile a 2,000-row list and compare pagination/virtualisation approaches.

<details><summary>Suggested solution / checkpoint</summary>

Record baseline performance, render fewer rows, then measure again.

</details>

### Production insight
Code splitting with `lazy` and `Suspense` can reduce initial bundle work.

**Common mistake:** Wrapping every value in `useMemo` without evidence.

---

## 20. Error Boundaries, Suspense and Resilience

### Core idea
Error boundaries can display fallback UI when descendant rendering fails; they do not catch every event-handler or async error. Suspense coordinates supported loading scenarios. Design recovery paths rather than only showing generic errors.

### Runnable example
```javascript
// Error boundary concept (class-based boundary)
import React from 'react';
class ErrorBoundary extends React.Component {
  state={failed:false};
  static getDerivedStateFromError(){return {failed:true};}
  componentDidCatch(error,info){console.error(error,info);}
  render(){return this.state.failed?<p role="alert">Something went wrong. Please reload.</p>:this.props.children;}
}
export default ErrorBoundary;
```

### Walkthrough
Wrap a route or risky subtree in `ErrorBoundary`. Test by intentionally throwing from a child during render.

### Practice challenge
Add a retry or navigation option to an error fallback.

<details><summary>Suggested solution / checkpoint</summary>

Provide a safe fallback and reset strategy; log errors without leaking sensitive data.

</details>

### Production insight
Use monitoring in production to learn which failures users encounter.

**Common mistake:** Expecting an error boundary to catch failed fetches handled asynchronously.

---

## 21. Architecture, Security and Deployment

### Core idea
Separate UI components, domain logic, API clients, routes and tests. Environment variables prefixed for client exposure are bundled publicly, so never put secrets in them. Deploy only after lint, test and build pass.

### Runnable example
```javascript
// Suggested structure
// src/components/
// src/features/courses/
// src/features/admissions/
// src/lib/api.js
// src/routes/
// src/styles/
// tests/
// package.json
```

### Walkthrough
Create a production build with `npm run build`. Inspect output and configure hosting fallback routes as needed. Keep authentication enforcement on the server.

### Practice challenge
Write a deployment checklist covering environment variables, routing, accessibility, errors and security.

<details><summary>Suggested solution / checkpoint</summary>

Verify `npm run build`, test a deep link, inspect console/network, and confirm no secrets appear in bundles.

</details>

### Production insight
For public SEO-critical pages, evaluate SSR or static generation rather than assuming client-only rendering is ideal.

**Common mistake:** Mistaking client-side route protection for server-side authorisation.

---

## 22. Advanced React and Engineering Trade-offs

### Core idea
Advanced React engineering involves choosing appropriate state ownership, server rendering, streaming, transitions, caching, component APIs and testing strategy. The right choice depends on application constraints, not trendiness.

### Runnable example
```jsx
import {useDeferredValue,useState} from 'react';
export default function SearchPreview(){
  const [query,setQuery]=useState('');
  const deferredQuery=useDeferredValue(query);
  return <><input value={query} onChange={e=>setQuery(e.target.value)} aria-label="Search"/><p>Filtering for {deferredQuery}</p></>;
}
```

### Walkthrough
A deferred value may lag behind urgent input updates; it does not itself debounce network requests. Measure responsiveness with realistic data.

### Practice challenge
Write an architecture decision record comparing SPA and SSR for a training academy website.

<details><summary>Suggested solution / checkpoint</summary>

Discuss SEO, hosting, complexity, authentication, caching, performance and team skills; justify a choice.

</details>

### Production insight
Keep up with official React release notes; APIs and recommended frameworks evolve.

**Common mistake:** Adopting advanced APIs without a user-facing performance or architecture need.

---


# Guided labs

| Lab | Deliverable | Acceptance test |
|---|---|---|
| 1 | First Vite React app | Builds without errors |
| 2 | Reusable course card | Props render correctly |
| 3 | Dynamic course list | Stable keys and empty state |
| 4 | Counter and quantity selector | Functional updates work |
| 5 | Favourites list | Immutable add/remove |
| 6 | Controlled enquiry form | Keyboard and validation work |
| 7 | Lifted-state course search | Sibling components stay in sync |
| 8 | Live clock | Interval cleanup works |
| 9 | Remote course list | Loading, error and empty states |
| 10 | Focus-on-error form | Focus moves appropriately |
| 11 | Theme context and reducer | Updates propagate correctly |
| 12 | Custom `useToggle` hook | Independent component instances |
| 13 | Three-route app | Deep-link refresh works |
| 14 | Component test suite | Tests user-visible interactions |
| 15 | Accessibility audit | No major keyboard blockers |

For each lab: sketch the component tree, identify the owner of state, implement, test, refactor and document what you learned.

# Portfolio projects

### Project A — Interactive portfolio (foundation)
Build reusable hero, skills, project and contact components. Add a theme toggle and accessible mobile navigation. **Deliverables:** repository, responsive deployment and README.

### Project B — Course discovery application (intermediate)
Create a course catalogue with search, categories, favourites, details and enquiry forms. Use routing, reusable components, immutable state and loading/error states. **Stretch:** persisted preferences.

### Project C — Student administration interface (advanced)
Build student records, course enrolments, filtering, pagination, reducer-driven state, component tests and accessible status messages. **Stretch:** mock API with error simulation and cancellation.

# Final capstone

## Training Academy Portal — Final assessment
Create a **React training academy application** with Home, Courses, Course Details, Admissions and Contact views. Use a reusable design system, semantic HTML, client-side routing, a course data source, controlled registration forms, meaningful validation, loading/error/empty states, a theme preference and automated component tests.

**Suggested structure:** `src/app/`, `src/components/`, `src/features/courses/`, `src/features/admissions/`, `src/hooks/`, `src/lib/`, `src/styles/`, `tests/`.

**Implementation milestones:**
1. Write user stories and accessibility acceptance criteria.
2. Sketch component hierarchy and decide state ownership.
3. Implement static layouts and responsive CSS.
4. Add routing, lists, forms and client-side state.
5. Connect mock/local API data and handle failures.
6. Write component and utility tests; run keyboard checks.
7. Build, deploy, test deep links and document.

**100-point rubric:** correct features 25; React state/data flow 20; accessibility 15; tests and resilience 15; design/responsiveness 10; architecture/performance 10; documentation 5. **Pass target:** 75+ with no critical accessibility or security flaw.

**Oral defence:** explain keys, state ownership, effect cleanup, immutable updates, your router choice, one test, and when you would choose SSR instead of a client-only app.

# Knowledge checks and answers

1. **What is a React component?** A reusable function or class defining part of the UI.
2. **Props versus state?** Props come from parents; state belongs to a component and changes over time.
3. **Why are keys important?** They help React track list item identity between renders.
4. **Why avoid mutating state?** React relies on new identities for predictable updates.
5. **When should you use an effect?** To synchronise with external systems, not to calculate derived render values.
6. **What does effect cleanup do?** Releases subscriptions, timers or obsolete requests.
7. **What is lifting state up?** Moving shared state to the closest common ancestor.
8. **What is context?** A way to provide values to descendants without passing props through every level.
9. **When use a reducer?** When multiple related state transitions benefit from explicit actions.
10. **What is a custom hook?** A function that packages reusable hook-based logic.
11. **What is a controlled input?** Its value comes from React state.
12. **What is an error boundary?** A fallback mechanism for certain descendant render errors.
13. **Does React include routing?** No; use a router or framework.
14. **Can client environment variables hold secrets?** No; they are exposed to browsers.
15. **How do you test UI?** Interact through accessible roles/labels and assert visible outcomes.
16. **What is memoisation?** Reusing a previous result when dependencies have not changed.
17. **What is hydration?** Attaching React interactivity to server-rendered markup.
18. **What is SSR?** Rendering HTML on the server before sending it to the browser.
19. **Why consider SEO architecture?** Client-only rendering can complicate indexing and initial content delivery.
20. **What distinguishes production readiness?** Accessibility, correctness, tests, security, performance, monitoring and documentation.

# Glossary

- **Component:** reusable unit of React UI.
- **Context:** descendant-accessible value provided by an ancestor.
- **Controlled input:** form control whose value is managed by state.
- **Effect:** synchronisation with an external system after rendering.
- **Hook:** React API used at the top level of components/custom hooks.
- **Hydration:** connecting React to server-rendered HTML.
- **JSX:** syntax extension describing React elements.
- **Key:** stable identity hint for array-rendered elements.
- **Props:** parent-supplied component inputs.
- **Reducer:** function calculating next state from current state and action.
- **Ref:** persistent mutable reference that does not trigger rerender.
- **Render:** React calculating the next UI description.
- **SPA:** single-page application with client-side navigation.
- **SSR:** server-side rendering.
- **State:** data retained by a component between renders.
- **Suspense:** coordination of supported asynchronous rendering boundaries.

# Learning roadmap and mastery checklist

| Week | Focus | Proof of learning |
|---|---|---|
| 1 | Vite, JSX, components, props | Course card gallery |
| 2 | Lists, keys, events, state | Interactive catalogue |
| 3 | Immutable state, forms, lifting state | Enquiry form |
| 4 | Effects, fetch, refs | Data-driven course browser |
| 5 | Context, reducers, custom hooks | Theme + favourites |
| 6 | Routing, styling | Multi-view app |
| 7 | Testing and accessibility | Automated tests + audit |
| 8 | Performance, resilience, architecture | Profiling and refactor |
| 9–10 | Capstone | Deployed academy portal |

**Mastery checklist:** I can set up a project; explain JSX; design components and props; render keyed lists; manage immutable state; build accessible forms; lift state; distinguish effects from render logic; cancel stale requests; use refs and context appropriately; write custom hooks; configure routes; test interactions; debug rerenders; deploy safely; and explain SPA/SSR trade-offs.

**Further reading:** [React Learn](https://react.dev/learn), [React Reference](https://react.dev/reference/react), [Vite Guide](https://vite.dev/guide/), [MDN Web Docs](https://developer.mozilla.org/), [Testing Library](https://testing-library.com/docs/react-testing-library/intro/), [WAI accessibility tutorials](https://www.w3.org/WAI/tutorials/).
