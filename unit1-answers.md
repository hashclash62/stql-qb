# Unit 1: Software Testing Basics Answers

Subject: Software Testing and Quality
Unit: Software Testing Basics

---

## 1. Interpret testing as an engineering activity with an example.

Software testing is an engineering activity because it is a planned, systematic, measurable, and controlled process used to evaluate software quality. It is not just running a program randomly. Like other engineering activities, testing uses defined methods, tools, documents, standards, test data, and expected results.

Testing as an engineering activity includes:

- Understanding requirements before testing.
- Designing test cases based on inputs, outputs, and conditions.
- Preparing a test environment or test bed.
- Executing tests in a controlled manner.
- Comparing actual output with expected output using a test oracle.
- Reporting defects with evidence.
- Measuring quality using test metrics.

Example: Consider an ATM cash withdrawal system. The tester does not simply try random withdrawals. The tester studies requirements such as valid PIN, sufficient balance, withdrawal limits, and receipt generation. Test cases are designed for valid withdrawal, wrong PIN, insufficient balance, and network failure.

```text
Requirement
     |
     v
Test case design
     |
     v
Controlled execution
     |
     v
Compare expected and actual result
     |
     v
Defect report or pass result
```

For example, if the balance is Rs. 5000 and the user withdraws Rs. 1000, the expected balance is Rs. 4000. If the system shows Rs. 4500, testing identifies a defect. Thus, testing works like an engineering discipline because it applies logic, planning, measurement, and verification to improve software quality.

---

## 2. Elaborate testing as a process in software development.

Testing as a process means testing is performed through a sequence of planned activities throughout software development. It starts from requirement analysis and continues until test closure. The purpose is to find defects early, verify that software meets requirements, and validate that the final product is useful for users.

The testing process generally includes the following steps:

1. Requirement analysis: Testers study the requirement document and identify testable requirements.
2. Test planning: The team decides scope, strategy, resources, schedule, risks, and tools.
3. Test case design: Test cases, test data, and expected results are prepared.
4. Test environment setup: Hardware, software, database, browser, network, and tools are configured.
5. Test execution: Test cases are executed and actual results are recorded.
6. Defect reporting: Defects are logged with steps to reproduce, severity, screenshots, and expected behavior.
7. Retesting and regression testing: Fixed defects are tested again, and related features are checked.
8. Test closure: Final reports, metrics, lessons learned, and sign-off are prepared.

```text
Requirements
     |
     v
Test planning
     |
     v
Test design
     |
     v
Environment setup
     |
     v
Test execution
     |
     v
Defect reporting and retesting
     |
     v
Test closure
```

Example: In a student result system, testing starts by checking rules such as pass marks, grade calculation, and result status. Testers then design cases for pass, fail, absent, invalid marks, and boundary marks. This process ensures that testing is organized, traceable, and useful in improving software quality.

---

## 3. Differentiate between verification and validation with examples.

Verification and validation are two important activities used to improve software correctness and quality.

Verification checks whether the product is being built correctly according to specifications. It usually focuses on documents, design, code, and development work products. Validation checks whether the correct product is being built for the user's actual needs. It focuses on executing the software and checking its behavior.

| Point | Verification | Validation |
|---|---|---|
| Meaning | Checks whether software follows specifications | Checks whether software satisfies user needs |
| Main question | Are we building the product right? | Are we building the right product? |
| Nature | Mostly static | Mostly dynamic |
| Execution required | Usually not required | Required |
| Examples | Requirement review, design review, code inspection | Functional testing, system testing, user acceptance testing |
| Defect detection | Early in development | During or after execution |

Example: For a login system, verification includes reviewing the requirement that password length must be at least 8 characters. Validation includes executing the login page and checking whether a 7-character password is actually rejected.

Another example: In a student result system, verification checks whether the grade calculation formula is correctly written in the design document. Validation checks whether the running software gives grade `A` for marks between 80 and 100.

Both verification and validation are needed. Verification reduces defects before coding or execution, while validation confirms that the final software works correctly for real users.

---

## 4. Illustrate the V-Model of testing with suitable diagram.

The V-Model is a software development and testing model in which each development phase has a corresponding testing phase. It is called the V-Model because the development activities are shown on the left side of the V, coding is at the bottom, and testing activities are shown on the right side.

The main idea of the V-Model is that testing should be planned early, not only after coding. For every development document, a related test activity is prepared.

```text
Requirement analysis           Acceptance testing
        \                         /
         \                       /
System design              System testing
           \                   /
            \                 /
Architecture design    Integration testing
              \             /
               \           /
Module design       Unit testing
                 \       /
                  \     /
                   Coding
```

Mapping of phases:

| Development phase | Corresponding testing phase |
|---|---|
| Requirement analysis | Acceptance testing |
| System design | System testing |
| Architecture design | Integration testing |
| Module design | Unit testing |
| Coding | Code implementation and unit test execution |

Example: In an online shopping system, requirements such as product search, cart, payment, and order tracking are collected. Acceptance tests are planned from these requirements. System design describes the whole application, so system tests are planned. Module design defines individual modules such as cart calculation, so unit tests are planned for them.

The V-Model improves quality because it connects testing with each development phase and helps detect defects early through verification and validation.

---

## 5. Describe phases of Software Testing Life Cycle (STLC).

Software Testing Life Cycle (STLC) is a sequence of testing activities performed to ensure that software meets quality expectations. It gives structure to the testing process and defines what testers do at each stage.

The main phases of STLC are:

1. Requirement analysis: Testers study requirements and identify what can be tested. Ambiguous, missing, or conflicting requirements are clarified.
2. Test planning: Test manager or test lead prepares the test plan. It includes scope, objectives, schedule, resources, risks, tools, entry criteria, and exit criteria.
3. Test case development: Testers write test cases, prepare test data, and define expected results.
4. Test environment setup: The required hardware, software, database, network, browser, and tools are configured. This environment is also called the test bed.
5. Test execution: Test cases are executed. Actual results are compared with expected results. Passed and failed cases are recorded.
6. Defect reporting and tracking: Failed cases are reported as defects. Developers fix them, and testers retest the fixes.
7. Test closure: Testing activities are summarized. Metrics such as total test cases, passed cases, failed cases, defect density, and defect status are reported.

```text
Requirement analysis
        |
        v
Test planning
        |
        v
Test case development
        |
        v
Test environment setup
        |
        v
Test execution
        |
        v
Defect tracking
        |
        v
Test closure
```

