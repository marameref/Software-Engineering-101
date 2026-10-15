
# Week 3 — Git, GitHub & Version Control

## Practical Software Engineering Foundation Programme

**Duration:** 1 Week  
**Sessions:** 3 Instructor-Led Sessions  
**Session Duration:** 2 Hours  
**Total Instructor-Led Time:** 6 Hours  
**Level:** Beginner  
**Prerequisites:** Weeks 0–2  
**Weekly Project:** Personal Portfolio — GitHub Repository

---

## Week Overview

Week 3 introduces Git and GitHub, two essential tools used by software engineers to track changes, manage project history, collaborate, and share software projects.

The student was introduced to GitHub during Week 0. This week focuses on learning how Git works and how to use GitHub as part of a practical software development workflow.

The student will create repositories, track file changes, make commits, connect local projects to GitHub, push and pull changes, and learn basic branching and collaboration concepts.

By the end of the week, the student should be able to manage the HTML/CSS portfolio project using Git and publish it to GitHub.

---

# Learning Objectives

By the end of Week 3, the student should be able to:

- Explain version control.
- Understand why software engineers use Git.
- Explain the difference between Git and GitHub.
- Understand repositories.
- Initialise a Git repository.
- Understand the working directory, staging area, and commit history.
- Track changes to project files.
- Create meaningful commits.
- View commit history.
- Connect a local repository to GitHub.
- Push changes to a remote repository.
- Pull changes from GitHub.
- Understand basic Git branches.
- Create and switch branches.
- Merge simple changes.
- Understand basic collaboration workflows.
- Write a project README.
- Understand the purpose of `.gitignore`.
- Publish a beginner project on GitHub.

---

# Session 1 — Introduction to Version Control & Local Git

**Duration:** 2 Hours

## 1. Review of Previous Weeks — 10 Minutes

Review:

- VS Code
- Project folders
- HTML
- CSS
- Personal portfolio project

Discussion:

How would we recover an earlier version of our website if we accidentally changed or deleted important code?

This introduces the problem that version control helps solve.

---

## 2. What is Version Control? — 15 Minutes

Version control is a system for tracking and managing changes made to files over time.

Without version control, developers might create files such as:

```text
portfolio-final.html
portfolio-final2.html
portfolio-final-fixed.html
portfolio-really-final.html
```

Git allows developers to track meaningful versions without manually creating multiple copies of the same project.

### Benefits

- Tracks changes
- Preserves project history
- Helps recover previous versions
- Supports collaboration
- Makes changes easier to review
- Helps organise software development

---

## 3. Git vs GitHub — 15 Minutes

### Git

Git is a distributed version control system used to track changes in files.

### GitHub

GitHub is an online platform for hosting Git repositories and supporting software development collaboration.

```text
Git
    ↓
Tracks changes locally

GitHub
    ↓
Hosts repositories online
```

Git and GitHub are related but are not the same thing.

---

## 4. Understanding Git Repositories — 15 Minutes

Topics include:

- Repository
- Local repository
- Remote repository
- Working directory
- Staging area
- Commit
- Commit history

### Basic Git Workflow

```text
Working Directory
        ↓
    git add
        ↓
   Staging Area
        ↓
   git commit
        ↓
 Local Repository
        ↓
    git push
        ↓
 Remote Repository
```

---

## 5. Configuring Git — 15 Minutes

Verify Git installation:

```bash
git --version
```

Configure Git identity:

```bash
git config --global user.name "Student Name"
git config --global user.email "student@example.com"
```

The email should be an address associated with the student's GitHub account or an appropriate GitHub-provided private email.

Verify configuration:

```bash
git config --global --list
```

---

## 6. Creating a Local Repository — 20 Minutes

Navigate into a practice project folder.

```bash
cd git-practice
```

Initialise Git:

```bash
git init
```

Check repository status:

```bash
git status
```

Create a file called:

```text
notes.txt
```

Add content to the file.

Stage the file:

```bash
git add notes.txt
```

Commit the change:

```bash
git commit -m "Add initial notes"
```

View commit history:

```bash
git log --oneline
```

---

## 7. Guided Practical — 20 Minutes

### Practical Exercise 1: My First Git Repository

The student will:

1. Create a project folder.
2. Initialise Git.
3. Create a text file.
4. Add information to the file.
5. Check Git status.
6. Stage the file.
7. Commit the changes.
8. Modify the file.
9. Create a second commit.
10. View the commit history.

### Expected Result

