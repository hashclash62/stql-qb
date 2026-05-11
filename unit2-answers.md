# Unit 2: Testing Techniques Answers

Subject: Software Testing and Quality
Unit: Testing Techniques

---

## 1. Given a system with multiple modules, demonstrate how Top-down and Bottom-up Integration Testing would be performed.

Integration testing checks whether different modules work correctly when combined. In a system with multiple modules, integration can be done using top-down or bottom-up strategy.

Example system: Online shopping application with modules:

- User Interface
- Login
- Product Search
- Cart
- Payment
- Order Management
- Database Access

Top-down integration starts from the top-level control module and gradually integrates lower-level modules. If lower modules are not ready, stubs are used.

```text
User Interface
      |
      v
Login / Product Search / Cart
      |
      v
Payment / Order / Database
```

Steps in top-down testing:

1. Test the main user interface flow.
2. Use stubs for unavailable modules such as payment or database.
3. Replace stubs with real modules one by one.
4. Test control flow and data flow between modules.

Bottom-up integration starts from lower-level modules and moves upward. If upper modules are not ready, drivers are used to call lower modules.

```text
Database / Payment / Order
      |
      v
Cart / Search / Login
      |
      v
User Interface
```

Steps in bottom-up testing:

1. Test database, payment, and order modules first.
2. Use drivers to call these modules.
3. Integrate middle-level modules such as cart and login.
4. Finally integrate the user interface.

Top-down testing detects design and control flow defects early, while bottom-up testing strongly verifies utility and service modules. Both approaches help find interface defects between modules.

---

## 2. A wholesaler sells printer cartridges. The minimum order quantity is 5. There is a 20% discount for orders of 100 or more printer cartridges. You have been asked to prepare test cases using various values for the number of printer cartridges ordered. Which of the following groups contain three test inputs that would be generated using Boundary Value Analysis?

Boundary Value Analysis (BVA) is a black box testing technique that selects values at the edges of input ranges because defects often occur at boundaries.

In this problem, there are two important boundaries:

- Minimum valid order quantity = 5
- Discount starts from quantity = 100

For each boundary, BVA selects values just below, at, and just above the boundary.

For minimum order quantity 5:

| Value | Meaning |
|---|---|
| 4 | Just below minimum, invalid |
| 5 | Boundary value, valid |
| 6 | Just above minimum, valid |

For discount boundary 100:

| Value | Meaning |
|---|---|
| 99 | Just below discount, no discount |
| 100 | Boundary value, discount applies |
| 101 | Just above discount, discount applies |

Therefore, valid BVA groups include:

- `4, 5, 6`
- `99, 100, 101`

Expected behavior:

| Quantity | Expected result |
|---|---|
| 4 | Reject order because it is below minimum |
| 5 | Accept order without discount |
| 99 | Accept order without discount |
| 100 | Accept order with 20% discount |
| 101 | Accept order with 20% discount |

Thus, if the given options contain `4, 5, 6` or `99, 100, 101`, those groups are generated using Boundary Value Analysis.

---

## 3. Compare black box and white box testing.

Black box testing and white box testing are two major testing approaches.

Black box testing checks software functionality without looking at internal code. The tester focuses on inputs, outputs, requirements, and user behavior. White box testing checks the internal structure, code, logic, paths, branches, loops, and data flow of the program.

| Point | Black box testing | White box testing |
|---|---|---|
| Focus | External behavior | Internal code structure |
| Knowledge of code | Not required | Required |
| Basis | Requirements and specifications | Program logic and design |
| Test design techniques | ECP, BVA, decision table, cause-effect graphing, state transition testing | Statement coverage, branch coverage, path coverage, data flow testing, loop testing |
| Performed mostly by | Testers | Developers and testers with code knowledge |
| Defects found | Missing functions, wrong output, interface issues | Logic errors, unreachable code, path errors, loop defects |
| Example | Test login with valid and invalid credentials | Check whether every branch in login code is executed |

Example: For a calculator, black box testing checks that `10 + 5` gives `15`. White box testing checks whether the addition method, condition statements, and error handling paths are executed.

Both approaches are important. Black box testing confirms that the system meets user requirements, while white box testing confirms that the internal implementation is properly tested.

---

## 4. Given a web application, apply Random Testing to generate test inputs and identify possible defects.

Random testing is a black box testing technique in which test inputs are selected randomly from the input domain. It is useful for finding unexpected defects because users may enter unpredictable data.

Example web application: Online registration form with fields name, email, age, mobile number, password, and address.

Random test inputs:

| Field | Random input | Possible defect detected |
|---|---|---|
| Name | `A`, `John123`, blank, 500 characters | Missing validation, layout break |
| Email | `abc`, `a@b.com`, `test@@mail.com` | Incorrect email validation |
| Age | `-5`, `0`, `18`, `999`, `abc` | Type handling or range validation defect |
| Mobile | `123`, `9999999999`, `abcdefghij` | Wrong mobile validation |
| Password | blank, `123`, long string, special characters | Weak password handling defect |
| Address | SQL-like input, emoji, very long text | Security or storage defect |

Random testing flow:

```text
Define input fields
      |
      v
Generate random values
      |
      v
Submit form
      |
      v
Observe behavior
      |
      v
Report crash, wrong validation, or security issue
```

Example defect: If the age field accepts `abc` and stores it in the database, it is a validation defect. If a 500-character name crashes the page, it is a robustness defect.

Random testing does not guarantee complete coverage, but it is useful for discovering defects caused by unexpected inputs.

---

## 5. Apply Equivalence Class Partitioning (ECP) and Boundary Value Analysis (BVA) to design test cases for a system that accepts age between 18 and 60. Justify your test cases.

Equivalence Class Partitioning (ECP) divides input data into groups that should behave similarly. Boundary Value Analysis (BVA) selects values near the edges of valid and invalid ranges.

Requirement: The system accepts age from 18 to 60 inclusive.

Equivalence classes:

| Class | Range | Validity | Representative value |
|---|---|---|---|
| EC1 | Age < 18 | Invalid | 17 |
| EC2 | 18 <= Age <= 60 | Valid | 30 |
| EC3 | Age > 60 | Invalid | 61 |

