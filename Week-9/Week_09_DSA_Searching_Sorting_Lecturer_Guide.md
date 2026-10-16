# WEEK 9 — DATA STRUCTURES, SEARCHING, SORTING & ALGORITHM COMPLEXITY

**Opsfuxion Technologies Limited**  
*Orchestrate Intelligence, Deliver with Precision.*

**Practical Software Engineering Foundation Programme — COMPLETE LECTURER'S TEACHING MANUAL**  
**Level:** Beginner progressing toward intermediate | **Contact:** Tuesday / Thursday / Saturday, 3 × 120 minutes (6 hours) | **Independent work:** 6–10 hours  
**Learner:** Uzoamaka | **Instructor edition:** contains solutions, assessment guidance and answer keys.

> **Teaching rule:** Explain → demonstrate → ask learner to predict → learner codes → test success and failure → discuss → commit. Never reveal a model answer until after a genuine independent attempt. A six-hour week is an introduction, not mastery of the entire subject.

**Prerequisites:** Week 8 OOP, Week 6 loops/collections, Week 5 pseudocode and flowcharts  
**End-of-week deliverable:** A Student Search & Sorting Toolkit with measured comparisons and written Big-O explanations.

## Instructor preparation

1. Verify `python3 --version`, VS Code, integrated terminal and Git are working; use Python 3.11+ syntax without third-party dependencies unless noted.
2. Create `Week-09/session-1`, `session-2`, `session-3`, `assignment`, `project`, `tests`, and `README.md`.
3. Prepare a starter file and a separate instructor-only solution file. Save terminal output/screenshots for review.
4. Check understanding through verbal explanation, not merely working code. Have the learner predict at least one output before executing each example.
5. Require meaningful Git commits at the end of each session, using the Week 3 workflow.

## Marking framework (100 points)

| Dimension | Points | What good looks like |
|---|---:|---|
| Correctness and requirements | 35 | Meets acceptance criteria; handles normal cases |
| Concepts and design | 20 | Correctly uses the week's main ideas |
| Input validation and edge cases | 15 | Handles bad, empty, boundary input |
| Code clarity and decomposition | 15 | Clear names, manageable functions, readable formatting |
| Tests and evidence | 10 | Reproducible test cases and expected results |
| Git and documentation | 5 | README, meaningful commits, runnable instructions |

**Mastery thresholds:** 85–100 excellent; 70–84 competent; 55–69 needs targeted practice; below 55 reteach before advancing. Ask the learner to explain *why* their approach works.

---

# SESSION 1 — ABSTRACT DATA TYPES, STACKS, QUEUES & LINEAR SEARCH (120 MIN)

| Minutes | Activity |
|---|---|
| 0–15 | Review Week 8 registry and lists |
| 15–35 | Data structure vs algorithm; operation costs |
| 35–60 | Stack: LIFO and list implementation |
| 60–80 | Queue: FIFO and `deque` |
| 80–105 | Linear search code-along and trace table |
| 105–120 | Practice, exit ticket and commit |

## 1.1 Mental models

**Data structure:** arrangement of data that supports particular operations. **Algorithm:** repeatable finite steps for solving a problem. **Abstract data type:** behaviour/interface independent of implementation. Choose structures by required operations, not popularity.

| Structure | Analogy | Core operations | Python choice |
|---|---|---|---|
| List | Ordered shelf | index, append, insert | `list` |
| Stack | Stack of plates | push, pop last | `list.append`, `list.pop` |
| Queue | Ticket line | enqueue, dequeue first | `collections.deque` |
| Dictionary | Phone directory | key lookup/update | `dict` |
| Set | Unique guest list | membership, uniqueness | `set` |

## 1.2 Stack: last in, first out (LIFO)

```python
undo_stack = []
undo_stack.append("typed A")
undo_stack.append("typed B")
print(undo_stack.pop())  # typed B
print(undo_stack.pop())  # typed A
```

**Trace:** push A → [A]; push B → [A,B]; pop → returns B, leaves [A]. `pop()` on empty list raises `IndexError`; check first.

**Student practice:** Simulate browser back history. **Solution:**

