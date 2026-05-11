# Chapter 1: Levels of Testing — Functional (Unit, Integration, System, Acceptance)

---

## Why Test in Levels?

Building software is like constructing a building. You don't pour all the concrete at once and hope for the best — you test the foundation, then the walls, then the roof, level by level.

Software testing works the same way:
- First test the smallest pieces (functions/classes)
- Then test how pieces work together (modules)
- Then test the whole building (system)
- Finally, have the client walk through and approve (acceptance)

Each level catches defects that the previous level isn't designed to catch. Catching a defect in a function is cheap. Catching it after full integration is expensive.

---

## Level 1: Unit Testing

### What It Tests
The **smallest testable unit** of software — a single function, method, or class — in **isolation** from everything else.

"Isolation" is key: you don't want a test failure in a unit to be caused by a problem in another unit. So you replace real dependencies with **stubs** (fake replacements that return fixed values) and **mock objects** (fake dependencies you can also verify interactions with).

### What Unit Testing Catches
- Computational errors (wrong formula, wrong operator)
- Logic errors (wrong condition in if/else, incorrect loop boundary)
- Missing edge cases (null input, zero, negative numbers, empty string)
- Off-by-one errors

### Who Writes Unit Tests
Developers write unit tests, usually alongside the code. In Test-Driven Development (TDD), they write the test *before* the code.

### Tools
- **Java:** JUnit, TestNG
- **Python:** pytest, unittest
- **JavaScript:** Jest, Mocha
- **C#:** NUnit, xUnit

### Banking App Example (Q1, Q3)
Testing the `calculateInterest(principal, rate, time)` function:
```
Test cases:
- calculateInterest(1000, 5, 1)  → should return 50 (5% of 1000 for 1 year)
- calculateInterest(0, 5, 1)     → should return 0 (edge case: zero principal)
- calculateInterest(1000, 0, 1)  → should return 0 (zero rate)
- calculateInterest(-100, 5, 1)  → should throw IllegalArgumentException
```

### OOP Units (Q20)
In procedural programming, the unit is a **function**.
In object-oriented programming, the unit is typically a **class** or a **method**.
When testing a class, you test each method independently, mocking out class dependencies.

---

## Level 2: Integration Testing

### What It Tests
How **two or more units work together** — testing the interactions and data flow between modules.

Integration testing is where you discover interface defects — problems at the seams between modules that unit tests never see (because unit tests test units in isolation).

### Common Integration Defects
- Incorrect data format passed between modules (module A sends a float, module B expects an int)
- Wrong sequence of function calls
- Missing or incorrect API contracts
- Shared resource conflicts (two modules accessing the same database table)
- Communication breakdowns (like the communication problem in Q17)

### Integration Strategies

#### Top-Down Integration
Start with the highest-level module and integrate downwards.

```
        M1
       / | \
      M2 M3 M4     ← Integrate these one by one
     /\  /\
   M5 M6 M7 M8
```

Lower modules not yet integrated are replaced by **stubs** (dummy implementations that return fixed data).

**Advantage:** Main control flow is tested early. High-level design flaws caught quickly.
**Disadvantage:** Need many stubs. Low-level utilities tested late.

#### Bottom-Up Integration
Start with the lowest-level modules and integrate upward.

Lower modules are tested first. Higher modules not yet integrated are replaced by **drivers** (test harnesses that call the lower modules and verify results).

**Advantage:** No stubs needed. Lower modules (which are often reused) are well tested.
**Disadvantage:** High-level control flow tested late. Need many drivers.

#### Sandwich / Hybrid Integration
Combine top-down and bottom-up simultaneously — high-level modules are tested top-down while low-level modules are tested bottom-up. They meet in the middle.

**Advantage:** Parallel testing of high and low levels.

#### Big Bang Integration
Integrate everything at once and test.

**Disadvantage:** When something fails, you don't know which integration caused it. Very hard to debug. Only used in small projects.

### Drivers vs Stubs

| Tool | Used In | Purpose |
|------|---------|---------|
| **Stub** | Top-down integration | Simulates a *lower* module not yet integrated |
| **Driver** | Bottom-up integration | Simulates a *higher* module that calls the unit being tested |

### External APIs (Q4)
Testing a system dependent on external APIs (payment gateway, weather service):
- Use **mock servers** to simulate the external API during testing
- Test all response scenarios: success, failure, timeout, malformed response
- Use contract testing (e.g., Pact) to ensure your integration assumptions match the actual API

