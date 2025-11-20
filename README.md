# Project 2 – Verification with Permissions (Progress Tracker)

**Course:** DTU – Program Verification  
**Project:** Project 2 – Verification with Permissions  
**Deadline:** December 5, 2025

---

## 👥 Team

- Matthew Asano (s225134)  
- Lawrence Ryan (s225243)  
- Mathias Spezia (s225115)

---

## 📊 Progress Summary

| Metric                                  | Current | Target         | Status |
|-----------------------------------------|---------|----------------|--------|
| **Total stars verified**                | `TBD`   | 30★ (max)      | ⬜     |
| **Stars needed for target grade**       | `TBD`   | e.g. 27★ (12)  | ⬜     |
| **Challenges with full functional proof** | `TBD/4` | 4/4           | ⬜     |
| **Challenges with time-credit proofs**  | `TBD/4` | 4/4            | ⬜     |
| **Files verifying with Silicon**        | `TBD/4` | 4/4            | ⬜     |
| **Files verifying with Carbon**         | `TBD/4` | 4/4            | ⬜     |

> Use ✅ / ⚠️ / ⬜ in the Status column as you update progress.

---

## ⭐ Challenge Overview & Status

| Challenge | File           | Stars | Main Focus                               | Status |
|----------:|----------------|:-----:|------------------------------------------|--------|
| 1         | `fibonacci.vpr`|  ★    | Recursive Fibonacci + tight runtime bound| ⬜     |
| 2         | `fastexp.vpr`  | ★★    | Fast exponentiation + runtime bound      | ⬜     |
| 3         | `dyn_array.vpr`| ★★★★★★ | Dynamic array + amortized analysis       | ⬜     |
| 4         | `bst.vpr`      | ★★★★★★ | BST insert + runtime + set abstraction   | ⬜     |

_Status legend suggestion:_  
- ✅ = Fully verified (both backends, including time credits)  
- ⚠️ = Partially verified / only one backend / missing time credits  
- ⬜ = Not started / no meaningful progress yet

---

## 📌 Challenge 1 – Recursive Fibonacci (★)

**File:** `fibonacci.vpr`  

| Task                                                         | Status |
|--------------------------------------------------------------|--------|
| Define mathematical Fibonacci specification (ghost function) | ⬜     |
| Prove functional correctness (base + recursive case)         | ⬜     |
| Add time-credit precondition and `consume_time_credit()`     | ⬜     |
| Derive runtime upper bound as function of `n`                | ⬜     |
| Argue tightness (smallest upper bound) in comments           | ⬜     |
| Verifies with **Silicon**                                    | ⬜     |
| Verifies with **Carbon**                                     | ⬜     |

---

## ⚡ Challenge 2 – Iterative Fast Exponentiation (★★)

**File:** `fastexp.vpr`  

| Task                                                            | Status |
|-----------------------------------------------------------------|--------|
| Understand / clean up given production code                     | ⬜     |
| Finish loop invariant & prove postcondition (functional)        | ⬜     |
| Add time credits: method entry + per loop iteration             | ⬜     |
| Derive runtime bound (ideally O(log e))                         | ⬜     |
| Document runtime bound in contract / comments                   | ⬜     |
| Verifies with **Silicon**                                       | ⬜     |
| Verifies with **Carbon**                                        | ⬜     |

---

## 🧱 Challenge 3 – Dynamic Arrays & Amortized Analysis

**File:** `dyn_array.vpr`  

### 3.1 – Dynamic Array Predicate (★)

| Task                                                     | Status |
|----------------------------------------------------------|--------|
| Define `dyn_array` predicate (capacity, length, etc.)    | ⬜     |
| Add permissions to underlying static array + fields      | ⬜     |
| Optional: ghost info (contents, saved credits)           | ⬜     |
| Basic fold/unfold lemmas working                         | ⬜     |

### 3.2 – Constructor `cons` (★)

| Task                                                         | Status |
|--------------------------------------------------------------|--------|
| Implement `cons(_capacity: Int) returns (arr: Ref)`          | ⬜     |
| Prove memory safety                                          | ⬜     |
| Prove `length == 0` and `capacity == _capacity`              | ⬜     |
| Show constant number of time credits is sufficient           | ⬜     |
| Verifies with **Silicon**                                    | ⬜     |
| Verifies with **Carbon**                                     | ⬜     |

### 3.3 – Abstraction Function `arr_contents` (★★)

| Task                                                                | Status |
|---------------------------------------------------------------------|--------|
| Define `arr_contents(arr: Ref): Seq[Int]` (or similar)              | ⬜     |
| Connect `arr_contents` to underlying array + length                 | ⬜     |
| Prove basic properties (length, element access)                     | ⬜     |
| Document intended invariants for later tasks                        | ⬜     |

### 3.4 – `append_nogrow` (★★★)

