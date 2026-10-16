# WEEK 3 — GIT, GITHUB & COLLABORATIVE DEVELOPMENT

**Opsfuxion Technologies Limited**  
*Orchestrate Intelligence, Deliver with Precision.*

**Practical Software Engineering Foundation Programme | Lecturer's Teaching Manual**  
**Level:** Beginner | **Contact time:** 3 sessions × 2 hours = 6 hours | **Prerequisite:** Week 2 responsive portfolio | **Deliverable:** GitHub-hosted portfolio repository with branches, pull request, README and published site

> **Instructor-use convention:** Keep **INSTRUCTOR SOLUTION** sections hidden until after learner attempts the task. All repository URLs and usernames shown are placeholders; use the student's own account and actual repository address. GitHub menus can change over time.

## Preparation and learning objectives

**Before class:** Student should have a GitHub account, Git installed, VS Code and a functioning Week 2 portfolio. Confirm `git --version`, account access, and which folder contains `index.html` and `styles.css`. **Do not put passwords, API keys, tokens, personal secrets or `.env` contents in Git.** For a beginner, use GitHub browser authentication or Git Credential Manager where available, rather than asking for a password in terminal.

By the end of Week 3, the student should explain version control; initialise and inspect a repository; stage and commit changes; understand working tree/staging area/history; create and switch branches; push to GitHub; open and merge a pull request; write a README; use `.gitignore`; and publish a static portfolio using GitHub Pages.

**Teaching vocabulary:** repository, working directory, staging area, commit, branch, remote, push, pull, clone, pull request, merge, conflict, README, `.gitignore`, deployment.

---

# SESSION 1 — GIT FUNDAMENTALS & LOCAL VERSION CONTROL (120 MINUTES)

| Time | Activity |
|---|---|
| 0–15 min | Review Week 2 portfolio and installation |
| 15–35 min | Why version control matters |
| 35–60 min | Initialise repo, status, add, commit |
| 60–80 min | Working tree, staging, history, diffs |
| 80–110 min | Guided changes and commits |
| 110–120 min | Exit quiz and homework briefing |

## 1. Lecture: Why Git?

**Say:** “Imagine changing your website and then wishing you could return to yesterday's working version. Git records meaningful snapshots of your project and lets you understand what changed and why.”

**Git vs GitHub:** Git is the version control tool that can work locally. GitHub is an online service for hosting Git repositories and collaborating. A Git repository can exist without GitHub.

**Analogy:** Working directory = desk with current work; staging area = items selected for the next snapshot; commit = labelled snapshot in project history.

### Install and configure (demonstration)

```bash
git --version
git config --global user.name "Student Name"
git config --global user.email "student@example.com"
git config --global --list
```

**Instructor note:** Use an email address the learner chooses; GitHub supports a private noreply commit email. Explain that commit identity is metadata, not login authentication.

## 2. Live demo — Initialise the Week 2 portfolio

Open the existing portfolio folder in VS Code, then use its terminal:

```bash
pwd
ls
git init
git status
```

**Explain:** `git init` creates Git metadata in `.git`; `git status` reports the branch, tracked/untracked files and staging status. Do not manually edit `.git`.

Create `.gitignore`:

```gitignore
.DS_Store
Thumbs.db
.env
.env.*
!.env.example
.vscode/
```

**Explain:** Ignore local files and secrets; `.gitignore` does not retroactively remove a file already tracked. If a secret has been committed, removing it in a new commit does not make it secret again—revoke/rotate it and seek help cleaning history.

Stage and commit:

```bash
git add index.html styles.css .gitignore
git status
git commit -m "Add responsive portfolio website"
git log --oneline
```

**Explain:** `git add` stages a version of the file; `git commit` records the staged snapshot. Files can change again after staging; use `git status` to inspect.

## 3. Inspect changes

Edit a heading in `index.html`, then run:

```bash
git status
git diff
git add index.html
git diff --staged
git commit -m "Improve portfolio introduction"
git log --oneline
```

