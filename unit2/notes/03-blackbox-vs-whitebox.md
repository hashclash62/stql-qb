# Chapter 3: Black Box vs White Box vs Gray Box Testing

---

## The Big Picture

Think of software as a locked safe. You can test it three ways:
- **Black box:** You can only see the outside. You try combinations and see what opens it.
- **White box:** You have the blueprints. You know exactly how the lock works internally and test every mechanism.
- **Gray box:** You have partial knowledge — maybe you know the model of lock but not the exact combination used.

Each approach reveals different kinds of defects.

---

## Black Box Testing

### What It Is
Testing based entirely on the **specification** — the expected inputs and outputs. The tester has no knowledge of the internal code structure.

### Characteristics
- Also called **specification-based** or **functional testing**
- Tests *what* the system does, not *how* it does it
- Test cases derived from requirements, use cases, user stories
- Can be done by testers who don't know how to program

### What It Finds
- Functional defects (system doesn't meet requirements)
- Missing features (requirement not implemented)
- Incorrect outputs for valid inputs
- Interface defects (wrong behaviour at UI or API boundary)
- Usability issues

### What It Misses
- Dead code (code that is never reached but might still contain bugs)
- Logic errors in branches that specification doesn't explicitly cover
- Performance issues inside specific code paths

### When to Use
- Acceptance testing, system testing
- When you want to test from the user's perspective
- When testers don't have source code access
- When testing third-party components

### Techniques
ECP, BVA, Decision Table, Cause-Effect Graphing, State Transition, Random Testing

---

## White Box Testing

### What It Is
Testing based on the **internal structure of the code** — logic, branches, paths, data flows. The tester reads the source code and designs tests to exercise specific code elements.

### Characteristics
- Also called **structural**, **glass-box**, or **code-based** testing
- Tests *how* the system does it
- Requires programming knowledge
- Coverage measured in terms of code elements (statements, branches, paths)

### What It Finds
- Logic errors (wrong condition, wrong operator)
- Dead code (unreachable code paths)
- Uninitialised variable usage
- Missing error handling in specific branches
- Loop boundary errors
- Performance bottlenecks in specific paths

### What It Misses
- Missing features (if a feature isn't coded, white box won't detect it's absent)
- Requirements not met (you test what was coded, not what was required)

### When to Use
- Unit testing (developer level)
- Security testing (looking for vulnerabilities in code paths)
- Optimisation testing (profiling specific paths)
- Safety-critical systems (aviation, medical — need formal path coverage proof)

### Techniques
CFG, Cyclomatic complexity, Branch/condition/path coverage, Data flow testing, Loop testing

---

## Gray Box Testing

### What It Is
A combination — tester has **partial knowledge** of the internal system. They know the architecture, database structure, or algorithms, but may not have full source code access.

### Characteristics
- Hybrid approach: functional tests informed by architectural knowledge
- Common in integration testing and API testing
- Tester might know: database schema, API design, system architecture, algorithms used

### What It Finds
- Integration defects that black box testing might miss (because you know how modules connect)
- Database-related defects (you know the schema — you can check data integrity)
- Security vulnerabilities at known API endpoints
- Configuration issues

### When to Use
- Integration testing
- API testing
- Security testing with partial architecture knowledge
- Web application testing (tester knows HTTP, cookies, sessions)

---

## Comparison Table

| Aspect | Black Box | White Box | Gray Box |
|--------|-----------|-----------|----------|
| **Knowledge needed** | Specification only | Full source code | Partial internal knowledge |
| **Who does it** | Testers (no coding needed) | Developers/technical testers | Testers with architectural knowledge |
| **Test design basis** | Requirements, spec | Code structure | Spec + partial internals |
| **Finds** | Functional gaps, missing features | Logic errors, dead code, coverage gaps | Integration defects, DB issues |
| **Misses** | Dead code, logic errors in spec gaps | Missing features, requirement violations | Depends on what partial info is available |
| **Coverage metric** | Requirement coverage | Code coverage | Both |
| **Used at level** | System, acceptance | Unit, component | Integration, API |

---

## When to Use Each — Practical Decision Guide

**Use Black Box when:**
- Testing from the end-user perspective
- Testing 3rd-party components you don't have source for
- Writing acceptance test cases from user stories
- Validating that requirements are actually implemented

**Use White Box when:**
- Testing individual functions/methods in unit testing
- Need proof of coverage for safety-critical standards
- Finding dead code or unreachable paths
- Security audit of known code

**Use Gray Box when:**
- Testing APIs (you know the API contract but not the implementation)
- Testing database integration (you have the schema)
- Finding defects at module boundaries
- Penetration testing (you have partial system knowledge)

---

## Static vs Dynamic Testing (Q18)

This is related but distinct — covers *when* testing executes the code.

| Aspect | Static Testing | Dynamic Testing |
|--------|---------------|-----------------|
| **Code execution** | No — examines code without running it | Yes — runs the code |
| **When** | Early in development | After code is written and compilable |
| **Techniques** | Code reviews, walkthroughs, static analysis tools | Unit tests, integration tests, all runtime testing |
| **Finds** | Syntax errors, standards violations, logic issues in reading | Runtime errors, functional defects, performance issues |
| **Tools** | SonarQube, ESLint, Checkstyle, Coverity | JUnit, Selenium, JMeter |

**Both contribute to quality:** Static testing (code review with SonarQube) catches code smells and security issues. Structural testing (JUnit with coverage) catches logic and integration defects. Together they form a strong quality safety net.

---

## Experience-Based Testing (Q8)

Not exactly black/white box — experience-based testing relies on the tester's expertise and intuition.

### Types

**Error Guessing:**
- The tester uses past experience to guess where bugs are likely to hide
- "I've seen many bugs around null handling, boundary conditions, and concurrency — let me specifically test those"
- No formal technique, but highly effective with experienced testers

**Exploratory Testing:**
- Simultaneous test design, execution, and learning
- No pre-written test cases — tester explores the application freely
- Uses findings from one test to decide what to test next
- Very effective for finding unexpected defects that scripted tests miss

**Checklist-Based Testing:**
- Use a checklist of commonly occurring defect types or test conditions
- More structured than error guessing but less formal than ECP/BVA

*Example of error guessing for a banking app:*
- Try transferring ₹0
- Try transferring more than the balance
- Try transferring to the same account
- Try a negative amount
- Try a very large amount (integer overflow?)
- Try concurrent transfers from the same account

---

## Quick Summary

- **Black box:** Test what it does; no code knowledge; finds functional gaps
- **White box:** Test how it works; needs code; finds structural/logic defects
- **Gray box:** Hybrid; partial internal knowledge; good for integration and API testing
- They are complementary — use all three for thorough coverage
- **Static testing** = review code without running it; **Dynamic testing** = run the code
- **Experience-based testing** = error guessing + exploratory testing; relies on tester expertise
- Neither black nor white box alone is sufficient — they catch different classes of defects