STLC helps the team test in an organized way and ensures that quality is measured instead of assumed.

---

## 6. Compare error, fault, defect, and failure and give examples.

Error, fault, defect, and failure are related terms, but they represent different stages of a problem in software.

| Term | Meaning | Example |
|---|---|---|
| Error | Human mistake made by a developer, tester, analyst, or user | Developer misunderstands discount formula |
| Fault | Incorrect logic or condition present in code or design due to an error | Code uses `>` instead of `>=` |
| Defect | A confirmed deviation between actual behavior and expected requirement | System gives wrong discount for exactly Rs. 1000 |
| Failure | External incorrect behavior observed when software runs | Customer receives incorrect bill |

Flow of relationship:

```text
Human error
     |
     v
Fault in code/design
     |
     v
Defect found during testing
     |
     v
Failure observed during execution
```

Example: In a student result system, the requirement says that a student passes if marks are greater than or equal to 40. A developer mistakenly writes `marks > 40`. This is a human error that creates a fault in the code. During testing, the tester finds that a student with exactly 40 marks is shown as fail. This is reported as a defect. If the system is released and a real student with 40 marks is marked fail, it becomes a failure.

Understanding these terms helps testers report issues clearly and helps developers locate the root cause.

---

## 7. Describe the role of test case and test suite in testing.

A test case is a set of conditions, inputs, execution steps, and expected results used to verify a specific requirement or behavior of software. A test suite is a collection of related test cases grouped together for execution.

A test case usually contains:

- Test case ID
- Requirement reference
- Test objective
- Preconditions
- Test input or test data
- Execution steps
- Expected result
- Actual result
- Status such as pass or fail

Example test case for login:

| Field | Value |
|---|---|
| Test case ID | TC_LOGIN_01 |
| Objective | Verify login with valid credentials |
| Input | Username: `student1`, Password: `Pass@123` |
| Expected result | User should login and dashboard should open |
| Status | Pass or Fail after execution |

A test suite groups multiple test cases. For example, a login test suite may contain test cases for valid login, invalid password, blank username, locked account, password reset, and session timeout.

```text
Test suite: Login Testing
      |
      +-- TC01 Valid login
      +-- TC02 Invalid password
      +-- TC03 Blank username
      +-- TC04 Locked account
      +-- TC05 Logout
```

The role of test cases is to make testing repeatable and measurable. The role of a test suite is to organize related tests and execute them efficiently. Together, they help maintain coverage, traceability, and consistency in testing.

---

## 8. Given a login system, apply the concept of a test oracle to verify whether the output is correct or not. Explain with an example.

A test oracle is a source used to decide whether the actual output of a test is correct or incorrect. It may be a requirement document, business rule, database value, previous correct version, mathematical formula, or expert decision.

For a login system, the test oracle can be the requirement specification that defines valid and invalid login behavior.

Example requirement:

- If username and password are correct, the user should be redirected to the dashboard.
- If password is incorrect, the system should display "Invalid username or password".
- If fields are blank, the system should show validation messages.
- If the account is locked, login should be denied.

Example test using oracle:

| Test input | Oracle / Expected result | Actual result | Decision |
|---|---|---|---|
| Valid username and password | Dashboard opens | Dashboard opens | Pass |
| Valid username, wrong password | Error message shown | Dashboard opens | Fail |
| Blank password | Password required message | Password required message | Pass |

Flow:

```text
Enter login data
      |
      v
System gives actual output
      |
      v
Compare with test oracle
      |
   +--+--+
   |     |
 Match  Mismatch
   |     |
 Pass   Defect
```

If a user enters correct credentials and the dashboard opens, the output matches the oracle. If a wrong password still allows login, the actual result does not match the oracle, so it is a defect. Thus, a test oracle helps testers judge correctness in a systematic way.

---

## 9. Describe software quality and its key attributes.

Software quality means the degree to which software satisfies stated requirements, user expectations, and quality standards. Good quality software performs its intended function correctly, reliably, efficiently, securely, and in a user-friendly manner.

Key attributes of software quality include:

- Correctness: The software produces correct results according to requirements. Example: A calculator gives correct addition and division results.
- Reliability: The software works consistently without frequent failures. Example: A banking system should not crash during transactions.
- Usability: The software is easy to learn and use. Example: A food delivery app should allow users to place orders without confusion.
- Efficiency: The software uses time, memory, network, and processor resources properly. Example: Search results should load quickly.
- Maintainability: The software can be modified, fixed, and improved easily. Example: Code with clear structure is easier to update.
- Portability: The software can run in different environments. Example: A web application works on Chrome, Firefox, and mobile browsers.
- Security: The software protects data from unauthorized access. Example: Passwords should not be stored in plain text.
- Testability: The software can be tested easily through clear inputs, outputs, and logs.

Software quality is not achieved only by testing at the end. It requires good requirements, design reviews, coding standards, testing, SQA activities, and continuous improvement. Testing helps measure quality, while software quality assurance helps improve the development process that produces quality.

---

## 10. Given a project with frequent defects, how would the SQA group act to improve quality? Apply their roles with suitable steps.

Software Quality Assurance (SQA) is a group or function responsible for ensuring that proper processes, standards, and quality practices are followed during software development. If a project has frequent defects, the SQA group should not only blame developers or testers. It should analyze the process and improve it.

Steps taken by the SQA group:

1. Analyze defect data: Study defect reports to find repeated defect types, affected modules, severity, and root causes.
2. Review development process: Check whether requirements, design, coding, reviews, and testing activities are being followed properly.
3. Improve requirement clarity: Conduct requirement reviews to reduce ambiguity and missing conditions.
4. Introduce review policies: Use inspections or walkthroughs for requirement documents, design documents, and code.
5. Define quality standards: Prepare coding standards, test case standards, defect reporting rules, and review checklists.
6. Strengthen testing process: Ensure that STLC phases are followed, including test planning, test case design, environment setup, execution, and closure.
7. Track metrics: Use metrics such as defect density, defect leakage, review defects, test coverage, and defect removal efficiency.
8. Conduct training: Train developers and testers on common defect areas, tools, and quality expectations.
9. Audit compliance: Check whether teams are following approved processes.
10. Support continuous improvement: Use lessons learned to update checklists, templates, and review plans.

```text
Frequent defects
      |
      v
Defect analysis
      |
      v
Root cause identification
      |
      v
Process improvement
      |
      v
Reviews, standards, metrics, training
      |
      v
Reduced defects
```

Thus, the SQA group improves quality by preventing defects, improving processes, and measuring results.