BVA values:

| Boundary | Test values |
|---|---|
| Lower boundary 18 | 17, 18, 19 |
| Upper boundary 60 | 59, 60, 61 |

Combined test cases:

| Test case | Age | Expected result | Technique |
|---|---|---|---|
| TC01 | 17 | Reject | ECP + BVA |
| TC02 | 18 | Accept | BVA |
| TC03 | 19 | Accept | BVA |
| TC04 | 30 | Accept | ECP |
| TC05 | 59 | Accept | BVA |
| TC06 | 60 | Accept | BVA |
| TC07 | 61 | Reject | ECP + BVA |

Justification: ECP reduces the number of test cases by selecting representatives from valid and invalid classes. BVA adds strength by testing values at and around the boundaries, where defects are common.

---

## 6. Apply Black Box Testing techniques (ECP, BVA) to test an online registration form and derive test cases.

Black box testing checks external behavior using requirements without considering internal code. For an online registration form, ECP and BVA can be applied to fields such as name, email, password, age, and mobile number.

Assume requirements:

- Name is mandatory and must contain 2 to 50 characters.
- Age must be between 18 and 60.
- Password must be 8 to 16 characters.
- Email must be in valid format.
- Mobile number must contain exactly 10 digits.

ECP test cases:

| Field | Valid class | Invalid class | Sample test |
|---|---|---|---|
| Name | 2-50 characters | blank, 1 char, more than 50 | `A`, `Amit`, 51 chars |
| Age | 18-60 | below 18, above 60, non-numeric | 17, 25, 61 |
| Password | 8-16 chars | less than 8, more than 16 | `abc`, `abcd1234` |
| Email | valid email format | missing `@`, missing domain | `abc`, `a@b.com` |
| Mobile | 10 digits | less/more than 10, letters | `123`, `9876543210` |

BVA test cases:

| Field | Boundary values |
|---|---|
| Name length | 1, 2, 3, 49, 50, 51 |
| Age | 17, 18, 19, 59, 60, 61 |
| Password length | 7, 8, 9, 15, 16, 17 |
| Mobile length | 9, 10, 11 |

Example expected behavior: Age `18` should be accepted, age `17` should be rejected. Password length `8` should be accepted, length `7` should be rejected.

These techniques provide strong test coverage while avoiding unnecessary exhaustive testing.

---

## 7. Apply white box testing approach with example.

White box testing is a testing approach where test cases are designed using knowledge of internal code, logic, branches, loops, and paths. It is also called structural testing.

Example code:

```java
String result(int marks) {
    if (marks >= 40) {
        return "Pass";
    } else {
        return "Fail";
    }
}
```

White box test design:

| Test case | Input | Path covered | Expected output |
|---|---|---|---|
| TC01 | 50 | `if` true branch | Pass |
| TC02 | 30 | `else` false branch | Fail |

Control flow:

```text
Start
  |
  v
marks >= 40?
  |       |
 Yes      No
  |       |
Pass     Fail
  \       /
   v     v
    End
```

Coverage achieved:

- Statement coverage: All statements are executed.
- Branch coverage: Both true and false branches are executed.
- Decision coverage: The decision `marks >= 40` is tested for both outcomes.

White box testing is useful for finding hidden logic errors, unreachable code, missing conditions, and loop defects. It is commonly used in unit testing and structural testing.

---

## 8. Analyze Experience-based testing techniques with examples.

Experience-based testing techniques use the tester's skill, domain knowledge, previous defect history, and intuition to design tests. These techniques are useful when documentation is incomplete, time is limited, or testers know common failure patterns.

Important experience-based techniques:

1. Error guessing: The tester guesses likely defects based on past experience. Example: In a login form, test blank password, wrong password, SQL injection input, and locked account.
2. Exploratory testing: Test design, execution, and learning happen together. Example: A tester explores an e-commerce checkout flow and tries changing quantity, applying coupon, going back, and refreshing the page.
3. Checklist-based testing: A tester uses a checklist of common issues. Example: Check mandatory fields, boundary values, error messages, session timeout, and broken links.
4. Fault attack testing: The tester intentionally targets areas where defects are likely. Example: Try uploading unsupported file types or extremely large files.

Benefits:

- Useful when formal test cases are not enough.
- Finds practical and user-focused defects.
- Works well with experienced testers.
- Helps supplement black box and white box techniques.

Limitation: Results depend heavily on tester skill and may not provide systematic coverage unless combined with structured techniques.

---

## 9. Examine the Structure-based (white-box) testing techniques.

Structure-based testing, also called white box testing, designs test cases using the internal structure of code. It focuses on how the software is implemented.

Major structure-based techniques:

1. Statement coverage: Ensures every executable statement is executed at least once.
2. Decision or branch coverage: Ensures every decision outcome, such as true and false, is executed.
3. Condition coverage: Ensures each individual condition in a compound decision becomes true and false.
4. Path coverage: Ensures different execution paths through the program are tested.
5. Control flow testing: Uses a control flow graph to test logic flow.
6. Data flow testing: Tests definition and use of variables to find issues such as unused variables or use before initialization.
7. Loop testing: Tests loops for zero, one, many, boundary, and maximum iterations.

Example:

```java
if (age >= 18 && citizen == true) {
    allowVote();
} else {
    reject();
}
```

Structure-based testing checks:

- True and false outcomes of the decision.
- Values of `age >= 18`.
- Values of `citizen == true`.
- All statements in both branches.

Structure-based testing improves code quality by revealing hidden logic defects, unreachable code, missing paths, and weak test coverage.

---

## 10. Apply all testing levels and explain their purpose with examples.

Testing levels are stages at which software is tested, from individual units to the complete system. The main levels are unit testing, integration testing, system testing, and acceptance testing.

| Testing level | Purpose | Example |
|---|---|---|
| Unit testing | Test individual functions or classes | Test grade calculation function |
| Integration testing | Test interaction between modules | Test cart module with payment module |
| System testing | Test complete application as a whole | Test full e-commerce workflow from login to order |
| Acceptance testing | Check whether system satisfies user/business needs | Customer verifies that order placement works as expected |

Example: Food delivery application.