| Task                                                                      | Status |
|---------------------------------------------------------------------------|--------|
| Specify preconditions (array not full)                                    | ⬜     |
| Prove memory safety + predicate preservation                              | ⬜     |
| Show constant time (constant time-credit precondition)                    | ⬜     |
| Prove `arr_contents(after) == arr_contents(before) ++ Seq(val)`           | ⬜     |
| Store extra time credits per appended element (for amortized analysis)    | ⬜     |
| Verifies with **Silicon**                                                 | ⬜     |
| Verifies with **Carbon**                                                  | ⬜     |

### 3.5 – `grow` (★★★★)

| Task                                                                      | Status |
|---------------------------------------------------------------------------|--------|
| Implement allocation of new array with doubled capacity                   | ⬜     |
| Copy elements from old to new array                                       | ⬜     |
| Prove memory safety + dynamic array predicate on result                   | ⬜     |
| Prove `capacity_after == 2 * capacity_before`                             | ⬜     |
| Prove `arr_contents` preserved                                            | ⬜     |
| Worst-case: allow capacity-dependent time credits                         | ⬜     |
| Amortized: use only constant credits in precondition + saved credits      | ⬜     |
| Verifies with **Silicon**                                                 | ⬜     |
| Verifies with **Carbon**                                                  | ⬜     |

### 3.6 – `append` (★★★★)

| Task                                                                      | Status |
|---------------------------------------------------------------------------|--------|
| Implement `append` using `append_nogrow` + `grow`                         | ⬜     |
| Prove memory safety                                                       | ⬜     |
| Prove `arr_contents(after) == arr_contents(before) ++ Seq(val)`           | ⬜     |
| Show **amortized constant time** using time credits + banker's method     | ⬜     |
| Verifies with **Silicon**                                                 | ⬜     |
| Verifies with **Carbon**                                                  | ⬜     |

---

## 🌳 Challenge 4 – Binary Search Trees

**File:** `bst.vpr`  

### 4.1 – `bst` Predicate (★★★)

| Task                                                 | Status |
|------------------------------------------------------|--------|
| Define `bst(self: Ref)` predicate                    | ⬜     |
| Encode structural + ordering invariants              | ⬜     |
| Add ghost abstraction (set/seq of stored values)     | ⬜     |
| Optional: ghost height function for runtime proofs   | ⬜     |

### 4.2 – `bst_insert` Implementation (★★★★)

| Task                                                                | Status |
|---------------------------------------------------------------------|--------|
| Implement standard BST insertion (`<`, `>`, no duplicates)          | ⬜     |
| Prove memory safety                                                 | ⬜     |
| Prove BST property is preserved                                     | ⬜     |
| Ensure behaviour is faithful (no “cheating” implementations)        | ⬜     |
| Verifies with **Silicon**                                           | ⬜     |
| Verifies with **Carbon**                                            | ⬜     |

### 4.3 – Time-Credit Runtime Bound (★★)

| Task                                                              | Status |
|-------------------------------------------------------------------|--------|
| Add `consume_time_credit()` at entry + per step                   | ⬜     |
| Relate required credits to tree height `h`                        | ⬜     |
| Prove upper bound `h + c` for some constant `c`                   | ⬜     |
| Comment on balanced case: `h = O(log n)`                          | ⬜     |

### 4.4 – Value-Set Equivalence (★★★)

| Task                                                                          | Status |
|-------------------------------------------------------------------------------|--------|
| Define `bst_values(tree): Set[Int]` (or similar)                              | ⬜     |
| Prove structural lemmas for inserting in left/right subtrees                  | ⬜     |
| Show `bst_values(after) == bst_values(before) ∪ {val}` (if `val` absent)      | ⬜     |
| Show `bst_values(after) == bst_values(before)` (if `val` already present)     | ⬜     |

---

## ⚠️ Known Issues / Open Items

> Use this as a scratchpad for problems you hit.

- ⬜ **Silicon** times out on: `dyn_array.vpr` (task 3.x)  
  _Notes: …_
- ⬜ **Carbon** fails due to triggers / quantifiers in: `bst.vpr`  
  _Notes: …_
- ⬜ Time-credit invariant for `append` not strong enough  
  _Notes: …_

---

## 🗓 Milestones (Fill as You Go)

| Date       | Milestone / Goal                                  | Status |
|------------|---------------------------------------------------|--------|
| 2025-11-xx | Finish Challenge 1 (Fibonacci)                    | ⬜     |
| 2025-11-xx | Fast exponentiation fully verified                | ⬜     |
| 2025-11-xx | `dyn_array.vpr`: 3.1–3.4 done                     | ⬜     |
| 2025-11-xx | `dyn_array.vpr`: amortized proof for `append`     | ⬜     |
| 2025-11-xx | `bst_insert` functionally correct + runtime bound | ⬜     |
| 2025-11-xx | All files pass on **Silicon** and **Carbon**      | ⬜     |

> Update dates + statuses as you progress (✅ / ⚠️ / ⬜).

---