---

## 11. A team needs to review code with limited time. Apply appropriate review technique (inspection or walkthrough) and justify your decision.

If a team needs to review code with limited time, a walkthrough is usually more appropriate than a formal inspection. A walkthrough is a review technique where the author explains the code to peers and receives feedback. It is less formal, faster, and easier to conduct when time is limited.

Inspection is more formal. It uses defined roles such as moderator, reader, recorder, and inspectors. It requires preparation, checklists, entry criteria, and detailed defect recording. Inspection is highly effective for critical modules, but it takes more time.

Walkthrough is suitable in this case because:

- It can be arranged quickly.
- The code author can explain logic directly.
- Team members can ask questions and identify obvious defects.
- It supports knowledge sharing.
- It is useful when the goal is quick review before further testing.

Example: Suppose a team has limited time to review a login validation module before release. The developer conducts a walkthrough and explains input validation, password checking, error messages, and session handling. Testers and peers identify missing checks for blank password and locked account.

Decision:

| Condition | Better technique |
|---|---|
| Limited time, quick feedback needed | Walkthrough |
| Safety-critical or high-risk module | Inspection |
| Need formal metrics and defect records | Inspection |
| Need informal understanding and early feedback | Walkthrough |

Therefore, for limited time, a walkthrough is justified. However, if the code belongs to a highly critical area such as banking payment or medical calculation, inspection should be preferred despite the extra time.

---

## 12. Apply the TDD approach to develop a module for student result processing. Show test cases and corresponding code logic.

Test Driven Development (TDD) is a development approach in which test cases are written before the actual code. The cycle is Red, Green, and Refactor.

```text
Write failing test
      |
      v
Write minimum code to pass
      |
      v
Refactor code
      |
      v
Repeat
```

Requirement: A student passes if marks are greater than or equal to 40. Grade is `A` for 80 and above, `B` for 60 to 79, `C` for 40 to 59, and `F` below 40. Marks must be between 0 and 100.

Test cases:

| Test case | Input | Expected output |
|---|---|---|
| TC01 | 85 | Pass, Grade A |
| TC02 | 65 | Pass, Grade B |
| TC03 | 40 | Pass, Grade C |
| TC04 | 39 | Fail, Grade F |
| TC05 | -5 | Invalid marks |
| TC06 | 105 | Invalid marks |

Example test logic:

```java
assertEquals("A", resultService.grade(85));
assertEquals("B", resultService.grade(65));
assertEquals("C", resultService.grade(40));
assertEquals("F", resultService.grade(39));
assertThrows(IllegalArgumentException.class, () -> resultService.grade(-5));
```

Corresponding code logic:

```java
String grade(int marks) {
    if (marks < 0 || marks > 100) {
        throw new IllegalArgumentException("Invalid marks");
    }
    if (marks >= 80) return "A";
    if (marks >= 60) return "B";
    if (marks >= 40) return "C";
    return "F";
}

boolean isPass(int marks) {
    if (marks < 0 || marks > 100) {
        throw new IllegalArgumentException("Invalid marks");
    }
    return marks >= 40;
}
```

By applying TDD, the developer first writes tests for expected behavior, then writes only enough code to pass those tests, and finally improves the code without changing behavior. This reduces defects and gives confidence in result processing logic.

---

## 13. Apply testing as an engineering activity for a banking application.

Testing a banking application as an engineering activity means applying systematic, planned, documented, and measurable testing practices to verify critical banking functions. Banking software deals with money, customer data, security, and legal responsibility, so testing must be disciplined.

Steps to apply engineering-based testing:

1. Requirement study: Understand account creation, login, balance inquiry, fund transfer, withdrawal, deposit, interest calculation, and statement generation.
2. Risk analysis: Identify high-risk areas such as fund transfer, authentication, transaction rollback, and data security.
3. Test planning: Decide scope, test levels, resources, schedule, tools, and entry/exit criteria.
4. Test case design: Prepare test cases for valid transactions, invalid inputs, boundary values, insufficient balance, duplicate transactions, and network failure.
5. Test bed setup: Configure database, test accounts, transaction limits, browser, server, and network conditions.
6. Test execution: Execute test cases and record actual results.
7. Defect reporting: Log defects with transaction ID, account details, expected result, actual result, and evidence.
8. Retesting and regression testing: Verify fixed defects and ensure related banking functions are not broken.

Example test case:

| Scenario | Expected result |
|---|---|
| Transfer Rs. 1000 from Account A with Rs. 5000 balance to Account B | Account A becomes Rs. 4000, Account B increases by Rs. 1000, transaction receipt is generated |

```text
Banking requirement
      |
      v
Risk-based test design
      |
      v
Controlled test bed
      |
      v
Execution and comparison
      |
      v
Defect reporting and quality improvement
```

This shows testing as an engineering activity because it uses planning, risk analysis, controlled execution, evidence, and measurable quality results.

---

## 14. Design a testing workflow for an e-commerce system using testing process.

A testing workflow for an e-commerce system should follow the testing process from requirement analysis to test closure. The system includes user registration, login, product search, cart, payment, order placement, cancellation, and tracking.

Workflow:

1. Requirement analysis: Study features such as product listing, cart calculation, discounts, payment, shipping charges, and order status.
2. Test planning: Define testing scope, resources, schedule, tools, browsers, mobile devices, and risks.
3. Test case design: Prepare test cases for product search, add to cart, remove from cart, coupon application, payment success, payment failure, and order confirmation.
4. Test data preparation: Create users, products, stock quantities, coupons, addresses, and payment test data.
5. Test bed setup: Configure web server, database, payment gateway sandbox, browsers, and test devices.
6. Test execution: Run test cases and record actual results.
7. Defect reporting: Report issues such as wrong cart total, failed payment handling, incorrect stock update, or missing order confirmation.
8. Retesting: Verify fixed defects.
9. Regression testing: Check that fixes did not break related functions like checkout or inventory.
10. Test closure: Prepare summary report and quality metrics.

```text
E-commerce requirements
        |
        v
Plan testing
        |
        v
Design test cases and data
        |
        v
Set up test bed
        |
        v
Execute tests
        |
        v
Report and retest defects
        |
        v
Closure report
```

Example: If the requirement says a 10% coupon should apply only on orders above Rs. 1000, test cases should check order values of Rs. 999, Rs. 1000, and Rs. 1001. This workflow ensures that testing is complete, traceable, and aligned with the business requirements.

---

## 15. Classify activities into verification and validation for an online voting system.

