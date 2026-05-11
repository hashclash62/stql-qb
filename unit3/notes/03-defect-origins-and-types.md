# Chapter 3: Defect Origins, Types, and Classification

---

## Where Do Defects Come From?

A defect in software is like a crack in a building — it doesn't appear out of nowhere. It was introduced at some point during the construction process. Knowing *where* and *why* defects originate helps us design better tests and better prevention strategies.

---

## Origins of Defects

Defects are introduced at every phase of the SDLC. The earlier a defect is introduced, the more expensive it is (if caught late).

### 1. Requirements Phase
**Origin:** Ambiguous, incomplete, contradictory, or misunderstood requirements.

*Examples:*
- "The system should respond quickly" — how quickly? No number specified.
- The customer said "display the last 10 transactions" but different team members understood "last 10 by date" vs "last 10 by amount"
- A feature requirement contradicts a security requirement

*Why it's costly:* A defect from a wrong requirement propagates through design, code, and testing. Everything built on the wrong foundation is wrong.

### 2. Design Phase
**Origin:** Flawed architecture, incorrect data structures, poor module interfaces, inadequate error handling design.

*Examples:*
- A module was designed to return NULL on failure but the calling module was designed expecting an empty list
- The database schema was designed with no indexing — correct but slow
- Error handling not designed for network failures

### 3. Coding Phase
**Origin:** Mistakes made while translating the design into code.

*Examples:*
- Using `=` instead of `==` in a condition
- Off-by-one error in a loop (`i < n` vs `i <= n`)
- Null pointer dereference
- Incorrect formula implementation

### 4. Communication Breakdown
**Origin:** Misunderstandings between team members — especially at module interfaces.

This is directly illustrated in **Q17 (Programmer A and B)**:
- Programmer A and B are working on interfacing modules but communicate poorly
- Likely defects: Interface defects (calling conventions, data format, parameter order, error return codes)
- Programmer A expects `getUser()` to return a User object; Programmer B's implementation returns a Map
- These defects only surface during integration testing, not unit testing

### 5. Testing Phase (Test Design Defects)
Even the testing process can introduce defects — incorrectly written test cases, wrong expected outputs, tests that don't actually cover the requirement.

---

## Defect Types

Understanding defect types helps you classify them correctly and design targeted tests.

### 1. Computational / Algorithmic Defects
**What:** Wrong calculation, wrong formula, incorrect algorithm, wrong data type.

*Examples:*
- Compound interest formula has wrong exponent
- Sorting algorithm is O(n²) instead of O(n log n) — works but fails performance requirements
- Integer overflow when summing large values

*Q16/Q27 scenario:* A code component calculates an output variable incorrectly.
- **Classification:** Computational/algorithmic defect
- **Causes:** Wrong formula in requirements; developer implemented incorrect formula; no review
- **Prevention:** Requirements review, code review, unit tests with edge-case values

### 2. Logic Defects
**What:** Incorrect conditional logic, wrong boolean expression, incorrect loop boundaries.

*Examples:*
- `if (balance > 0)` should be `if (balance >= 0)`
- A loop runs one iteration too many
- AND/OR conditions swapped in access control check

### 3. Interface / Integration Defects (Q19)
**What:** Mismatches at module boundaries — wrong data format, wrong parameter type, wrong sequence of calls.

*Examples:*
- Function A passes customer ID as String; Function B expects Integer
- Module calls `createOrder()` before `validatePayment()` — wrong sequence
- API returns dates in MM/DD/YYYY; consumer parses as DD/MM/YYYY → wrong dates

*These are the most common defects found during integration testing.*

### 4. Data Defects
**What:** Problems with data handling — incorrect data format, wrong data values, data corruption.

*Examples:*
- A field accepts negative values for age (should be validated)
- Truncation: storing "Alexander" in a 5-char field → "Alexa"
- Currency values stored as float → rounding errors in financial calculations

### 5. Performance Defects
**What:** The system is functionally correct but fails to meet performance requirements.

*Examples:*
- Correct query result, but takes 30 seconds (requirement: < 2 seconds)
- Memory leak — application slows down over 24 hours
- N+1 query problem — 1,000 database queries where 1 join query would suffice

*Q28 scenario:* A defect that only appears under heavy load is a performance/concurrency defect — not caught by functional testing, requires load/stress testing.

### 6. Usability Defects
**What:** The system works correctly but is confusing or difficult for users.

*Examples:*
- Error messages are cryptic technical codes (not user-friendly)
- Critical button is not visible without scrolling
- Forms don't indicate which fields are mandatory

---

## Defect Classification Framework

When classifying a defect (for Q6, Q11, Q16, Q27), answer:

| Dimension | What to identify |
|-----------|-----------------|
| **Type** | Computational, Logic, Interface, Data, Performance, Usability |
| **Origin** | Requirements, Design, Code, Communication |
| **Severity** | Critical, Major, Moderate, Minor |
| **Location** | Which module/component/function |
| **Discovery phase** | Unit, Integration, System, UAT, Production |

---

## Defect Severity Levels (Q11)

**Severity** = How badly the defect impacts system functionality or the user.

This is different from **Priority** (how urgently the defect needs to be fixed — a business decision). A cosmetic typo on the login screen might have low severity but high priority because executives will see it tomorrow.

| Severity Level | Description | Example |
|---------------|-------------|---------|
| **Critical / Blocker** | System crash, data loss, security breach, core feature completely broken | Login doesn't work at all, payment processes incorrectly |
| **Major / High** | Important feature broken, significant impact, but workaround exists | Search function returns wrong results |
| **Moderate / Medium** | Feature partially broken, minor workaround available | Sorting works but slow on large datasets |
| **Minor / Low** | Cosmetic issues, minor UI problems, enhancement requests | Typo in error message, minor alignment issue |

**Impact on testing priority:**
- Critical defects → immediate fix, block release, re-test top priority
- Major defects → must fix before release
- Moderate defects → fix in current release if possible, else defer
- Minor defects → low priority, can be deferred to next release

---

## Q17: Communication-Caused Defects (Detailed Analysis)

**Scenario:** Programmer A (poor communicator, doesn't get along with Programmer B) and Programmer B are working on interfacing modules.

**Likely defect types:**
- **Interface defects:** Different assumptions about what data is passed between modules
- **Sequence defects:** A assumes B initialises a shared resource; B assumes A does it
- **Error handling defects:** A doesn't know that B returns error code -1 for failure (assumes 0)
- **Data format defects:** Different assumptions about date formats, encoding, units

**Likely origins:**
- Lack of shared interface specification (poor documentation)
- No joint design review
- No integration test plan agreed upon

**Prevention:** A formal interface specification document agreed and signed off by both programmers. Mandatory integration test planning before coding begins.

---

## Quick Summary

- Defects originate from requirements, design, coding, and communication failures
- Requirement defects are the most expensive when caught late
- Defect types: Computational, Logic, Interface, Data, Performance, Usability
- Interface/Integration defects are the most common in integration testing
- Severity ≠ Priority: Severity is technical impact; Priority is business urgency
- Understanding defect origin guides both test design and defect prevention