A local Git repository containing multiple meaningful commits.

---

## 8. Review — 10 Minutes

Questions:

1. What is version control?
2. What is Git?
3. What is GitHub?
4. What is a repository?
5. What does `git init` do?
6. What does `git status` show?
7. What does `git add` do?
8. What does `git commit` do?

---

# Session 1 Assignment

## Git Practice Challenge

Create a repository called:

```text
my-git-practice
```

Create:

```text
notes.txt
goals.txt
```

Make at least three meaningful commits.

Example commit messages:

```text
Add introduction notes
Add software engineering goals
Update learning goals
```

Use `git log --oneline` to inspect the commit history.

**Deliverable:** Local Git practice repository.

---

# Session 2 — GitHub Repositories & Remote Workflows

**Duration:** 2 Hours

## 1. Assignment Review — 15 Minutes

Review the local repository.

The student should demonstrate:

- Repository location
- Git status
- Staging
- Commits
- Commit history

---

## 2. Understanding Remote Repositories — 15 Minutes

A remote repository is a version of a Git repository hosted somewhere else, such as GitHub.

Topics include:

- Local vs remote repositories
- Remote names
- `origin`
- Push
- Pull
- Clone
- Basic authentication

---

## 3. Creating a GitHub Repository — 20 Minutes

The student will:

1. Log in to GitHub.
2. Create a new repository.
3. Choose a repository name.
4. Add a description.
5. Select public or private visibility.
6. Review the repository URL.

Suggested repository:

```text
personal-portfolio
```

For an existing local Git project, create an empty GitHub repository without automatically adding a README or other files.

---

## 4. Connecting a Local Repository to GitHub — 25 Minutes

Navigate to the existing portfolio project:

```bash
cd personal-portfolio
```

Initialise Git if it is not already a repository:

```bash
git init
```

Stage project files:

```bash
git add .
```

Create the first commit:

```bash
git commit -m "Add personal portfolio website"
```

Set the main branch:

```bash
git branch -M main
```

Connect the GitHub repository:

```bash
git remote add origin https://github.com/USERNAME/personal-portfolio.git
```

Replace `USERNAME` with the actual GitHub username.

Push the project:

```bash
git push -u origin main
```

GitHub authentication may require a browser-based sign-in, credential manager, or another supported authentication method.

---

## 5. Understanding Push, Pull & Clone — 20 Minutes

### Push

Uploads local commits to a remote repository.

```bash
git push
```

### Pull

Fetches and integrates changes from a remote branch.

```bash
git pull
```

### Clone

Creates a local copy of an existing remote repository.

```bash
git clone https://github.com/USERNAME/REPOSITORY.git
```

The student will practise cloning a suitable practice repository into a separate folder.

---

## 6. Guided Practical — 15 Minutes

### Practical Exercise 2: Publish Your Portfolio

The student will:

1. Open the HTML/CSS portfolio.
2. Initialise Git if necessary.
3. Create the first commit.
4. Create a GitHub repository.
5. Connect the local repository.
6. Push the project.
7. Open the repository in a browser.
8. Verify that all project files are present.

### Expected Result

The student's personal portfolio source code is available in a GitHub repository.

---

## 7. Review — 10 Minutes

Questions:

1. What is a remote repository?
2. What does `origin` mean?
3. What does `git push` do?
4. What does `git pull` do?
5. What does `git clone` do?
6. What is the difference between a local and remote repository?

---

# Session 2 Assignment

Make three improvements to the portfolio website.

Examples:

- Update the About Me section.
- Improve the navigation styling.
- Add a new interest or learning goal.

Each improvement should have a separate meaningful commit.

Push all changes to GitHub.

**Deliverable:** Updated portfolio repository with visible commit history.

---

# Session 3 — Branches, README Files & Basic Collaboration

**Duration:** 2 Hours

## 1. Assignment Review — 15 Minutes

The student will open the portfolio repository on GitHub and demonstrate the changes made.

Review:

- Commit history
- Commit messages
- Repository structure
- Project files
- Successful push

---

## 2. Introduction to Git Branches — 20 Minutes

Branches allow developers to work on changes separately from the main development line.

Topics include:

- Main branch
- Feature branches
- Why branches are useful
- Switching branches
- Basic merging

### Create a Branch

```bash
git switch -c feature/update-about
```

### View Branches

```bash
git branch
```

### Switch to Main

```bash
git switch main
```

### Merge a Branch

```bash
git merge feature/update-about
```

