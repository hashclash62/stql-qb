# Unit 4: Software Test Automation — Notes Index

## How to Use These Notes

Start with Chapter 1 (scope and what to automate) to set the context. Then Chapter 3 (architecture) is the highest-value chapter for exams. Chapter 6 (random + PBT) is a frequently asked distinct topic — read it separately.

---

## Reading Order

| File | Topic | Covers QB Questions |
|------|-------|---------------------|
| [mental-model.md](../mental-model.md) | Topic groupings + priority guide | All |
| [01-what-is-automation-and-scope.md](./01-what-is-automation-and-scope.md) | Definition, objectives, what to automate, scope, exit criteria | Q9, Q17, Q18, Q19, Q20, Q24 |
| [02-skills-for-automation.md](./02-skills-for-automation.md) | Technical/testing/domain skills, DevOps testing | Q1, Q3, Q26 |
| [03-design-and-architecture.md](./03-design-and-architecture.md) | Framework types, POM, hybrid, V&V model, remote execution, automation script | Q4, Q21, Q22, Q23, Q25, Q32, Q34 |
| [04-tool-requirements-and-selection.md](./04-tool-requirements-and-selection.md) | Tool categories, selection factors, deployment, build and release | Q6, Q8, Q10, Q11, Q12, Q13 |
| [05-challenges-in-automation.md](./05-challenges-in-automation.md) | GUI fragility, pop-ups, config management, maintenance, flaky tests, edge cases | Q2, Q14, Q15, Q16, Q33 |
| [06-random-and-property-based-testing.md](./06-random-and-property-based-testing.md) | Random testing, PBT, real-time systems, regression automation | Q5, Q7, Q27, Q28, Q29, Q30, Q31 |

---

## Syllabus Coverage Checklist

- [x] Software Test Automation — definition and objectives
- [x] Skills needed for Automation
- [x] Scope of Automation
- [x] Design and Architecture for Automation
- [x] Requirements for a Test Tool
- [x] Challenges in Automation
- [x] Automated test generation — using Random Testing
- [x] Property-Based Testing for Real-Time Systems

---

## Key Diagrams to Draw in Exam

1. **Hybrid Automation Framework** — folder structure diagram with layers: tests → business layer → page objects → utils → data/config
2. **Remote execution diagram** — Test Console → distributes to Machine 1, 2, 3 (with browser/OS labels)
3. **Automation in V-Model** — same V-shape as Unit 1, but with automation tools annotated at each level
4. **CI/CD pipeline with automation** — Commit → Build → Smoke Tests → Deploy Staging → Regression → Deploy Prod
5. **Random Testing vs PBT comparison table** — 6 rows of comparison
6. **PBT property example** — a property definition + what the tool does with it

---

## Quick-Revision Cheat Sheet

### Test Automation Objectives
- Speed up regression testing
- Improve consistency (no human error)
- Enable CI/CD continuous testing
- Free engineers for creative/exploratory work

### What to Automate vs Not
| ✅ Automate | ❌ Don't Automate |
|------------|-----------------|
| Regression, smoke, performance | Exploratory, usability |
| API tests | One-time tests |
| Data-driven tests | Frequently changing UI |
| Standard-based tests | Ad hoc, first-time tests |

### Framework Types (in order of sophistication)
1. Linear — record/playback (fragile)
2. Modular — reusable functions
3. Data-Driven — logic + data separated
4. Keyword-Driven — English keyword tables
5. Page Object Model — each page = a class
6. Hybrid — combines all above

### POM Key Idea
```
LoginPage.java holds ALL locators + actions for login page
LoginTest.java uses LoginPage → tests don't touch HTML directly
UI change → update LoginPage only → all tests automatically fixed
```

### Tool Categories
| Need | Tool |
|------|------|
| Web UI | Selenium, Cypress, Playwright |
| API | RestAssured, Postman |
| Performance | JMeter, Gatling, k6 |
| Mutation testing | PIT |
| Test reporting | Allure, ExtentReports |
| Test data | Mockaroo, Faker |

### Random Testing vs PBT
| | Random | PBT |
|-|--------|-----|
| Input | Random | Random |
| Oracle | Predefined per input | Property (universal rule) |
| Output on fail | Crash/error found | Minimal failing example (shrunk) |
| Use | Stress testing, fuzzing | Invariant validation |

### PBT Properties Examples
- Sort: output has same length, is ordered, has same elements
- Add: commutative `add(a,b) == add(b,a)`
- Encode/decode: round-trip `encode(decode(x)) == x`
- Banking: balance never negative, total money conserved

### Top Automation Challenges
1. UI changes break tests → POM + stable locators
2. Pop-ups interrupt → explicit waits + dismiss in test env
3. Config mess → layered properties files + env variables
4. High maintenance → POM + independent tests + data factories
5. Flaky tests → explicit waits + test isolation