```python
history = []
def visit(page):
    history.append(page)
def back():
    if len(history) < 2:
        return None
    history.pop()
    return history[-1]
visit("home"); visit("courses"); visit("profile")
assert back() == "courses"
```

## 1.3 Queue: first in, first out (FIFO)

```python
from collections import deque
requests = deque()
requests.append("Ada")
requests.append("Chika")
print(requests.popleft())  # Ada
```

**Explain:** `list.pop(0)` shifts later elements and is typically O(n); `deque.popleft()` is O(1) at either end. `deque` is in Python's standard library.

**Student practice:** Ticket queue, reject processing an empty queue. **Solution:**

```python
from collections import deque
queue = deque(["T001", "T002"])
def next_ticket():
    return queue.popleft() if queue else None
assert next_ticket() == "T001"
assert next_ticket() == "T002"
assert next_ticket() is None
```

## 1.4 Linear search

**Problem:** Find a student ID in an unsorted list. Check each item until a match or end.

```text
ALGORITHM LinearSearch(items, target)
    FOR index FROM 0 TO LENGTH(items)-1
        IF items[index] = target THEN RETURN index
    END FOR
    RETURN -1
END
```

```python
def linear_search(items, target):
    for index, item in enumerate(items):
        if item == target:
            return index
    return -1

assert linear_search(["S3", "S1", "S2"], "S1") == 1
assert linear_search([], "S1") == -1
```

| Iteration | Index | Item | Target | Result |
|---|---:|---|---|---|
| 1 | 0 | S3 | S1 | Continue |
| 2 | 1 | S1 | S1 | Return 1 |

**Complexity:** best O(1), worst O(n), extra space O(1). The O notation describes growth, not precise seconds. Explain why early exit helps typical cases but does not improve worst-case complexity.

### Independent exercise

Write a case-insensitive search for a student's name, returning all matching indices rather than only the first. **Solution:**

```python
def find_all_names(names, target):
    return [i for i, name in enumerate(names)
            if name.casefold() == target.casefold()]
assert find_all_names(["Ada", "Chika", "ADA"], "ada") == [0, 2]
```

**Homework:** Diagram a stack, queue and linear search with four items. Write a 150-word explanation of why queue and stack order differ.

---
# SESSION 2 — BINARY SEARCH, SORTING & BIG-O (120 MIN)

| Minutes | Activity |
|---|---|
| 0–15 | Quiz on LIFO, FIFO and search |
| 15–45 | Binary search with paper cards |
| 45–70 | Bubble sort with trace table |
| 70–90 | Selection sort and built-in `sorted` |
| 90–110 | Big-O reasoning and comparisons |
| 110–120 | Exercise review and commit |

## 2.1 Binary search: sorted data required

**Say:** “Imagine looking for a word in a dictionary. You do not start on page one. You split the remaining range approximately in half.” Binary search is correct only when items are sorted according to the same comparison rule.

```python
def binary_search(items, target):
    low, high = 0, len(items) - 1
    while low <= high:
        middle = (low + high) // 2
        if items[middle] == target:
            return middle
        if items[middle] < target:
            low = middle + 1
        else:
            high = middle - 1
    return -1

assert binary_search([2, 5, 8, 11, 15], 11) == 3
assert binary_search([2, 5, 8], 9) == -1
```

**Trace for 11:** low=0, high=4, middle=2→8 (too small); low=3, high=4, middle=3→11 (found). **Time:** O(log n); **iterative extra space:** O(1). If data is unsorted, sort first (often O(n log n)) or use linear search. Explain that index refers to the *sorted list*, not the original unsorted order.

### Binary search debugging challenge

Student is given `while low < high:` and misses single-item ranges. Ask for failing input `[7]`, target `7`; fix to `low <= high`. Also test empty list, first, last, absent.

## 2.2 Bubble sort

```python
def bubble_sort(values):
    items = values.copy()  # do not mutate caller's list
    n = len(items)
    for end in range(n - 1, 0, -1):
        swapped = False
        for i in range(end):
            if items[i] > items[i + 1]:
                items[i], items[i + 1] = items[i + 1], items[i]
                swapped = True
        if not swapped:
            break
    return items

assert bubble_sort([5, 1, 4, 2]) == [1, 2, 4, 5]
```

