# Chapter 2: Levels of Testing — Non-Functional (Performance, Recovery, Regression, Configuration)

---

## What is Non-Functional Testing?

Once you know the software *works correctly* (functional tests pass), the next question is: does it work *well*?

Non-functional testing answers:
- Is it fast enough? (Performance)
- Does it survive heavy load? (Load/Stress)
- Can it recover from failure? (Recovery)
- Does it still work after code changes? (Regression)
- Does it work on all supported hardware/software combinations? (Configuration)

A login function that works correctly but takes 30 seconds is not acceptable. Non-functional testing catches these issues.

---

## Performance Testing (Q12, Q31)

### What it is
Testing how well the system performs under various conditions — measuring speed, responsiveness, stability, and resource usage.

**Why it matters:** Users abandon slow applications. In a banking system, a slow transaction engine can cause timeouts, incorrect balances, or compliance violations.

### Types of Performance Tests

#### Load Testing
**What:** Tests behaviour under *expected* normal load.

*Goal:* Verify the system meets performance requirements (e.g., response time < 2 seconds) when used by the expected number of concurrent users.

*Example:* An e-commerce site expects 10,000 simultaneous users during a sale event. Load test simulates 10,000 users and verifies response time stays under 2 seconds.

#### Stress Testing
**What:** Tests behaviour *beyond* normal capacity — pushes the system to its limits and beyond.

*Goal:* Find the breaking point. Understand how the system fails (gracefully or catastrophically). Find the maximum capacity.

*Example:* Keep increasing concurrent users — 10,000, 20,000, 50,000 — until the system starts failing. Does it give error messages (good) or corrupt data (bad)?

#### Spike Testing
**What:** Sudden, extreme increase in load for a short period.

*Example:* A flash sale starts exactly at midnight. Traffic spikes from 1,000 to 50,000 users in 10 seconds. Does the system handle this sudden spike?

#### Soak/Endurance Testing
**What:** Runs the system under normal load for an extended period (hours, days).

*Goal:* Find memory leaks, resource exhaustion that only appear over time.

*Example:* Running a server continuously for 72 hours at normal load — does memory usage gradually creep up until the server crashes?

### Performance Testing Tools
- **Apache JMeter** — open source, widely used for HTTP load testing
- **Gatling** — high-performance load testing
- **Locust** — Python-based, scriptable load testing
- **k6** — modern developer-focused load testing

### Online Fast Food System (Q24 — Performance)
Performance test objectives:
- Response time for order placement < 3 seconds under 200 concurrent users
- Bill calculation < 1 second
- System remains stable during lunch rush (spike of 500 orders in 5 minutes)

---

## Recovery Testing (Q12, Q22)

### What it is
Testing how well the system **recovers from failures** — crashes, hardware failures, network outages, power cuts.

*Goal:* Verify the system can return to normal operation after failure, and that data integrity is maintained.

### What to Test
- **System crash recovery:** After a forced crash (kill the process), does the system restart correctly? Is data consistent?
- **Network failure recovery:** If the network drops during a transaction, is the transaction rolled back correctly? No duplicate charges?
- **Hardware failure:** If a disk fails, does the system fail over to backup?
- **Data corruption:** If data is corrupted, does the system detect it and recover?

### Metrics
- **Recovery Time Objective (RTO):** Maximum acceptable time to restore the system
- **Recovery Point Objective (RPO):** Maximum acceptable data loss (how old can the last good backup be?)

### Cancer Therapy Laser System (Q22 — Recovery)
A laser therapy system must:
- Stop laser operation immediately and safely on software error
- Restart in a known safe state (not resume mid-operation)
- Log all events for audit trail

*Recovery test:* Simulate power failure mid-session. Verify: laser powers off safely, patient data is preserved, system restarts in "safe" state requiring technician confirmation before resuming.

---

## Regression Testing (Q23, Q29)

### What it is
Re-running previously passing tests after a **code change** to verify that the change didn't break anything that was working before.

*Analogy:* Fixing one leak in a pipe without checking that you didn't accidentally create a new leak somewhere else.

