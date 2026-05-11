# Chapter 2: V-Model of Testing and Software Testing Life Cycle (STLC)

## The Analogy Before the Definition

Imagine you're planning a surprise party. As you plan each part:
- You decide on a menu → you need to taste-test that menu later
- You pick a venue → you need to visit and verify the venue later
- You invite guests → you need to confirm their attendance later

Every planning decision creates a corresponding check. That's the V-Model.

---

## The V-Model

The V-Model shows that every **development phase** has a corresponding **testing phase**. They happen in parallel — the left side of the V is development (going down), the right side is testing (going up).

```
Requirements Analysis        ←→   Acceptance Testing
        |                                  ^
  System Design              ←→   System Testing
        |                                  ^
  Architecture/HLD           ←→   Integration Testing
        |                                  ^
  Detailed Design/LLD        ←→   Unit Testing
        |                                  ^
        └────────── Coding ───────────────┘
```

### How it works:
- At each level on the LEFT, test cases are **designed** (not executed yet)
- At each level on the RIGHT, those test cases are **executed**
- The left side goes down (into more detail), the right side comes back up (testing bigger pieces)

### Left side → Right side mapping

| Development Phase | What is produced | Testing Phase | What is verified |
|-------------------|-----------------|---------------|-----------------|
| Requirements Analysis | User requirements doc | Acceptance Testing | Does it meet user needs? |
| System Design | Overall system architecture | System Testing | Does the system work end-to-end? |
| High-Level Design | Module interfaces | Integration Testing | Do modules work together? |
| Low-Level Design | Detailed logic of each unit | Unit Testing | Does each function work correctly? |
| Coding | The actual code | — | (all right-side tests are against this) |

### Real Example — Banking App

| Dev Phase | What's designed | Test Phase | Example test |
|-----------|----------------|------------|-------------|
| Req. Analysis | "User can transfer money" | Acceptance | Bank UAT: real user completes a transfer |
| System Design | Login → Dashboard → Transfer → Confirmation | System | Full end-to-end transfer flow |
| HLD | Auth module ↔ Payment module interface | Integration | Auth module correctly passes session to Payment module |
| LLD | `calculateFee(amount)` logic | Unit | `calculateFee(1000)` returns `10.0` |

### Why V-Model matters

Without V-Model thinking:
- Testers wait until code is done to start writing tests
- By then, requirements are forgotten or ambiguous
- Defects found late are expensive to fix

With V-Model:
- Test cases are written alongside development
- Issues in requirements/design are caught early (via inspection)
- Testing is not an afterthought — it's built into the process

---

## Software Testing Life Cycle (STLC)

STLC is the sequence of activities performed specifically by the testing team. It runs inside the broader V-Model.

### The 6 Phases of STLC

#### Phase 1: Requirement Analysis
- Testers study the requirements document
- Identify testable vs non-testable requirements
- Clarify ambiguities with stakeholders
- Output: **Requirement Traceability Matrix (RTM)** — maps each requirement to a test case

#### Phase 2: Test Planning
- Define test scope, approach, resources, schedule
- Identify tools to be used
- Estimate effort
- Output: **Test Plan document**

#### Phase 3: Test Case Development (Design)
- Write detailed test cases
- Prepare test data
- Review and peer-check test cases
- Output: **Test Case documents, Test Scripts**

#### Phase 4: Test Environment Setup
- Set up hardware, software, network
- Install the application being tested
- Configure test data
- Output: **Ready test environment, smoke test pass**

#### Phase 5: Test Execution
- Run test cases
- Compare actual vs expected output
- Log defects for failed tests
- Output: **Test execution results, Defect reports**

#### Phase 6: Test Closure
- Evaluate exit criteria (coverage %, defect rate, etc.)
- Prepare test summary report
- Archive test artefacts
- Conduct retrospective
- Output: **Test Closure Report, Lessons Learned**

### STLC Summary Table

| Phase | Key Activity | Entry Criteria | Exit Criteria |
|-------|-------------|----------------|---------------|
| Req. Analysis | Read BRS/FRS | Requirements doc available | RTM created |
| Test Planning | Write test plan | RTM available | Test plan approved |
| Test Design | Write test cases | Test plan approved | Test cases reviewed |
| Environment Setup | Configure test env | Test cases ready | Smoke test passed |
| Test Execution | Run tests, log bugs | Test env ready | All test cases run |
| Test Closure | Report and archive | Test execution done | Report signed off |

### Real Example — Food Delivery App (Q20)

| Phase | Activity |
|-------|----------|
| Req. Analysis | Read requirements: "User can place order, track delivery, cancel order" |
| Test Planning | Scope: ordering + payment + tracking. Timeline: 2 weeks. Tools: Jira, Postman |
| Test Design | Write 150 test cases (ordering flow, payment gateway, GPS tracking, cancellation) |
| Env Setup | Set up test restaurant accounts, sandbox payment, mock GPS feed |
| Execution | Run 150 tests. 130 pass, 20 fail. Log defects. |
| Closure | 18/20 defects fixed, 2 deferred. Sign-off given. Final report shared. |

---

## Roles in STLC (Q30)

| Role | Responsibilities |
|------|-----------------|
| Test Manager | Plans resources, communicates with stakeholders, signs off |
| Test Lead | Coordinates the team, tracks progress, reports daily status |
| Test Engineer/Tester | Writes and executes test cases, logs defects |
| Test Architect | Designs the test framework and strategy |
| Automation Engineer | Writes automation scripts, maintains CI/CD tests |
| Business Analyst | Clarifies requirements, reviews acceptance test cases |
| Developer | Fixes defects, provides builds, supports unit testing |

---

## Quick Summary

| Concept | One-liner |
|---------|-----------|
| V-Model | Maps each dev phase to a test phase — tests designed left, executed right |
| Acceptance Testing | Checks user requirements (right side of top of V) |
| System Testing | Checks full system end-to-end |
| Integration Testing | Checks how modules interact |
| Unit Testing | Checks individual functions/methods |
| STLC | 6-phase testing process: Req Analysis → Planning → Design → Setup → Execution → Closure |
| RTM | Traceability matrix linking each requirement to test cases |