In an online voting system, verification activities check whether documents, design, and code follow the specification. Validation activities check whether the running system behaves correctly for voters, administrators, and election rules.

Verification activities:

- Review requirement document for voter eligibility rules.
- Check design document for authentication, vote recording, and result calculation.
- Inspect code for duplicate vote prevention logic.
- Review database design for voter ID, candidate ID, and vote records.
- Verify security policy for access control and data confidentiality.
- Review test cases for coverage of valid and invalid voting scenarios.

Validation activities:

- Execute test where a valid voter logs in and casts one vote.
- Test that an invalid voter cannot vote.
- Test that the same voter cannot vote twice.
- Test that votes are counted correctly.
- Test that voting closes after the deadline.
- Test user interface behavior on mobile and desktop.
- Perform user acceptance testing with election officers.

Example classification:

| Activity | Type | Reason |
|---|---|---|
| Reviewing voter eligibility requirement | Verification | Document is checked without execution |
| Testing actual vote submission | Validation | Running software behavior is checked |
| Code inspection for duplicate vote logic | Verification | Code is statically reviewed |
| Checking final vote count after execution | Validation | Actual output is compared with expected result |

Both verification and validation are necessary because online voting requires correctness, security, reliability, and trust.

---

## 16. Apply V&V techniques to ensure correctness of a student result system.

Verification and validation techniques can be applied to a student result system to ensure that marks, grades, pass/fail status, and reports are correct.

Verification techniques:

1. Requirement review: Check whether rules for passing marks, grace marks, grading, absent students, and revaluation are clearly written.
2. Design review: Verify that the system design includes modules for marks entry, grade calculation, result generation, and report printing.
3. Code inspection: Review code for boundary conditions such as exactly 40 marks or 100 marks.
4. Test case review: Ensure test cases cover pass, fail, absent, invalid marks, and boundary values.

Validation techniques:

1. Unit testing: Test grade calculation and pass/fail logic separately.
2. Integration testing: Test marks entry with result generation.
3. System testing: Test the complete student result system from data entry to final report.
4. User acceptance testing: Ask exam department users to verify whether reports match expected academic rules.

Example:

| Scenario | Expected behavior |
|---|---|
| Marks = 40 | Student should pass |
| Marks = 39 | Student should fail |
| Marks = 101 | System should reject invalid marks |
| Student absent | Result should show absent according to rule |

```text
Verify rules and design
        |
        v
Inspect code and test cases
        |
        v
Execute test cases
        |
        v
Compare actual result with expected result
```

Using both V&V techniques ensures that the system is built according to rules and also works correctly when used.

---

## 17. Apply V&V when requirements are unclear to reduce defects.

When requirements are unclear, defects increase because developers and testers may interpret the same requirement differently. Verification and validation should be applied early to clarify expectations and reduce defects.

Steps:

1. Requirement verification: Review the requirement document to find ambiguous words such as "fast", "secure", "easy", or "proper".
2. Ask clarification questions: Discuss unclear points with customers, business analysts, and users.
3. Prepare examples: Convert unclear requirements into concrete examples.
4. Define acceptance criteria: Write measurable conditions that must be satisfied.
5. Create traceability: Link each requirement to test cases.
6. Prototype if needed: Use simple screens or sample outputs to validate user expectations.
7. Review test cases early: Confirm whether test cases match the intended requirement.
8. Validate with users: Execute sample scenarios and confirm whether the behavior is acceptable.

Example: Requirement says, "The result should be generated quickly." This is unclear. After verification, it can be clarified as, "The result for one class of 60 students should be generated within 5 seconds." Validation can then test whether the running system satisfies this condition.

```text
Unclear requirement
       |
       v
Review and ask questions
       |
       v
Define measurable acceptance criteria
       |
       v
Design test cases
       |
       v
Validate with actual execution
```

Thus, V&V reduces defects by removing ambiguity before coding and confirming correct behavior after implementation.

---

## 18. Relate development phases with testing phases using the V-Model.

The V-Model relates each development phase with a corresponding testing phase. Testing activities are planned in parallel with development activities. This helps detect defects early and ensures that every development output has a related test activity.

Relationship between phases:

| Development phase | Testing phase | Explanation |
|---|---|---|
| Requirement analysis | Acceptance testing | User requirements are used to design acceptance tests |
| System design | System testing | Complete system design is used to plan system tests |
| Architecture design | Integration testing | Interfaces between modules are tested |
| Module design | Unit testing | Individual modules are tested against module design |
| Coding | Test execution starts at unit level | Code is implemented and tested |

Diagram:

```text
Requirement analysis -------- Acceptance testing
          \                  /
           \                /
System design -------- System testing
             \          /
              \        /
Architecture design -- Integration testing
                \    /
                 \  /
              Module design
                   |
                 Coding
                   |
              Unit testing
```

Example: In a food delivery application, the requirement "user can place an order" is related to acceptance testing. The system design for restaurant, cart, payment, and delivery modules is related to system testing. The interface between cart and payment is related to integration testing. The price calculation function is related to unit testing.

The V-Model shows that testing is not an activity done only after coding. It is connected to every phase of development.

---

## 19. Apply the V-Model in an Agile-like environment.

The V-Model can be applied in an Agile-like environment by using a smaller V-cycle for each sprint or user story. Agile development is iterative, while the V-Model is usually shown as sequential. However, its main principle, early test planning for each development activity, can still be used.

Application in Agile:

1. Select a user story for the sprint.
2. Clarify acceptance criteria with the product owner.
3. Plan acceptance tests from the user story.
4. Design the module and prepare unit and integration tests.
5. Implement the code.
6. Execute unit, integration, system, and acceptance tests for that story.
7. Fix defects within the sprint.
8. Perform regression testing for existing features.

```text
User story
    |
    v
Acceptance criteria -------- Acceptance tests
        \                   /
         \                 /
Design and tasks ---- Integration/System tests
           \             /
            \           /
          Coding -- Unit tests
```

Example: For an Agile sprint in an e-commerce project, the user story is "As a user, I want to apply a coupon to my cart." The team verifies acceptance criteria such as minimum order value and coupon expiry. Developers write code, and testers execute unit, integration, and acceptance tests within the sprint.

Thus, the V-Model can support Agile by applying verification and validation in short cycles instead of waiting until the end of the project.

---

## 20. Apply STLC phases for a food delivery application.

STLC phases can be applied to a food delivery application to test features such as restaurant search, menu display, cart, payment, order placement, delivery tracking, and cancellation.