**Dry run:** [5,1,4,2] → swap 5/1 → [1,5,4,2] → swap 5/4 → [1,4,5,2] → swap 5/2 → [1,4,2,5]; next pass swaps 4/2 → [1,2,4,5]. Worst O(n²), best O(n) with early-stop flag, auxiliary O(n) here because we copy input (in-place core uses O(1)).

## 2.3 Selection sort

```python
def selection_sort(values):
    items = values.copy()
    for i in range(len(items)):
        smallest = i
        for j in range(i + 1, len(items)):
            if items[j] < items[smallest]:
                smallest = j
        items[i], items[smallest] = items[smallest], items[i]
    return items

assert selection_sort([4, 2, 3, 1]) == [1, 2, 3, 4]
```

**Explain:** Find smallest remaining item and move it into place; time O(n²) even for sorted data, because comparisons continue. Python's built-in `sorted()` uses an efficient stable sorting algorithm; prefer it in real applications unless implementing algorithms for learning.

## 2.4 Big-O from first principles

| Operation | Typical / worst time | Reason |
|---|---|---|
| `list[i]` | O(1) | Direct indexed access |
| List membership `x in list` | O(n) | May scan all items |
| `dict[key]` | O(1) average | Hash table; worst-case caveats |
| Stack push/pop at end | O(1) amortised | End of dynamic array |
| Queue `deque.popleft()` | O(1) | Efficient end operation |
| Linear search | O(n) | Potentially inspect all n |
| Binary search | O(log n) | Halves remaining range |
| Bubble/selection sort | O(n²) worst | Nested passes/comparisons |
| Python `sorted()` | O(n log n) worst | Production sorting implementation |

**Important:** Distinguish time complexity from memory complexity, best/average/worst cases, and asymptotic analysis from measured wall-clock time. Ask why 1,000,000 items require roughly 20 halving decisions: 2²⁰ ≈ 1,048,576.

### Practice questions + solutions

1. Does binary search work on `[9,2,5]`? **No**, not reliably; sort first.
2. Is O(n²) always slower than O(n log n) for every small input? **No**, constants and input sizes matter.
3. How many comparisons in linear search worst case for 7 items? **7**.
4. Why copy in bubble sort? **Avoid modifying caller's list**; costs O(n) memory.
5. If we need all matching names, can a first-match binary search directly solve it? **No**; extend search around match or use another approach.

**Homework:** Implement descending selection sort; **solution change** `if items[j] > items[largest]: largest=j` and corresponding variable names. Compare against `sorted(values, reverse=True)`.

---
# SESSION 3 — CAPSTONE: STUDENT SEARCH & SORTING TOOLKIT (120 MIN)

| Minutes | Activity |
|---|---|
| 0–20 | Design records and search requirements |
| 20–50 | Implement and explain search functions |
| 50–75 | Implement sorting strategies |
| 75–95 | Integrate CLI and test |
| 95–110 | Measure, interpret and document |
| 110–120 | Demo, feedback and commit |

## 3.1 Requirements

Represent students as dictionaries containing `id`, `name`, `score`. Provide: search by ID; filter by name fragment; sort by score ascending/descending; search sorted numeric IDs using binary search; reject duplicate IDs; report missing items. Do not use SQLite yet (Week 10).

## 3.2 Complete instructor solution (`student_toolkit.py`)

