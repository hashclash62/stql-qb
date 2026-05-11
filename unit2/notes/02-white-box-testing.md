# Chapter 2: White Box Testing Techniques

---

## What is White Box Testing?

Imagine you're testing a recipe, and this time you *can* see the recipe card. You can look at every step, every ingredient, and design tests to verify that every single instruction is executed correctly under different conditions.

That's white box testing. You design tests based on the **internal structure of the code** — the logic, branches, loops, and data flows. The goal is to make sure every part of the code is exercised.

**When to use:** Unit testing, security testing, optimisation validation — anywhere you have access to the source code and want structural coverage guarantees.

---

## Control Flow Graph (CFG)

### What It Is
A **Control Flow Graph (CFG)** is a visual representation of a program's execution flow. Every statement or group of sequential statements becomes a **node**, and every possible transfer of control (branch, loop, function call return) becomes an **edge**.

### Building a CFG

**Rules:**
- Sequential statements with no branches → single node
- Every decision (if, while, for, switch) → splits into two edges
- Each edge represents a possible path from one node to another
- The graph starts at an **entry node** and ends at an **exit node**

### Example: Simple `if-else`

```python
if (x > 0):        # Node 1: decision
    y = x * 2      # Node 2: true branch
else:
    y = -x         # Node 3: false branch
print(y)           # Node 4: merge point
```

CFG:
```
    [1: x > 0?]
    /          \
[2: y=x*2]  [3: y=-x]
    \          /
    [4: print(y)]
```

---

## Cyclomatic Complexity (Q20)

### What It Is
**Cyclomatic complexity (V(G))** is a quantitative measure of the number of linearly independent paths through a program. Developed by Thomas McCabe.

### Formula

$$V(G) = E - N + 2P$$

Where:
- **E** = number of edges in the CFG
- **N** = number of nodes in the CFG
- **P** = number of connected components (usually 1 for a single program/function)

**Simplified for a single function:** `V(G) = number of decision points + 1`

A decision point is any `if`, `while`, `for`, `case`, `&&`, `||` in the code.

### What Cyclomatic Complexity Means

| V(G) | Interpretation |
|------|---------------|
| 1–10 | Simple, low risk, easy to test |
| 11–20 | Moderate complexity |
| 21–50 | High complexity, difficult to test |
| 51+ | Very high risk, consider refactoring |

### How It Guides Testing
Cyclomatic complexity gives the **minimum number of test cases** needed to achieve full branch coverage. If V(G) = 5, you need at least 5 test cases to cover all independent paths.

**Testability:** Higher V(G) = harder to test, more likely to have defects, more maintenance effort.

### Worked Example: `foo()` from Q20

```
Module foo()
  Read(x)                      -- Node 1
  While(i < x) do begin        -- Node 2 (decision)
    a[i] = b[i] * x            -- Node 3
    if a[i] > 50 then          -- Node 4 (decision)
      Print("over limit")      -- Node 5
    else
      Print("OK")              -- Node 6
    i = i + 1                  -- Node 7
  End
  Print("end of nonsense")     -- Node 8 (exit)
```

Decision points: `while` condition + `if` condition = **2 decisions**

V(G) = 2 + 1 = **3**

Minimum 3 test cases needed:
1. Loop never executes (i >= x from the start)
2. Loop executes, `a[i] <= 50` (prints "OK")
3. Loop executes, `a[i] > 50` (prints "over limit")

---

## Code Coverage Criteria

### Statement Coverage
Every **executable statement** in the code must be executed at least once.

*Weakness:* You can have 100% statement coverage and still miss a false branch of an if-statement that has no else clause.

### Branch Coverage (Decision Coverage)
Every **branch** (true/false outcome) of every decision must be executed at least once.

*Stronger than statement coverage.* If `if (x > 0)` exists in the code, you need at least one test where it's true and one where it's false.

### Condition Coverage
Every **individual boolean sub-expression** in a compound condition must be tested as both true and false.

*Example for Q17:* `if (age < 65 and married == true)`

- C1: `age < 65`
- C2: `married == true`

Condition coverage requires:
- C1 = true, C2 = true
- C1 = true, C2 = false
- C1 = false, C2 = true
- C1 = false, C2 = false

### Decision-Condition Coverage
Both branch coverage AND condition coverage must be satisfied.

### MC/DC (Modified Condition/Decision Coverage)
Each condition must **independently affect** the decision outcome. Used in safety-critical systems (aviation software — DO-178C standard).

### Q17: Choosing Coverage Criteria for `if (age < 65 and married == true)`

