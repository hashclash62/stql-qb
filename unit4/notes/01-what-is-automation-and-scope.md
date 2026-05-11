# Chapter 1: What is Test Automation and What Should You Automate?

## The Analogy Before the Definition

Imagine a factory that makes 1000 bottles per hour. A human quality inspector can manually check maybe 50 bottles per hour — and gets tired, distracted, and misses things. An automated sensor checks every single bottle at full speed, consistently, without getting tired.

Test automation is that sensor for software. You write a script once, and it can test your software thousands of times, instantly, without human fatigue.

---

## What is Test Automation? (Q18)

Test automation is the use of **software tools** to execute test cases, compare actual results with expected results, and report outcomes — **automatically**, without manual intervention.

The test engineer:
1. Writes a test script (code that exercises the application)
2. Runs the script
3. The tool reports: how many passed, how many failed, what the failures were

The engineer doesn't click through the app manually — the script does it.

---

## Objectives of Test Automation

- **Reduce manual effort** for repetitive tests (especially regression)
- **Increase test execution speed** — run 500 tests in 10 minutes vs. 2 days manually
- **Improve consistency** — a script always does the same steps; humans make mistakes
- **Enable continuous testing** — integrated into CI/CD pipelines, tests run on every code commit
- **Extend test coverage** — more test cases can be run in the same time
- **Free engineers for creative work** (Q17) — automation handles the mundane; testers focus on exploratory and design

---

## Types of Testing Suitable for Automation (Q19)

Not everything should be automated. Here's a guide:

### ✅ Good for Automation

| Testing Type | Why Automation Works Well |
|-------------|--------------------------|
| Regression testing | Run the same tests after every change — tedious manually |
| Performance testing | Simulating 10,000 concurrent users is only possible with tools |
| Smoke testing | Quick sanity check after every build — needs to be fast |
| Data-driven testing | Same test with 100 data sets — easy to loop in automation |
| API testing | No UI, pure logic — very stable, easy to automate |
| Load testing | Can't simulate load without tools |
| Repeated execution | Same test case run hundreds of times for soak testing |

### ❌ Poor for Automation / Should Stay Manual

| Testing Type | Why Manual is Better |
|-------------|---------------------|
| Exploratory testing | Requires human creativity and intuition |
| Usability testing | "Does this feel intuitive?" — needs human judgment |
| One-time tests | Not worth writing a script for a test run once |
| Frequently changing UI | Scripts break every release — high maintenance |
| Ad hoc testing | No fixed steps to automate |
| First-time testing of new features | You don't know what to expect yet |

---

## Scope of Automation (Q20, Q24)

The scope defines **how wide** you cast the automation net.

### 1. Types of Testing
Automate: regression, smoke, performance, API  
Don't automate: exploratory, usability, UAT

### 2. Stable Application Areas
Only automate features that are **unlikely to change frequently**. If the UI changes every sprint, your selenium scripts will break every sprint.

> Core business logic (login, checkout, payment calculation) is stable → good to automate  
> Marketing banners, homepage layout → changes often → keep manual

### 3. Standard-Based Tests
Tests that follow a fixed standard or protocol (e.g., API must return JSON conforming to a schema, accessibility tests following WCAG) are excellent automation candidates.

### 4. Management Aspects
- ROI consideration: Does the cost of writing + maintaining the script justify the savings?
- If a test runs once a month: probably not worth automating
- If a test runs 50 times per month: definitely worth automating
- Rule of thumb: automate if the test will run enough times that automation time < manual time

### Scope Formula (rough)
```
Break-even point = Script writing time / Time saved per run

If total runs > break-even point → automation is worth it
```

Example: Writing a regression script takes 4 hours. Each manual run takes 30 min. Break-even = 4 hours / 0.5 hours = 8 runs. After 8 runs, automation saves time.

---

## When to Stop Testing (Q9)

Exit criteria define when enough testing has been done:

| Criterion | Example |
|-----------|---------|
| Test coverage | 90% code coverage achieved |
| Defect rate | Less than 2 new defects per day for 3 consecutive days |
| Defect density | Fewer than 0.5 defects/KLOC remaining |
| Test execution | All test cases executed, 95% pass |
| Schedule | Deadline reached with acceptable risk |
| Risk-based | All high-priority test cases passed |

---

## Quick Summary

| Concept | One-liner |
|---------|-----------|
| Test automation | Scripts execute tests automatically and report results |
| Objectives | Speed, consistency, regression coverage, free engineers for creative work |
| Good for automation | Regression, smoke, API, performance, data-driven |
| Bad for automation | Exploratory, usability, one-time, frequent UI changes |
| Scope | Stable features, standard-based tests, high ROI tests |
| When to stop | Exit criteria met: coverage, defect rate, schedule |
