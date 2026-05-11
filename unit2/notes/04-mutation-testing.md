# Chapter 4: Mutation Testing

---

## The Problem Mutation Testing Solves

Imagine you hire a security guard to protect a building and you want to know if they're actually paying attention. You test them by staging a fake break-in. If they catch the fake intruder, you know they're alert. If they don't, you know your security has gaps.

That's exactly what mutation testing does for your test suite. It stages "fake bugs" (mutations) in your code, then checks if your tests catch them. If your tests don't catch a deliberately introduced bug, they won't catch a real one either.

**Mutation testing tests the quality of your tests — not the quality of your code.**

---

## How Mutation Testing Works

### Step 1: Take the original program

```java
public int add(int a, int b) {
    return a + b;
}
```

### Step 2: Apply mutation operators to create "mutants"

A **mutation operator** is a small, syntactic rule that changes one thing at a time.

| Mutant | Change | Mutated Code |
|--------|--------|-------------|
| M1 | Arithmetic: `+` → `-` | `return a - b;` |
| M2 | Arithmetic: `+` → `*` | `return a * b;` |
| M3 | Return constant | `return 0;` |

### Step 3: Run your test suite against each mutant

- **Killed mutant:** At least one test fails when run against the mutant ✅ (your test caught the bug)
- **Surviving mutant:** All tests still pass despite the code change ❌ (your tests missed this bug)

### Step 4: Calculate the Mutation Score

$$\text{Mutation Score} = \frac{\text{Killed Mutants}}{\text{Total Mutants} - \text{Equivalent Mutants}} \times 100\%$$

---

## Equivalent Mutants

An **equivalent mutant** is a mutant where the code is syntactically different but behaviourally identical — no test can possibly kill it because the behaviour hasn't actually changed.

*Example:*

Original: `for (i = 0; i < n; i++)`

Mutant: `for (i = 0; i != n; i++)`

When `i` starts at 0 and increments by 1, `i < n` and `i != n` are behaviourally identical (assuming n ≥ 0). This mutant is equivalent — no test can distinguish it.

**Equivalent mutants are excluded from the mutation score denominator** because killing them is impossible, not a test weakness.

---

## Worked Example: Q22 Calculation

**Given:**
- Total mutants generated = 35
- Dead (killed) mutants = 29
- Equivalent mutants = 2

**Calculation:**

$$\text{Mutation Score} = \frac{29}{35 - 2} \times 100\% = \frac{29}{33} \times 100\% \approx 87.9\%$$

**Is the test set mutation adequate?**

A mutation score of ~88% is generally considered good but not excellent. A commonly cited threshold for "mutation adequate" is 90%+.

**Should she develop additional test cases?**

Yes. 4 non-equivalent mutants survived (33 - 29 = 4 survivors). She should:
1. Examine which mutants survived — what code changes did they represent?
2. Identify which input conditions those changes affect
3. Add test cases that specifically target those conditions
4. Re-run to verify the new tests kill the surviving mutants

---

## Common Mutation Operators

| Category | Operator | Example Change |
|----------|---------|---------------|
| **Arithmetic** | AOR | `+` → `-`, `*` → `/` |
| **Relational** | ROR | `<` → `<=`, `>` → `!=`, `==` → `!=` |
| **Logical** | LOR | `&&` → `\|\|`, `\|\|` → `&&` |
| **Unary** | UOI | Insert/remove negation: `x` → `-x`, `!x` → `x` |
| **Statement** | SDL | Delete a statement entirely |
| **Constant** | CR | Replace constant: `1` → `0`, `100` → `99` |

---

## Mutation Testing for `if (balance >= min_balance)` (BVA connection)

| Mutant | Change | Killed by |
|--------|--------|-----------|
| M1: `>=` → `>` | Strict comparison | Test case where `balance == min_balance` |
| M2: `>=` → `<=` | Reversed | Test case where `balance > min_balance` |
| M3: `>=` → `==` | Equality only | Multiple balance values |

This shows why **boundary value tests** are effective at killing relational operator mutations. ECP + BVA test design produces test suites with high mutation scores.

---

## Why Mutation Testing Over Traditional Testing? (Q34)

| Aspect | Traditional Testing | Mutation Testing |
|--------|--------------------|----|
| What it evaluates | Software correctness | Test suite quality |
| What it finds | Software bugs | Gaps in test cases |
| Can 100% coverage guarantee thorough testing? | No | Mutation testing reveals this |
| Cost | Lower | Higher (many mutants × test runs) |
| When useful | Always | When you need to prove test thoroughness |

**Key argument for mutation testing:**

Code coverage (e.g., 90% branch coverage) tells you that a branch was *executed*. It does NOT tell you that your test would fail if the branch had a bug in it. A test can pass through a branch with `assert True` — it covers the branch but doesn't verify the output.

Mutation testing is the only technique that directly measures whether your tests are **sensitive enough to detect defects**.

**Practical justification:**
- Safety-critical systems (medical, aviation, automotive) must demonstrate that tests are thorough
- Regulatory bodies may require mutation score evidence
- When a test suite grows over years, mutation testing identifies tests that are no longer contributing (checking stale coverage)

---

## Mutation Testing Tools

| Language | Tool |
|----------|------|
| Java | **PIT (Pitest)** — most popular, fast, integrates with Maven/Gradle |
| Python | **MutPy**, **mutmut** |
| JavaScript | **Stryker** |
| C/C++ | **Mull**, **mutate++** |

PIT example: Run `mvn test-compile pitest:mutationCoverage` in a Maven project. Generates an HTML report showing which mutants were killed/survived, colour-coded on the source code.

---

## Quick Summary

- Mutation testing = deliberately introduce small code bugs (mutants) and check if your tests catch them
- **Killed mutant:** A test detected the change ✅ — your tests are effective here
- **Surviving mutant:** No test failed ❌ — a gap in your test cases
- **Equivalent mutant:** Mutant is syntactically different but behaviourally identical — excluded from score
- **Mutation Score** = Killed / (Total − Equivalent) × 100% — higher is better, ≥90% is generally good
- Mutation testing reveals whether tests are *sensitive* to defects, not just whether they execute code
- BVA and ECP test designs naturally kill relational and boundary operator mutations
- Main limitation: computationally expensive (many mutants × full test run each)