**Demonstrate:** `git diff` shows unstaged tracked changes; `git diff --staged` shows staged changes. `git log --oneline` shows abbreviated history.

## 4. Guided practical (STUDENT TASK)

1. Confirm the portfolio contains `index.html` and `styles.css`.
2. Initialise Git if not already done.
3. Add a `.gitignore`.
4. Make the first commit.
5. Change the About paragraph.
6. Inspect changes with `git diff`.
7. Commit with a descriptive message.
8. Show at least two commits in `git log --oneline`.

### INSTRUCTOR SOLUTION — Command sequence

```bash
git init
git status
git add index.html styles.css .gitignore
git commit -m "Create initial portfolio"
# Edit the About section and save
git diff
git add index.html
git commit -m "Update About section"
git log --oneline
```

**Expected:** Two commits; clean working tree after second commit. If `.gitignore` did not exist, create it before `git add`. If Git says “nothing to commit,” check whether the file actually changed and was saved.

### Common mistakes and corrections

| Mistake | Explanation/fix |
|---|---|
| `fatal: not a git repository` | Run inside project directory; use `pwd`, `ls`, then `git init` if appropriate. |
| Author identity unknown | Configure `user.name` and `user.email`. |
| “Nothing to commit” | No staged changes; save edits and inspect `git status`. |
| Wrong files staged | Use `git status`; unstage with `git restore --staged filename` (for tracked files) or `git rm --cached filename` if needed. |
| Committing secrets | Stop, rotate secret, seek guidance; never assume deleting a file from latest commit removes history. |

### Session 1 exit questions — answer key

1. **What is Git?** Distributed version control software.
2. **What is GitHub?** Repository hosting and collaboration service.
3. **What does `git init` do?** Initialises a repository.
4. **What does `git add` do?** Stages changes.
5. **What does `git commit` do?** Records a snapshot of staged changes.
6. **What does `git status` show?** State of working tree/staging and branch.

### Homework 1 (STUDENT TASK)

Make three small, purposeful portfolio improvements (e.g. project description, skill card, contact link). Commit each separately with a descriptive message. Submit a screenshot or copied output of `git log --oneline` and a paragraph explaining staging versus committing.

**INSTRUCTOR ANSWER:** Good history might show `Update contact email link`, `Add CSS skills card`, `Clarify project description`. The staging area selects changes for the next commit; committing stores that selection in history.

---

# SESSION 2 — GITHUB REMOTES, BRANCHES & PULL REQUESTS (120 MINUTES)

| Time | Activity |
|---|---|
| 0–15 min | Homework review |
| 15–35 min | Local vs remote repositories |
| 35–60 min | Create GitHub repo and push |
| 60–80 min | Branching and switching |
| 80–105 min | Pull request demonstration and practice |
| 105–120 min | Review, conflicts overview and questions |

## 1. Lecture: Local and remote repositories

**Say:** “Git works on your laptop. A remote repository is another copy of the project, commonly hosted on GitHub. Pushing shares local commits; pulling brings remote updates into your current branch.”

Explain `origin` as a conventional remote name; `main` as a common default branch name; `git push` vs `git pull` vs `git clone`.

## 2. Create GitHub repository and push

**Instructor demo:** On GitHub, create a new repository named `student-portfolio`. When pushing an existing local repository, create it **without** initialising a README or `.gitignore` online to avoid unrelated initial histories. Choose public if the learner agrees to public publishing and the portfolio contains no sensitive information.

Copy the **actual** HTTPS remote URL from GitHub:

```bash
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/student-portfolio.git
git remote -v
git push -u origin main
```

**Explain:** `-u` records upstream tracking. Authentication may open a browser. Never paste credentials into class notes or screenshots.

**Troubleshooting:** If `origin` already exists, inspect `git remote -v` and, only after confirming the correct destination, use `git remote set-url origin ACTUAL_URL`. If push is rejected, inspect remote history and discuss safe integration; do not teach force-push as a default fix.