1. Requirement analysis: Study requirements such as user registration, restaurant listing, food item availability, delivery address, payment, and order tracking. Identify testable requirements and unclear points.
2. Test planning: Decide scope, test strategy, schedule, resources, tools, devices, browsers, and risks. Payment and order placement should be treated as high-risk areas.
3. Test case development: Prepare test cases for adding food items, applying coupons, calculating delivery charges, successful payment, failed payment, order cancellation, and delivery status updates.
4. Test data preparation: Create sample users, restaurants, menu items, coupons, delivery locations, and payment test cards.
5. Test environment setup: Configure application server, database, payment gateway sandbox, map/location service, and mobile/browser test environment.
6. Test execution: Run all test cases and compare actual results with expected results.
7. Defect reporting and tracking: Report defects such as wrong bill amount, unavailable item added to cart, or incorrect delivery time.
8. Retesting and regression testing: Retest fixed defects and check that related features still work.
9. Test closure: Prepare test summary report including executed cases, passed cases, failed cases, open defects, and quality status.

Example test case:

| Scenario | Expected result |
|---|---|
| User orders food worth Rs. 500 with Rs. 50 delivery charge | Total amount should be Rs. 550 before discount |

STLC ensures that the food delivery application is tested in an organized way before release.

---

## 21. A login system crashes when incorrect input is given. Apply your understanding to classify error, fault, defect, and failure.

In this scenario, the login system crashes when incorrect input is given. The problem can be classified using error, fault, defect, and failure.

- Error: The human mistake may be that the developer forgot to handle invalid input, such as blank username or special characters.
- Fault: The code contains faulty logic, such as directly accessing a value without checking whether it is null.
- Defect: During testing, the tester observes that the login module does not handle incorrect input as required. This mismatch between expected and actual behavior is reported as a defect.
- Failure: The visible crash of the running login system is a failure because the software is not behaving correctly during execution.

Example:

Requirement: If username or password is invalid, show an error message and remain on the login page.

Actual behavior: The system crashes with an exception when the password field is blank.

```text
Developer forgets input validation
        |
        v
Null or invalid input handling fault in code
        |
        v
Tester reports crash as defect
        |
        v
Running system crashes: failure
```

Correct behavior should be:

- Validate input before processing.
- Show a proper error message.
- Do not crash.
- Log the technical error for debugging if needed.

Thus, the crash is a failure, while the missing validation in code is the fault that caused the defect.

---

## 22. Make use of test cases for a login module or any given application.

Test cases are used to verify whether a login module works according to requirements. A login module usually checks username, password, validation messages, authentication, session creation, and logout behavior.

Sample test cases for login module:

| Test case ID | Scenario | Input | Expected result |
|---|---|---|---|
| TC_LOGIN_01 | Valid login | Correct username and password | User should be redirected to dashboard |
| TC_LOGIN_02 | Invalid password | Correct username, wrong password | Error message should be displayed |
| TC_LOGIN_03 | Blank username | Empty username, valid password | Username required message should be shown |
| TC_LOGIN_04 | Blank password | Valid username, empty password | Password required message should be shown |
| TC_LOGIN_05 | Both fields blank | Empty username and password | Required field messages should be shown |
| TC_LOGIN_06 | SQL injection input | `' OR '1'='1` | Login should fail and system should not crash |
| TC_LOGIN_07 | Locked account | Locked user credentials | Access should be denied with proper message |
| TC_LOGIN_08 | Logout | Logged-in user clicks logout | Session should end and login page should open |

Execution process:

```text
Select test case
      |
      v
Enter test data
      |
      v
Execute login
      |
      v
Compare actual result with expected result
      |
      v
Mark Pass or Fail
```

These test cases help verify normal behavior, invalid behavior, boundary conditions, and security-related input handling. They also make testing repeatable and easier to track.

---

## 23. Apply any four testing principles in a real-time system.

Testing principles guide testers in planning effective testing. In a real-time system, such as an online railway reservation system, these principles help prioritize important and risky areas.

1. Testing shows presence of defects, not their absence: Testing can show that defects exist, but it cannot prove that the system has no defects. For railway reservation, passing test cases for booking and cancellation does not guarantee that all possible failures are removed.

2. Exhaustive testing is impossible: It is not possible to test every combination of train, date, class, passenger type, quota, payment method, and cancellation rule. Therefore, testers should use risk-based and priority-based testing.

3. Early testing saves time and cost: Requirements such as seat availability, waiting list, RAC, and refund rules should be reviewed early. Finding mistakes in these rules before coding reduces expensive rework.

4. Defect clustering: Most defects are often found in a few modules. In railway reservation, defects may cluster in payment, seat allocation, and cancellation modules. Testers should give more attention to these high-risk modules.

Application:

```text
Identify critical modules
        |
        v
Prioritize high-risk test cases
        |
        v
Test early and repeatedly
        |
        v
Use defect data to focus testing
```

These principles help testers make practical decisions when time, resources, and test data are limited.

---

## 24. Apply TDD for implementing login functionality.

Test Driven Development (TDD) can be applied to login functionality by writing tests before writing the login code. The login module should authenticate users based on valid credentials and reject invalid input.

Requirement:

- Valid username and password should allow login.
- Wrong password should reject login.
- Blank fields should return validation errors.
- Locked user should not be allowed to login.

TDD cycle:

```text
Red: write failing test
      |
      v
Green: write minimum code to pass
      |
      v
Refactor: improve code
```

Sample test cases:

| Test case | Input | Expected output |
|---|---|---|
| TC01 | Valid username and password | Login success |
| TC02 | Valid username, wrong password | Login failed |
| TC03 | Blank username | Validation error |
| TC04 | Blank password | Validation error |
| TC05 | Locked account | Login denied |

Example test logic:

```java
assertTrue(authService.login("student1", "Pass@123"));
assertFalse(authService.login("student1", "wrong"));
assertThrows(IllegalArgumentException.class,
    () -> authService.login("", "Pass@123"));
```

Example code logic:

```java
boolean login(String username, String password) {
    if (username == null || username.isBlank()) {
        throw new IllegalArgumentException("Username required");
    }
    if (password == null || password.isBlank()) {
        throw new IllegalArgumentException("Password required");
    }
    User user = userRepository.findByUsername(username);
    if (user == null || user.isLocked()) {
        return false;
    }
    return user.getPassword().equals(password);
}
```

Using TDD ensures that important login behavior is defined before coding. It also supports regression testing when login logic is changed later.

