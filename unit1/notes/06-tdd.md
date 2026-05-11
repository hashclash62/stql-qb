# Chapter 6: Test Driven Development (TDD)

## The Analogy Before the Definition

Imagine you're building a chair. Normally: build the chair → sit on it → see if it holds. 

TDD reverses this: before building, you write down "the chair must hold 120kg, must be stable on uneven floors, must not wobble." THEN you build. You don't even pick up a hammer until you know exactly what "done" looks like.

That's TDD. You write the test first. The test fails (because the code doesn't exist). Then you write the code to make the test pass.

---

## What is TDD?

Test Driven Development is a software development approach where you:
1. **Write a test** for a small piece of functionality
2. **Run it** — it fails (Red), because the code doesn't exist yet
3. **Write the minimum code** needed to make it pass
4. **Run it again** — it passes (Green)
5. **Refactor** the code — clean it up without changing behaviour
6. **Repeat** for the next small piece of functionality

The mantra: **Red → Green → Refactor**

---

## The TDD Cycle in Detail

```
    ┌──────────────────────────────────────────┐
    │                                          │
    │    1. Write a FAILING test (RED)         │
    │               ↓                          │
    │    2. Write MINIMUM code to pass (GREEN) │
    │               ↓                          │
    │    3. REFACTOR code (stay GREEN)         │
    │               ↓                          │
    │    4. Next requirement → go to step 1    │
    │                                          │
    └──────────────────────────────────────────┘
```

Each cycle should be **small** — typically 5–10 minutes per cycle.

---

## TDD Walkthrough — Login Functionality (Q24)

Requirement: "A login function should return `true` for valid credentials and `false` for invalid credentials."

### Step 1: Write the failing test (RED)

```java
@Test
public void testValidLogin() {
    LoginService login = new LoginService();
    assertTrue(login.authenticate("alice", "pass123"));
}
```

Run this test → **FAILS** because `LoginService` and `authenticate()` don't exist yet.

### Step 2: Write minimum code to pass (GREEN)

```java
public class LoginService {
    public boolean authenticate(String username, String password) {
        return username.equals("alice") && password.equals("pass123");
    }
}
```

Run the test → **PASSES**. But this is hardcoded — that's fine for now!

### Step 3: Refactor

Now improve the code to look up a database:

```java
public class LoginService {
    private UserRepository repo;

    public LoginService(UserRepository repo) {
        this.repo = repo;
    }

    public boolean authenticate(String username, String password) {
        User user = repo.findByUsername(username);
        if (user == null) return false;
        return user.getPassword().equals(password);
    }
}
```

Update the test to use a mock/stub for the repository. Tests still pass.

### Step 4: Add next test case

```java
@Test
public void testInvalidLogin() {
    LoginService login = new LoginService(mockRepo);
    assertFalse(login.authenticate("alice", "wrongpass"));
}

@Test
public void testEmptyUsername() {
    LoginService login = new LoginService(mockRepo);
    assertFalse(login.authenticate("", "pass123"));
}
```

Each new test drives a new bit of code to be written.

---

## TDD for Student Result Processing (Q12)

Requirement: "Calculate a student's grade based on marks."
- ≥90 → A
- ≥75 → B
- ≥60 → C
- <60 → Fail

### TDD steps:

**Test 1 (RED):**
```java
@Test
public void testGradeA() {
    ResultProcessor rp = new ResultProcessor();
    assertEquals("A", rp.getGrade(95));
}
```

**Code 1 (GREEN → hardcoded):**
```java
public String getGrade(int marks) {
    return "A"; // hardcoded just to pass first test
}
```

**Test 2 forces real logic:**
```java
@Test
public void testGradeB() {
    assertEquals("B", rp.getGrade(80));
}
```

Now "A" hardcoded fails for Test 2. You must write real logic:
```java
public String getGrade(int marks) {
    if (marks >= 90) return "A";
    if (marks >= 75) return "B";
    if (marks >= 60) return "C";
    return "Fail";
}
```

Both tests pass. Continue adding Test 3 (grade C), Test 4 (Fail), Test 5 (boundary: exactly 90), etc.

---

## TDD in a Team Unfamiliar with Automation (Q34)

If the team doesn't know automation tools:

1. **Start simple** — use JUnit for Java (built into most IDEs, no special setup)
2. **Use a kata** — practice TDD on a simple exercise (e.g., FizzBuzz) before applying to production code
3. **Pair program** — experienced developer + unfamiliar developer work together
4. **Go slow** — write one tiny test at a time; don't try to automate everything at once
5. **Show value early** — when TDD catches a regression that would have reached production, the team believes in it

---

## Benefits of TDD

| Benefit | Why it matters |
|---------|---------------|
| Acts as documentation | Tests show exactly what the code is supposed to do |
| Catches regressions instantly | Every time you change code, all existing tests re-run |
| Forces simple design | Hard-to-test code = bad design; TDD forces modular code |
| Confidence to refactor | With tests passing, you can clean up code safely |
| Fewer defects in production | Defects are caught at the moment of writing, not months later |
| Reduces debugging time | You know exactly which function broke (the one that just failed) |

---

## Challenges of TDD

| Challenge | Description |
|-----------|-------------|
| Mindset shift | Developers find it counter-intuitive to write tests before code |
| Slow initially | Takes time to write tests, feels like less "productive" work |
| Hard for UI | TDD works great for logic, but is tricky for UI interactions |
| Legacy code | Hard to apply TDD on existing code without refactoring |
| Team discipline | One person skipping tests breaks the whole approach |
| Mock complexity | Heavy use of mocks/stubs can make tests fragile |

---

## TDD vs Traditional Testing

| | TDD | Traditional Testing |
|-|-----|---------------------|
| When tests written | Before code | After code |
| Who writes tests | Developer | Tester (often) |
| Test coverage | High (every feature has a test) | Depends on time/resource |
| Defect detection | During coding | After coding complete |
| Design quality | Forces modular design | No design impact |
| Documentation | Tests are living documentation | Separate test docs |

---

## Quick Summary

| Concept | One-liner |
|---------|-----------|
| TDD | Write failing test → write code to pass → refactor → repeat |
| Red | Test is written and fails (code doesn't exist yet) |
| Green | Minimum code written to make test pass |
| Refactor | Clean up code without breaking tests |
| Benefit: documentation | Tests show intended behaviour of every function |
| Benefit: catch regressions | Old tests re-run on every change |
| Challenge: mindset | Developers must write tests before code — takes getting used to |