## 3. Branching

A branch lets us work on a change without immediately altering the main line of development.

```bash
git switch -c feature/contact-section
# Edit and save index.html or styles.css
git status
git add index.html styles.css
git commit -m "Improve contact section"
git push -u origin feature/contact-section
```

**Explain:** `git switch -c` creates and switches to a new branch. A branch points to a sequence of commits; it is not a separate physical folder by default.

## 4. Pull requests

On GitHub:

1. Open the repository.
2. Choose the new branch or the prompt to compare/open a pull request.
3. Set base `main`, compare `feature/contact-section`.
4. Give the PR a clear title and description.
5. Review **Files changed**.
6. Merge the PR when ready.
7. Return locally and synchronise:

```bash
git switch main
git pull --ff-only origin main
```

**Note:** `--ff-only` refuses to create an implicit merge commit; if histories diverge, stop and inspect rather than forcing an update. Deleting the feature branch after merge is optional.

### Guided practical (STUDENT TASK)

Create a branch `feature/projects-section`, add a third project card, commit, push, open a PR, explain the diff and merge it. Verify `main` contains the new card.

### INSTRUCTOR SOLUTION — Command/reference workflow

```bash
git switch main
git pull --ff-only origin main
git switch -c feature/projects-section
# Add third project card in index.html
git add index.html
git commit -m "Add third portfolio project"
git push -u origin feature/projects-section
# Open, review and merge PR on GitHub
git switch main
git pull --ff-only origin main
git log --oneline -5
```

**Expected evidence:** Branch visible on GitHub; PR shows meaningful file change; merge completed; main contains update. If branch protection blocks direct merge, follow repository permissions rather than bypassing them.

## 5. Mini-lecture: Merge conflicts (introductory)

A conflict can occur when different branches modify the same area and Git cannot safely combine them automatically.

**Illustrative markers (do not leave these in final files):**

```text
<<<<<<< HEAD
<h2>My Work</h2>
=======
<h2>Featured Projects</h2>
>>>>>>> feature/projects-section
```

**Instructor explanation:** Choose the correct final content, remove markers, test the HTML, stage and finish the merge according to Git's instructions. **Do not deliberately create a complicated conflict** if time is limited; demonstrate conceptually.

### Homework 2 (STUDENT TASK)

Open another feature branch, improve the portfolio footer or navigation, create a PR with a meaningful description including **What changed** and **How tested**, and merge after review. Submit the PR URL.

**INSTRUCTOR SOLUTION RUBRIC:** Branch created, one purposeful change, descriptive commit, PR description, review, merge, main updated. Example PR text: “Added a navigation link to the Contact section. Tested by opening index.html and clicking the link.”

---

# SESSION 3 — README, `.gitignore`, GITHUB PAGES & WEEKLY PROJECT (120 MINUTES)

| Time | Activity |
|---|---|
| 0–15 min | Review branch and PR homework |
| 15–35 min | README and project documentation |
| 35–50 min | `.gitignore` and repository hygiene |
| 50–80 min | Publish portfolio with GitHub Pages |
| 80–105 min | Independent final project and verification |
| 105–120 min | Demo, quiz and feedback |

## 1. README lecture

**Say:** “Someone who opens your repository should understand what the project does and how to view it without asking you for instructions.”

Explain Markdown headings (`#`), bullets (`-`), links (`[text](url)`), code fences, screenshots and relative paths.

### INSTRUCTOR REFERENCE SOLUTION — `README.md`

```markdown
# Student Portfolio

A responsive personal portfolio created while learning HTML and CSS.

## Features
- About, Skills, Projects and Contact sections
- Flexbox layout
- Mobile-friendly styling

## Technologies
- HTML5
- CSS3
- Git and GitHub

## Run locally
1. Download or clone this repository.
2. Open `index.html` in a web browser.

## Live website
[View my portfolio](https://YOUR_USERNAME.github.io/student-portfolio/)

## What I learned
I practised semantic HTML, CSS layouts, Git commits and pull requests.
```

