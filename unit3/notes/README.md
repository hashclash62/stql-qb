# Unit 3: Levels of Testing and Defect Management — Notes Index

## How to Use These Notes

Read chapters in order. Chapter 1 and 2 build your understanding of the testing levels. Chapters 3-5 build your understanding of defects — where they come from, how they're managed, and how to prevent them.

---

## Reading Order

| File | Topic | Covers QB Questions |
|------|-------|---------------------|
| [mental-model.md](../mental-model.md) | Topic groupings + study guide | All |
| [01-levels-of-testing-functional.md](./01-levels-of-testing-functional.md) | Unit, Integration, System, Alpha, Beta, UAT | Q1, Q3, Q4, Q14, Q15, Q20, Q25, Q26, Q34, Q35, Q36, Q37 |
| [02-levels-of-testing-nonfunctional.md](./02-levels-of-testing-nonfunctional.md) | Performance, Load, Stress, Recovery, Regression, Configuration | Q12, Q13, Q21, Q22, Q23, Q24, Q28, Q29, Q30, Q31 |
| [03-defect-origins-and-types.md](./03-defect-origins-and-types.md) | Defect origins, types, classification, severity | Q2, Q6, Q11, Q16, Q17, Q19, Q27, Q28 |
| [04-defect-lifecycle-and-repository.md](./04-defect-lifecycle-and-repository.md) | Defect lifecycle states, repository contents, test planning | Q5, Q7, Q8, Q9, Q10, Q18 |
| [05-defect-injection-and-prevention.md](./05-defect-injection-and-prevention.md) | Mutation testing, defect prevention techniques, root cause analysis | Q32, Q33 |

---

## Syllabus Coverage Checklist

- [x] Unit testing
- [x] Integration testing
- [x] System testing
- [x] Performance testing
- [x] Recovery testing
- [x] Regression testing
- [x] Alpha, Beta, and Acceptance testing
- [x] Test Planning
- [x] Test Reports and Monitoring Test Effectiveness
- [x] Origins of defects
- [x] Defect Types
- [x] Defect repository and test design
- [x] Defect severity
- [x] Life cycle of defect
- [x] Defect Reports — Track, Retest, and Close
- [x] Defect Injection and Prevention

---

## Key Diagrams to Draw in Exam

1. **Defect Lifecycle Diagram** — state machine with all states (New, Open, Fixed, Verified, Closed, Rejected, Deferred, Reopened) and transitions
2. **Testing Levels Pyramid** — Unit at base → Integration → System → Acceptance at top (show defect types caught at each level)
3. **Integration Strategies Diagram** — Top-down (with stubs) and Bottom-up (with drivers) side by side on same module tree
4. **Alpha vs Beta vs UAT Comparison Table** — Who, Where, When, Goal
5. **Defect Repository Table** — list of 10+ important fields with purpose

---

## Quick-Revision Cheat Sheet

### Testing Levels

| Level | Tests What | Catches |
|-------|-----------|---------|
| Unit | Individual function/class | Logic, computation, boundary |
| Integration | Module interactions | Interface, data format, sequence |
| System | Full system vs requirements | System-level failures, non-functional |
| Acceptance | Business needs met | Unmet requirements, usability |

### Integration Strategies

| Strategy | Starts at | Needs | Tests first |
|----------|-----------|-------|-------------|
| Top-Down | Highest module | Stubs | High-level flow |
| Bottom-Up | Lowest modules | Drivers | Low-level utilities |
| Sandwich | Both ends | Stubs + Drivers | Both simultaneously |

### Alpha vs Beta vs UAT

| | Alpha | Beta | UAT |
|-|-------|------|-----|
| Who | Internal users | External selected users | Client/end users |
| Where | Developer's site | User's environment | User's environment |
| Goal | Find defects internally | Real-world issues + feedback | Formal business acceptance |

### Performance Testing Types

| Type | Load Level | Goal |
|------|-----------|------|
| Load | Expected normal | Verify meets requirements |
| Stress | Above normal | Find breaking point |
| Spike | Sudden extreme | Handle sudden traffic burst |
| Soak | Normal for long period | Find memory leaks |

### Defect Types

1. Computational / Algorithmic
2. Logic
3. Interface / Integration
4. Data
5. Performance
6. Usability

### Defect Lifecycle States
New → Open → In Progress → Fixed → Verified → Closed
(With branches: Rejected, Deferred, Reopened)

### Defect Severity Levels

| Severity | Example |
|---------|---------|
| Critical | Login broken, data corruption |
| Major | Important feature broken |
| Moderate | Feature partially broken |
| Minor | Cosmetic, typo |

### Defect Prevention Techniques

1. Requirements reviews
2. Design reviews
3. Code reviews
4. Coding standards + checklists
5. Test-Driven Development (TDD)
6. Pair programming
7. Root Cause Analysis (5 Whys)
8. Defect prevention meetings

### Mutation Testing Key Terms
- **Mutant:** A version of the code with a small injected defect
- **Killed mutant:** A test case detected the mutation ✅
- **Survived mutant:** No test detected it ❌
- **Mutation Score** = Killed / Total × 100%
