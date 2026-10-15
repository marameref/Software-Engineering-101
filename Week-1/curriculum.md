# Week 1 — Software Engineering Foundations & HTML

## Practical Software Engineering Foundation Programme

**Duration:** 1 Week  
**Sessions:** 3 Instructor-Led Sessions  
**Session Duration:** 2 Hours  
**Total Instructor-Led Time:** 6 Hours  
**Level:** Beginner  
**Weekly Project:** Personal Profile Website — Version 1

---

## Week Overview

Week 1 marks the beginning of the formal technical curriculum.

The student will be introduced to software engineering as a discipline, understand the basic components of modern software systems, learn how websites communicate with servers, and begin building webpages using HTML.

The emphasis throughout the week is on understanding concepts and applying them practically rather than memorising terminology.

By the end of the week, the student should be capable of creating a structured HTML webpage independently from a set of requirements.

---

# Learning Objectives

By the end of Week 1, the student should be able to:

- Explain what software is.
- Explain what software engineering is.
- Understand the difference between programming and software engineering.
- Identify frontend, backend and database components.
- Understand the basic client-server model.
- Explain at a basic level what happens when a website is visited.
- Understand the role of HTML.
- Create a valid HTML document.
- Use common HTML elements.
- Create headings, paragraphs, lists, links and images.
- Understand HTML attributes.
- Understand basic semantic HTML.
- Create a basic HTML form.
- Translate simple requirements into a webpage.
- Build a complete HTML-only personal webpage.

---

# Session 1 — Software Engineering Foundations & Introduction to HTML

## 1. What is Software?

Introduction to software and how software is used in everyday life.

Examples may include:

- Web browsers
- Mobile applications
- Desktop applications
- Operating systems
- Banking applications
- Social media platforms
- Websites and web applications

Topics include:

- Software
- Hardware vs software
- Programs
- Applications
- Basic categories of software

---

## 2. What is Software Engineering?

Introduction to software engineering as a discipline.

### Programming

Programming involves writing instructions that computers can execute.

### Software Engineering

Software engineering involves the broader process of:

- Understanding problems
- Gathering requirements
- Planning solutions
- Designing systems
- Writing code
- Testing software
- Deploying software
- Maintaining and improving software

Basic software lifecycle:

```text
Problem
   ↓
Requirements
   ↓
Planning
   ↓
Design
   ↓
Development
   ↓
Testing
   ↓
Deployment
   ↓
Maintenance
```

---

## 3. Requirements Thinking Exercise

Scenario:

> A school currently records student attendance manually and wants software to help manage attendance.

The student will consider:

- What problem needs to be solved?
- Who will use the system?
- What should users be able to do?
- What information should the system store?
- What features might be required?

The objective is to begin thinking about software from the perspective of **problems and requirements**, rather than immediately thinking about code.

---

## 4. Introduction to Software Components

### Frontend

The part of an application users see and interact with.

Examples include:

- Buttons
- Navigation
- Forms
- Text
- Images
- Pages

Common frontend technologies include:

```text
HTML
CSS
JavaScript
```

### Backend

The part of an application responsible for operations behind the user interface.

Examples include:

- Processing information
- Authentication
- Business logic
- Communicating with databases
- Handling requests

### Database

A system used to store and retrieve information.

Examples of information stored by applications include:

- User accounts
- Products
- Orders
- Messages
- Student records
- Transactions

### API

A basic introduction to APIs as a mechanism through which software systems can communicate.

APIs will be studied in greater detail later in the programme.

---

## 5. Basic Application Architecture

Introduction to the relationship between major application components.

```text
User
  ↓
Frontend
  ↓
Backend
  ↓
Database
```

Later applications may also involve APIs:

```text
Frontend ↔ API ↔ Backend ↔ Database
```

---

## 6. How the Web Works

Introduction to:

- Browser
- Client
- Server
- Internet
- Domain
- URL
- Request
- Response

Basic flow:

```text
User enters a website address
            ↓
Browser sends a request
            ↓
Server receives the request
            ↓
Server sends a response
            ↓
Browser displays the webpage
```

---

## 7. Introduction to HTML

**HTML — HyperText Markup Language**

HTML is used to describe the structure and meaning of webpage content.

Create:

```text
Week-01/
└── index.html
```

First HTML document:

```html
<!DOCTYPE html>
<html>
<head>
    <title>My First Website</title>
</head>

<body>
    <h1>Hello World!</h1>
    <p>This is my first webpage.</p>
</body>
</html>
```

The student will:

1. Create the file in VS Code.
2. Save the file.
3. Open the webpage in a browser.
4. Modify the HTML.
5. Refresh the browser.
6. Observe the changes.

---

# Session 1 Assignment

Explain the following concepts in your own words:

1. What is software?
2. What is software engineering?
3. What is frontend development?
4. What is backend development?
5. What is a database?
6. What happens when you visit a website?
7. What is HTML?

---

# Session 2 — HTML Fundamentals & Page Structure

## 1. Review

Review concepts from Session 1:

- Software
- Software engineering
- Frontend
- Backend
- Database
- Browser
- Client and server
- HTML

---

## 2. Anatomy of HTML

Example:

```html
<p>Hello World</p>
```

Breakdown:

```text
<p>            Opening tag
Hello World    Content
</p>           Closing tag
```

Together, these form an HTML element.

---

## 3. HTML Attributes

Example:

```html
<a href="https://example.com">Visit Website</a>
```

Introduction to:

- Elements
- Tags
- Attributes
- Attribute values
- Content

---

## 4. HTML Document Structure

Basic HTML structure:

```html
<!DOCTYPE html>
<html>

<head>
    <title>My Website</title>
</head>

<body>

</body>

</html>
```

Topics include:

- `<!DOCTYPE html>`
- `<html>`
- `<head>`
- `<title>`
- `<body>`

---

## 5. HTML Headings

HTML provides six levels of headings.

```html
<h1>Main Heading</h1>
<h2>Section Heading</h2>
<h3>Subheading</h3>
<h4>Heading</h4>
<h5>Heading</h5>
<h6>Heading</h6>
```

Discussion of heading hierarchy and why headings should represent document structure rather than simply text size.

---

## 6. Paragraphs & Text

```html
<p>This is a paragraph.</p>
```

Text emphasis:

```html
<strong>Important text</strong>

<em>Emphasised text</em>
```

---

## 7. HTML Lists

### Unordered List

```html
<ul>
    <li>Python</li>
    <li>HTML</li>
    <li>Git</li>
</ul>
```

### Ordered List

```html
<ol>
    <li>Plan</li>
    <li>Build</li>
    <li>Test</li>
</ol>
```

---

## 8. Hyperlinks

```html
<a href="https://example.com">Visit Website</a>
```

Topics include:

- Anchor elements
- `href`
- External links
- Basic introduction to internal links

---

## 9. Images

```html
<img src="profile.jpg" alt="Profile photograph">
```

Topics include:

- `img`
- `src`
- `alt`
- Image paths
- Relative file paths
- Importance of alternative text

---

# Session 2 Guided Practical — About Me Page

Create a webpage containing:

```text
ABOUT ME

Name

Short Introduction

My Interests
- Interest 1
- Interest 2
- Interest 3

Why I Want to Study Software Engineering

My Goals
1. Goal 1
2. Goal 2
3. Goal 3

Useful Links
```

The student will determine which HTML elements are appropriate for each requirement.

---

# Session 2 Assignment — My Profile

Create:

```text
my-profile.html
```

The webpage should contain:

- Student name as the main heading
- Short personal introduction
- Education section
- Hobbies and interests
- Explanation of why Software Engineering was chosen
- Three learning goals
- At least one ordered list
- At least one unordered list
- At least two links
- At least one image
- Appropriate headings
- Appropriate paragraphs

The student should attempt the assignment independently using notes, previous examples, documentation, and research where necessary.

---

# Session 3 — Semantic HTML, Forms & Weekly Project

## 1. Assignment Review

The student will present the Session 2 assignment.

Discussion will include:

- File organisation
- HTML structure
- Choice of elements
- Attributes
- Lists
- Images
- Links
- Code readability
- Problems encountered
- How problems were solved

The student should be able to explain the code rather than simply demonstrate that it works.

---

## 2. Introduction to Semantic HTML

Semantic HTML uses elements that describe the meaning and purpose of content.

Introduction to:

```html
<header>
<nav>
<main>
<section>
<article>
<footer>
```

Example:

```html
<body>

    <header>
        <h1>My Website</h1>
    </header>

    <nav>
        <!-- Navigation -->
    </nav>

    <main>

        <section>
            <h2>About Me</h2>
            <p>...</p>
        </section>

    </main>

    <footer>
        <p>Copyright information</p>
    </footer>

</body>
```

Topics include:

- Meaningful document structure
- Code readability
- Basic accessibility awareness
- Choosing elements based on purpose

---

## 3. Introduction to HTML Forms

Basic example:

```html
<form>

    <label for="name">Name:</label>
    <input type="text" id="name" name="name">

    <label for="email">Email:</label>
    <input type="email" id="email" name="email">

    <label for="message">Message:</label>
    <textarea id="message" name="message"></textarea>

    <button type="submit">Submit</button>

</form>
```

Introduction to:

- `<form>`
- `<label>`
- `<input>`
- `<textarea>`
- `<button>`
- `type`
- `name`
- `id`

The student will also discuss why an HTML-only form does not automatically store or process submitted information.

This reinforces the relationship between the frontend and backend.

---

# Week 1 Project

## Personal Profile Website — Version 1

The student will build an HTML-only personal website from a set of requirements.

No CSS is required during Week 1.

---

## Project Requirements

### Header

Include:

- Student name
- Short introduction

### Navigation

Create navigation links for:

```text
Home
About
Education
Interests
Goals
Contact
```

### About Section

Include a short personal introduction.

### Education Section

Include relevant educational information.

### Interests Section

Include an unordered list of interests.

### Software Engineering Goals

Include an ordered list of learning or career goals.

### Why Software Engineering?

Include a paragraph explaining the student's interest in Software Engineering.

### Profile Image

Include at least one image with appropriate alternative text.

### Useful Resources

Include at least two external links.

### Contact Section

Create a basic contact form containing:

- Name
- Email
- Message
- Submit button

### Footer

Example:

```text
© 2026 Student Name
```

---

# Suggested Project Structure

```text
Week-01/
│
└── personal-profile/
    │
    ├── index.html
    │
    └── images/
        └── profile.jpg
```

---

# Independent Build

The student should attempt the project independently.

The student may:

- Review previous work
- Review lesson notes
- Consult documentation
- Research unfamiliar concepts
- Ask conceptual questions

The objective is to begin transitioning from:

> Following instructions

to:

> Understanding requirements and deciding how to implement them.

---

# Week 1 Knowledge Check

The student should be able to explain:

1. What is software?
2. What is software engineering?
3. What is the difference between programming and software engineering?
4. What is frontend development?
5. What is backend development?
6. What is a database?
7. What is a client?
8. What is a server?
9. What happens when a browser requests a webpage?
10. What is HTML?
11. What is an HTML element?
12. What is an HTML attribute?
13. What is semantic HTML?
14. What is an HTML form?
15. Why can't HTML alone permanently store submitted form data?

---

# Week 1 Assessment

| Assessment Area | Weight |
|---|---:|
| Understanding of concepts | 20% |
| HTML structure | 20% |
| Correct use of HTML elements | 20% |
| Practical independence & problem-solving | 20% |
| Organisation & code readability | 10% |
| Assignment completion | 10% |
| **Total** | **100%** |

---

# Expected Outcome

By the end of Week 1, the student should understand the basic relationship between:

```text
Software Engineering
        ↓
Web Development
        ↓
Frontend / Backend
        ↓
HTML
```

The student should also understand the simplified web communication process:

```text
Browser
   ↓
Request
   ↓
Server
   ↓
Response
```

Most importantly, the student should be able to start with an empty HTML file and independently create a structured webpage containing:

- Headings
- Paragraphs
- Lists
- Links
- Images
- Semantic sections
- Basic forms

---

# Week 1 Deliverables

By the end of the week, the student should have completed:

- `index.html` — First HTML page
- `my-profile.html` — HTML fundamentals assignment
- Personal Profile Website — Version 1
- Week 1 written knowledge exercises

---

## Next

**Week 2 — CSS Fundamentals, Styling & Responsive Web Design**

Week 2 will introduce CSS and demonstrate how HTML structure can be transformed into a visually designed webpage.
