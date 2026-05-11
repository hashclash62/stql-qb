# Unit 1: Software Testing Basics — Notes Index

## How to Use These Notes

Start with Chapter 3 (definitions) if you're blanking on vocabulary. Then read Chapters 1 and 2 for the process and model. Chapters 4–6 are more focused topics. The cheat sheet at the bottom is your last-day revision tool.

---

## Reading Order

| File | Topic | Covers QB Questions |
|------|-------|---------------------|
| [mental-model.md](../mental-model.md) | Topic groupings + priority guide | All |
| [01-testing-as-engineering-activity.md](./01-testing-as-engineering-activity.md) | Testing as an activity and a process, V&V | Q1, Q2, Q3, Q13, Q14, Q15, Q16, Q17 |
| [02-vmodel-and-stlc.md](./02-vmodel-and-stlc.md) | V-Model, STLC phases, roles | Q4, Q5, Q18, Q19, Q20, Q25, Q30 |
| [03-basic-definitions.md](./03-basic-definitions.md) | Error/fault/defect/failure, test case, oracle, test bed, harness, SQA | Q6, Q7, Q8, Q9, Q10, Q21, Q22, Q26, Q27, Q31, Q32, Q33, Q35, Q39 |
| [04-testing-principles-and-tester-role.md](./04-testing-principles-and-tester-role.md) | 7 testing principles, tester's role, Agile vs traditional | Q23, Q28, Q36, Q37, Q38 |
| [05-reviews.md](./05-reviews.md) | Inspection, walkthrough, review policies, review metrics | Q11 |
| [06-tdd.md](./06-tdd.md) | TDD Red-Green-Refactor, examples, benefits, challenges | Q12, Q24, Q29, Q34 |

---

## Syllabus Coverage Checklist

- [x] Introduction to testing as an engineering activity
- [x] Testing as a process
- [x] Verification and Validation (V&V)
- [x] V-Model of testing
- [x] Testing Life Cycle — Roles and activities (STLC)
- [x] Basic definitions — errors, faults, defects, failures
- [x] Basic definitions — test case, test, test bed, test oracle, test harness
- [x] Software quality and software quality assurance group
- [x] Testing Principles (all 7)
- [x] Tester's role in a software development organisation
- [x] Reviews as a testing activity
- [x] Types of reviews — inspections and walkthroughs
- [x] Need for review policies
- [x] Components of review plans
- [x] Review metrics
- [x] Introduction to Test Driven Development

---

## Key Diagrams to Draw in Exam

1. **V-Model** — Left side dev phases going down, right side test phases going up, arrows connecting each pair across the bottom (meeting at coding)
2. **Error → Fault → Defect → Failure chain** — a horizontal arrow diagram with labels and examples at each stage
3. **TDD cycle** — Red → Green → Refactor circle with brief description at each stage
4. **STLC phases table** — 6 rows: Phase, Key Activity, Entry Criteria, Exit Criteria
5. **Walkthrough vs Inspection comparison table** — at least 5 rows
6. **Defect chain for a given scenario** — draw a 4-box chain with arrows

---

## Quick-Revision Cheat Sheet

### Verification vs Validation
| | Verification | Validation |
|-|-------------|-----------|
| Question | Building it right? | Building the right thing? |
| When | During development | End / user involvement |
| Method | Reviews, inspections | Testing, demos |
| Involves execution? | No | Yes |

### V-Model Mapping
```
Requirements  ←→  Acceptance Testing
System Design ←→  System Testing
HLD           ←→  Integration Testing
LLD           ←→  Unit Testing
              Coding (bottom)
```

### STLC in Order
1. Requirement Analysis → RTM
2. Test Planning → Test Plan
3. Test Case Development → Test Cases
4. Test Environment Setup → Ready Env
5. Test Execution → Defect Reports
6. Test Closure → Summary Report

### Definitions One-liners
- **Error** = Human mistake (in the mind)
- **Fault** = Wrong code/document (written down)
- **Defect** = Found and reported fault
- **Failure** = System does something wrong at runtime
- **Test Case** = Input + steps + expected output
- **Test Bed** = Complete environment for testing
- **Test Oracle** = Mechanism to judge pass/fail
- **Test Harness** = Driver + Stubs + tools for component testing
- **SQA Group** = Ensures the process is followed, not just the product tested

### 7 Testing Principles (memorise names)
1. Shows presence of defects, not absence
2. Exhaustive testing is impossible
3. Early testing (shift left)
4. Defect clustering (80/20 rule)
5. Pesticide paradox (update tests regularly)
6. Context dependent
7. Absence of errors fallacy

### Reviews: Walkthrough vs Inspection
| | Walkthrough | Inspection |
|-|-------------|-----------|
| Led by | Author | Moderator |
| Formality | Low | High |
| Checklist | No | Yes |
| Defect logging | Optional | Mandatory |

### Review Metrics
- **Defect Density** = Defects / Size (per KLOC)
- **Defect Detection Rate** = Defects in review / Total defects
- **Inspection Rate** = LOC / Hours (aim: 100–200 LOC/hour)

### TDD Cycle
```
RED (write failing test)
  → GREEN (write minimum code to pass)
    → REFACTOR (clean up, keep tests green)
      → repeat for next requirement
```

Benefits: documentation, catches regressions, forces good design  
Challenges: mindset shift, slow start, UI is hard to TDD