**Instructor note:** Replace placeholder URL with actual published URL after deployment. Do not claim features that have not been built.

## 2. `.gitignore` lecture

Explain that `.gitignore` tells Git which **untracked** files to ignore. It is not a security boundary or a way to erase secrets from history.

```gitignore
.DS_Store
Thumbs.db
.env
.env.*
!.env.example
.vscode/
```

**Practice:** Create a temporary `.DS_Store`-like filename or `notes.tmp`, add `notes.tmp` to `.gitignore`, then run `git status`. Note that a previously tracked file needs separate handling.

## 3. Publish with GitHub Pages

**Prerequisites:** Public repository (or an eligible plan supporting private repo publishing), `index.html` at repository root, `main` pushed, and permission to configure Pages.

**Instructor demo (current GitHub UI may vary):**

1. Open the GitHub repository.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**.
4. Select branch **main**, folder **/(root)**, and save.
5. Wait for the deployment to complete and open the displayed site URL.
6. Check navigation, CSS, layout and links.

**Typical project-site URL:** `https://YOUR_USERNAME.github.io/student-portfolio/`. This is a pattern, not a guaranteed URL; copy the actual link GitHub displays.

**Important:** GitHub Pages hosts static files. It does **not** provide a Python backend or automatically process HTML contact-form submissions. If the contact form has `action="#"`, it is only a demonstration, not a working email service.

**Debugging publication:** Check Pages deployment status; confirm `index.html` at selected source; verify case-sensitive file paths and CSS `href="styles.css"`; avoid root-absolute asset paths like `/styles.css` on project sites unless intentionally configured.

## 4. Weekly project — GitHub-ready portfolio (STUDENT BRIEF)

**Scenario:** Turn the Week 2 responsive portfolio into a properly version-controlled, documented and publicly viewable project.

**Requirements:**
- Local Git repository with meaningful commit history.
- Remote GitHub repository.
- At least one feature branch.
- At least one reviewed and merged PR.
- `README.md` describing project and local setup.
- `.gitignore` appropriate for project.
- Working GitHub Pages URL.
- Portfolio sections and mobile responsiveness preserved.
- No secrets or private personal information in repository.

**Suggested final structure:**

```text
student-portfolio/
├── index.html
├── styles.css
├── README.md
└── .gitignore
```

### INSTRUCTOR REFERENCE SOLUTION — End-to-end checklist

```bash
# From portfolio directory, if Git has not yet been initialised:
git init
git branch -M main
# Ensure README.md and .gitignore have been created
git add index.html styles.css README.md .gitignore
git commit -m "Prepare portfolio for GitHub"
# Add actual remote copied from GitHub:
git remote add origin https://github.com/YOUR_USERNAME/student-portfolio.git
git push -u origin main
# New feature:
git switch -c feature/portfolio-update
# Edit portfolio and save
git add index.html styles.css
git commit -m "Polish portfolio layout"
git push -u origin feature/portfolio-update
# Open and merge PR in GitHub, then:
git switch main
git pull --ff-only origin main
```

**Do not run this entire block blindly:** If repository and remote already exist from earlier sessions, continue from their current state instead of reinitialising or adding duplicate remotes.

## 5. Final practical assessment (STUDENT TASK)

Without step-by-step prompts, ask learner to:

1. Explain Git vs GitHub.
2. Run `git status` and explain output.
3. Make a small change and commit it.
4. Show the recent commit history.
5. Identify the main branch and remote.
6. Show the merged pull request.
7. Open README and explain its purpose.
8. Open the deployed site on desktop and phone width.
9. Explain why a static HTML contact form does not send email automatically.

### INSTRUCTOR MODEL ANSWERS

