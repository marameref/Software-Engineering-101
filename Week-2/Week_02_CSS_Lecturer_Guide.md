# WEEK 2 — CSS FUNDAMENTALS, LAYOUT & RESPONSIVE DESIGN

**Opsfuxion Technologies Limited**  
*Orchestrate Intelligence, Deliver with Precision.*

**Practical Software Engineering Foundation Programme | Lecturer's Teaching Manual**  
**Level:** Beginner | **Contact time:** 3 sessions × 2 hours = 6 hours | **Prerequisite:** Week 1 HTML | **Deliverable:** Responsive personal portfolio

> **Instructor-use convention:** Sections marked **STUDENT TASK** should be attempted without revealing the subsequent **INSTRUCTOR SOLUTION**. Solutions are reference implementations, not the only acceptable answers. Allow independent practice between classes; the six hours are not intended to contain every assignment.

## Teaching goals and preparation

By the end of this week, the learner should be able to explain CSS, attach an external stylesheet, write selectors and declarations, distinguish margin/padding/border, use `box-sizing`, apply Flexbox, and use a media query to adapt a portfolio for narrow screens.

**Before class:** Ensure the Week 1 semantic HTML profile page exists, VS Code and a browser work, and the learner can save and refresh a page. Create a working folder `week-02-css/`. Explain that CSS changes presentation, while HTML gives content structure. No JavaScript is required.

**Materials:** VS Code, browser with DevTools, sample profile page, and optional phone-sized browser preview.

**Success criteria:** Portfolio contains a readable header/navigation, About, Skills, Projects and Contact sections; consistent spacing/colours; a Flexbox layout; and at least one effective media query. The page remains usable at approximately 375px viewport width.

---

# SESSION 1 — CSS BASICS, SELECTORS, COLOURS AND TYPOGRAPHY (120 MINUTES)

| Time | Teaching activity | Instructor direction |
|---|---|---|
| 0–10 min | Week 1 review | Ask learner to identify `header`, `main`, `section`, `footer`, `class` and `id`. |
| 10–30 min | What CSS does | Contrast unstyled HTML with the same HTML after applying CSS. |
| 30–50 min | Syntax and stylesheet linking | Live-code a stylesheet and show the browser update. |
| 50–75 min | Selectors and cascade | Demonstrate element, class, ID and grouped selectors. |
| 75–95 min | Colour, text, fonts | Make the page visually coherent. |
| 95–115 min | Guided practical | Student styles a mini profile card. |
| 115–120 min | Exit ticket | Student explains a selector and a declaration. |

## 1. Lecture: HTML vs CSS

**Say:** “HTML answers *what is on the page?* CSS answers *how should it look?* If we want every heading to be navy, we should not manually decorate every heading in HTML. We define a CSS rule.”

A CSS rule has a **selector** and a **declaration block**:

```css
h1 {
  color: navy;
  font-size: 2rem;
}
```

Explain that `h1` selects elements; `color` and `font-size` are properties; `navy` and `2rem` are values; semicolons separate declarations. CSS comments use `/* ... */`.

### Three ways to add CSS

1. **Inline:** `<h1 style="color: navy;">Hello</h1>` — useful for demonstration, not the preferred project approach.
2. **Internal:** `<style>h1 { color: navy; }</style>` inside `<head>` — useful for small demos.
3. **External:** `<link rel="stylesheet" href="styles.css">` inside `<head>` — **recommended** for the project.

**Ask:** Why is one external stylesheet easier to maintain than repeating inline styles? **Expected:** Centralised changes, separation of concerns, reuse.

## 2. Live demonstration: Create the first stylesheet

**index.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Portfolio</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <header class="site-header">
    <h1>Uzoamaka's Portfolio</h1>
    <p>Future Software Engineer</p>
  </header>
  <main>
    <section id="about">
      <h2>About Me</h2>
      <p>I enjoy learning to build useful software.</p>
    </section>
  </main>
