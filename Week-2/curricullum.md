
# Week 2 — CSS Fundamentals, Styling & Responsive Web Design

## Practical Software Engineering Foundation Programme

**Duration:** 1 Week  
**Sessions:** 3 Instructor-Led Sessions  
**Session Duration:** 2 Hours  
**Total Instructor-Led Time:** 6 Hours  
**Level:** Beginner  
**Prerequisite:** Week 1 — HTML Fundamentals  
**Weekly Project:** Personal Portfolio Website — Version 2

---

## Week Overview

Week 2 introduces Cascading Style Sheets (CSS), the technology used to control the visual presentation of webpages.

Building on the HTML knowledge acquired in Week 1, the student will learn how to style text, apply colours, control spacing, arrange webpage elements, and create layouts that adapt to different screen sizes.

The primary objective is to transform the HTML-only personal profile website developed in Week 1 into a visually appealing, organised, and responsive personal portfolio.

The student will also begin understanding the importance of separating webpage structure from presentation.

---

# Learning Objectives

By the end of Week 2, the student should be able to:

- Explain what CSS is and why it is used.
- Understand the relationship between HTML and CSS.
- Apply CSS using an external stylesheet.
- Understand CSS selectors and declarations.
- Style headings, paragraphs, links, and other HTML elements.
- Apply colours, fonts, borders, and backgrounds.
- Understand the CSS Box Model.
- Use margin and padding to control spacing.
- Understand basic CSS specificity and the cascade.
- Use Flexbox to create simple layouts.
- Understand responsive web design.
- Use media queries to adapt layouts to smaller screens.
- Use browser developer tools to inspect and troubleshoot CSS.
- Transform an HTML-only webpage into a styled, responsive website.

---

# Session 1 — Introduction to CSS & Basic Styling

**Duration:** 2 Hours

## 1. Review of Week 1 — 15 Minutes

Review the personal profile website created during Week 1.

Discussion topics:

- HTML document structure
- Semantic HTML
- Headings and paragraphs
- Lists
- Images
- Links
- Forms
- HTML attributes

The student will open the Week 1 project and explain how the HTML document is structured.

### Discussion Question

Why does our HTML webpage look relatively plain even though all the information is present?

This question introduces the purpose of CSS.

---

## 2. What is CSS? — 15 Minutes

**CSS — Cascading Style Sheets**

CSS is a stylesheet language used to control the appearance and layout of HTML documents.

CSS can control:

- Colours
- Fonts
- Text sizes
- Backgrounds
- Borders
- Spacing
- Alignment
- Layouts
- Responsive behaviour

### HTML vs CSS

```text
HTML → Structure and Content

CSS  → Styling and Presentation
```

Example:

HTML determines that a piece of text is a heading.

CSS determines how that heading looks.

---

## 3. Ways to Apply CSS — 20 Minutes

Introduce three approaches:

### Inline CSS

```html
<h1 style="color: blue;">Hello World</h1>
```

### Internal CSS

```html
<head>
    <style>
        h1 {
            color: blue;
        }
    </style>
</head>
```

### External CSS

Create a separate file called `style.css`.

```css
h1 {
    color: blue;
}
```

Connect the stylesheet to HTML:

```html
<head>
    <link rel="stylesheet" href="style.css">
</head>
```

### Discussion

Why are external stylesheets generally preferred for larger projects?

Introduce:

- Separation of concerns
- Reusability
- Maintainability
- Cleaner code organisation

**Recommended approach for this programme:** External CSS.

---

## 4. Understanding CSS Syntax — 20 Minutes

Example:

```css
h1 {
    color: purple;
    font-size: 32px;
}
```

Breakdown:

```text
h1          → Selector

color       → Property

purple      → Value

font-size   → Property

32px        → Value
```

Topics include:

- Selectors
- Declaration blocks
- Properties
- Values
- Semicolons
- Curly braces
- CSS comments

### CSS Comments

```css
/* This styles the main heading */
h1 {
    color: purple;
}
```

---

## 5. CSS Selectors — 20 Minutes

Introduce:

### Element Selector

```css
p {
    color: black;
}
```

### Class Selector

```css
.introduction {
    color: green;
}
```

### ID Selector

```css
#main-title {
    color: navy;
}
```

### Grouping Selectors