```python
STUDENTS = [
    {"id": 103, "name": "Ada", "score": 82},
    {"id": 101, "name": "Chika", "score": 91},
    {"id": 104, "name": "Ngozi", "score": 73},
    {"id": 102, "name": "Tobi", "score": 91},
]


def find_by_id_linear(students, student_id):
    for student in students:
        if student["id"] == student_id:
            return student
    return None


def filter_by_name(students, fragment):
    query = fragment.casefold().strip()
    return [s for s in students if query in s["name"].casefold()]


def sort_by_score(students, descending=False):
    # Tie-break by ID for deterministic ordering
    return sorted(students,
                  key=lambda s: (-s["score"] if descending else s["score"], s["id"]))


def find_by_id_binary(students, student_id):
    ordered = sorted(students, key=lambda s: s["id"])
    low, high = 0, len(ordered) - 1
    while low <= high:
        mid = (low + high) // 2
        current = ordered[mid]["id"]
        if current == student_id:
            return ordered[mid]
        if current < student_id:
            low = mid + 1
        else:
            high = mid - 1
    return None


def main():
    while True:
        print("\n1 Search ID  2 Search name  3 Score ranking  4 Exit")
        option = input("Choose: ").strip()
        if option == "1":
            try:
                identifier = int(input("Student ID: "))
            except ValueError:
                print("ID must be a number")
                continue
            print(find_by_id_linear(STUDENTS, identifier) or "Not found")
        elif option == "2":
            print(filter_by_name(STUDENTS, input("Name fragment: ")))
        elif option == "3":
            for student in sort_by_score(STUDENTS, descending=True):
                print(student)
        elif option == "4":
            break
        else:
            print("Choose 1–4")


if __name__ == "__main__":
    main()
```

**Engineering nuance:** `find_by_id_binary` sorts every time, so the *whole operation* is O(n log n), not O(log n). Binary search itself is O(log n) **after** a sorted list already exists. Have student explain why dictionary indexing by ID is often better for repeated lookups.

## 3.3 Automated tests (`test_student_toolkit.py`)

```python
import unittest
from student_toolkit import (
    STUDENTS, find_by_id_linear, find_by_id_binary,
    filter_by_name, sort_by_score
)

class ToolkitTests(unittest.TestCase):
    def test_found_and_missing(self):
        self.assertEqual(find_by_id_linear(STUDENTS, 101)["name"], "Chika")
        self.assertIsNone(find_by_id_linear(STUDENTS, 999))

    def test_binary_search(self):
        self.assertEqual(find_by_id_binary(STUDENTS, 104)["name"], "Ngozi")
        self.assertIsNone(find_by_id_binary([], 1))

    def test_sort_and_filter(self):
        self.assertEqual(sort_by_score(STUDENTS, True)[0]["id"], 101)
        self.assertEqual(filter_by_name(STUDENTS, "AD")[0]["name"], "Ada")

if __name__ == "__main__":
    unittest.main()
```

## 3.4 Optional measurement lab

```python
from time import perf_counter
from student_toolkit import find_by_id_linear

records = [{"id": i} for i in range(100_000)]
start = perf_counter()
result = find_by_id_linear(records, 99_999)
seconds = perf_counter() - start
print(result, f"{seconds:.6f}s")
```

**Warn:** One measurement is noisy and not a rigorous benchmark. Repeat trials, warm up, vary sizes and compare equivalent operations. Avoid claiming empirical results without running them.

## 3.5 Student assignment and model answer

**Task:** Implement recursive factorial with base case and input validation; demonstrate call stack for `factorial(4)`. **Solution:**

```python
def factorial(n):
    if not isinstance(n, int) or n < 0:
        raise ValueError("n must be a non-negative integer")
    if n <= 1:
        return 1
    return n * factorial(n - 1)

assert factorial(0) == 1
assert factorial(4) == 24
```

**Trace:** `factorial(4)` → 4×factorial(3) → 4×3×factorial(2) → 4×3×2×factorial(1) → 24. **Complexity:** O(n) time and O(n) call-stack space; recursion is not automatically faster.

**Extension:** Implement bubble sort on student scores without calling `sorted`; compare to `sort_by_score`. Ensure stable tie policy is documented.

## 3.6 Final quiz with answers

1. LIFO structure? **Stack**.
2. FIFO structure? **Queue**.
3. Why `deque` for queue? **Efficient front removal**.
4. Precondition for binary search? **Sorted comparable data**.
5. Linear search worst-case? **O(n)**.
6. Binary search worst-case (already sorted)? **O(log n)**.
7. Bubble sort worst-case? **O(n²)**.
8. What is a base case? **Condition ending recursion**.
9. Why deterministic tie-break? **Predictable output and reproducible tests**.
10. Is `sorted` forbidden in real apps? **No; normally preferred**.

**Completion checklist:** Student can trace searches on paper; can implement at least one sort without copying; tests absent/present/first/last/duplicates; can explain Big-O in plain language; submits code, README and test evidence.