### Banking App Integration Example (Q1, Q3)
After unit testing `calculateInterest()` and `getUserAccount()` separately, integration testing verifies:
- Does `applyInterest(userId)` correctly call both functions and update the account?
- Does the data format (account ID type) match between modules?
- If `getUserAccount()` returns null, does `applyInterest()` handle it gracefully?

---

## Level 3: System Testing

### What It Tests
The **complete, integrated system** — tested against the original system requirements to verify the system does what it's supposed to do.

System testing is the first level that treats the software as a "black box" from the user's perspective. Testers don't care about internal code structure — they care whether the system meets its requirements.

### What System Testing Covers
- Functional correctness of the full system
- Compliance with requirements (functional and non-functional)
- Performance, security, reliability (covered in Chapter 2)
- Error handling and recovery
- Data handling and integrity

### Fast Food Restaurant System Example (Q24)
System testing for an online fast food ordering system:

| Test Type | Objective | Approach |
|-----------|-----------|---------|
| Functional | Orders relay to kitchen correctly | Input test orders, verify kitchen display |
| Calculation | Bill and change are correct | Enter orders, verify totals |
| Security | Only authorised waitpersons can log in | Attempt login with invalid credentials |
| Inventory | Inventory updates on each order | Place orders, verify stock decrements |
| Multi-user | Multiple terminals work simultaneously | Simulate concurrent orders from 5 terminals |

### Configuration Testing (Q21)
Some systems run in many hardware/software configurations. Air traffic control runs on different hardware setups.

**Configuration testing checks:** Does the software work correctly across all supported configurations?
- Different operating systems
- Different screen resolutions / display types
- Different hardware (radar detectors, communication devices)
- Different network environments

You document all supported configurations and test each one systematically.

### Cancer Therapy Laser System (Q22)
A real-time safety-critical system:
- **Safety testing:** Does it fail safely? No harmful output on software error.
- **Reliability testing:** Does it operate without failure over extended periods?
- **Access control testing:** Only qualified technicians can log in.
- **Hardware interface testing:** Software correctly controls laser hardware.
- **Recovery testing:** After power failure, does it restart safely?

---

## Level 4: Acceptance Testing

### What It Tests
Whether the system **meets the business needs** of the users and stakeholders. This is the final gate before release.

Acceptance testing is not about finding bugs — it's about confirming the system is ready for deployment.

### Alpha Testing (Q14, Q34, Q37)

**What it is:** Testing conducted *inside the organisation* by internal users (not the development team) in a controlled environment before external release.

**Who:** QA team, selected employees, internal business users.
**Where:** Developer's site / controlled environment.
**Goal:** Find defects before exposing the product to external users. Validate against business requirements from an internal user perspective.

*Example (Q34):* Developers in a hospital management system find and fix defects during internal testing before external release. This *is* alpha testing.

---

### Beta Testing (Q14, Q35, Q37)

**What it is:** Testing conducted by a **limited group of real users outside the organisation** in a real environment before the final public release.

**Who:** Selected real users (often volunteers or early-access program participants).
**Where:** User's own environment (real conditions).
**Goal:** Discover defects that only appear in real usage, collect user experience feedback, validate usability.

*Example (Q35):* A mobile banking app released to 1000 selected users outside the organisation for feedback before final launch — this is beta testing.

---

### User Acceptance Testing (UAT)

**What it is:** Final testing by the **client or end users** to verify the system meets their business requirements and they formally accept it.

**Who:** Client representatives, actual end users.
**Goal:** Formal acceptance — the client signs off that the software meets what was agreed in the contract.

*Example (Q36):* End users checking whether a library management system satisfies business needs before deployment — this is UAT.

---

### Alpha vs Beta vs UAT — Summary

| Aspect | Alpha | Beta | UAT |
|--------|-------|------|-----|
| Who | Internal users | External selected users | Client/End users |
| Where | Controlled environment | Real user environment | Real environment |
| Goal | Find defects before external release | Find real-world issues, gather feedback | Formal business acceptance |
| Timing | Before beta | Before public release | Before formal delivery |

---

### Q37: The Full Progression

Software tested internally (alpha) → then by selected users (beta) → then approved by client (UAT). These are three distinct acceptance stages, each with its own purpose.

---

## Quick Summary

- **Unit testing:** Smallest unit (function/class) in isolation. Catches computational and logic errors.
- **Integration testing:** How units work together. Catches interface and communication defects. Use stubs (top-down) or drivers (bottom-up).
- **System testing:** Full system vs requirements. Catches system-level failures and non-compliance.
- **Alpha testing:** Internal users, controlled environment, before external release.
- **Beta testing:** Real external users, real environment, before public launch.
- **UAT:** Client/end users verify business requirements are met before formal delivery.
- Each level catches different defects — all levels are needed.