```css
h1, h2, h3 {
    font-family: Arial, sans-serif;
}
```

Explain the difference between classes and IDs.

Introduce basic specificity and how CSS resolves conflicting rules.

---

## 6. Guided Practical — 20 Minutes

### Practical Exercise 1: Style Your First Webpage

Using the Week 1 personal profile website:

1. Create a `style.css` file.
2. Link it to `index.html`.
3. Change the webpage background colour.
4. Change heading colours.
5. Apply a font family.
6. Change paragraph text size.
7. Style navigation links.
8. Create at least two CSS classes.
9. Apply a class to multiple HTML elements.

### Expected Result

A styled version of the Week 1 HTML webpage.

---

## 7. Session Review — 10 Minutes

The student should explain:

1. What is CSS?
2. Why do we use CSS?
3. What is a selector?
4. What is a CSS property?
5. What is the difference between a class and an ID?
6. Why do we use external stylesheets?

---

# Session 1 Assignment

## CSS Styling Challenge

Using the personal profile website:

- Apply a consistent colour scheme.
- Style all major headings.
- Improve paragraph readability.
- Style navigation links.
- Add background colours.
- Create and use at least three CSS classes.
- Keep CSS in a separate stylesheet.

**Deliverable:** Personal Profile Website — Basic Styling Version

---

# Session 2 — CSS Box Model, Layouts & Flexbox

**Duration:** 2 Hours

## 1. Review — 15 Minutes

Review the Session 1 assignment.

Discuss:

- Correct stylesheet linking
- CSS selectors
- Colour choices
- Code readability
- Problems encountered

---

## 2. Understanding the CSS Box Model — 25 Minutes

Every HTML element is represented as a rectangular box.

The CSS Box Model consists of:

```text
+-----------------------------------+
|             MARGIN                |
|   +---------------------------+   |
|   |          BORDER           |   |
|   |   +-------------------+   |   |
|   |   |      PADDING      |   |   |
|   |   |   +-----------+   |   |   |
|   |   |   |  CONTENT  |   |   |   |
|   |   |   +-----------+   |   |   |
|   |   +-------------------+   |   |
|   +---------------------------+   |
+-----------------------------------+
```

Topics include:

- Content
- Padding
- Border
- Margin
- Width
- Height
- `box-sizing`

### Example

```css
.card {
    width: 300px;
    padding: 20px;
    border: 2px solid black;
    margin: 15px;
    box-sizing: border-box;
}
```

### Discussion

What is the difference between margin and padding?

---

## 3. Display Properties — 15 Minutes

Introduction to:

- Block elements
- Inline elements
- Inline-block
- `display: none`

Examples:

```css
span {
    display: inline;
}

section {
    display: block;
}
```

---

## 4. Introduction to Flexbox — 30 Minutes

Flexbox is a CSS layout system used to arrange elements in rows or columns.

Topics include:

- Flex container
- Flex items
- `display: flex`
- `flex-direction`
- `justify-content`
- `align-items`
- `gap`
- `flex-wrap`

### Example

```css
.navigation {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 20px;
}
```

### Demonstration

Create three boxes and arrange them horizontally.

Then change their arrangement vertically.

---

## 5. Guided Practical — 25 Minutes

### Practical Exercise 2: Create a Portfolio Layout

Using Flexbox:

1. Arrange navigation links horizontally.
2. Create a header with a name and navigation.
3. Place an image beside an introduction.
4. Create three interest or skill cards.
5. Add spacing between sections.
6. Use margins and padding to improve readability.

### Expected Result

A portfolio webpage with organised sections and improved layout.

---

## 6. Review — 10 Minutes

Questions:

1. What is the CSS Box Model?
2. What is padding?
3. What is margin?
4. What does `display: flex` do?
5. What is the difference between `justify-content` and `align-items`?

---

# Session 2 Assignment

Improve the layout of the portfolio website.

Requirements:

- Create a horizontal navigation.
- Add consistent spacing between sections.
- Use Flexbox in at least two areas.
- Create three visually distinct cards.
- Improve the layout of the profile image.
- Keep the HTML and CSS organised.

**Deliverable:** Personal Portfolio — Layout Version

---

# Session 3 — Responsive Web Design & Weekly Project

**Duration:** 2 Hours

## 1. Assignment Review — 15 Minutes

The student will demonstrate the improvements made to the portfolio.