### Why It's Important (Q23)
When a new software release is developed:
- New features are added
- Old bugs are fixed
- Code is refactored

Any of these changes can unintentionally break existing functionality. Regression testing is the safety net.

**What items from the previous release are useful? (Q23):**
- All previously passing test cases (the regression test suite)
- Defect reports from the previous release (to ensure those defects aren't reintroduced)
- Requirements documents (to check new release still meets all original requirements)
- Performance baselines (to catch performance regressions)

### Regression Testing Strategy
Running the entire test suite after every change is expensive. Smart regression testing:
- **Risk-based selection:** Run tests for areas most likely affected by the change
- **Prioritisation:** Run smoke tests first, then critical paths, then full suite
- **Automation:** Regression testing is the best candidate for automation — run overnight without human effort

### 100% Unit Test Coverage Still Has Integration Defects (Q30)
This is a classic exam scenario. Why can you have 100% unit test coverage and still find defects during integration?

- Unit tests test **units in isolation** using mocks/stubs
- The mock might return values that the real dependency never returns in practice
- Interface defects between modules are NOT caught by unit tests
- Data format mismatches between modules only appear during integration
- **Coverage measures which lines were executed, not whether interactions are correct**

*Solution:* Add integration tests. Track integration test coverage separately.

---

## Configuration Testing (Q21)

### What it is
Testing the software on all the different hardware, software, and network configurations it must support.

### When It Matters
- Systems deployed across different operating systems (Windows/Linux/macOS)
- Systems with hardware integrations (displays, sensors, printers)
- Enterprise software that runs in different database/network configurations
- Embedded systems in varied hardware environments

### Air Traffic Control System (Q21)
The system interfaces with:
- Different display types (various sizes, resolutions)
- Different radar detector models
- Different communication devices (radio frequencies, protocols)
- Different configurations (single controller, multiple controllers)

**Configuration test approach:**
1. Document all supported configurations (hardware + software combinations)
2. Create a configuration matrix (which combos are most critical/common)
3. Test each configuration with a core functional test suite
4. Pay special attention to interactions with each hardware device type
5. Test boundary configurations (minimum spec hardware, maximum users)

---

## Handling Load-Only Defects (Q28)

**Scenario:** A defect occurs only under heavy load; it doesn't appear during functional testing.

**Defect type:** Performance/concurrency defect — likely a race condition, resource exhaustion, or connection pool overflow.

**Detection strategy:**
- Add load testing to the test suite (functional tests alone won't find this)
- Use concurrent test execution tools (JMeter, Gatling)
- Monitor resource usage (CPU, memory, DB connections) during load tests
- Add stress tests to find the exact load threshold where the defect appears

**Prevention:**
- Code reviews focused on thread safety, connection pooling, locking
- Static analysis tools that detect common concurrency anti-patterns
- Load testing in CI pipeline (at least a lightweight version)

---

## Preventing Regression Defects (Q29)

When many defects come from code changes to existing functionality:

1. **Automated regression test suite:** Every commit triggers automated regression tests
2. **CI/CD pipeline:** No code merges unless regression tests pass
3. **Feature flags:** New code disabled by default, gradually enabled — reduces regression risk
4. **Code coverage monitoring:** Ensure changes don't reduce test coverage
5. **Static analysis:** Detects dangerous code patterns before testing
6. **Peer code review:** Reviewer specifically checks: "could this break anything else?"
7. **Changelog discipline:** Document what changed — helps testers focus regression efforts

---

## Quick Summary

- **Performance testing** = Does the system meet speed/capacity requirements?
- **Load testing** = Normal expected load
- **Stress testing** = Beyond normal — find the breaking point
- **Spike testing** = Sudden extreme load burst
- **Soak testing** = Extended normal load — find slow leaks
- **Recovery testing** = Can the system recover from failures with data integrity intact?
- **Regression testing** = After any change, verify nothing previously working is now broken
- **Configuration testing** = Does it work across all supported hardware/software environments?
- 100% unit test coverage does NOT guarantee no integration defects
- Regression testing is best automated — the ideal candidate for CI/CD integration