---

## 25. Make use of STLC phases using a given requirement document.

STLC phases can be applied directly using a requirement document. The requirement document acts as the main input for identifying test conditions, designing test cases, preparing test data, and validating software behavior.

Example requirement: "A user should be able to register with name, email, mobile number, and password. Email must be unique and password must have at least 8 characters."

Application of STLC:

1. Requirement analysis: Identify testable conditions such as mandatory name, valid email format, unique email, valid mobile number, and password length.
2. Test planning: Define scope as registration testing. Decide resources, schedule, browser/device coverage, and risks such as duplicate accounts.
3. Test case development: Prepare test cases for valid registration, duplicate email, invalid email, short password, blank fields, and invalid mobile number.
4. Test data preparation: Create sample valid users, duplicate email data, invalid email data, and boundary password values.
5. Test environment setup: Configure web application, database, email service if required, and browser environment.
6. Test execution: Execute the prepared test cases and record actual results.
7. Defect reporting: If duplicate email is accepted, report it as a defect with steps and screenshots.
8. Retesting and regression testing: Retest the fixed duplicate email issue and check that valid registration still works.
9. Test closure: Prepare report showing total cases, passed cases, failed cases, defects fixed, and pending risks.

```text
Requirement document
        |
        v
Test conditions
        |
        v
Test cases and test data
        |
        v
Execution and defect tracking
        |
        v
Closure report
```

Thus, the requirement document is converted into planned and traceable testing activities through STLC.

---

## 26. Identify how an error leads to failure in a railway reservation system.

An error is a human mistake. If the error is introduced into software design or code, it becomes a fault. When testing identifies the mismatch, it is treated as a defect. When the software runs and produces incorrect behavior, it becomes a failure.

Example in railway reservation:

Requirement: If all confirmed seats are booked, the next passenger should be placed on the waiting list.

Human error: The developer misunderstands the seat allocation rule and forgets to check the number of available confirmed seats.

Fault: The code always assigns a confirmed seat without checking availability.

Defect: During testing, the tester finds that the system confirms a ticket even when all seats are already booked.

Failure: In real use, two passengers receive confirmed tickets for the same seat, causing incorrect reservation behavior.

```text
Developer misunderstands rule
        |
        v
Wrong seat allocation logic
        |
        v
Tester detects overbooking defect
        |
        v
Passenger receives wrong confirmed ticket
```

This example shows that a small human error can create a fault in the system, which becomes a defect during testing and a failure during actual operation. Proper requirement review, code inspection, and test cases for full-seat conditions can reduce such failures.

---

## 27. Apply test oracle for validating outputs in a calculator system.

A test oracle is used to decide whether the output produced by the software is correct. In a calculator system, the oracle can be mathematical rules, known correct results, or a trusted calculator.

Examples of oracle-based validation:

| Operation | Input | Oracle / Expected result | Actual result | Decision |
|---|---|---|---|---|
| Addition | 10 + 5 | 15 | 15 | Pass |
| Subtraction | 10 - 5 | 5 | 4 | Fail |
| Multiplication | 6 * 7 | 42 | 42 | Pass |
| Division | 10 / 2 | 5 | 5 | Pass |
| Division by zero | 10 / 0 | Error message | Error message | Pass |

Process:

```text
Enter calculator input
        |
        v
Get actual output
        |
        v
Compare with mathematical oracle
        |
        v
Pass or fail decision
```

Example: For input `10 - 5`, the mathematical oracle says the expected output is `5`. If the calculator displays `4`, the actual output does not match the oracle, so the test fails and a defect is reported.

The test oracle is important because testing requires a clear expected result. Without an oracle, the tester may execute the calculator but cannot confidently decide whether the output is correct.

---

## 28. Apply testing principles to prioritize test cases under constraints.

When time, budget, or resources are limited, testers cannot execute all test cases with equal priority. Testing principles help prioritize test cases logically.

Application of principles:

1. Exhaustive testing is impossible: Since all combinations cannot be tested, select important and representative test cases.
2. Defect clustering: Give higher priority to modules where more defects were found earlier.
3. Early testing: Execute tests for critical requirements early so serious defects are found sooner.
4. Pesticide paradox: Update test cases regularly because repeating the same tests may stop finding new defects.
5. Testing is context dependent: Prioritize based on the type of system. A banking system needs stronger testing for transactions and security, while an e-commerce system needs strong testing for cart, payment, and order flow.

Example: For an e-commerce application with limited time, priority should be:

| Priority | Test area | Reason |
|---|---|---|
| High | Login, payment, order placement | Business-critical and high-risk |
| High | Cart total and discounts | Financial correctness |
| Medium | Product search and filters | Important but less risky |
| Low | UI color and minor alignment | Lower business impact |

```text
Limited time
     |
     v
Identify risk and business impact
     |
     v
Prioritize critical test cases
     |
     v
Execute high-priority tests first
```

Thus, testing principles help testers focus on the most valuable test cases when complete testing is not possible.

---

## 29. Show step-by-step application of TDD for a given requirement.

Test Driven Development (TDD) follows the Red-Green-Refactor cycle. The developer writes a failing test first, then writes minimum code to pass it, and finally improves the code.

Given requirement: "A library system should calculate fine as Rs. 5 per day if a book is returned late. If days late are zero or negative, fine should be Rs. 0."

Step 1: Write the first failing test.

```java
assertEquals(0, fineCalculator.calculate(0));
```

Step 2: Write minimum code to pass.

```java
int calculate(int daysLate) {
    return 0;
}
```

Step 3: Add another failing test.

```java
assertEquals(25, fineCalculator.calculate(5));
```

Step 4: Update code.

```java
int calculate(int daysLate) {
    if (daysLate <= 0) {
        return 0;
    }
    return daysLate * 5;
}
```

Step 5: Add boundary and invalid tests.

```java
assertEquals(0, fineCalculator.calculate(-2));
assertEquals(5, fineCalculator.calculate(1));
```

Step 6: Refactor if needed. The code is already simple, so no major refactoring is needed.

TDD flow:

```text
Requirement
    |
    v
Write failing test
    |
    v
Write simple code
    |
    v
Run test
    |
    v
Refactor
    |
    v
Repeat for next rule
```

This approach ensures that the requirement is converted into executable tests before implementation, reducing misunderstanding and defects.

---

## 30. Choose roles and responsibilities in STLC for a startup project.

In a startup project, the team is usually small, so one person may handle multiple roles. Still, STLC responsibilities should be clearly assigned to avoid confusion and missed testing activities.