Discuss layout choices, spacing, and the use of Flexbox.

---

## 2. Introduction to Responsive Web Design — 20 Minutes

Responsive web design allows webpages to adapt to different screen sizes.

Examples:

- Desktop computers
- Laptops
- Tablets
- Smartphones

### Discussion

Why should a website work on both a laptop and a mobile phone?

Introduce:

- Flexible layouts
- Relative sizing
- Responsive images
- Mobile-friendly design
- Viewport

### HTML Viewport Meta Tag

```html
<meta name="viewport"
      content="width=device-width, initial-scale=1.0">
```

---

## 3. CSS Units & Responsive Images — 15 Minutes

Introduce:

- `px`
- `%`
- `rem`
- `vw`

Example:

```css
.container {
    width: 90%;
    max-width: 1000px;
    margin: 0 auto;
}

img {
    max-width: 100%;
    height: auto;
}
```

---

## 4. Introduction to Media Queries — 20 Minutes

Media queries allow CSS rules to apply under certain conditions.

Example:

```css
.navigation {
    display: flex;
    gap: 20px;
}

@media (max-width: 600px) {
    .navigation {
        flex-direction: column;
    }
}
```

The student will observe how the navigation changes when the browser window becomes narrower.

---

## 5. Browser Developer Tools — 10 Minutes

Introduction to:

- Inspect Element
- Viewing applied CSS
- Testing different screen sizes
- Identifying CSS errors
- Responsive device simulation

---

# Week 2 Project

## Personal Portfolio Website — Version 2

**Project Type:** HTML + CSS

The student will transform the HTML-only personal profile created in Week 1 into a styled and responsive portfolio website.

### Project Requirements

The website should include:

1. A styled header.
2. Navigation links.
3. A profile image.
4. An About Me section.
5. An Education section.
6. An Interests section.
7. Software Engineering learning goals.
8. A contact form interface.
9. A footer.
10. A consistent colour scheme.
11. Readable typography.
12. Proper spacing.
13. At least two Flexbox layouts.
14. Basic responsive behaviour.
15. An external CSS stylesheet.

---

## Suggested Project Structure

```text
Week-02/
└── personal-portfolio/
    ├── index.html
    ├── style.css
    └── images/
        └── profile.jpg
```

---

## Independent Project Work — 30 Minutes

The student will work on the project independently.

The instructor will provide guidance where necessary without completing the project on the student's behalf.

The student should:

- Review project requirements.
- Identify the sections requiring styling.
- Write CSS rules.
- Test the website in a browser.
- Inspect the layout on different screen sizes.
- Fix identified issues.

---

## Project Completion & Homework

Complete any unfinished styling and test the website at desktop and mobile widths.

The final website should be submitted with all required files.

---

# Week 2 Knowledge Check

1. What is CSS?
2. What is the difference between HTML and CSS?
3. What is a CSS selector?
4. What is a class selector?
5. What is an ID selector?
6. What is CSS specificity?
7. What is the CSS Box Model?
8. What is the difference between margin and padding?
9. What is Flexbox?
10. What does `justify-content` do?
11. What is responsive web design?
12. What is a media query?
13. Why should images be responsive?
14. What are browser developer tools?
15. Why should HTML and CSS be kept in separate files?

---

# Week 2 Assessment

| Assessment Area | Weight |
|---|---:|
| CSS fundamentals | 20% |
| Correct styling and selectors | 20% |
| Layout and Box Model | 20% |
| Responsive design | 15% |
| Independence and debugging | 15% |
| Project completion and organisation | 10% |
| **Total** | **100%** |

---

# Week 2 Deliverables

By the end of the week, the student should have completed:

- External CSS stylesheet
- CSS styling assignment
- Flexbox layout exercise
- Responsive Personal Portfolio — Version 2
- Week 2 knowledge check

---

# Expected Outcome

By the end of Week 2, the student should be able to:

- Style HTML webpages using CSS.
- Create and use external stylesheets.
- Apply CSS selectors.
- Control spacing using the Box Model.
- Arrange elements using Flexbox.
- Create basic responsive layouts.
- Test webpages using browser developer tools.
- Independently style and improve an existing HTML project.

---

## Next

**Week 3 — Git, GitHub & Version Control**

Week 3 introduces professional version control and project management using Git and GitHub.