| Coverage Type | Test Cases Needed | What is tested |
|--------------|-------------------|----------------|
| Simple decision coverage | 2 (whole condition true + false) | Branch outcomes |
| Condition coverage | 4 (all combos of C1 and C2) | Each sub-condition independently |
| Decision-condition coverage | 4 (satisfies both) | Both branch and sub-conditions |

---

## Data Flow Testing (Q23, Q25)

### The Idea
Data flow testing tracks **how variables are used** through the program. Every variable has:
- **Definition (def):** Where a variable is assigned a value
- **Use (use):** Where a variable's value is read/consumed
  - **c-use (computation use):** Used in a calculation
  - **p-use (predicate use):** Used in a condition (if, while)

A **def-use path** is a path from a definition to a corresponding use.

### Why It Matters
Data flow testing catches bugs like:
- A variable is **defined but never used** (wasted computation, may indicate missing logic)
- A variable is **used without being defined** (undefined behaviour, runtime error)
- A variable is **defined twice without being used** between the definitions (first definition is useless)

### Binary Search Data Flow Example (Q25)

For `binsearch(int x, int v[], int n)`:

Key variables and their def-use paths:

| Variable | Defined at | Used at | Path |
|----------|-----------|---------|------|
| `low` | Line: `low = 0` | `low <= high`, `mid = (low+high)/2`, `low = mid+1` | def → p-use, c-use |
| `high` | Line: `high = n-1` | `low <= high`, `mid = (low+high)/2`, `high = mid-1` | def → p-use, c-use |
| `mid` | Line: `mid = (low+high)/2` | `x < v[mid]`, `x > v[mid]`, `return mid` | def → p-use, c-use |
| `x` | Parameter | `x < v[mid]`, `x > v[mid]` | param → p-use |

**Test cases to cover all def-use paths:**
- TC1: `x` found at first try (mid = answer on first iteration) — covers `return mid`
- TC2: `x` in lower half (high = mid-1) — covers `high` definition in loop
- TC3: `x` in upper half (low = mid+1) — covers `low` definition in loop
- TC4: `x` not in array — covers `return -1`

### Fixing Data Flow Issues (Q23)
When you see:
- **Variable defined but never used:** Possible missing logic (result was computed but never returned or displayed)
- **Variable used before definition:** Initialise all variables before use; add defensive checks

*Prevention strategy:* Use static analysis tools (SonarQube, FindBugs) that detect these patterns automatically during code review.

---

## Loop Testing (Q21)

### Why Loops Need Special Attention
Loops are where many bugs live: off-by-one errors, infinite loops, wrong initialisation. Standard testing might only test the "typical" case. Loop testing defines specific test cases based on iteration count.

### Loop Testing Criteria — Test These Cases

For any loop (e.g., `for (i = 0; i < 50; i++)`):

| Test Case | Description | Why |
|-----------|-------------|-----|
| **0 iterations** | Condition false immediately, loop body never executes | Tests skip case |
| **1 iteration** | Loop body executes exactly once | Tests minimal execution |
| **2 iterations** | Loop body executes twice | Tests minimal repetition |
| **Typical middle value** | Some representative value (e.g., 25 for a 0–50 loop) | Tests normal behaviour |
| **Max - 1** | One less than maximum (49) | Tests near-boundary |
| **Max** | Exactly at maximum (50) | Tests at upper boundary |
| **Max + 1** | If possible, test beyond maximum | Tests boundary overrun |

### For the Q21 Loop: `for (i = 0; i < 50; i++)`

| Test | i range | text_box/value size |
|------|---------|---------------------|
| 0 iterations | i starts ≥ 50 (empty array) | Nothing copied |
| 1 iteration | Array size = 1 | One element copied |
| 2 iterations | Array size = 2 | Two elements copied |
| 25 iterations | Array size = 25 | Middle case |
| 49 iterations | Array size = 49 | Near-max |
| 50 iterations | Array size = 50 | Full loop |

---

## Quick Summary

- **White box testing** = tests based on internal code structure; requires access to source code
- **CFG** = visual map of all possible execution paths through the code
- **Cyclomatic complexity** V(G) = E − N + 2 = decision points + 1 → minimum number of test paths
- **Statement coverage** = every line executed; **Branch coverage** = every true/false branch taken
- **Condition coverage** = every individual boolean sub-expression tested true and false
- **Data flow testing** = tracks variable definition and use; catches undefined/unused variable bugs
- **Loop testing** = specifically test 0, 1, 2, typical, max-1, max iterations for every loop
- Higher cyclomatic complexity = more test cases needed, harder to test, higher defect risk
