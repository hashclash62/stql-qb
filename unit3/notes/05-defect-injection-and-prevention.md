# Chapter 5: Defect Injection and Defect Prevention

---

## Two Sides of the Same Coin

There are two proactive quality strategies that go beyond just "run tests and log defects":

1. **Defect Injection** — Deliberately put defects in to test whether your testing can find them
2. **Defect Prevention** — Build processes and habits that stop defects from being introduced in the first place

Both are about being smarter about quality, not just reactive.

---

## Defect Injection (Mutation Testing)

### What It Is (Q32)
**Defect injection** (or **mutation testing**) is the practice of *deliberately introducing known defects* (called "mutants") into a program to evaluate whether your tests can detect them.

**The logic:** If your test suite can't find a deliberately injected defect, what confidence do you have that it'll find accidental real defects?

It tests the *quality of your tests* — not the quality of your code.

### How It Works

1. Take the original program
2. Make a small, syntactic change to create a "mutant" (e.g., change `+` to `-`, or `>` to `>=`)
3. Run your existing test suite against the mutant
4. If a test fails → the mutation was **killed** (your tests detected the change) ✅
5. If all tests still pass → the mutation **survived** (your tests missed this type of change) ❌

### Example Mutations

Original code:
```python
if balance >= min_balance:
    allow_transaction()
```

Mutants:
```python
if balance > min_balance:     # Mutant 1: >= changed to >
if balance <= min_balance:    # Mutant 2: >= changed to <=
if balance != min_balance:    # Mutant 3: >= changed to !=
```

If your tests don't have a test case where `balance == min_balance`, Mutant 1 will survive — your tests aren't thorough enough for boundary conditions.

### Mutation Score
```
Mutation Score = (Killed Mutants / Total Mutants) × 100%
```

A mutation score of 90% means your tests detect 90% of the introduced mutations. Higher is better.

### Where Defect Injection Is Used (Q32)
- Evaluate test suite completeness without knowing actual defects
- Find gaps in test coverage (what scenarios aren't being tested)
- Justify test improvement investments
- Safety-critical systems (aerospace, medical) where testing thoroughness must be demonstrated

### Tools
- **PIT (PITest)** — Java mutation testing tool, widely used
- **MutPy** — Python mutation testing
- **Stryker** — JavaScript/TypeScript mutation testing

---

## Defect Prevention Techniques (Q33)

### What It Is
Defect prevention means taking systematic steps to reduce the *rate at which defects are introduced* — addressing root causes rather than symptoms.

**The ROI argument:** Preventing 1 defect at requirements stage costs less than finding it during system testing, which costs far less than a customer reporting it in production.

### Prevention Techniques

#### 1. Requirements Reviews and Walkthroughs
Read the requirements document carefully with a diverse team (developer, tester, business analyst, product owner). Catch ambiguities and contradictions before coding begins.

*Example:* A requirements review catches "The system should handle large files" — reviewers ask "how large?" and get a specific answer: "up to 500MB." Without this, developers might implement a 10MB limit.

#### 2. Design Reviews
Review the software architecture and module interfaces before implementation. Catch design flaws early.

*Example:* A design review catches that two modules both write to the same database table without locking — a recipe for data corruption under concurrent use.

#### 3. Code Reviews / Peer Reviews
Before code is merged, another developer reads it and checks for:
- Logic errors
- Missing error handling
- Security vulnerabilities
- Coding standard violations
- Missing tests

*Example:* A code review catches an SQL query built by string concatenation — a SQL injection vulnerability that would have been a critical security defect in production.

#### 4. Coding Standards and Checklists
Define and enforce agreed-upon coding conventions, naming standards, and common pitfall checklists.

*Examples:*
- "Always validate user inputs before processing"
- "Never use floating-point for currency calculations — use Decimal"
- "Always handle null return values"

Teams that follow coding standards have measurably lower defect rates.

#### 5. Test-Driven Development (TDD)
Write the test before writing the code. The developer can only write code to make that test pass.

**Benefits:**
- Forces clear thinking about requirements before coding
- Every piece of code is covered by a test from day one
- Makes refactoring safe (existing tests verify correctness)

#### 6. Pair Programming
Two developers work together at one keyboard — one writes code, the other reviews in real time.

**Benefits:**
- Defects caught immediately (second set of eyes)
- Knowledge sharing reduces knowledge silos
- Higher upfront cost, lower overall defect cost

#### 7. Root Cause Analysis (Causal Analysis)
After every significant defect, conduct a root cause analysis: *why* did this defect occur?

Use the **5 Whys technique:**
- Defect: Payment calculation is wrong
- Why? → The formula in the code is wrong
- Why? → The developer implemented the wrong formula
- Why? → The formula in the requirements document was ambiguous
- Why? → The business analyst used a shorthand that was misunderstood
- Why? → No formal review process for requirements documents
- **Root cause:** No requirements review process → **Fix: Implement mandatory requirements review**

This is how you fix the *process*, not just the symptom.

#### 8. Defect Prevention Meetings / Analysis Sessions
Regularly review collected defect data with the team. Identify patterns:
- "30% of our defects are input validation errors" → Add input validation to the coding checklist
- "20% of defects come from environment configuration mismatches" → Standardise environment setup with Docker

---

## Improving Software Reliability with Defect Prevention (Q33)

**Real-world scenario:** A hospital management system has high defect rates. Defect prevention strategy:

1. **Causal analysis** of recent defects → 40% are data type mismatches between modules
2. **Root cause:** No interface specification document
3. **Prevention:** Introduce mandatory interface specification documents, reviewed by both module owners before coding
4. **Coding checklist update:** Add "verify all parameter types match interface spec" to code review checklist
5. **Result after 2 releases:** Data type defects drop from 40% to 5%

This is how defect prevention creates long-term reliability improvement — not by testing more, but by introducing fewer defects.

---

## Quick Summary

- **Defect injection (mutation testing):** Deliberately introduce defects to test whether your test suite can find them — measures test quality, not code quality
- **Mutation score** = (killed mutants / total mutants) × 100% — higher is better
- **Defect prevention** addresses the root causes of defect introduction, not just the symptoms
- Key prevention techniques: requirements reviews, design reviews, code reviews, coding standards, TDD, pair programming, root cause analysis
- Root cause analysis + causal analysis transforms defect data into process improvements
- Prevention is fundamentally cheaper than detection, which is fundamentally cheaper than fixing in production