1. Unit testing: Test function that calculates delivery charge.
2. Integration testing: Test cart total with coupon and payment module.
3. System testing: Test user registration, restaurant search, cart, payment, and tracking together.
4. Acceptance testing: Business owner checks whether the app supports real food ordering requirements.

```text
Unit testing
     |
     v
Integration testing
     |
     v
System testing
     |
     v
Acceptance testing
```

Each level has a different purpose. Unit testing finds local code defects, integration testing finds interface defects, system testing finds end-to-end defects, and acceptance testing confirms business readiness.

---

## 11. Apply Decision Table Testing to a real-world system and construct a decision table to derive effective test cases.

Decision Table Testing is a black box testing technique used when system behavior depends on combinations of conditions. It is useful for business rules.

Example: Online shopping discount system.

Rules:

- If customer is a member, give 10% discount.
- If order amount is Rs. 5000 or more, give 5% additional discount.
- If coupon is valid, give Rs. 500 off.
- If coupon is invalid, do not apply coupon discount.

Conditions and actions:

| Conditions / Actions | R1 | R2 | R3 | R4 |
|---|---|---|---|---|
| Member? | Y | Y | N | N |
| Amount >= 5000? | Y | N | Y | N |
| Valid coupon? | Y | N | Y | N |
| Apply 10% member discount | Y | Y | N | N |
| Apply 5% amount discount | Y | N | Y | N |
| Apply coupon discount | Y | N | Y | N |

Derived test cases:

| Test case | Member | Amount | Coupon | Expected result |
|---|---|---|---|---|
| TC01 | Yes | 6000 | Valid | 10% + 5% + coupon discount |
| TC02 | Yes | 3000 | Invalid | 10% only |
| TC03 | No | 7000 | Valid | 5% + coupon discount |
| TC04 | No | 2000 | Invalid | No discount |

Decision table testing ensures that important combinations of conditions are covered and that business rules are not missed.

---

## 12. Evaluate the situations where Regression Testing is required and explain its significance.

Regression testing is performed to ensure that existing functionality still works after changes are made. It checks that new code changes, defect fixes, or configuration changes have not broken previously working features.

Situations where regression testing is required:

- After fixing a defect.
- After adding a new feature.
- After modifying existing functionality.
- After code refactoring.
- After database changes.
- After integration with a new module or external service.
- After environment, server, library, or configuration changes.
- Before release.

Example: In an e-commerce system, a developer fixes a coupon calculation defect. Regression testing should check not only coupon logic but also cart total, payment, order placement, and invoice generation because they are related.

Significance:

- Detects side effects of changes.
- Protects stable features from accidental breakage.
- Builds confidence before release.
- Supports continuous maintenance.
- Reduces production defects.

```text
Code change or defect fix
        |
        v
Run related old test cases
        |
        v
Check for broken existing behavior
        |
        v
Approve or report regression defect
```

Regression testing is important because software changes continuously, and even a small change can affect other parts of the system.

---

## 13. Compare re-testing and regression testing.

Re-testing and regression testing are both performed after changes, but their purposes are different.

Re-testing checks whether a specific defect has been fixed. Regression testing checks whether the fix or change has affected other existing functionality.

| Point | Re-testing | Regression testing |
|---|---|---|
| Purpose | Verify that a reported defect is fixed | Verify that unchanged features still work |
| Scope | Narrow, defect-specific | Wider, related and existing areas |
| Test cases used | Failed test cases are executed again | Previously passed test cases are executed |
| When performed | After developer fixes a defect | After any change, fix, enhancement, or integration |
| Automation suitability | Can be manual or automated | Often automated for efficiency |
| Example | Recheck login with blank password after fix | Check login, logout, forgot password, and session after login fix |

Example: A defect says that wrong password allows login. After the fix, the tester enters wrong password again to confirm login fails. This is re-testing. Then the tester checks valid login, logout, password reset, and locked account behavior to ensure nothing else broke. This is regression testing.

Both are necessary. Re-testing confirms the defect fix, while regression testing protects existing functionality.

---

## 14. Given a Software Requirement Specification (SRS) of a given application, apply Requirement-Based Testing to design relevant test cases and ensure requirement coverage.

Requirement-Based Testing designs test cases directly from the Software Requirement Specification (SRS). The goal is to ensure that every requirement is covered by one or more test cases.

Example SRS for login system:

- R1: User must enter username and password.
- R2: Valid credentials should allow login.
- R3: Invalid credentials should show an error message.
- R4: After three failed attempts, account should be locked.
- R5: User should be able to logout.

Requirement-based test cases:

| Requirement | Test case | Expected result |
|---|---|---|
| R1 | Submit blank username or password | Required field message |
| R2 | Enter valid username and password | Dashboard opens |
| R3 | Enter invalid password | Error message shown |
| R4 | Enter wrong password three times | Account locked |
| R5 | Click logout after login | Session ends and login page opens |

Requirement traceability matrix:

| Requirement ID | Covered by test cases | Status |
|---|---|---|
| R1 | TC01, TC02 | Covered |
| R2 | TC03 | Covered |
| R3 | TC04 | Covered |
| R4 | TC05 | Covered |
| R5 | TC06 | Covered |

Requirement-Based Testing ensures that no requirement is missed. It also helps identify unclear, incomplete, or untestable requirements early.

---

## 16. Analyze and differentiate between Black-box, White-box, and Gray-box testing, and justify when each should be used.

Black-box, white-box, and gray-box testing differ based on the tester's knowledge of the system internals.

| Testing type | Internal knowledge | Focus | Example |
|---|---|---|---|
| Black-box testing | No code knowledge | Inputs, outputs, requirements | Test login with valid and invalid credentials |
| White-box testing | Full code knowledge | Code paths, branches, loops, data flow | Test every branch in authentication code |
| Gray-box testing | Partial internal knowledge | External behavior plus some design/database/API knowledge | Test login using UI and verify session record in database |

When to use black-box testing:

- During system and acceptance testing.
- When testing user-facing functionality.
- When testers only have requirements.
- For ECP, BVA, decision table, state transition, and cause-effect testing.

When to use white-box testing:

- During unit testing.
- When code coverage is required.
- To test complex logic, loops, branches, and data flow.
- When developers need to verify internal correctness.

When to use gray-box testing:

- During integration and API testing.
- When tester knows database structure or architecture.
- For security, session, workflow, and data validation testing.

All three are useful. Black-box checks user behavior, white-box checks implementation, and gray-box combines practical system knowledge with external testing.

---

## 17. Below is a simple example showing the decision statement with compound predicate: `if (age < 65 and married == true) { Do X. Do Y } Else Do Z`. Which testing technique will you select to write test cases for: 1) Simple decision coverage, 2) Condition coverage, 3) Decision-condition coverage.

The given decision has a compound predicate:

```text
C1: age < 65
C2: married == true
Decision: C1 AND C2
```

Code behavior:

- If both C1 and C2 are true, execute X and Y.
- Otherwise, execute Z.

1. Simple decision coverage:

This technique requires the overall decision to become true at least once and false at least once.

| Test case | Age | Married | Decision | Expected |
|---|---|---|---|---|
| TC01 | 30 | true | True | Do X, Do Y |
| TC02 | 70 | true | False | Do Z |

2. Condition coverage:

This technique requires each individual condition to take true and false values at least once.

| Test case | Age | Married | C1 | C2 | Expected |
|---|---|---|---|---|---|
| TC01 | 30 | true | T | T | Do X, Do Y |
| TC02 | 70 | false | F | F | Do Z |

3. Decision-condition coverage:

This technique requires both decision coverage and condition coverage.

| Test case | Age | Married | C1 | C2 | Decision | Expected |
|---|---|---|---|---|---|---|
| TC01 | 30 | true | T | T | T | Do X, Do Y |
| TC02 | 70 | true | F | T | F | Do Z |
| TC03 | 30 | false | T | F | F | Do Z |

Decision-condition coverage is stronger because it checks individual condition outcomes and overall decision outcomes.

---

## 18. Given a software module, apply static testing and structural testing techniques to identify defects and demonstrate how each method contributes to software quality.

Static testing checks software work products without executing the code. Structural testing checks internal code structure by executing test cases designed from code logic. Both improve quality in different ways.

Example module: Student result calculation.

Static testing activities:

- Review requirement: Pass marks, grade rules, and invalid marks.
- Inspect design: Check whether result calculation, data validation, and report generation are properly defined.
- Code review: Look for wrong operators, missing validation, duplicate code, and unclear logic.
- Checklist review: Verify boundary values such as 39, 40, 100, and 101.

Defects found by static testing:

- Ambiguous grade rule.
- Missing invalid marks condition.
- Code uses `>` instead of `>=`.

Structural testing activities:

- Statement coverage: Execute all statements.
- Branch coverage: Test pass and fail branches.
- Condition coverage: Test grade conditions.
- Data flow testing: Check that marks are defined before use.
- Loop testing: If multiple subjects are processed, test zero, one, and many subjects.

```text
Static testing: find defects before execution
Structural testing: find defects through code execution paths
```

Static testing improves quality by preventing defects early. Structural testing improves quality by verifying that code paths, conditions, and variable usage are correctly exercised.

---

## 19. Suppose a program allows a user to search for a part name in a specific group of part records. The user inputs the record number believed to hold the part, and the part name to search for. The program informs the user if the record number is within the legal range (1-1000). If not, an error message "record number is out of range" is issued. If within range and the part is found, it returns "part found," else "part not found." Identify input and output conditions (causes and effects). Draw a cause-and-effect graph and a decision table. Generate a set of test inputs and expected outputs.

Cause-effect graphing is a black box testing technique that converts input conditions into output effects and derives test cases.

Causes:

- C1: Record number is within legal range 1-1000.
- C2: Part name exists in the given record.

Effects:

- E1: Display "record number is out of range".
- E2: Display "part found".
- E3: Display "part not found".

Cause-effect graph:

```text
             +----------------+
C1 = False ->| Out of range   |-> E1
             +----------------+

C1 = True AND C2 = True  -----------------> E2
C1 = True AND C2 = False -----------------> E3
```

Decision table:

| Conditions / Effects | R1 | R2 | R3 |
|---|---|---|---|
| C1: Record in range | N | Y | Y |
| C2: Part found in record | - | Y | N |
| E1: Out of range message | Y | N | N |
| E2: Part found | N | Y | N |
| E3: Part not found | N | N | Y |

Generated test cases:

| Test case | Record number | Part name | Assumption | Expected output |
|---|---|---|---|---|
| TC01 | 0 | Bolt | Below range | record number is out of range |
| TC02 | 1001 | Bolt | Above range | record number is out of range |
| TC03 | 50 | Nut | Record 50 contains Nut | part found |
| TC04 | 50 | Screw | Record 50 does not contain Screw | part not found |
| TC05 | 1 | Washer | Boundary lower valid record | part found or part not found based on data |
| TC06 | 1000 | Bolt | Boundary upper valid record | part found or part not found based on data |

This technique ensures that each logical rule is tested and each output effect is covered.

---

## 20. Draw control flow graph for the code given below. Clearly label each node linked to its corresponding statement. Calculate cyclomatic complexity. How can this value be used to measure testability? Describe how cyclomatic complexity number and the flow graph can be used to design white box tests covering all branches. **Code:** `Module foo() /* a[] and b[] are global variables */ Begin Int i, x Read(x) While(i<x) do begin a[i] = b[i] * x if a[i] > 50 then Print("array a is over the limit"); else Print("OK") i = i + 1 End Print("end of nonsense"); End.`

Control Flow Graph (CFG) represents the flow of control between program statements. For the given module, assume `i` is initialized before the loop or should be initialized as part of correct code. If `i` is not initialized, that is a data flow defect.

Labeled nodes:

| Node | Statement |
|---|---|
| 1 | Start |
| 2 | Declare `i, x` and read `x` |
| 3 | Check `while (i < x)` |
| 4 | `a[i] = b[i] * x` |
| 5 | Check `if (a[i] > 50)` |
| 6 | Print "array a is over the limit" |
| 7 | Print "OK" |
| 8 | `i = i + 1` |
| 9 | Print "end of nonsense" |
| 10 | End |

Control flow graph:

```text
  1
  |
  v
  2
  |
  v
  3 ----False----> 9 -> 10
  |
 True
  v
  4
  |
  v
  5
 / \
T   F
v   v
6   7
 \ /
  v
  8
  |
  +-----> 3
```

Cyclomatic complexity:

Using formula `V(G) = number of decision nodes + 1`.

Decision nodes are:

- `while (i < x)`
- `if (a[i] > 50)`

Therefore:

```text
V(G) = 2 + 1 = 3
```

Cyclomatic complexity 3 means there are three independent paths to test. A higher value indicates more complex code and lower testability because more paths are needed for adequate branch coverage.

Independent paths:

| Path | Description |
|---|---|
| P1 | Loop condition false immediately: 1-2-3-9-10 |
| P2 | Loop true and `a[i] > 50`: 1-2-3-4-5-6-8-3-9-10 |
| P3 | Loop true and `a[i] <= 50`: 1-2-3-4-5-7-8-3-9-10 |

White box tests should be designed to cover these paths. For example, choose `x` so the loop is skipped, choose values of `b[i]` and `x` so `a[i] > 50`, and choose values so `a[i] <= 50`.

---

## 21. For the following looping construct, describe the set of tests you would develop based on the number of loop iterations in accordance with loop testing criteria: `for (i = 0; i < 50; i++) { text_box[i] = value[i]; full = full-1; }`

Loop testing is a white box testing technique used to test loops for correct behavior at minimum, normal, boundary, and maximum iterations.

Given loop:

```java
for (i = 0; i < 50; i++) {
    text_box[i] = value[i];
    full = full - 1;
}
```

This is a simple loop with fixed maximum iterations of 50. Loop testing criteria suggest testing:

- Zero iterations if possible.
- One iteration.
- Two iterations.
- Typical number of iterations.
- Maximum minus one iteration.
- Maximum iteration.
- More than maximum if input can influence the loop.

Since the loop condition is fixed as `i < 50`, normally it executes exactly 50 times. To apply loop testing, the code can be considered with controlled loop limit or tested in context.

Test set:

| Test case | Iterations | Purpose |
|---|---|---|
| TC01 | 0 | Check behavior when no values are copied, if loop limit can be 0 |
| TC02 | 1 | Check first iteration handling |
| TC03 | 2 | Check transition from first to next iteration |
| TC04 | 25 | Check normal middle case |
| TC05 | 49 | Check just below maximum |
| TC06 | 50 | Check maximum valid loop count |
| TC07 | 51 | Check that loop does not exceed array limit, if external size is used |

For this exact loop, the most important test is 50 iterations, and array sizes of `text_box` and `value` must be at least 50. Defects may include off-by-one error, array index out of bounds, or wrong decrement of `full`.

---

## 22. A programmer using a mutation analysis tool finds that 35 mutants have been generated for program module A. Using a test set, she finds 29 dead mutants and 2 equivalent mutants. What is the mutation score (MS) for module A? Is her test set mutation adequate? Should she develop additional test cases? Justify.

Mutation testing creates small changes in the program called mutants. A test case kills a mutant if it detects the changed behavior. Equivalent mutants are mutants that behave the same as the original program and cannot be killed.

Mutation score formula:

```text
Mutation Score = Dead Mutants / (Total Mutants - Equivalent Mutants)
```

Given:

- Total mutants = 35
- Dead mutants = 29
- Equivalent mutants = 2

Calculation:

```text
MS = 29 / (35 - 2)
MS = 29 / 33
MS = 0.8787
MS = 87.87%
```

So, the mutation score is approximately `87.88%`.

Live non-equivalent mutants:

```text
35 - 29 - 2 = 4
```

This means 4 mutants are still alive and can possibly be killed by better test cases.

Is the test set mutation adequate? It depends on the adequacy threshold decided by the project. If the required threshold is 85%, then the test set is adequate. If the required threshold is 90% or higher, it is not adequate.

Additional test cases should be developed to kill the 4 live non-equivalent mutants, especially if the module is critical.

---

## 23. During data flow testing, you observe that certain variables are defined but never used, while others are used without being initialized. How would you modify your testing strategy to detect and prevent such issues early in the development lifecycle?

Data flow testing focuses on the lifecycle of variables: where they are defined, where they are used, and whether they are properly initialized before use.

Observed issues:

- Defined but never used: A variable is assigned a value but never used later.
- Used without initialization: A variable is read before it gets a valid value.

Modified testing strategy:

1. Add static code analysis: Use review checklists or tools to detect unused variables and uninitialized variables before execution.
2. Perform code inspection: Review variable definitions and uses during peer review.
3. Create Def-Use tables: For each variable, record definition points and use points.
4. Apply data flow coverage: Design tests to cover definition-use paths.
5. Include compiler warnings: Treat warnings about unused or uninitialized variables as defects.
6. Add unit tests for paths: Test branches where variables may or may not be assigned.
7. Review during early development: Apply data flow checks during coding, not only after system testing.

Example:

```java
int total;
if (discountAllowed) {
    total = price - discount;
}
print(total);
```

If `discountAllowed` is false, `total` may be used without being initialized. A test case with `discountAllowed = false` should be added.

This strategy prevents data-related defects early and improves reliability, maintainability, and code clarity.

---

## 24. Draw a state transition diagram for a simple stack machine. Assume the stack holds n data items where n is a small positive number. It has operations "push" and "pop" that cause the stack pointer to increment or decrement, respectively. The stack can enter states such as "full" (n items) and "empty" (no items). Popping from empty or pushing on full causes a transition to an error state. Based on your diagram, develop a set of black box test cases covering key state transitions.

State transition testing is a black box technique used when system behavior depends on current state and input events.

For a stack machine, states are:

- Empty: stack has 0 items.
- Partial: stack has between 1 and n-1 items.
- Full: stack has n items.
- Error: invalid operation such as pop on empty or push on full.

State transition diagram:

```text
                 pop
            +----------+
            |          v
        +--------+   +---------+
push -> | Empty  |-->| Partial |
        +--------+   +---------+
            |          |   ^
            | pop      |   | pop
            v          v   |
        +--------+   +------+
        | Error  |   | Full |
        +--------+   +------+
                       |
                       | push
                       v
                    +-------+
                    | Error |
                    +-------+
```