Suggested roles:

| Role | Responsibilities |
|---|---|
| Product owner / founder | Provides requirements, priorities, and acceptance criteria |
| Test lead / QA owner | Prepares test plan, defines scope, tracks testing progress, reports quality status |
| Tester / QA engineer | Writes test cases, prepares test data, executes tests, reports defects |
| Developer | Performs unit testing, fixes defects, supports test environment setup |
| DevOps / technical owner | Sets up test server, database, builds, deployments, and monitoring |
| Customer representative | Performs user acceptance testing and confirms business behavior |

STLC responsibility mapping:

1. Requirement analysis: Product owner, tester, and developer clarify requirements.
2. Test planning: QA owner decides what to test first based on risk and business priority.
3. Test case development: Tester writes test cases and reviews them with developer/product owner.
4. Environment setup: Developer or DevOps person prepares test environment.
5. Test execution: Tester executes functional tests; developer runs unit tests.
6. Defect tracking: Tester reports defects; developer fixes; QA owner tracks status.
7. Test closure: QA owner prepares summary and release recommendation.

For a startup, role clarity is more important than having many people. Even if one person performs multiple roles, responsibilities should be documented so that testing remains organized.

---

## 31. Analyze and justify whether a given issue is defect or failure.

A defect is a flaw or mismatch between expected and actual behavior found in software. A failure is the visible incorrect behavior of the software during execution. The same issue may be described differently depending on the context.

Example issue: "When a user clicks the Pay button, the payment page shows an error and the order is not placed."

Analysis:

- If the tester reports this during testing because the system does not meet the expected payment requirement, it is a defect.
- If the same issue happens during actual use and the user cannot place an order, it is a failure.

Justification:

| Situation | Classification | Reason |
|---|---|---|
| Tester finds wrong behavior in test environment | Defect | It is reported as a deviation from requirement |
| Customer experiences wrong behavior in production | Failure | The running system fails to provide expected service |
| Code contains wrong API URL for payment gateway | Fault | It is the internal cause |
| Developer typed the wrong URL due to misunderstanding | Error | It is the human mistake |

Example requirement: "Payment must be completed and order must be created after successful card authorization." If the system receives successful payment response but does not create the order, the tester reports a defect. If released to users, the same wrong behavior becomes a failure.

Thus, an issue is called a defect when it is identified as a problem in the software, and it is called a failure when the software actually behaves incorrectly during execution.

---

## 32. Outline a test bed for a given application.

A test bed is the complete testing environment required to execute test cases. It includes hardware, software, network, database, tools, test data, and configuration needed for testing.

Example application: Online shopping system.

Test bed outline:

| Component | Details |
|---|---|
| Hardware | Test machines, mobile devices, server machine if required |
| Operating system | Windows, Linux, Android, iOS depending on scope |
| Browser | Chrome, Firefox, Edge, mobile browser |
| Application server | Web server or application runtime |
| Database | Test database with sample users, products, orders, and coupons |
| Network | Stable internet, slow network simulation if needed |
| External services | Payment gateway sandbox, email/SMS test service |
| Test data | User accounts, product catalog, stock values, addresses, coupons |
| Tools | Defect tracking tool, test management tool, automation tool if used |
| Configuration | Environment variables, API endpoints, user roles, access permissions |

```text
Tester machine
     |
     v
Browser / mobile device
     |
     v
Test server
     |
     v
Test database
     |
     v
External sandbox services
```

A good test bed should be close to the real production environment but safe for testing. It should not use real payment or customer data. A properly prepared test bed ensures reliable, repeatable, and meaningful test execution.

---

## 33. Design and justify an appropriate test bed for a given system.

An appropriate test bed should match the type, risk, users, and environment of the system being tested. For example, consider a college examination result system.

Designed test bed:

| Component | Test bed design |
|---|---|
| Server | Test application server similar to production configuration |
| Database | Separate test database with sample students, subjects, marks, and rules |
| User roles | Admin, faculty, exam officer, student |
| Test data | Valid marks, invalid marks, absent students, failed students, toppers, revaluation cases |
| Browsers | Chrome, Firefox, Edge |
| Devices | Desktop and mobile browser for student result viewing |
| Tools | Test management sheet/tool, defect tracker, logs, database viewer |
| Security setup | Role-based access for marks entry and result viewing |
| Backup | Test database backup before major test cycles |

Justification:

- A separate test database prevents damage to real student records.
- Multiple roles are needed because faculty, admin, and students perform different actions.
- Boundary test data such as 39, 40, 100, and 101 marks helps test correctness.
- Browser and device coverage ensures usability for different users.
- Logs and defect tracking help investigate failures.
- Backup helps restore data and repeat tests.

Architecture:

```text
Faculty/Admin browser       Student browser
          |                       |
          +----------+------------+
                     |
                     v
             Test application server
                     |
                     v
              Test result database
```

This test bed is appropriate because it supports functional testing, role-based testing, validation of calculation rules, and safe test execution without affecting real academic data.

---

## 34. Apply TDD in a team unfamiliar with automation tools.

If a team is unfamiliar with automation tools, TDD should be introduced gradually. The main idea of TDD is to think about expected behavior before writing code. Automation helps, but the team can first learn the method using simple unit tests and small examples.

Steps to apply TDD:

1. Start with training: Explain Red-Green-Refactor using simple examples such as calculator or grade calculation.
2. Choose a small module: Do not start with a complex feature. Select simple logic such as password validation.
3. Write manual expected cases first: If tools are unfamiliar, write test scenarios in a table before converting them to automated tests.
4. Introduce one testing framework: Use a simple unit testing tool suitable for the programming language.
5. Write one failing test: Begin with a single clear requirement.
6. Write minimum code: Implement only what is needed to pass the test.
7. Refactor: Improve code after tests pass.
8. Repeat and review: Practice in pairs so developers learn faster.

Example:

| Requirement | Test case |
|---|---|
| Password must have at least 8 characters | `isValid("abc")` should return false |
| Password with 8 characters is valid | `isValid("abcd1234")` should return true |

```text
Simple requirement
      |
      v
Write expected case
      |
      v
Convert to simple automated test
      |
      v
Write code
      |
      v
Run and improve
```

The team should not try to automate everything at once. Starting small builds confidence and gradually makes TDD part of normal development.

---

## 35. Apply test harness for automating a module.

A test harness is a collection of tools, drivers, stubs, test data, and scripts used to execute tests automatically and collect results. It supports testing a module even when the complete application is not available.

