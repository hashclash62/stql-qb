# Chapter 2: Skills Needed for Test Automation

## The Analogy Before the Definition

A driver's licence alone doesn't qualify you to drive a Formula 1 car. Test automation is to manual testing what F1 racing is to regular driving — it requires all the same base skills, plus a whole new set of technical ones layered on top.

---

## Why Skills Matter

A common mistake: "Let's just record our manual tests and play them back." This works for 5 minutes. Then the UI changes, the recorded script breaks, and no one knows how to fix it because no one on the team knows how the script works.

Good automation requires people who can **write**, **maintain**, and **debug** automation code.

---

## Skills Needed for Automation (Q3, Q26)

### 1. Programming/Scripting Skills
The most fundamental requirement. Automation test scripts are code.

| Language/Tool | Common Use |
|--------------|------------|
| Java | Selenium WebDriver, TestNG, JUnit |
| Python | Pytest, Selenium, Robot Framework |
| JavaScript | Cypress, Playwright |
| C# | Selenium with NUnit, SpecFlow |
| Shell scripting | Build and CI/CD pipeline scripts |

The automation engineer must be able to:
- Write functions, loops, conditions
- Handle exceptions (test doesn't crash when element not found)
- Read and parse files (test data from CSV/Excel/JSON)
- Work with version control (Git)

### 2. Testing Knowledge
Automation without testing knowledge = fast bad tests.

- Understand test design techniques (ECP, BVA — Unit 2)
- Know what makes a good test case (one purpose, clear assertion)
- Understand defect lifecycle (log, track, verify)
- Know when to automate vs. not

### 3. Tool Knowledge
Specific tools used in the project:

| Category | Tools |
|----------|-------|
| Web UI | Selenium, Cypress, Playwright |
| API | Postman, RestAssured, SoapUI |
| Mobile | Appium, Espresso |
| Performance | JMeter, Gatling |
| Test management | Jira, TestRail |
| CI/CD | Jenkins, GitHub Actions |

### 4. Domain Knowledge
An automation engineer testing a banking app needs to understand:
- What a transaction looks like
- What constraints exist (e.g., can't transfer negative amount)
- What edge cases matter in finance

Without domain knowledge, they'll automate the obvious paths and miss the critical ones.

### 5. Framework and Architecture Knowledge
Understanding framework concepts:
- Page Object Model (POM) — for maintainable UI tests
- Data-driven framework — separates test data from test logic
- Keyword-driven framework — test steps described in keywords
- CI/CD integration — running tests automatically on every commit

### 6. Analytical and Debugging Skills
When a test fails:
- Is it a real defect? Or a flaky test? Or an environment issue?
- How to read stack traces
- How to debug a script step by step
- How to write logs and screenshots in automation to aid diagnosis

---

## Junior Tester Automation Skills Scenario (Q26)

> "A junior tester is assigned to develop automation scripts for regression testing."

What skills should they have?

**Must-have (basics):**
- At least one scripting language (Python or Java)
- Basic Selenium or Cypress usage
- Ability to write JUnit/TestNG tests
- Understanding of regression testing concepts
- Ability to use Git for version control

**Good to have:**
- Page Object Model
- Read/write test data from files
- Integrate with CI tool (Jenkins basic setup)

**Mentoring they'll need:**
- Framework design decisions
- When to use waits (explicit vs implicit in Selenium)
- How to handle flaky tests
- CI/CD integration and configuration

---

## DevOps Environment Testing Challenges (Q1)

In DevOps, code is deployed multiple times per day. Testing must keep up.

| Challenge | Mitigation |
|-----------|-----------|
| Tests must run fast (feedback within 10 min) | Parallelise test execution; only run smoke on every commit |
| Environment differences (dev ≠ staging ≠ prod) | Use containerisation (Docker) for consistent test environments |
| Frequent changes break tests | Robust Page Object Model; stable selectors (IDs over XPath) |
| No dedicated "test phase" | Integrate tests into CI/CD pipeline — run on every merge |
| Multiple test environments | Configuration management for environment-specific settings |

---

## Quick Summary

| Skill | Why it matters |
|-------|---------------|
| Programming | Scripts are code — must be written, maintained, debugged |
| Testing knowledge | Good automation = good test design |
| Tool knowledge | Need to use the right tool for the right type of test |
| Domain knowledge | Understand what's being tested to test it meaningfully |
| Framework knowledge | Maintainable architecture (POM, data-driven) |
| Debugging | Diagnose script failures vs real defects |