</body>
</html>
```

**styles.css**

```css
body {
  font-family: Arial, sans-serif;
  background-color: #f4f7fb;
  color: #243247;
  line-height: 1.6;
}
.site-header {
  background-color: #17365d;
  color: white;
  text-align: center;
}
h2 { color: #17365d; }
```

**Demonstrate:** Save files, refresh, then temporarily change `href` to a nonexistent filename. Ask why styles disappear. Restore it. Show DevTools → Inspect → Styles.

## 3. Selectors, specificity and cascade

| Selector | Example | Meaning |
|---|---|---|
| Element | `p { ... }` | All paragraphs |
| Class | `.card { ... }` | Elements with class `card` |
| ID | `#about { ... }` | Element with ID `about` |
| Descendant | `.card p { ... }` | Paragraphs inside `.card` |
| Group | `h1, h2 { ... }` | Both headings |
| Pseudo-class | `a:hover { ... }` | Link when hovered |

**Explain simply:** If rules compete for the same property, CSS considers origin, importance, specificity and source order. For these beginner exercises, an ID selector is more specific than a class, and a class more specific than an element selector; among equally specific rules, the later one generally wins. Do not teach “the last rule always wins.”

**Quick check:**

```css
p { color: black; }
.note { color: green; }
```

For `<p class="note">Hello</p>`, which colour appears? **Answer:** Green, because `.note` is more specific.

## 4. Typography and colour

Explain `font-family`, `font-size`, `font-weight`, `line-height`, `text-align`, `color`, `background-color`; contrast `px` (fixed CSS pixel) with `rem` (relative to root font size). Encourage readable text and sufficient contrast. Use colour consistently: primary, accent, neutral background.

**Instructor prompt:** “Why should we not use pale-yellow text on a white background?” **Answer:** Poor readability/contrast.

## 5. Guided practical — Profile card (STUDENT TASK, 20 MINUTES)

Given:

```html
<article class="profile-card">
  <h2>Uzoamaka</h2>
  <p class="role">Aspiring Software Engineer</p>
  <p>Learning HTML, CSS and Python.</p>
  <a href="mailto:student@example.com">Contact me</a>
</article>
```

**Task:** Set a white card background, dark text, navy heading, purple role, and coloured link. Explain each selector aloud. Try one `:hover` rule.

### INSTRUCTOR SOLUTION — Profile card

```css
body { background: #f3f5f9; font-family: Arial, sans-serif; color: #263238; }
.profile-card { background: white; }
.profile-card h2 { color: #17365d; }
.role { color: #6941c6; font-weight: bold; }
.profile-card a { color: #075bb5; }
.profile-card a:hover { text-decoration: none; }
```

**Common mistakes:** Writing `background-color = white` instead of `background-color: white;`; forgetting the `.` for class selectors; not linking stylesheet; CSS file named `style.css` while HTML points to `styles.css`.

### Session 1 exit questions and answers

1. **What does CSS stand for?** Cascading Style Sheets.
2. **Which tag connects external CSS?** `<link rel="stylesheet" href="styles.css">`.
3. **What selects a class?** A dot, e.g. `.card`.
4. **What does `color` affect?** Foreground text colour (in common text contexts).
5. **Why use a stylesheet?** Reusability and maintainability.

### Homework 1 — Style Week 1 HTML page (STUDENT TASK)

Add an external stylesheet; style `body`, `header`, `h1`, `h2`, paragraphs and links; use at least two classes and a hover state; provide a 5–8 sentence explanation of selectors used. **Submission:** `index.html`, `styles.css`, screenshot and short reflection.

**INSTRUCTOR SOLUTION CHECKLIST:** Link works; selectors target intended elements; text legible; no inline styling necessary; valid braces/colons/semicolons; two meaningful classes. **Reference snippet:**

```css
body { margin: 0; font-family: Arial, sans-serif; color: #243247; }
header { background: #17365d; color: white; padding: 2rem; }
h2 { color: #17365d; }
.highlight { font-weight: bold; color: #6941c6; }
.contact-link { color: #075bb5; }
.contact-link:hover { text-decoration: underline; }
```

---

# SESSION 2 — BOX MODEL, SPACING AND FLEXBOX (120 MINUTES)

| Time | Activity |
|---|---|
| 0–15 min | Homework review and correction |
| 15–40 min | Box model: content, padding, border, margin |
| 40–55 min | Width, `box-sizing`, `max-width` |
| 55–80 min | Flexbox: axes, direction, gap, alignment |
| 80–110 min | Guided navigation and skills layout |
| 110–120 min | Review and questions |

## 1. Box model lecture

Every CSS box has **content → padding → border → margin**. Padding is inside the border; margin is outside it.

```css
.card {
  width: 300px;
  padding: 20px;
  border: 2px solid #17365d;
  margin: 16px;
}
```

**Worked calculation:** Under default `box-sizing: content-box`, the element’s border-box width is `300 + 20 + 20 + 2 + 2 = 344px`. Margins add external space, not to the border-box width. With `box-sizing: border-box`, the specified `width: 300px` includes content, padding and border.

**Recommended reset:**

```css
*, *::before, *::after { box-sizing: border-box; }
body { margin: 0; }
```

**Demonstrate:** Inspect the box model in DevTools and change padding from `10px` to `30px`.

## 2. Layout widths

```css
.container {
  width: min(90%, 1100px);
  margin-inline: auto;
}
```

Explain percentage width, maximum readable page width, and auto horizontal margins. `min(90%, 1100px)` chooses the smaller size, keeping the container narrow on phones and capped on large screens.

## 3. Flexbox lecture

**Say:** “Flexbox helps arrange children in a row or column, and control spacing and alignment.”

```css
.nav-links {
  display: flex;
  gap: 1rem;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}
```

Explain:
- `display: flex`: creates a flex formatting context.
- `flex-direction: row | column`: sets main axis direction.
- `justify-content`: distributes space along main axis.
- `align-items`: aligns items along cross axis.
- `gap`: space between items.
- `flex-wrap`: allows items to move to another line.

**Check for understanding:** When `flex-direction: column`, which direction does `justify-content` act along? **Answer:** Vertical main axis.

## 4. Guided practical — Navigation and skill cards (STUDENT TASK)

HTML:

```html
<nav class="nav-links" aria-label="Main navigation">
  <a href="#about">About</a>
  <a href="#skills">Skills</a>
  <a href="#projects">Projects</a>
  <a href="#contact">Contact</a>
</nav>
<section id="skills" class="container">
  <h2>Skills</h2>
  <div class="skills-list">
    <div class="skill-card">HTML</div>
    <div class="skill-card">CSS</div>
    <div class="skill-card">Git</div>
  </div>
</section>
```

**Tasks:** Horizontal nav with spacing; cards side-by-side and wrapping; consistent padding/border; centered container; check at narrow width.

### INSTRUCTOR SOLUTION

```css
*, *::before, *::after { box-sizing: border-box; }
body { margin: 0; font-family: Arial, sans-serif; }
.container { width: min(90%, 1000px); margin-inline: auto; }
.nav-links { display: flex; flex-wrap: wrap; justify-content: center; gap: 1.25rem; padding: 1rem; background: #17365d; }
.nav-links a { color: white; text-decoration: none; }
.skills-list { display: flex; flex-wrap: wrap; gap: 1rem; }
.skill-card { flex: 1 1 150px; padding: 1.25rem; background: #eef3fa; border: 1px solid #cad6e5; border-radius: 10px; text-align: center; }
```

**Instructor discussion:** `flex: 1 1 150px` means grow allowed, shrink allowed, preferred basis 150px; wrapping handles narrower widths.

## 5. Independent practice — Fix the broken card (STUDENT TASK)

```css
.card {
  width: 100%;
  padding: 40px;
  border: 5px solid blue;
}
```

A card spills outside its parent. Ask the learner to explain a likely cause and propose two fixes.

**INSTRUCTOR SOLUTION:** Default content-box width plus padding/border can exceed parent. Use `box-sizing: border-box;` and/or a global reset. Reduce padding if needed; avoid hardcoded oversized widths.

### Homework 2 — Portfolio layout

Style a page with header, navigation, About, three Skills cards and two Projects cards. Use Flexbox for at least two groups; demonstrate margin/padding/border; use `max-width` or `min()` for content width. **Submission:** Files and desktop screenshot.

**INSTRUCTOR SOLUTION HINT:** `.project-list {display:flex; flex-wrap:wrap; gap:1rem}` and `.project-card {flex:1 1 250px; padding:1rem; border:1px solid #ddd}`. Review semantic HTML from Week 1 rather than replacing sections with arbitrary `div`s.

---

# SESSION 3 — RESPONSIVE DESIGN, MEDIA QUERIES AND WEEKLY PROJECT (120 MINUTES)

| Time | Activity |
|---|---|
| 0–15 min | Review Homework 2 |
| 15–35 min | Responsive design principles |
| 35–55 min | Media queries and mobile layout |
| 55–95 min | Guided weekly portfolio build |
| 95–110 min | Browser tests and debugging |
| 110–120 min | Presentation and knowledge check |

## 1. Responsive design lecture

**Say:** “Responsive design makes a page usable on different screen widths. We are not creating separate websites for phones and computers; we are adapting one layout.”

Teach:
- Viewport meta tag: `<meta name="viewport" content="width=device-width, initial-scale=1.0">`.
- Flexible layouts: `%`, `max-width`, `flex-wrap`.
- Responsive images: `img { max-width: 100%; height: auto; }`.
- Breakpoints based on when content needs adjustment, not on a specific device brand.

## 2. Media query demonstration

```css
.hero { display: flex; gap: 2rem; align-items: center; }
.hero > * { flex: 1; min-width: 0; }

@media (max-width: 600px) {
  .hero { flex-direction: column; text-align: center; }
  .nav-links { flex-direction: column; align-items: center; }
}
```

**Demonstrate:** Resize DevTools viewport from ~1200px to ~375px. Explain that the media query applies at widths **600px and below**. Ask student to change the breakpoint to 700px and observe.

## 3. Weekly project — Responsive personal portfolio (STUDENT BRIEF)

**Scenario:** Create a clean portfolio introducing yourself as an aspiring software engineer.

**Required sections:** Header with name and role; navigation; About; Skills (at least 3); Projects (at least 2 with short descriptions); Contact (email link or HTML contact form); footer.

**Technical requirements:** Separate `index.html` and `styles.css`; semantic HTML; at least one class selector and one ID selector; a consistent colour palette; box model spacing; Flexbox for skills/projects/nav; media query; no horizontal scrolling at 375px; readable text; links work.

**Stretch goals (optional):** Focus styles for keyboard navigation, hover transitions, responsive image, CSS custom properties.

### INSTRUCTOR REFERENCE SOLUTION — `index.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Uzoamaka | Portfolio</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <header class="site-header">
    <div class="container">
      <h1>Uzoamaka</h1>
      <p>Aspiring Software Engineer</p>
      <nav class="nav-links" aria-label="Main navigation">
        <a href="#about">About</a>
        <a href="#skills">Skills</a>
        <a href="#projects">Projects</a>
        <a href="#contact">Contact</a>
      </nav>
    </div>
  </header>
  <main class="container">
    <section id="about">
      <h2>About Me</h2>
      <p>I am learning to design and build accessible, useful websites.</p>
    </section>
    <section id="skills">
      <h2>Skills</h2>
      <div class="card-row">
        <article class="card"><h3>HTML</h3><p>Page structure</p></article>
        <article class="card"><h3>CSS</h3><p>Visual styling</p></article>
        <article class="card"><h3>Git</h3><p>Version control</p></article>
      </div>
    </section>
    <section id="projects">
      <h2>Projects</h2>
      <div class="card-row">
        <article class="card"><h3>Profile Page</h3><p>My first semantic HTML page.</p></article>
        <article class="card"><h3>Contact Form</h3><p>A simple HTML form with required fields.</p></article>
      </div>
    </section>
    <section id="contact">
      <h2>Contact</h2>
      <p>Email: <a href="mailto:student@example.com">student@example.com</a></p>
    </section>
  </main>
  <footer class="site-footer"><p>© 2026 Uzoamaka</p></footer>
</body>
</html>
```

### INSTRUCTOR REFERENCE SOLUTION — `styles.css`

```css
:root { --navy: #17365d; --accent: #6b46c1; --paper: #f4f7fb; --text: #243247; }
*, *::before, *::after { box-sizing: border-box; }
html { scroll-behavior: smooth; }
body { margin: 0; font-family: Arial, sans-serif; line-height: 1.6; color: var(--text); background: var(--paper); }
.container { width: min(90%, 1000px); margin-inline: auto; }
.site-header { background: var(--navy); color: white; padding: 2.5rem 0 1rem; text-align: center; }
.site-header h1 { margin: 0; font-size: 2.2rem; }
.nav-links { display: flex; flex-wrap: wrap; justify-content: center; gap: 1.25rem; margin-top: 1.25rem; }
.nav-links a { color: white; text-decoration: none; padding: .3rem; }
.nav-links a:hover, .nav-links a:focus-visible { text-decoration: underline; }
main section { padding-block: 1.5rem; }
h2 { color: var(--navy); }
.card-row { display: flex; flex-wrap: wrap; gap: 1rem; }
.card { flex: 1 1 240px; min-width: 0; padding: 1.25rem; border: 1px solid #d3deea; border-radius: 12px; background: white; }
.card h3 { color: var(--accent); margin-top: 0; }
a { color: #075bb5; }
.site-footer { text-align: center; padding: 1rem; background: var(--navy); color: white; }
@media (max-width: 600px) {
  .site-header { padding-top: 1.5rem; }
  .nav-links { flex-direction: column; gap: .4rem; }
  .card-row { flex-direction: column; }
  .card { flex-basis: auto; }
}
```

**Explain after demonstration:** The sample intentionally uses CSS variables as an optional preview, not a requirement for mastery. The main teaching points are selectors, box model, Flexbox and media queries.

## 4. Testing checklist (STUDENT TASK)

- [ ] Stylesheet loads without errors.
- [ ] Navigation links scroll to correct sections.
- [ ] All headings and paragraphs are readable.
- [ ] Cards have visible spacing and boundaries.
- [ ] Layout works at desktop width (~1200px).
- [ ] Layout works at tablet width (~768px).
- [ ] Layout works at mobile width (~375px).
- [ ] No unintended horizontal overflow.
- [ ] Email link opens an email client when configured.
- [ ] No broken file paths.

## 5. Troubleshooting guide (INSTRUCTOR)

| Symptom | Likely cause | How to teach the fix |
|---|---|---|
| No styles | Wrong stylesheet path | Inspect `<link href>` and filename. |
| Selector has no effect | Missed `.`/`#` or overridden rule | Inspect element and applied styles. |
| Cards overflow | Fixed widths or content-box sizing | Add `box-sizing: border-box`, use flexible widths. |
| Mobile layout cramped | No wrapping/media query | Test `flex-wrap` and column layout. |
| Navigation links fail | Mismatched `href="#..."` and `id` | Compare target strings exactly. |
| Image stretches | Fixed width and height | Use `max-width: 100%; height: auto`. |

## 6. Weekly assessment rubric

| Area | Weight | Full-credit evidence |
|---|---:|---|
| HTML structure and semantic sections | 15% | Correct meaningful tags and working anchors |
| CSS syntax, selectors, typography | 20% | Valid styles, clear visual hierarchy |
| Box model and spacing | 20% | Consistent padding, margins and borders |
| Flexbox implementation | 20% | Working flexible card/nav layouts |
| Responsive behaviour | 15% | Usable on desktop and phone widths |
| Independence and explanation | 10% | Student can explain and adjust their code |
| **Total** | **100%** | |

**Instructor marking note:** Do not award full marks solely for visual resemblance to the model answer. Ask the learner to change a colour, adjust spacing and explain why the media query works.

## 7. Week 2 final knowledge check — with answer key

1. **What is CSS?** A language for describing HTML presentation.
2. **What is a selector?** A pattern targeting elements to style.
3. **Class vs ID selector?** `.class` can apply to many elements; `#id` targets an identifier intended to be unique in a document.
4. **Margin vs padding?** Outside vs inside border.
5. **What does `box-sizing: border-box` do?** Includes padding and border within specified width/height.
6. **What is Flexbox?** A one-dimensional layout system for arranging items.
7. **What does `gap` do?** Creates spacing between flex/grid items.
8. **What does `flex-wrap` do?** Allows items to wrap onto additional lines.
9. **What is a media query?** Conditional CSS based on features such as viewport width.
10. **Why include viewport meta tag?** Helps mobile browsers use appropriate viewport sizing.
11. **Why use an external stylesheet?** Reuse and maintainability.
12. **How can you debug a CSS rule?** Browser DevTools Inspect/Styles and verify selectors, file paths and precedence.

## 8. Deliverables and handoff to Week 3

Submit `index.html`, `styles.css`, project screenshot(s), brief reflection and instructor feedback. **Do not require Git commands yet:** Week 3 introduces version control and publishing. Preserve the working folder for the next module.

---

**© 2026 Opsfuxion Technologies Limited — Lecturer's teaching material.**