The student will learn that merging integrates changes from one branch into another.

---

## 3. Introduction to GitHub Pull Requests — 15 Minutes

A pull request is a proposal to merge changes from one branch into another, often allowing those changes to be reviewed first.

Topics include:

- Feature branches
- Pull requests
- Code review
- Comments
- Approvals
- Merging changes

The student will create a simple pull request on her own practice repository, with instructor guidance.

---

## 4. Writing a README File — 20 Minutes

A README provides useful information about a software project.

Create:

```text
README.md
```

Introduce Markdown formatting:

```markdown
# Personal Portfolio

## About

This is my personal portfolio website.

## Technologies Used

- HTML
- CSS

## Features

- About Me
- Education
- Interests
- Contact Form Interface

## What I Learned

I learned how to structure and style webpages.
```

Topics include:

- Markdown headings
- Bullet points
- Links
- Code blocks
- Project descriptions
- Documentation

---

## 5. Introduction to .gitignore — 10 Minutes

A `.gitignore` file tells Git which untracked files or patterns to ignore.

Example:

```gitignore
.DS_Store
Thumbs.db
.vscode/
```

Explain why developers may exclude:

- Temporary files
- Generated files
- Local environment settings
- Secrets and credentials

**Important:** Never commit passwords, API keys, or other secrets to GitHub. `.gitignore` does not remove secrets that have already been committed.

---

# Week 3 Project

## Personal Portfolio — GitHub Repository

The student will prepare the portfolio project for presentation on GitHub.

### Project Requirements

1. A properly organised project folder.
2. A local Git repository.
3. A remote GitHub repository.
4. A main branch.
5. At least five meaningful commits across the week's work.
6. At least one feature branch.
7. At least one pull request.
8. A README.md file.
9. A suitable .gitignore file.
10. All project files successfully pushed to GitHub.

---

## Suggested Project Structure

```text
personal-portfolio/
│
├── index.html
├── style.css
├── README.md
├── .gitignore
└── images/
    └── profile.jpg
```

---

## Independent Project Work — 30 Minutes

The student will:

1. Review the repository.
2. Create a feature branch.
3. Make a small change.
4. Stage and commit the change.
5. Push the branch to GitHub.
6. Open a pull request.
7. Review the changes.
8. Merge the pull request.
9. Verify the main branch contains the update.
10. Confirm the README is displayed correctly.

The instructor will guide the student where necessary.

---

## Project Completion & Homework

Complete any unfinished GitHub tasks.

Verify that:

- The repository is accessible.
- The correct files are present.
- The README is clear.
- The commit history is visible.
- The feature branch workflow has been completed.
- No sensitive information has been committed.

---

# Week 3 Knowledge Check

1. What is version control?
2. What is Git?
3. What is GitHub?
4. What is the difference between Git and GitHub?
5. What is a repository?
6. What is a local repository?
7. What is a remote repository?
8. What is a commit?
9. What is the staging area?
10. What does `git status` do?
11. What does `git add` do?
12. What does `git commit` do?
13. What does `git push` do?
14. What does `git pull` do?
15. What does `git clone` do?
16. What is a branch?
17. What is a pull request?
18. What is a README?
19. What is `.gitignore`?
20. Why should passwords and API keys never be committed to a repository?

---

# Week 3 Assessment

| Assessment Area | Weight |
|---|---:|
| Understanding of Git concepts | 20% |
| Local Git operations | 20% |
| GitHub repository management | 20% |
| Branching and pull requests | 15% |
| README and project organisation | 15% |
| Independence and troubleshooting | 10% |
| **Total** | **100%** |

---

# Week 3 Deliverables

By the end of Week 3, the student should have completed:

- Local Git practice repository
- GitHub portfolio repository
- Multiple meaningful commits
- Feature branch exercise
- Pull request exercise
- Project README
- .gitignore file
- Week 3 knowledge check

---

# Expected Outcome

By the end of Week 3, the student should be able to:

- Explain Git and GitHub confidently.
- Initialise and manage a Git repository.
- Track and commit file changes.
- View project history.
- Connect a local repository to GitHub.
- Push and pull changes.
- Clone a repository.
- Create and switch branches.
- Understand and complete a basic pull request.
- Write project documentation.
- Maintain a basic professional GitHub repository.

---

## Next

**Week 4 — Python Programming Fundamentals**

Week 4 introduces Python programming, variables, data types, user input, operators, and the development of the student's first command-line applications.
