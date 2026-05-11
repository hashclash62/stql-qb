# Chapter 3: Basic Definitions — The Core Vocabulary

## Why Vocabulary Matters

In software testing, the same word used loosely can mean very different things. Examiners and interviewers specifically test whether you know the precise meaning of these terms. Get this chapter solid — it's directly tested in Q6, Q21, Q26, Q31, Q32.

---

## Error → Fault → Defect → Failure — The Chain

This is a cause-and-effect chain. One thing leads to the next.

### The Human Analogy
1. A student **misunderstands** a math concept (error in the person's head)
2. The student writes a **wrong formula** on the answer sheet (fault — the wrong thing is now documented)
3. The exam paper has a **wrong answer** (defect — the artifact has the problem)
4. The student **fails the exam** (failure — the expected outcome was not achieved)

### Formal Definitions

#### Error (Mistake)
A human action that produces an incorrect result. It happens **in the developer's mind**.

> "The developer misunderstood that array indices start at 0, not 1."

The error itself is invisible — it's a mental mistake.

#### Fault (Bug)
The result of an error that exists in the source code or document. The incorrect thing is now **written down somewhere**.

> "The code says `arr[1]` instead of `arr[0]`."

A fault is in the artifact (code, design doc, requirements). It hasn't caused any problem yet — it's just sitting there waiting.

#### Defect
Often used interchangeably with "fault" in practice, but technically — a defect is a fault that has been found and reported (through code review, static analysis, or testing). It's a **documented fault**.

> "Bug report #142: array starts from index 1 instead of 0."

#### Failure
When the system does something that was not expected or does not do what was required. Failure happens at **runtime** when a fault is triggered by some input.

> "The login screen shows the second user's info instead of the first user's. The system has failed."

Not every fault causes a failure:
- A fault in code that is never executed = no failure
- A fault in code that is executed but doesn't change output in a visible way = no failure (yet)

### The Login Crash Example (Q21)

> "A login system crashes when incorrect input is given."

| Stage | What happened |
|-------|--------------|
| Error | Developer assumed the input would always be valid; forgot to handle invalid input |
| Fault | No null-check or validation written in the login function |
| Defect | Tester found and logged: "login() crashes on invalid input" |
| Failure | User types junk into the login form → app crashes → user can't log in |

### Railway Reservation Example (Q26)

| Stage | What happened |
|-------|--------------|
| Error | Developer wrote the seat calculation logic incorrectly |
| Fault | Incorrect calculation formula in `calculateAvailableSeats()` |
| Defect | Code review or test reveals the calculation is wrong |
| Failure | User sees "0 seats available" when 50 seats are free → booking fails |

---

## Test Case

A test case is a set of **conditions, inputs, and expected results** that checks a specific behaviour of the system.

A well-written test case contains:
- **Test Case ID** — unique identifier
- **Description** — what is being tested
- **Preconditions** — what must be set up before
- **Input data** — what you feed into the system
- **Steps** — exactly how to execute
- **Expected output** — what the system SHOULD do
- **Actual output** — what it actually did (filled during execution)
- **Status** — Pass / Fail

### Login Module Example (Q22)

| Field | Value |
|-------|-------|
| ID | TC_LOGIN_001 |
| Description | Valid login |
| Precondition | User exists in DB with username "alice", password "pass123" |
| Input | username="alice", password="pass123" |
| Steps | 1. Go to /login, 2. Enter credentials, 3. Click Login |
| Expected | User is redirected to dashboard |
| Actual | (filled during execution) |

| ID | Test | Input | Expected |
|----|------|-------|----------|
| TC_LOGIN_001 | Valid login | alice / pass123 | Redirects to dashboard |
| TC_LOGIN_002 | Wrong password | alice / wrongpass | "Invalid credentials" message |
| TC_LOGIN_003 | Empty username | "" / pass123 | "Username required" message |
| TC_LOGIN_004 | SQL injection | `' OR '1'='1` | Input rejected, no login |

A **test suite** is a collection of related test cases (e.g., all test cases for the login module).

---

## Test Bed

A test bed is the **complete environment** in which tests are executed. It includes:
- Hardware (servers, devices)
- Operating system
- Software under test + dependencies
- Test data
- Network configuration
- Any simulators or stubs

Think of it as the "stage" set up for testing. Without a proper test bed, test results are unreliable.

### Example Test Bed for an E-commerce App (Q32, Q33)

```
Test Bed:
├── Web server: Apache on Ubuntu 22.04
├── Application: e-commerce app v1.5
├── Database: MySQL 8.0 with seed data (100 products, 20 users)
├── Browser: Chrome 120, Firefox 121
├── Network: 100 Mbps local, throttled to 3G for mobile tests
├── Payment: Sandbox payment gateway (Razorpay test mode)
└── Tools: Selenium 4, JMeter for load
```

---

## Test Oracle

A test oracle is the mechanism that tells you whether the actual output is **correct or incorrect**. It's how you decide "pass" or "fail".

Types of test oracles:
- **Specified oracle** — the spec/requirements document says what the output should be
- **Previous version oracle** — compare output to an older known-good version
- **Human oracle** — a domain expert manually checks if the result is reasonable
- **Statistical oracle** — uses probability/sampling to assess correctness (used in AI/ML testing)
- **Derived oracle** — derive expected output from a related test (metamorphic testing)

### Calculator System Example (Q27)

> For `2 + 3`, the oracle says the answer must be `5`. If the system shows `6`, the oracle tells us: FAIL.

> For a more complex case: `sqrt(16)` — the oracle (specification) says the answer is `4.0`. Anything else = FAIL.

When there's **no oracle** (the "oracle problem"), it's very hard to write automated tests. This is why AI/ML testing is difficult — there's often no clear "correct" output.

---

## Test Harness

A test harness is the **combination of stubs, drivers, and tools** used to support testing of a component.

When testing a module in isolation, it doesn't have:
- Its real parent (which calls it) → replaced by a **Driver**
- Its real dependencies (which it calls) → replaced by **Stubs**

```
Driver → [Module Under Test] → Stub
```

**Driver:** Simulates the caller. Calls the module with test inputs.
**Stub:** Simulates a dependency. Returns hard-coded "good enough" outputs.

### Example (Q35)

Testing a `PaymentProcessor` module before the `BankAPI` module is ready:

```
TestDriver.java (driver)
    → calls PaymentProcessor.processPayment(1000)
        → PaymentProcessor calls BankAPI.debit(1000)
            → BankAPIStub returns "SUCCESS" (stub)
```

The harness = TestDriver + BankAPIStub + test data files.

---

## Software Quality

Quality in software means the software **satisfies its stated requirements** and **meets user expectations**.

Key quality attributes (ISO 25010):

| Attribute | Meaning | Example |
|-----------|---------|---------|
| Functionality | Does it do what it should? | Login works correctly |
| Reliability | Does it work consistently? | Doesn't crash under load |
| Usability | Is it easy to use? | UI is intuitive |
| Efficiency | Is it fast and resource-efficient? | Response < 2 seconds |
| Maintainability | Is it easy to change? | Code is modular, documented |
| Portability | Does it work across platforms? | Works on Chrome, Firefox, Safari |
| Security | Is it protected from threats? | Passwords are hashed, HTTPS used |

---

## Software Quality Assurance (SQA) Group

The SQA group is the team responsible for ensuring that the **software development process** produces a quality product. They focus on the process, not just the product.

### SQA Group Activities (Q10)

If a project has frequent defects:
1. **Process audit** — review development processes to find where defects originate
2. **Standards enforcement** — ensure coding standards and review processes are followed
3. **Metrics collection** — track defect density, test coverage, review effectiveness
4. **Root cause analysis** — find the source of recurring defect types
5. **Training** — ensure developers and testers have needed skills
6. **Tool evaluation** — assess if better tools can catch defects earlier

### SQA vs Testing Team

| | SQA Group | Testing Team |
|-|-----------|-------------|
| Focus | Process | Product |
| Question | "Are we following the right process?" | "Does the product work?" |
| Activity | Audits, standards, metrics | Test design and execution |
| Coverage | Entire SDLC | Test phase mainly |

---

## Quick Summary

| Term | One-liner |
|------|-----------|
| Error | Human mistake (in the developer's mind) |
| Fault/Bug | Incorrect code or document resulting from an error |
| Defect | A found and reported fault |
| Failure | System doesn't behave as expected at runtime |
| Test Case | Input + steps + expected output for one specific check |
| Test Suite | Collection of related test cases |
| Test Bed | Complete environment for testing (hardware, software, data, tools) |
| Test Oracle | The mechanism deciding if output is correct (pass/fail judge) |
| Test Harness | Drivers + stubs + tools to support isolated component testing |
| Software Quality | Meets requirements + meets user expectations |
| SQA Group | Team that ensures the development process produces quality output |