More clearly:

```text
Empty --push--> Partial
Empty --pop---> Error
Partial --push repeatedly--> Full
Partial --pop repeatedly--> Empty
Full --pop--> Partial
Full --push--> Error
```

Assume stack capacity `n = 3`.

Test cases:

| Test case | Initial state | Operation sequence | Expected final state / output |
|---|---|---|---|
| TC01 | Empty | push | Partial |
| TC02 | Empty | pop | Error: cannot pop from empty |
| TC03 | Empty | push, push, push | Full |
| TC04 | Full | pop | Partial |
| TC05 | Full | push | Error: cannot push on full |
| TC06 | Partial | pop until no items | Empty |
| TC07 | Partial | push until capacity reached | Full |

These test cases cover normal transitions and invalid transitions, which are essential for state-based behavior.

---

## 25. Design test cases for the binary search code below using Data Flow testing. Write a table for each variable separately and select input data to cover all Def-Use Paths: `int binsearch(int x, int v[], int n) { int low, high, mid; low = 0; high = n-1; while (low <= high) { mid = (low+high)/2; if (x < v[mid]) high = mid - 1; else if (x > v[mid]) low = mid + 1; else return mid; } return -1; }`

Data flow testing designs tests based on definitions and uses of variables. A definition is where a variable gets a value. A use is where the value is read.

Variables: `x`, `v`, `n`, `low`, `high`, `mid`.

Def-Use table:

| Variable | Definition | Uses |
|---|---|---|
| `x` | Function parameter | Compared in `x < v[mid]` and `x > v[mid]` |
| `v[]` | Function parameter | Used in `v[mid]` |
| `n` | Function parameter | Used in `high = n - 1` |
| `low` | `low = 0`, `low = mid + 1` | Used in `while (low <= high)` and `mid = (low + high) / 2` |
| `high` | `high = n - 1`, `high = mid - 1` | Used in `while (low <= high)` and `mid = (low + high) / 2` |
| `mid` | `mid = (low + high) / 2` | Used in `v[mid]`, `high = mid - 1`, `low = mid + 1`, `return mid` |

Selected input data:

Assume sorted array:

```text
v = [10, 20, 30, 40, 50], n = 5
```

Test cases:

| Test case | Input `x` | Expected output | Def-use paths covered |
|---|---|---|---|
| TC01 | 30 | 2 | Initial `low`, `high`, `mid`, direct successful return |
| TC02 | 10 | 0 | Path where `x < v[mid]`, `high = mid - 1`, then found |
| TC03 | 50 | 4 | Path where `x > v[mid]`, `low = mid + 1`, then found |
| TC04 | 25 | -1 | Both search narrowing and not found return |
| TC05 | 5 | -1 | Repeated `high` updates until loop exits |
| TC06 | 60 | -1 | Repeated `low` updates until loop exits |
| TC07 | 10 with `n = 0` | -1 | `high = -1`, loop skipped |

Data flow focus:

- TC01 covers `mid` definition to `return mid`.
- TC02 covers `high = mid - 1`.
- TC03 covers `low = mid + 1`.
- TC04, TC05, and TC06 cover loop exit and `return -1`.
- TC07 checks behavior when `low <= high` is false at the start.

These tests help ensure that all important variable definitions reach their uses correctly.

---

## 26. Given a Java program, apply JUnit testing and demonstrate how test cases are designed and executed, highlighting key features of JUnit test cases.

JUnit is a Java testing framework used to write and execute automated unit tests. It helps verify small units of code such as methods and classes.

Example Java class:

```java
public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }

    public int divide(int a, int b) {
        if (b == 0) {
            throw new IllegalArgumentException("Cannot divide by zero");
        }
        return a / b;
    }
}
```

JUnit test cases:

```java
import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;

class CalculatorTest {
    Calculator calculator = new Calculator();

    @Test
    void addShouldReturnSum() {
        assertEquals(15, calculator.add(10, 5));
    }

    @Test
    void divideShouldReturnQuotient() {
        assertEquals(2, calculator.divide(10, 5));
    }

    @Test
    void divideByZeroShouldThrowException() {
        assertThrows(IllegalArgumentException.class,
            () -> calculator.divide(10, 0));
    }
}
```

Key features of JUnit:

- `@Test` marks a method as a test case.
- Assertions such as `assertEquals`, `assertTrue`, and `assertThrows` compare expected and actual results.
- Tests can be executed automatically by IDE, build tools, or CI systems.
- JUnit reports pass/fail results clearly.

JUnit improves testing by making tests repeatable, automated, and useful for regression testing.

---

## 27. Write JUnit test cases for the following code to achieve 90% code coverage: `public class SelectionSort { public static void selectionSort(int[] arr) { if (arr == null || arr.length <= 1) { return; } int n = arr.length; for (int i = 0; i < n - 1; i++) { int minIndex = i; for (int j = i + 1; j < n; j++) { if (arr[j] < arr[minIndex]) { minIndex = j; } } int temp = arr[minIndex]; arr[minIndex] = arr[i]; arr[i] = temp; } } }`

To achieve high code coverage for `SelectionSort`, test cases should cover null input, single element array, already sorted array, unsorted array, reverse sorted array, duplicate values, and negative values.

JUnit test cases:

```java
import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;

class SelectionSortTest {

    @Test
    void nullArrayShouldNotThrowException() {
        assertDoesNotThrow(() -> SelectionSort.selectionSort(null));
    }

    @Test
    void singleElementArrayShouldRemainSame() {
        int[] arr = {5};
        SelectionSort.selectionSort(arr);
        assertArrayEquals(new int[]{5}, arr);
    }

    @Test
    void alreadySortedArrayShouldRemainSorted() {
        int[] arr = {1, 2, 3, 4};
        SelectionSort.selectionSort(arr);
        assertArrayEquals(new int[]{1, 2, 3, 4}, arr);
    }

    @Test
    void unsortedArrayShouldBeSorted() {
        int[] arr = {4, 2, 5, 1, 3};
        SelectionSort.selectionSort(arr);
        assertArrayEquals(new int[]{1, 2, 3, 4, 5}, arr);
    }

    @Test
    void reverseSortedArrayShouldBeSorted() {
        int[] arr = {5, 4, 3, 2, 1};
        SelectionSort.selectionSort(arr);
        assertArrayEquals(new int[]{1, 2, 3, 4, 5}, arr);
    }

    @Test
    void duplicateValuesShouldBeSorted() {
        int[] arr = {3, 1, 2, 1};
        SelectionSort.selectionSort(arr);
        assertArrayEquals(new int[]{1, 1, 2, 3}, arr);
    }

    @Test
    void negativeValuesShouldBeSorted() {
        int[] arr = {-1, -5, 3, 0};
        SelectionSort.selectionSort(arr);
        assertArrayEquals(new int[]{-5, -1, 0, 3}, arr);
    }
}
```

Coverage justification:

- Null and single element tests cover the early return condition.
- Sorted and unsorted tests cover the loops.
- Reverse sorted and unsorted arrays cover the `if (arr[j] < arr[minIndex])` true branch.
- Already sorted array covers the false branch.
- Duplicate and negative tests improve data coverage.

These tests should achieve around 90% or more code coverage, depending on the coverage tool.

---

## 28. Apply JUnit annotations to design and execute test cases for a Java program.

JUnit annotations provide structure for writing and executing test cases. They control test methods, setup, cleanup, repeated tests, and disabled tests.

Common JUnit 5 annotations:

| Annotation | Purpose |
|---|---|
| `@Test` | Marks a method as a test case |
| `@BeforeEach` | Runs before each test method |
| `@AfterEach` | Runs after each test method |
| `@BeforeAll` | Runs once before all tests |
| `@AfterAll` | Runs once after all tests |
| `@Disabled` | Skips a test temporarily |
| `@DisplayName` | Gives a readable name to a test |
| `@RepeatedTest` | Repeats a test multiple times |

Example:

```java
import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.*;

class LoginServiceTest {
    LoginService service;

    @BeforeAll
    static void initAll() {
        System.out.println("Start tests");
    }

    @BeforeEach
    void init() {
        service = new LoginService();
    }

    @Test
    @DisplayName("Valid credentials should allow login")
    void validLoginShouldPass() {
        assertTrue(service.login("admin", "admin123"));
    }

    @Test
    void invalidLoginShouldFail() {
        assertFalse(service.login("admin", "wrong"));
    }

    @AfterEach
    void cleanup() {
        service = null;
    }
}
```

JUnit annotations make tests organized, repeatable, and easy to execute. They are useful for automated unit testing and regression testing.

---

## 29. A module allows a user to enter a new widget. The input specification states that a widget identifier should consist of 3-15 alphanumeric characters of which the first two must be letters. Three conditions apply: (i) must consist of alphanumeric characters, (ii) total characters between 3 and 15, (iii) first two characters must be letters. Write test cases using Equivalence Class Partitioning and Boundary Value Analysis.

The widget identifier has three rules:

- It must contain only alphanumeric characters.
- Length must be between 3 and 15.
- First two characters must be letters.

Equivalence classes:

| Condition | Valid class | Invalid class |
|---|---|---|
| Character type | Only letters and digits | Contains special characters |
| Length | 3 to 15 characters | Less than 3, more than 15 |
| First two characters | Both are letters | First or second character is not a letter |

ECP test cases:

| Test case | Input | Expected result | Reason |
|---|---|---|---|
| TC01 | `AB1` | Accept | Valid minimum length |
| TC02 | `AB123XYZ` | Accept | Valid alphanumeric |
| TC03 | `A1B` | Reject | Second character is not letter |
| TC04 | `1AB` | Reject | First character is not letter |
| TC05 | `AB@12` | Reject | Special character used |
| TC06 | `AB` | Reject | Length less than 3 |
| TC07 | `AB12345678901234` | Reject | Length more than 15 |

BVA test cases for length:

| Length | Example input | Expected result |
|---|---|---|
| 2 | `AB` | Reject |
| 3 | `AB1` | Accept |
| 4 | `AB12` | Accept |
| 14 | `AB123456789012` | Accept |
| 15 | `AB1234567890123` | Accept |
| 16 | `AB12345678901234` | Reject |

These tests cover valid and invalid partitions and boundary values where defects are likely.

---

## 30. Analyze Cause-Effect Graphing and derive test cases for any given applications like online payment/ATM/Login page.

Cause-Effect Graphing is a black box testing technique used to identify logical relationships between input conditions and output actions. It is useful when outputs depend on combinations of inputs.

Example: ATM cash withdrawal.

Causes:

- C1: Card is valid.
- C2: PIN is correct.
- C3: Account has sufficient balance.
- C4: ATM has enough cash.

Effects:

- E1: Allow cash withdrawal.
- E2: Display invalid card message.
- E3: Display incorrect PIN message.
- E4: Display insufficient balance message.
- E5: Display ATM cash unavailable message.

Cause-effect graph:

```text
C1 AND C2 AND C3 AND C4 --------> E1
NOT C1 -------------------------> E2
C1 AND NOT C2 ------------------> E3
C1 AND C2 AND NOT C3 -----------> E4
C1 AND C2 AND C3 AND NOT C4 ----> E5
```

Decision table:

| Conditions / Effects | R1 | R2 | R3 | R4 | R5 |
|---|---|---|---|---|---|
| Valid card | N | Y | Y | Y | Y |
| Correct PIN | - | N | Y | Y | Y |
| Sufficient balance | - | - | N | Y | Y |
| ATM cash available | - | - | - | N | Y |
| Invalid card message | Y | N | N | N | N |
| Incorrect PIN message | N | Y | N | N | N |
| Insufficient balance | N | N | Y | N | N |
| ATM cash unavailable | N | N | N | Y | N |
| Allow withdrawal | N | N | N | N | Y |

Derived test cases:

| Test case | Card | PIN | Balance | ATM cash | Expected output |
|---|---|---|---|---|---|
| TC01 | Invalid | - | - | - | Invalid card |
| TC02 | Valid | Wrong | - | - | Incorrect PIN |
| TC03 | Valid | Correct | Low | - | Insufficient balance |
| TC04 | Valid | Correct | Enough | Not enough | ATM cash unavailable |
| TC05 | Valid | Correct | Enough | Enough | Cash withdrawal allowed |

