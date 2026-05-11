# Unit 2: Testing Techniques — Notes Index

## How to Use These Notes

Read Chapter 1 and 2 first (black box and white box techniques) — they are the bulk of this unit. Chapter 3 gives you the comparison vocabulary. Chapters 4 and 5 cover mutation testing, regression, and JUnit which are more focused topics.

---

## Reading Order

| File | Topic | Covers QB Questions |
|------|-------|---------------------|
| [mental-model.md](../mental-model.md) | Topic groupings + study guide | All |
| [01-black-box-testing.md](./01-black-box-testing.md) | ECP, BVA, Decision Table, Cause-Effect Graphing, State Transition | Q2, Q4, Q5, Q6, Q8, Q11, Q14, Q19, Q24, Q29, Q30, Q31, Q32 |
| [02-white-box-testing.md](./02-white-box-testing.md) | CFG, Cyclomatic complexity, coverage criteria, data flow, loop testing | Q7, Q9, Q17, Q18, Q20, Q21, Q23, Q25 |
| [03-blackbox-vs-whitebox.md](./03-blackbox-vs-whitebox.md) | Comparison of BB / WB / Gray box, static vs dynamic, experience-based | Q3, Q8, Q16, Q18 |
| [04-mutation-testing.md](./04-mutation-testing.md) | Mutants, mutation operators, mutation score, equivalent mutants | Q22, Q33, Q34 |
| [05-regression-and-junit.md](./05-regression-and-junit.md) | Re-testing vs regression, JUnit annotations, writing test cases | Q12, Q13, Q26, Q27, Q28 |

---

## Syllabus Coverage Checklist

- [x] Structural testing
- [x] Black box approach — Random testing
- [x] Black box approach — Equivalence Class Partitioning
- [x] Black box approach — Boundary Value Analysis
- [x] Black box approach — Cause-Effect Graphing
- [x] Black box approach — State Transition Testing
- [x] White box approach — Test adequacy criteria
- [x] White box approach — Code coverage and Control Flow Graphs
- [x] White box approach — Paths
- [x] White box approach — Data flow testing
- [x] White box approach — Loop testing
- [x] Mutation testing
- [x] Writing JUnit tests

---

## Key Diagrams to Draw in Exam

1. **Control Flow Graph** — draw nodes for each statement block, edges for branches, label each node; show entry and exit
2. **ECP Table** — columns: Class, Description, Representative Value, Expected Result
3. **BVA Table** — columns: Boundary, Values (min-1, min, min+1, max-1, max, max+1), Expected
4. **Decision Table** — rows = conditions + actions, columns = rules (all combinations)
5. **State Transition Diagram** — states as circles, transitions as arrows labelled with event/action
6. **Cause-Effect Graph** — causes on left, effects on right, logical connectors in between
7. **Black Box vs White Box comparison table** — at least 6 rows of comparison

---

## Quick-Revision Cheat Sheet

### ECP in 3 Steps
1. Identify all input conditions (rules, ranges)
2. Create valid and invalid equivalence classes for each
3. Write one test case per class

### BVA in 3 Steps
1. Find all boundaries (lower and upper)
2. For each boundary, test: boundary−1, boundary, boundary+1
3. Total test cases = 2 × (number of boundaries) × 3

### Decision Table Structure
```
            Rule 1  Rule 2  Rule 3  ...
Condition 1   Y       Y       N
Condition 2   Y       N       Y
Action 1      ✓       ✗       ✗
Action 2      ✗       ✓       ✓
```
For N binary conditions → maximum 2^N rules

### Cyclomatic Complexity
```
V(G) = E - N + 2P    (E = edges, N = nodes, P = components)
V(G) = number of decision points + 1    (shortcut)
```
= minimum number of independent test paths needed

### Code Coverage Levels (weakest → strongest)
1. Statement coverage — every line executed
2. Branch coverage — every true/false branch taken
3. Condition coverage — every sub-condition true and false
4. Decision-Condition coverage — both branch + condition
5. Path coverage — every distinct path (often infeasible for loops)

### Data Flow Testing Terms
- **def:** Variable assigned a value
- **use:** Variable's value is read
- **def-use path:** Path from definition to use
- **def without use:** Wasted computation (potential logic error)
- **use before def:** Undefined behaviour (runtime error)

### Loop Testing — Required Test Cases
For `for (i = 0; i < N; i++)`:
- 0 iterations (skip loop entirely)
- 1 iteration
- 2 iterations
- Typical middle value
- N−1 iterations
- N iterations (maximum)

### Mutation Testing
```
Mutation Score = Killed / (Total − Equivalent) × 100%
```
- ≥90% = mutation adequate
- Surviving mutants → add test cases targeting those conditions
- Equivalent mutants = different code, same behaviour → can never be killed

### Re-testing vs Regression Testing
| | Re-testing | Regression Testing |
|-|-----------|-------------------|
| Purpose | Confirm fix worked | Catch new breakage |
| Scope | One test case | Full test suite |
| Trigger | Defect marked Fixed | Any code change |

### JUnit Key Annotations
| Annotation | Runs |
|-----------|------|
| `@BeforeClass` | Once before all tests |
| `@Before` | Before each test |
| `@Test` | The test itself |
| `@After` | After each test |
| `@AfterClass` | Once after all tests |

### Black Box vs White Box
| | Black Box | White Box |
|-|-----------|-----------|
| Knowledge | Spec only | Source code |
| Tests | Functional behaviour | Code structure |
| Finds | Missing features, wrong outputs | Dead code, logic errors |
| Level | System, Acceptance | Unit |
