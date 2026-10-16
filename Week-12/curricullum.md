
# 🎓 WEEK 12 — FINAL CAPSTONE DEVELOPMENT & PRESENTATION

<div align="center">

![Capstone](https://img.shields.io/badge/Capstone-Final_Project-D4A43A?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-Application-3776AB?style=for-the-badge&logo=python&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-Database-003B57?style=for-the-badge&logo=sqlite&logoColor=white)
![Status](https://img.shields.io/badge/Stage-Final_Assessment-16A085?style=for-the-badge)

**Practical Software Engineering Foundation Programme**

**Training Provider:** Opsfuxion Technologies Limited

*Orchestrate Intelligence, Deliver with Precision.*

</div>

---

## 📋 Programme Information

| Item | Details |
|---|---|
| Module | Week 12 — Final Capstone Development & Presentation |
| Duration | 1 Week |
| Sessions | 3 instructor-led sessions |
| Session Duration | 2 Hours |
| Total Contact Hours | 6 Hours |
| Level | Beginner |
| Prerequisites | Weeks 0–11 |
| Primary Technologies | Python, SQLite, Git, GitHub |
| Final Project | Student Management System |
| Learning Approach | Independent development, testing, documentation and presentation |

---

# 📖 Week Overview

Week 12 represents the final stage of the Practical Software Engineering Foundation Programme.

Throughout the programme, the student has developed foundational skills in:

- Developer tools
- HTML and CSS
- Git and GitHub
- Python programming
- Computational thinking
- Data structures
- Loops
- Functions
- Modular programming
- Object-Oriented Programming
- Searching and sorting
- SQL and databases
- Software design
- Testing
- Documentation

The final capstone combines these concepts into one practical software application.

The student will complete a Student Management System that stores student records, manages examination scores, performs basic searching and sorting, and generates academic reports.

The final week also emphasises software testing, documentation, technical communication and project presentation.

---

# 🎯 Learning Objectives

By the end of Week 12, the student should be able to:

- Complete a software project from defined requirements.
- Apply OOP concepts in a practical application.
- Integrate Python with SQLite.
- Implement student registration.
- Retrieve and update student records.
- Implement searching and sorting.
- Record and validate examination scores.
- Calculate academic averages.
- Generate student reports.
- Organise code into modules.
- Handle expected errors.
- Write and execute tests.
- Document a software project.
- Use Git and GitHub to track development.
- Explain the application architecture.
- Demonstrate a working application.
- Reflect on technical challenges and lessons learned.

---

# 🏆 FINAL CAPSTONE PROJECT

## Student Management System

### Project Type

Python Command-Line Application with SQLite Database

### Project Description

Develop a Student Management System for a fictional educational institution.

The system should help an administrator register students, manage student information, record examination results and generate basic academic reports.

The application must store data persistently using SQLite.

---

# 📌 Core Functional Requirements

## 1. Student Registration

The application must allow users to:

- Register new students.
- Enter student names.
- Enter ages.
- Enter courses.
- Assign or generate unique student IDs.
- Validate essential information.
- Save records to SQLite.

## 2. View Student Records

The application must:

- Retrieve saved student records.
- Display student IDs.
- Display names.
- Display ages.
- Display courses.
- Handle an empty database.

## 3. Student Search

The application must:

- Search for students by ID.
- Display matching records.
- Handle missing student IDs.

### Algorithm Requirement

The student should demonstrate linear search on an in-memory collection as part of the project.

Database lookups may use SQL queries.

## 4. Update Student Information

The application should allow users to:

- Update student names.
- Update ages.
- Update courses.
- Save changes to SQLite.

## 5. Delete Student Records

The application should:

- Allow deletion by student ID.
- Request confirmation before deletion.
- Handle unknown IDs.
- Apply a documented policy for related examination results.

## 6. Examination Score Management

The application must:

- Record student examination scores.
- Associate scores with student IDs.
- Validate scores between 0 and 100.
- Retrieve recorded scores.

## 7. Academic Reports

The application must:

- Display student information.
- Display examination scores.
- Calculate average scores.
- Determine Pass or Fail.
- Display a formatted academic report.

### Pass Rule

An average score of 50 or above is a pass.

## 8. Searching and Sorting

The application should demonstrate:

- Linear search
- Sorting by student name
- Sorting by examination score or average

At least one manually implemented sorting algorithm from Week 9 should be included for educational purposes.

## 9. Input Validation

The application must:

- Reject invalid ages.
- Reject examination scores outside 0–100.
- Handle invalid numeric input.
- Reject empty required fields.
- Handle invalid menu selections.

## 10. Persistent Storage

The application must:

- Use SQLite.
- Save student records.
- Save examination results.
- Retrieve records after restarting.
- Use parameterised SQL queries.

---

# 🧱 Suggested Application Architecture

```text
               USER
                |
                v
       Command-Line Menu
                |
                v
        Application Logic
                |
        +-------+-------+
        |               |
        v               v
 Student Services   Result Services
        |               |
        +-------+-------+
                |
                v
        Database Layer
                |
                v
         SQLite Database
```

---

# 📂 Suggested Project Structure

```text
student-management-system/
│
├── main.py
│
├── models/
│   ├── __init__.py
│   ├── student.py
│   └── result.py
│
├── services/
│   ├── __init__.py
│   ├── student_service.py
│   └── result_service.py
│
├── database/
│   ├── __init__.py
│   ├── connection.py
│   └── schema.sql
│
├── algorithms/
│   ├── __init__.py
│   ├── searching.py
│   └── sorting.py
│
├── utils/
│   ├── __init__.py
│   └── validators.py
│
├── tests/
│   ├── test_students.py
│   ├── test_results.py
│   └── test_algorithms.py
│
├── docs/
│   ├── requirements.md
│   ├── design.md
│   └── test-plan.md
│
├── .gitignore
└── README.md
```

### Note

This is a suggested structure. The student may use a simpler design if it is easier to understand and maintain.

Correct functionality and understanding are more important than unnecessary complexity.

---

# 🗓️ SESSION 1 — CORE APPLICATION DEVELOPMENT

**Duration:** 2 Hours

## Session Breakdown

| Activity | Duration |
|---|---:|
| Review Week 11 Prototype | 15 minutes |
| Finalise Architecture | 15 minutes |
| Student CRUD Implementation | 35 minutes |
| Examination Results Integration | 35 minutes |
| Testing and Review | 20 minutes |
| **Total** | **120 minutes** |

---

## Session Objectives

The student will:

1. Review the prototype.
2. Identify incomplete features.
3. Implement student management operations.
4. Integrate examination scores.
5. Test database persistence.

---

## 1. Prototype Review — 15 Minutes

Review:

- Application startup
- Database connection
- Student registration
- Student listing
- Input validation
- Existing documentation

### Discussion

Which requirements are already implemented?

Which features remain incomplete?

---

## 2. Finalise Architecture — 15 Minutes

Review the project structure.

Confirm responsibilities for:

- Main application
- Student model
- Student services
- Result services
- Database operations
- Validation functions

### Student Task

Explain the responsibility of each module.

---

## 3. Student CRUD Implementation — 35 Minutes

Implement or complete:

- Register student
- View students
- Find student
- Update student
- Delete student

### Important Requirements

- Unique student IDs
- Parameterised SQL queries
- Validation
- Appropriate error messages

---

## 4. Examination Results Integration — 35 Minutes

Implement:

- Add examination score
- Retrieve student scores
- Calculate average
- Determine Pass or Fail
- Display academic report

### Example

```text
====================================
         ACADEMIC REPORT
====================================

Student ID: 103
Name: Uzoamaka
Course: Software Engineering

Mathematics: 85
English: 78
Physics: 90

Average: 84.33
Status: PASS

====================================
```

---

## 5. Testing and Review — 20 Minutes

Test:

1. Register a student.
2. Retrieve the student.
3. Add examination scores.
4. Calculate an average.
5. Restart the application.
6. Confirm that records persist.

---

# 📝 SESSION 1 ASSIGNMENT

## Complete Core Features

The student must complete:

- Student CRUD
- Examination score recording
- Academic report generation
- Basic input validation
- Database persistence

### Deliverable

A working Student Management System with the core functional requirements implemented.

---

# 🗓️ SESSION 2 — ALGORITHMS, TESTING & DOCUMENTATION

**Duration:** 2 Hours

## Session Breakdown

| Activity | Duration |
|---|---:|
| Assignment Review | 15 minutes |
| Searching and Sorting Integration | 30 minutes |
| Automated Testing | 30 minutes |
| Error Handling and Edge Cases | 20 minutes |
| Documentation Review | 15 minutes |
| Knowledge Check | 10 minutes |
| **Total** | **120 minutes** |

---

## 1. Assignment Review — 15 Minutes

Review:

- Student CRUD
- Database persistence
- Examination results
- Academic reports

---

## 2. Searching and Sorting Integration — 30 Minutes

Implement:

- Linear search
- Sorting by name
- Sorting by score or average

### Discussion

Why might the application use SQL for production-style database retrieval while also implementing searching algorithms for educational purposes?

### Student Task

Explain the difference between:

- Searching in memory
- Querying a database
- Sorting with Python
- Sorting with SQL

---

## 3. Automated Testing — 30 Minutes

Create tests for:

- Average calculation
- Grade determination
- Score validation
- Linear search
- Sorting
- Student registration
- Database operations

### Example

```python
import unittest

def calculate_average(scores):
    if not scores:
        return None

    return sum(scores) / len(scores)


class TestAcademicResults(unittest.TestCase):

    def test_average(self):
        self.assertEqual(
            calculate_average([70, 80, 90]),
            80
        )

    def test_empty_scores(self):
        self.assertIsNone(
            calculate_average([])
        )


if __name__ == "__main__":
    unittest.main()
```

### Running Tests

```bash
python3 -m unittest discover -s tests
```

---

## 4. Error Handling & Edge Cases — 20 Minutes

Test:

- Empty database
- Unknown student ID
- Duplicate student ID
- Negative age
- Invalid score
- Non-numeric input
- Student with no examination scores
- Invalid menu selection
- Missing related records

### Discussion

Why should applications handle unexpected user input?

---

## 5. Documentation Review — 15 Minutes

Review the project README.

### Required Sections

- Project title
- Description
- Features
- Technologies
- Installation
- Running the application
- Usage
- Project structure
- Testing
- Known limitations
- Future improvements

---

## 6. Knowledge Check — 10 Minutes

1. What is integration testing?
2. What is an edge case?
3. Why should database operations be tested?
4. Why should searching and sorting functions be tested?
5. What is the purpose of project documentation?

---

# 📝 SESSION 2 ASSIGNMENT

## Final Testing & Documentation

The student must:

1. Complete remaining features.
2. Run all automated tests.
3. Fix identified defects.
4. Test invalid inputs.
5. Update project documentation.
6. Commit changes to GitHub.
7. Prepare for the final demonstration.

---

# 🗓️ SESSION 3 — FINAL DEMONSTRATION, PRESENTATION & ASSESSMENT

**Duration:** 2 Hours

## Session Breakdown

| Activity | Duration |
|---|---:|
| Final Code Review | 20 minutes |
| Live Application Demonstration | 30 minutes |
| Technical Presentation | 20 minutes |
| Technical Questions | 20 minutes |
| Final Assessment and Feedback | 20 minutes |
| Reflection and Next Steps | 10 minutes |
| **Total** | **120 minutes** |

---

## 1. Final Code Review — 20 Minutes

Review:

- Project structure
- Python syntax
- Classes and objects
- Functions
- Database integration
- Searching and sorting
- Input validation
- Tests
- Documentation

---

## 2. Live Application Demonstration — 30 Minutes

The student must demonstrate:

1. Starting the application.
2. Registering a student.
3. Viewing student records.
4. Searching for a student.
5. Updating student information.
6. Recording examination scores.
7. Generating an academic report.
8. Sorting student records.
9. Deleting a test record.
10. Restarting the application and verifying persistence.

---

## 3. Technical Presentation — 20 Minutes

The student should prepare a short presentation covering:

### Project Introduction

- What is the project?
- What problem does it solve?

### Technology Stack

- Python
- SQLite
- Git
- GitHub

### System Architecture

- Main application
- Models
- Services
- Database
- Algorithms

### Challenges

- Difficult concepts
- Errors encountered
- Debugging techniques

### Lessons Learned

- Programming
- Databases
- Testing
- Software engineering practices

---

## 4. Technical Questions — 20 Minutes

Sample questions:

1. Why did you choose Python?
2. What is OOP?
3. What is a class?
4. What is a database?
5. What is SQLite?
6. What is CRUD?
7. How are student records stored?
8. What is a primary key?
9. What is linear search?
10. What is sorting?
11. Why do we validate input?
12. How did you test the application?
13. What happens when an invalid student ID is entered?
14. What was the most difficult part of the project?
15. What would you improve with more time?

---

## 5. Final Assessment & Feedback — 20 Minutes

Evaluate the student using the capstone assessment rubric.

Provide feedback on:

- Technical understanding
- Code quality
- Independent problem-solving
- Application functionality
- Testing
- Documentation
- Presentation
- Areas for improvement

---

## 6. Reflection & Next Steps — 10 Minutes

Ask the student to reflect on:

1. What have I learned?
2. Which concepts do I understand best?
3. Which concepts need more practice?
4. Which project am I most proud of?
5. What do I want to learn next?

---

# 📊 FINAL CAPSTONE ASSESSMENT RUBRIC

| Assessment Area | Weight |
|---|---:|
| Functional requirements | 25% |
| Python and OOP implementation | 15% |
| Database integration | 15% |
| Searching and sorting | 10% |
| Testing and error handling | 10% |
| Code quality and organisation | 10% |
| Documentation and GitHub | 5% |
| Technical presentation | 10% |
| **Total** | **100%** |

---

# 🏅 Suggested Performance Classification

| Score | Classification |
|---|---|
| 90–100% | Excellent |
| 80–89% | Very Good |
| 70–79% | Good |
| 60–69% | Satisfactory |
| 50–59% | Developing |
| Below 50% | Needs Improvement |

These are internal programme assessment categories, not university degree classifications.

---

# 📦 FINAL PROGRAMME DELIVERABLES

The student should submit:

1. Completed Student Management System.
2. GitHub repository containing source code.
3. SQLite database schema.
4. Automated tests.
5. Software Requirements Document.
6. System Design Document.
7. Test Plan.
8. Project README.
9. Final project presentation.
10. Personal learning reflection.

---

# 🧠 FINAL PROGRAMME KNOWLEDGE CHECK

## Developer Tools

1. What is VS Code?
2. What is Git?
3. What is GitHub?
4. What is a repository?
5. What is a commit?

## Web Development

6. What is HTML?
7. What is CSS?
8. What is responsive design?
9. What is the difference between frontend and backend development?

## Python Programming

10. What is Python?
11. What is a variable?
12. What is a data type?
13. What is a conditional statement?
14. What is a loop?
15. What is a function?

## Data Structures & OOP

16. What is a list?
17. What is a dictionary?
18. What is a class?
19. What is an object?
20. What is inheritance?

## Algorithms

21. What is an algorithm?
22. What is linear search?
23. What is binary search?
24. What is sorting?
25. What is Big O notation?

## Databases

26. What is SQL?
27. What is SQLite?
28. What is a primary key?
29. What is CRUD?
30. What is a parameterised query?

## Software Engineering

31. What is SDLC?
32. What is a functional requirement?
33. What is software testing?
34. What is debugging?
35. Why is documentation important?

---

# 🎓 EXPECTED PROGRAMME OUTCOMES

Upon successful completion of the programme, the student should have foundational competence in:

### Software Development Tools

- VS Code
- Terminal navigation
- Git
- GitHub

### Frontend Foundations

- HTML
- CSS
- Responsive layouts

### Python Programming

- Variables
- Data types
- Operators
- Conditional statements
- Loops
- Functions
- Modules

### Computer Science Foundations

- Data structures
- Algorithms
- OOP
- Searching
- Sorting
- Basic complexity analysis

### Database Development

- Relational database concepts
- SQL
- SQLite
- CRUD operations
- Python database integration

### Software Engineering Practices

- Requirements analysis
- Software design
- Testing
- Debugging
- Documentation
- Version control
- Technical presentation

---

# 🚀 RECOMMENDED NEXT LEARNING PATH

Following completion of the programme, the student may progress into:

1. Intermediate Python Programming
2. JavaScript Fundamentals
3. React.js Development
4. Next.js Fundamentals
5. Backend Development with FastAPI
6. REST API Development
7. PostgreSQL
8. Advanced Data Structures and Algorithms
9. Software Testing and CI/CD
10. Cloud Computing and Deployment

---

# 🏁 PROGRAMME COMPLETION

Successful completion should be based on:

- Participation in training activities.
- Completion of required assignments.
- Demonstrated understanding of foundational concepts.
- Submission of the final capstone.
- Successful project demonstration.
- Final assessment.

Any certificate or internship-completion letter issued by the training provider should accurately describe the programme, its duration and the work completed.

---

<div align="center">

### 🎓 Congratulations on Completing the Programme!

**Practical Software Engineering Foundation Programme**

**Opsfuxion Technologies Limited**

*Orchestrate Intelligence, Deliver with Precision.*

© 2026 Opsfuxion Technologies Limited. All Rights Reserved.

</div>