Cause-effect graphing improves test effectiveness by covering combinations of conditions clearly.

---

## 31. Apply Cause-Effect Graphing technique to a login system or decision-based application and derive test cases from the cause-effect graph.

For a login system, output depends on combinations of input conditions such as username, password, and account status.

Causes:

- C1: Username exists.
- C2: Password is correct.
- C3: Account is active.

Effects:

- E1: Login successful.
- E2: Invalid username or password message.
- E3: Account inactive or locked message.

Cause-effect graph:

```text
C1 AND C2 AND C3 -----------> E1
NOT C1 ---------------------> E2
C1 AND NOT C2 --------------> E2
C1 AND C2 AND NOT C3 -------> E3
```

Decision table:

| Conditions / Effects | R1 | R2 | R3 | R4 |
|---|---|---|---|---|
| Username exists | N | Y | Y | Y |
| Password correct | - | N | Y | Y |
| Account active | - | - | N | Y |
| Invalid username/password | Y | Y | N | N |
| Account inactive message | N | N | Y | N |
| Login successful | N | N | N | Y |

Test cases:

| Test case | Username | Password | Account status | Expected result |
|---|---|---|---|---|
| TC01 | Not existing | Any | - | Invalid username or password |
| TC02 | Existing | Wrong | Active | Invalid username or password |
| TC03 | Existing | Correct | Inactive | Account inactive or locked |
| TC04 | Existing | Correct | Active | Login successful |

This technique ensures that all important decision combinations are covered and that the login system gives correct outputs for each condition.

---

## 32. Analyze Cause-Effect Graphing and derive test cases for a given scenario like an online shopping discount system.

Cause-Effect Graphing helps test systems where multiple input conditions decide the final output. In an online shopping discount system, discount may depend on membership, order amount, coupon validity, and festival offer.

Assume rules:

- Member customers get 10% discount.
- Orders of Rs. 5000 or more get 5% discount.
- Valid coupon gives Rs. 500 off.
- Invalid coupon gives no coupon discount.

Causes:

- C1: Customer is a member.
- C2: Order amount >= Rs. 5000.
- C3: Coupon is valid.

Effects:

- E1: Apply member discount.
- E2: Apply amount discount.
- E3: Apply coupon discount.
- E4: No discount.

Cause-effect relation:

```text
C1 -------------> E1
C2 -------------> E2
C3 -------------> E3
NOT C1 AND NOT C2 AND NOT C3 ---> E4
```

Decision table:

| Conditions / Effects | R1 | R2 | R3 | R4 |
|---|---|---|---|---|
| Member | Y | Y | N | N |
| Amount >= 5000 | Y | N | Y | N |
| Coupon valid | Y | N | Y | N |
| Member discount | Y | Y | N | N |
| Amount discount | Y | N | Y | N |
| Coupon discount | Y | N | Y | N |
| No discount | N | N | N | Y |

Test cases:

| Test case | Member | Amount | Coupon | Expected result |
|---|---|---|---|---|
| TC01 | Yes | 6000 | Valid | Member + amount + coupon discount |
| TC02 | Yes | 3000 | Invalid | Member discount only |
| TC03 | No | 7000 | Valid | Amount + coupon discount |
| TC04 | No | 2000 | Invalid | No discount |

These test cases cover major combinations and ensure the discount logic is tested systematically.

---

## 33. Apply Mutation Testing to a given program and demonstrate how mutants are created and killed using test cases. Explain with a suitable example.

Mutation testing evaluates the quality of test cases by making small changes to the program and checking whether tests detect those changes. The changed versions are called mutants. If a test fails on a mutant, the mutant is killed.

Original program:

```java
boolean isPass(int marks) {
    return marks >= 40;
}
```

Mutants:

| Mutant | Changed code | Type of mutation |
|---|---|---|
| M1 | `return marks > 40;` | Relational operator changed |
| M2 | `return marks <= 40;` | Relational operator changed |
| M3 | `return marks >= 50;` | Constant changed |

Test cases:

```java
assertTrue(isPass(40));
assertTrue(isPass(60));
assertFalse(isPass(39));
```

Killing mutants:

| Mutant | Test that kills it | Reason |
|---|---|---|
| M1: `marks > 40` | `isPass(40)` | Original returns true, mutant returns false |
| M2: `marks <= 40` | `isPass(60)` | Original returns true, mutant returns false |
| M3: `marks >= 50` | `isPass(40)` | Original returns true, mutant returns false |

Mutation testing process:

```text
Original program
      |
      v
Create mutants
      |
      v
Run test suite
      |
      v
Killed mutants and live mutants
      |
      v
Improve test cases
```

If mutants remain alive, it means the current test cases may be weak. Mutation testing helps improve test adequacy.

---

## 34. Justify the use of Mutation Testing over traditional testing techniques.

Mutation testing is used to evaluate the strength of a test suite. Traditional testing techniques such as statement coverage or branch coverage measure whether code was executed, but they do not always prove that tests can detect incorrect behavior.

Justification for mutation testing:

- It checks test effectiveness, not only code execution.
- It reveals weak assertions in test cases.
- It helps identify missing boundary tests.
- It forces testers to think about small code faults.
- It gives a mutation score, which is a measurable adequacy criterion.

Example:

Original code:

```java
return age >= 18;
```

A traditional coverage test with `age = 20` may execute the statement and give 100% statement coverage. But if the code is mutated to:

```java
return age > 18;
```

The test with `age = 20` still passes. A stronger test with `age = 18` is needed to kill the mutant. This shows that coverage alone may be insufficient.

Comparison:

| Traditional coverage | Mutation testing |
|---|---|
| Checks whether code was executed | Checks whether tests detect faults |
| May give high coverage with weak assertions | Reveals weak or missing tests |
| Easier and faster | More powerful but costlier |
| Useful for coverage measurement | Useful for test adequacy measurement |

Mutation testing should not completely replace traditional techniques, but it is valuable when high confidence is required, especially for critical modules.