- Git manages versions; GitHub hosts and facilitates collaboration.
- `git status` shows branch and changed/staged/untracked files.
- A commit records staged changes, with a descriptive message.
- `git log --oneline` lists commits.
- `git branch` shows local branches; `git remote -v` shows remote URLs.
- PR documents a proposed change, review and merge.
- README documents purpose, setup and usage.
- GitHub Pages serves static site files; form submission needs a backend/service.

## 6. Troubleshooting guide

| Symptom | Likely cause | Instructor fix |
|---|---|---|
| `git: command not found` | Git not installed or PATH issue | Install Git, restart terminal, verify `git --version`. |
| `fatal: not a git repository` | Wrong directory | Navigate to project and inspect files. |
| Push authentication fails | Credentials or account setup | Use browser-based authentication / credential helper; do not request passwords. |
| `remote origin already exists` | Remote already configured | Inspect `git remote -v`; set correct URL if necessary. |
| Push rejected | Remote branch has commits not locally integrated | Fetch and inspect; integrate safely; avoid force-push as default. |
| PR has no changes | Branch identical to base or changes not pushed | Inspect branch, commits and remote. |
| Pages shows 404 | Wrong Pages source, path, or deployment not finished | Check Settings → Pages, source branch/root and deployment status. |
| Published CSS missing | Wrong relative path or filename case | Inspect browser network tab and `href`. |
| `.gitignore` not working | File already tracked | Explain ignore applies to untracked files; remove from index if appropriate. |

## 7. Assessment rubric

| Area | Weight | Full-credit evidence |
|---|---:|---|
| Git fundamentals and local commits | 25% | Status/add/commit/log used correctly |
| GitHub remote and push | 15% | Repo online and synced |
| Branch and pull request workflow | 25% | Meaningful branch, PR, review and merge |
| README and `.gitignore` | 15% | Accurate documentation and appropriate exclusions |
| GitHub Pages publication | 15% | Live site works, styles load, links function |
| Independent explanation | 5% | Learner can articulate commands and choices |
| **Total** | **100%** | |

**Scoring guidance:** 90–100 excellent; 80–89 very good; 70–79 good; 60–69 satisfactory; 50–59 developing; below 50 needs improvement. These are internal training categories.

## 8. Knowledge check — with answers

1. **What is version control?** Recording and managing changes to files over time.
2. **Git vs GitHub?** Local/distributed VCS vs online hosting/collaboration platform.
3. **What is a repository?** A project with version-controlled history.
4. **What does `git init` do?** Creates repository metadata.
5. **What does `git status` do?** Shows current repository state.
6. **What does `git add` do?** Stages changes.
7. **What does `git commit` do?** Records staged snapshot.
8. **What does `git log --oneline` show?** Condensed commit history.
9. **What is a branch?** A movable reference to a line of commits.
10. **What is `origin`?** Conventional name for a remote.
11. **What does `git push` do?** Sends local commits/refs to a remote.
12. **What does `git pull` do?** Fetches and integrates remote changes into current branch.
13. **What is a pull request?** A proposal to review and merge branch changes.
14. **What is a merge conflict?** Git cannot automatically combine overlapping changes.
15. **Why have a README?** Explain project, usage and setup.
16. **What is `.gitignore` for?** Excluding matching untracked files from normal tracking.
17. **Does `.gitignore` protect secrets already committed?** No.
18. **What is GitHub Pages?** Static website hosting from a repository.
19. **Can GitHub Pages run a Python server?** No, not as a backend on Pages.
20. **Why make small commits?** Easier review, troubleshooting and understanding.

## 9. Deliverables and transition to Week 4

**Student submits:** GitHub repo URL, deployed site URL, PR URL, README, `.gitignore`, screenshot(s) of desktop/mobile view, short reflection. Instructor verifies links and reviews commit history.

**Transition:** Week 4 Part 1 begins Python fundamentals (variables, types, operators and I/O). The supplementary Week 4 Part 2 React introduction is separate and should not displace the Python foundation.

---

**© 2026 Opsfuxion Technologies Limited — Lecturer's teaching material.**
