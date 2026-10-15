
# 🧠 WEEK 9 — DATA STRUCTURES & ALGORITHMS (DSA)

<div align="center">

![Python](https://img.shields.io/badge/Python-DSA-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Algorithms](https://img.shields.io/badge/Algorithms-Searching_%26_Sorting-7C3AED?style=for-the-badge)
![Level](https://img.shields.io/badge/Level-Beginner-16A085?style=for-the-badge)
![Project](https://img.shields.io/badge/Project-Search_%26_Sort-D4A43A?style=for-the-badge)

**Practical Software Engineering Foundation Programme**

**Training Provider:** Opsfuxion Technologies Limited

*Orchestrate Intelligence, Deliver with Precision.*

</div>

---

## 📋 Programme Information

| Item | Details |
|---|---|
| Module | Week 9 — Data Structures & Algorithms |
| Duration | 1 Week |
| Sessions | 3 instructor-led sessions |
| Session Duration | 2 Hours |
| Total Contact Hours | 6 Hours |
| Level | Beginner |
| Prerequisites | Weeks 4–8 |
| Primary Language | Python 3 |
| Weekly Project | Student Record Search & Sorting Tool |
| Learning Approach | Algorithm design, tracing, implementation, testing and analysis |

---

# 📖 Week Overview

In Week 6, the student learned how to use Python collections such as lists, tuples, dictionaries and sets.

In Week 8, the student learned how to organise data and behaviour using classes and objects.

Week 9 introduces Data Structures and Algorithms from a computer science perspective.

The student will explore how information can be organised, accessed, searched and sorted.

The module also introduces basic algorithm efficiency and the idea that different solutions to the same problem may require different amounts of work.

The emphasis is on understanding algorithms through diagrams, manual tracing, practical coding exercises and small projects.

---

# 🎯 Learning Objectives

By the end of Week 9, the student should be able to:

- Explain what a data structure is.
- Explain what an algorithm is.
- Differentiate between data structures and algorithms.
- Understand abstract data types.
- Explain stacks and queues.
- Implement a basic stack using a Python list.
- Implement a basic queue using `collections.deque`.
- Understand LIFO and FIFO.
- Explain linear search.
- Implement linear search.
- Explain binary search.
- Implement binary search on sorted data.
- Understand basic sorting algorithms.
- Implement bubble sort.
- Understand selection sort.
- Compare searching approaches.
- Explain recursion at an introductory level.
- Understand base cases.
- Explain the purpose of Big O notation.
- Recognise O(1), O(n), O(log n) and O(n²).
- Trace simple algorithms manually.
- Test searching and sorting functions.
- Apply DSA concepts to student records.

---

# 🗓️ SESSION 1 — DATA STRUCTURES, STACKS & QUEUES

**Duration:** 2 Hours

## Session Breakdown

| Activity | Duration |
|---|---:|
| Review of Week 8 | 10 minutes |
| Introduction to DSA | 20 minutes |
| Stacks and LIFO | 25 minutes |
| Queues and FIFO | 25 minutes |
| Guided Practical | 30 minutes |
| Knowledge Check | 10 minutes |
| **Total** | **120 minutes** |

---

## 1. Review of Week 8 — 10 Minutes

Review:

- Classes
- Objects
- Methods
- Student Management System
- Lists of student objects

### Discussion

Suppose the school has 1,000 student records.

How can the system find a particular student efficiently?

How should the system process students waiting in a registration queue?

These questions introduce data structures and algorithms.

---

## 2. Introduction to DSA — 20 Minutes

### What is a Data Structure?

A data structure defines how information is organised and accessed.

### What is an Algorithm?

An algorithm is a finite sequence of instructions used to solve a problem.

### Examples

| Problem | Possible Approach |
|---|---|
| Store student records | List or dictionary |
| Process waiting students | Queue |
| Implement undo operations | Stack |
| Find a student | Searching algorithm |
| Arrange scores | Sorting algorithm |

### Discussion

Why might one data structure be more suitable than another?

---

## 3. Understanding Stacks — 25 Minutes

A stack follows:

**LIFO — Last In, First Out**

The most recently added item is removed first.

### Everyday Example

A stack of plates.

The last plate placed on top is the first plate removed.

### Python Implementation

```python
stack = []

stack.append("Book A")
stack.append("Book B")
stack.append("Book C")

print(stack)

last_item = stack.pop()

print("Removed:", last_item)
print("Remaining:", stack)
```

### Stack Operations

- Push — Add an item
- Pop — Remove the top item
- Peek — View the top item
- Is Empty — Check whether the stack contains items

### Simple Stack Class

```python
class Stack:
    def __init__(self):
        self.items = []

    def push(self, item):
        self.items.append(item)

    def pop(self):
        if not self.items:
            return None

        return self.items.pop()

    def peek(self):
        if not self.items:
            return None

        return self.items[-1]
```

### Discussion

Where might stacks be used in software?

Examples:

- Undo functionality
- Backtracking
- Expression evaluation
- Function call management

---

## 4. Understanding Queues — 25 Minutes

A queue follows:

**FIFO — First In, First Out**

The first item added is the first item removed.

### Everyday Example

People waiting in a bank.

The first person in line is normally served first.

### Python Implementation

```python
from collections import deque

queue = deque()

queue.append("Ada")
queue.append("Chidi")
queue.append("Uzoamaka")

print(queue)

first_student = queue.popleft()

print("Served:", first_student)
```

### Queue Operations

- Enqueue — Add an item
- Dequeue — Remove the first item
- Front — View the first item
- Is Empty — Check whether the queue is empty

### Why Use `deque`?

A `deque` supports efficient removal from the beginning of a queue.

Removing the first item from a Python list using `pop(0)` requires shifting the remaining elements.

---

## 5. Guided Practical — 30 Minutes

### Exercise 1: Student Registration Queue

Create:

`student_queue.py`

### Requirements

1. Create an empty queue.
2. Add at least five student names.
3. Display the waiting queue.
4. Process the first student.
5. Display the remaining queue.
6. Continue until all students have been processed.

### Extension

Create a menu that allows users to:

- Add a student
- Process the next student
- View the queue
- Exit

---

## 6. Knowledge Check — 10 Minutes

1. What is DSA?
2. What is a stack?
3. What does LIFO mean?
4. What is a queue?
5. What does FIFO mean?
6. What is the difference between a stack and a queue?
7. Why might a queue be useful in a school registration system?

---

# 📝 SESSION 1 ASSIGNMENT

## Browser History Simulator

Create:

`browser_history.py`

### Scenario

A web browser keeps track of visited pages.

### Requirements

1. Create a stack.
2. Add visited webpage names.
3. Display the current page.
4. Implement a Back operation.
5. Display the previous page after going back.
6. Handle an empty history safely.

### Deliverable

A working Python application demonstrating stack operations.

---

# 🗓️ SESSION 2 — SEARCHING ALGORITHMS & INTRODUCTORY BIG O

**Duration:** 2 Hours

## Session Breakdown

| Activity | Duration |
|---|---:|
| Assignment Review | 15 minutes |
| Linear Search | 25 minutes |
| Binary Search | 30 minutes |
| Introduction to Big O | 20 minutes |
| Guided Practical | 20 minutes |
| Knowledge Check | 10 minutes |
| **Total** | **120 minutes** |

---

## 1. Assignment Review — 15 Minutes

Review:

- Stack operations
- LIFO
- Handling empty collections
- Correct program behaviour

---

## 2. Linear Search — 25 Minutes

Linear search examines items one after another until the required value is found or the collection ends.

### Example

```python
def linear_search(numbers, target):
    for index, number in enumerate(numbers):
        if number == target:
            return index

    return -1
```

### Usage

```python
numbers = [10, 25, 40, 55, 70]

result = linear_search(numbers, 40)

print("Index:", result)
```

### Discussion

What happens if the target is the last item?

What happens if the target does not exist?

---

## 3. Binary Search — 30 Minutes

Binary search works on sorted data.

It repeatedly divides the search interval into two parts.

### Example

```python
def binary_search(numbers, target):
    left = 0
    right = len(numbers) - 1

    while left <= right:
        middle = (left + right) // 2

        if numbers[middle] == target:
            return middle

        elif numbers[middle] < target:
            left = middle + 1

        else:
            right = middle - 1

    return -1
```

### Usage

```python
numbers = [10, 20, 30, 40, 50, 60, 70]

result = binary_search(numbers, 50)

print("Index:", result)
```

### Important Rule

Binary search requires the data to be sorted according to the same ordering used by the search.

### Guided Discussion

Compare searching for a number in:

- An unsorted list
- A sorted list

---

## 4. Introduction to Big O Notation — 20 Minutes

Big O notation describes how an algorithm's resource usage grows as input size increases.

At this stage, focus on recognising common time-complexity patterns.

### Common Examples

| Complexity | Name | Example |
|---|---|---|
| O(1) | Constant | Accessing a list item by index |
| O(log n) | Logarithmic | Binary search |
| O(n) | Linear | Linear search |
| O(n²) | Quadratic | Basic nested-loop comparison |

### Example: O(1)

```python
numbers = [10, 20, 30]

print(numbers[0])
```

### Example: O(n)

```python
for number in numbers:
    print(number)
```

### Example: O(n²)

```python
for first in numbers:
    for second in numbers:
        print(first, second)
```

### Discussion

Why does algorithm efficiency matter when data becomes large?

---

## 5. Guided Practical — 20 Minutes

### Exercise 2: Student ID Search

Create:

`student_search.py`

### Requirements

1. Store a list of student IDs.
2. Ask for a student ID.
3. Use linear search to locate the ID.
4. Display whether it was found.
5. Display its position when found.
6. Test an ID that does not exist.

### Extension

Create a sorted list of numeric IDs and implement binary search.

---

## 6. Knowledge Check — 10 Minutes

1. What is linear search?
2. What is binary search?
3. Why must binary search use sorted data?
4. What does O(n) mean?
5. What does O(log n) mean?
6. Which search is generally more efficient for large sorted lists?

---

# 📝 SESSION 2 ASSIGNMENT

## Search Algorithm Comparison

Create:

`search_comparison.py`

### Requirements

1. Create a sorted list containing at least 20 numbers.
2. Implement linear search.
3. Implement binary search.
4. Search for the same target using both algorithms.
5. Count the number of comparisons made.
6. Display the results.
7. Explain the difference in the number of comparisons.

### Deliverable

A Python script and a short written comparison.

### Important Note

The number of comparisons depends on the target and data.

The purpose is to observe algorithm behaviour, not to claim that binary search always makes fewer comparisons for every possible input.

---

# 🗓️ SESSION 3 — SORTING, RECURSION & WEEKLY PROJECT

**Duration:** 2 Hours

## Session Breakdown

| Activity | Duration |
|---|---:|
| Assignment Review | 15 minutes |
| Introduction to Sorting | 15 minutes |
| Bubble Sort | 20 minutes |
| Selection Sort | 15 minutes |
| Introduction to Recursion | 15 minutes |
| Weekly Project Development | 30 minutes |
| Project Review | 10 minutes |
| **Total** | **120 minutes** |

---

## 1. Assignment Review — 15 Minutes

Review:

- Linear search
- Binary search
- Comparison counts
- Sorted data
- Basic algorithm efficiency

---

## 2. Introduction to Sorting — 15 Minutes

Sorting arranges information according to a defined order.

Examples:

- Scores from lowest to highest
- Student names alphabetically
- Products by price
- Records by date

### Built-in Sorting

```python
scores = [75, 40, 90, 60]

scores.sort()

print(scores)
```

### Discussion

Why should programmers understand sorting algorithms when Python already provides sorting functions?

Because understanding how algorithms work develops computational thinking and problem-solving skills.

---

## 3. Bubble Sort — 20 Minutes

Bubble sort repeatedly compares adjacent items and swaps them when they are in the wrong order.

### Example

```python
def bubble_sort(numbers):
    result = numbers.copy()
    n = len(result)

    for i in range(n):
        for j in range(0, n - i - 1):
            if result[j] > result[j + 1]:
                result[j], result[j + 1] = (
                    result[j + 1],
                    result[j]
                )

    return result
```

### Usage

```python
scores = [75, 40, 90, 60]

sorted_scores = bubble_sort(scores)

print(sorted_scores)
```

### Discussion

How does the largest number move towards the end of the list?

### Complexity

This basic implementation uses O(n²) comparisons in the worst case.

---

## 4. Selection Sort — 15 Minutes

Selection sort repeatedly finds the smallest remaining value and places it in the correct position.

### Example

```python
def selection_sort(numbers):
    result = numbers.copy()

    for i in range(len(result)):
        min_index = i

        for j in range(i + 1, len(result)):
            if result[j] < result[min_index]:
                min_index = j

        result[i], result[min_index] = (
            result[min_index],
            result[i]
        )

    return result
```

### Usage

```python
numbers = [64, 25, 12, 22, 11]

print(selection_sort(numbers))
```

### Discussion

How is selection sort different from bubble sort?

---

## 5. Introduction to Recursion — 15 Minutes

Recursion occurs when a function calls itself.

A recursive function needs a stopping condition called a **base case**.

### Example

```python
def countdown(number):
    if number == 0:
        print("Done!")
        return

    print(number)
    countdown(number - 1)
```

### Usage

```python
countdown(5)
```

### Discussion

What happens if the base case is missing?

### Important Note

Recursion is introduced conceptually this week.

More advanced recursive algorithms can be explored later.

---

# 🏆 WEEK 9 PROJECT — STUDENT RECORD SEARCH & SORTING TOOL

## Project Description

Develop a Python application that manages a collection of student records and demonstrates searching and sorting algorithms.

The project should build on the Student Management System developed in Week 8.

---

## Functional Requirements

The application must:

1. Store multiple student records.
2. Display all student records.
3. Search for a student using linear search.
4. Sort students by examination score.
5. Sort students alphabetically by name.
6. Display the highest score.
7. Display the lowest score.
8. Handle missing student records.
9. Provide a simple command-line menu.
10. Exit the application safely.

---

## Required Algorithms

The project should include:

- Linear search
- Bubble sort or selection sort
- Basic comparison of algorithm behaviour

### Optional Extension

Implement binary search on a sorted collection of student IDs.

---

## Example Student Data

```python
students = [
    {"id": 101, "name": "Ada", "score": 75},
    {"id": 102, "name": "Chidi", "score": 45},
    {"id": 103, "name": "Uzoamaka", "score": 90},
    {"id": 104, "name": "Emeka", "score": 65},
]
```

---

## Suggested Menu

```text
====================================
     STUDENT SEARCH & SORT TOOL
====================================

1. View Students
2. Search Student
3. Sort by Score
4. Sort by Name
5. Highest Score
6. Lowest Score
7. Exit

Select an option:
```

---

## Suggested Project Structure

```text
Week-09/
│
├── exercises/
│   ├── student_queue.py
│   ├── linear_search.py
│   ├── binary_search.py
│   ├── bubble_sort.py
│   └── selection_sort.py
│
├── assignments/
│   ├── browser_history.py
│   └── search_comparison.py
│
└── projects/
    └── student-search-sort/
        ├── main.py
        ├── searching.py
        ├── sorting.py
        ├── student_data.py
        └── README.md
```

---

# 🧪 Suggested Test Cases

| Test Case | Expected Result |
|---|---|
| Search existing student | Student found |
| Search unknown student | Not found |
| Search empty list | No crash |
| Sort scores ascending | Correct order |
| Sort names alphabetically | Correct order |
| Sort already sorted records | Correct order preserved |
| Sort one record | No error |
| Find highest score | Correct student or score |
| Find lowest score | Correct student or score |
| Exit application | Program terminates |

---

# 🧠 Week 9 Knowledge Check

1. What is a data structure?
2. What is an algorithm?
3. What does DSA stand for?
4. What is an abstract data type?
5. What is a stack?
6. What does LIFO mean?
7. What is a queue?
8. What does FIFO mean?
9. What is linear search?
10. What is binary search?
11. Why must binary search use sorted data?
12. What is sorting?
13. What is bubble sort?
14. What is selection sort?
15. What is recursion?
16. What is a base case?
17. What is Big O notation?
18. What does O(1) represent?
19. What does O(n) represent?
20. What does O(log n) represent?
21. What does O(n²) represent?
22. Why does algorithm efficiency matter?
23. What is the difference between searching and sorting?
24. Why should algorithms be tested with empty collections?
25. How can searching and sorting improve a Student Management System?

---

# 📊 Week 9 Assessment

| Assessment Area | Weight |
|---|---:|
| Understanding DSA concepts | 20% |
| Stacks and queues | 15% |
| Searching algorithms | 20% |
| Sorting algorithms | 20% |
| Introductory complexity analysis | 10% |
| Testing and debugging | 5% |
| Weekly project completion | 10% |
| **Total** | **100%** |

---

# 📦 Week 9 Deliverables

- Student Registration Queue
- Browser History Simulator
- Linear Search Exercise
- Binary Search Exercise
- Search Algorithm Comparison
- Bubble Sort Exercise
- Selection Sort Exercise
- Student Record Search & Sorting Tool
- Week 9 Knowledge Check
- Documented GitHub commits

---

# 🎓 Expected Learning Outcomes

By the end of Week 9, the student should be able to:

- Explain foundational DSA concepts.
- Implement stacks and queues.
- Understand LIFO and FIFO.
- Implement linear search.
- Implement binary search on sorted data.
- Implement simple sorting algorithms.
- Understand recursion conceptually.
- Recognise basic Big O complexity classes.
- Trace and test algorithms.
- Apply searching and sorting to student records.

---

## ⏭️ Next Module

**Week 10 — Databases & SQL**

The student will learn:

- Relational database fundamentals
- Tables, rows and columns
- Primary keys
- SQL queries
- CRUD operations
- SQLite
- Python database integration

The Week 10 project will involve building a Student Records Database.

---

<div align="center">

### 🚀 Think Logically. Build Systematically. Improve Continuously.

**Opsfuxion Technologies Limited**

*Orchestrate Intelligence, Deliver with Precision.*

© 2026 Opsfuxion Technologies Limited.

</div>