Example module: Student grade calculation module.

Components of a test harness:

- Test driver: Calls the module under test with different inputs.
- Stub: Replaces dependent modules that are not ready.
- Test data: Inputs such as marks 85, 40, 39, -1, and 101.
- Expected results: Grade and pass/fail status.
- Execution script: Runs all tests automatically.
- Result report: Shows pass/fail status.

```text
Test data
    |
    v
Test driver ----> Module under test
    |                    |
    |                    v
    +---------- Compare actual output
                 with expected output
                    |
                    v
                Test report
```

Example test driver logic:

```java
assertEquals("A", gradeCalculator.grade(85));
assertEquals("C", gradeCalculator.grade(40));
assertEquals("F", gradeCalculator.grade(39));
```

If the grade module depends on a database but the database is not ready, a stub can return fixed marks for testing.

Using a test harness improves automation, repeatability, and speed. It is especially useful in unit testing and integration testing because modules can be tested independently.

---

## 36. Apply tester responsibilities in handling critical production defects.

A critical production defect is a serious issue found after release that affects real users, business operations, data, money, or security. The tester has an important role in handling it carefully and quickly.

Tester responsibilities:

1. Understand and confirm the issue: Collect user report, screenshots, logs, affected data, time, browser/device, and steps to reproduce.
2. Reproduce the defect: Try to reproduce the issue in a safe test or staging environment.
3. Classify severity and priority: A payment failure, data loss, or security issue should be marked critical.
4. Report clearly: Create a defect report with summary, environment, steps, expected result, actual result, evidence, severity, and impact.
5. Communicate with team: Inform developer, test lead, project manager, and support team.
6. Support root cause analysis: Help identify whether the defect is due to code, data, configuration, or environment.
7. Verify the fix: Retest the fixed issue carefully.
8. Perform regression testing: Check related modules to ensure the fix does not create new issues.
9. Update test cases: Add new test cases so the same defect is caught in future.
10. Participate in review: Help identify why the defect escaped testing.

```text
Production issue reported
        |
        v
Reproduce and collect evidence
        |
        v
Log critical defect
        |
        v
Fix by developer
        |
        v
Retest and regression test
        |
        v
Closure and prevention
```

The tester's responsibility is not only to report the defect but also to help the team fix, verify, and prevent similar defects.

---

## 37. Summarize conflict between developer and tester using role clarity.

Conflict between developers and testers usually occurs when their roles are misunderstood. A developer may feel that testers are finding faults in their work, while testers may feel that developers are not taking defects seriously. Role clarity reduces this conflict.

Developer role:

- Understand requirements and design.
- Write correct and maintainable code.
- Perform unit testing.
- Fix defects reported by testers.
- Explain technical limitations or design decisions.

Tester role:

- Understand requirements from the user's point of view.
- Design and execute test cases.
- Find defects and report them with evidence.
- Verify fixes and perform regression testing.
- Give quality information to the team.

Common conflict example:

| Situation | Cause of conflict | Role clarity solution |
|---|---|---|
| Tester reports many defects | Developer feels blamed | Defects should be treated as product issues, not personal criticism |
| Developer rejects defect | Requirement is unclear | Use requirement document and test oracle for decision |
| Tester says feature failed | Developer says it works on their machine | Use common test bed and reproducible steps |

```text
Unclear roles
     |
     v
Blame and conflict
     |
     v
Clear responsibilities and evidence
     |
     v
Better teamwork and quality
```

Developers and testers have a common goal: delivering quality software. Developers build the product, while testers provide independent quality evaluation. Clear roles, respectful communication, and evidence-based defect reporting reduce conflict.

---

## 38. Apply tester roles in Agile vs traditional development.

Tester roles differ in Agile and traditional development because the development approach is different. In traditional development, testing often happens after major development phases. In Agile, testing is continuous and happens within each sprint.

Tester role in traditional development:

- Study complete requirement documents.
- Prepare test plans after requirements are finalized.
- Design test cases based on specifications.
- Execute tests after coding is completed.
- Report defects in a formal defect tracking system.
- Perform system testing, regression testing, and acceptance support.
- Prepare test summary and closure reports.

Tester role in Agile development:

- Participate in sprint planning and requirement discussions.
- Help define acceptance criteria for user stories.
- Design tests early in the sprint.
- Test continuously as features are developed.
- Collaborate closely with developers and product owner.
- Perform exploratory testing and regression testing.
- Support automation and continuous feedback.

Comparison:

| Aspect | Traditional | Agile |
|---|---|---|
| Timing of testing | Mostly after development phase | Throughout each sprint |
| Requirement style | Detailed documents | User stories and acceptance criteria |
| Communication | More formal | Continuous collaboration |
| Tester involvement | Often later | From the beginning |
| Defect feedback | After test cycle | Immediate within sprint |

In both approaches, the tester's main responsibility is to provide quality information. The difference is that Agile testers work more continuously and collaboratively, while traditional testers work more phase-wise and formally.

---

## 39. Apply software quality attributes to evaluate an application.

Software quality attributes can be used as criteria to evaluate whether an application is good, reliable, useful, and maintainable. Consider an online food delivery application.

Evaluation using quality attributes:

| Quality attribute | How to evaluate | Example |
|---|---|---|
| Correctness | Check whether features work according to requirements | Cart total, delivery charge, and discount are calculated correctly |
| Reliability | Check whether the app works without frequent crashes | App should not fail during order placement |
| Usability | Check ease of use and clarity | User can search restaurant and place order easily |
| Efficiency | Check response time and resource usage | Menu and checkout pages load quickly |
| Security | Check protection of user data and payment flow | Unauthorized user cannot access another user's order |
| Maintainability | Check whether code and design can be changed easily | New coupon rule can be added without breaking checkout |
| Portability | Check whether app works in different environments | App works on Android, iOS, and web browser |
| Testability | Check whether features can be tested clearly | Inputs, outputs, logs, and test data are available |

Example evaluation:

If the food delivery app calculates the total bill correctly but crashes during payment, correctness may be acceptable for cart calculation, but reliability is poor. If the app works but users cannot easily find the checkout button, usability is poor. If a user can view another user's order by changing the order ID, security is poor.

```text
Application
     |
     v
Evaluate quality attributes
     |
     v
Identify weak areas
     |
     v
Improve design, code, testing, and process
```

Thus, software quality attributes help testers and SQA teams evaluate an application from multiple angles instead of checking only whether basic functions work.
