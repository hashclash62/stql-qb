# Chapter 3: Design and Architecture for Test Automation

## The Analogy Before the Definition

If you build a house without a blueprint, every room is different, pipes don't connect, and you can't add a second floor later without tearing everything down. Automation without architecture is the same — it works initially, then becomes unmaintainable as the application grows.

A good automation architecture is the blueprint that makes your test suite maintainable, scalable, and reusable.

---

## Why Architecture Matters (Q4, Q25, Q32)

Without architecture:
- Duplicated code everywhere — change one button ID, update 200 scripts
- Test logic mixed with test data — hard to add new data sets
- Scripts are fragile — any UI change breaks everything
- New team members can't understand or extend the suite

With good architecture:
- Changes in UI → update in ONE place (page object)
- New test data → add to a spreadsheet/file, no code change
- New team members → read the structure, understand immediately

---

## Common Automation Framework Types

### 1. Linear (Record and Playback)
The simplest approach — record your actions, replay them.

```
Record → Script → Replay
```

- ✅ Easy to start, no coding
- ❌ Breaks on any UI change, no reuse, hard to maintain
- **Use case:** Demos, one-off tests. Never for real automation.

---

### 2. Modular Framework
Test logic broken into reusable functions/modules.

```
loginModule()  +  searchModule()  +  checkoutModule()
```

- ✅ Reuse modules across tests
- ❌ Test data still hardcoded inside modules
- **Use case:** Small to medium projects

---

### 3. Data-Driven Framework
Test logic separated from test data. Data stored externally (CSV, Excel, JSON, DB).

```
TestScript.java ← reads from ← testdata.csv
```

```
[username, password, expected_result]
alice, pass123, SUCCESS
bob, wrongpass, FAIL
"", pass123, ERROR
```

- ✅ Add new test cases just by adding rows to the data file
- ✅ Non-technical people can add test data
- ❌ Need code to read the data files
- **Use case:** When many variations of the same test are needed

---

### 4. Keyword-Driven Framework
Test steps written as keywords (like English commands) in a table. The framework interprets the keywords.

```
| Keyword       | Parameter 1 | Parameter 2 |
|---------------|-------------|-------------|
| OpenBrowser   | Chrome      |             |
| GoToURL       | /login      |             |
| EnterText     | username    | alice        |
| EnterText     | password    | pass123      |
| ClickButton   | Login       |             |
| VerifyText    | Welcome     |             |
```

- ✅ Non-technical stakeholders can write tests
- ✅ Highly reusable keyword library
- ❌ More complex to set up initially
- **Use case:** Acceptance testing involving business analysts

---

### 5. Page Object Model (POM) — Most Common for Web
Each web page/screen gets its own **class**. The class contains the locators (how to find elements) and the actions (what to do with them).

```
LoginPage.java
    - usernameField
    - passwordField
    - loginButton
    - enterUsername(String)
    - enterPassword(String)
    - clickLogin()

LoginTest.java
    - uses LoginPage to write tests
    - doesn't know about HTML — just calls loginPage.enterUsername("alice")
```

**Why this is powerful:**
- If the button ID changes → update in ONE place (LoginPage.java)
- All tests using LoginPage automatically get the fix
- Tests read like plain English: `loginPage.enterUsername("alice").clickLogin()`

---

### 6. Hybrid Framework
Combines Data-Driven + Keyword-Driven + POM. The most common real-world setup.

```
Architecture:
├── pages/          — Page Objects (POM layer)
│   ├── LoginPage.java
│   └── CheckoutPage.java
├── tests/          — Test classes
│   └── LoginTest.java
├── data/           — Test data files
│   └── loginData.csv
├── utils/          — Utilities (screenshot, reporting, wait helpers)
└── config/         — Environment config (URLs, credentials per env)
```

---

## Architecture for Banking App Automation (Q32)

> "A banking application requires frequent updates and regression testing across multiple modules."

Recommended architecture:

```
┌─────────────────────────────────────────┐
│           Test Runner (TestNG/JUnit)     │
├─────────────────────────────────────────┤
│         Test Layer (test classes)        │
│  LoginTest  TransferTest  AccountTest   │
├─────────────────────────────────────────┤
│        Business Layer (workflows)        │
│  LoginFlow  MoneyTransferFlow           │
├─────────────────────────────────────────┤
│         Page Object Layer               │
│  LoginPage  DashboardPage  TransferPage │
├─────────────────────────────────────────┤
│           Framework Utilities           │
│  DriverManager  WaitHelper  Screenshot  │
├─────────────────────────────────────────┤
│         Data and Config Layer           │
│  testdata/   config/dev.properties     │
└─────────────────────────────────────────┘
```

Justification:
- POM layer: UI changes only require updates in page classes
- Business layer: full workflows reusable across multiple tests
- Data layer: new test cases added without touching code
- Config layer: run same tests against dev/staging/prod by switching config

---

## V&V Model and Automation (Q23)

Automation can be applied at every level of the V-Model:

```
Requirements        ←→   Acceptance Tests (automated via BDD/Cucumber)
System Design       ←→   System Tests (automated Selenium/Cypress end-to-end)
HLD                 ←→   Integration Tests (automated API tests with RestAssured)
LLD                 ←→   Unit Tests (automated JUnit/TestNG)
```

Left side: as each level is designed, automation test scripts are written  
Right side: those scripts execute automatically in the CI pipeline

---

## Remote Execution — Test Console and Execution Machines (Q22)

For large test suites, tests run on multiple machines in parallel. A **test console** coordinates this.

```
                  ┌─── Test Console ───┐
                  │  (orchestrator)    │
                  │  - distributes     │
                  │    test cases      │
                  │  - collects results│
                  └─────────┬──────────┘
           ┌────────────────┼────────────────┐
           ↓                ↓                ↓
    Machine 1         Machine 2         Machine 3
  (runs TC 1–50)   (runs TC 51–100)  (runs TC 101–150)
    Chrome           Firefox           IE/Edge
    Windows          Linux             MacOS
```

**Benefits:**
- Parallel execution — 150 tests run in 1/3 the time
- Cross-browser / cross-OS coverage simultaneously
- Test console aggregates results into one report

**Tools that support this:** Selenium Grid, BrowserStack, Sauce Labs, TestNG parallel execution

---

## Automation Script Example (Q21)

> "Execute two instances of scen1 in a loop for 10 times. scen1 executes testProgram1 (TC 2,1,5), testProgram2, and testProgram3."

```java
for (int i = 0; i < 10; i++) {
    // Run two instances simultaneously (parallel threads)
    Thread instance1 = new Thread(() -> {
        testProgram1(new int[]{2, 1, 5});
        testProgram2();
        testProgram3();
    });

    Thread instance2 = new Thread(() -> {
        testProgram1(new int[]{2, 1, 5});
        testProgram2();
        testProgram3();
    });

    instance1.start();
    instance2.start();
    instance1.join();
    instance2.join();
}
```

---

## Quick Summary

| Framework Type | Key idea |
|---------------|---------|
| Linear | Record and playback — fragile, no reuse |
| Modular | Reusable modules — better, but data still hardcoded |
| Data-Driven | Test logic + data separated — easy to add test cases |
| Keyword-Driven | English keyword tables — non-technical authors |
| Page Object Model | Each page = a class — change locator in one place |
| Hybrid | Best of all — POM + data-driven + keyword |

| Remote execution concept | Role |
|--------------------------|------|
| Test console | Orchestrates and distributes test cases to machines |
| Execution machine | Runs assigned test cases in its own environment |
| Parallel execution | Multiple machines run different tests simultaneously |
