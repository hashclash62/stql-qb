# Unit 3: Levels of Testing and Defect Management Answers

Subject: Software Testing and Quality
Unit: Levels of Testing and Defect Management

---

## 1. Apply different levels of testing (Unit, Integration, System, and Acceptance testing) to a banking application and demonstrate how each level is performed with suitable examples.

Levels of testing are performed from small code units to the complete business system. In a banking application, these levels are important because the software handles money, accounts, authentication, and customer data.

Unit testing checks individual functions or classes separately. For example, a developer tests the interest calculation method, balance update method, or PIN validation method.

| Unit test example | Expected result |
|---|---|
| Calculate interest for Rs. 10000 at 5% | Interest should be Rs. 500 |
| Withdraw Rs. 1000 from Rs. 5000 | Balance should become Rs. 4000 |
| Enter wrong PIN | Authentication should fail |

Integration testing checks whether modules work correctly together. For example, fund transfer requires account validation, balance check, transaction update, and notification modules.

```text
Login module
     |
     v
Account module
     |
     v
Transaction module
     |
     v
Notification module
```

System testing checks the complete banking application as one system. A tester checks end-to-end flows such as login, balance inquiry, fund transfer, mini statement, and logout.

Acceptance testing checks whether the application satisfies customer and bank requirements. Bank staff or client representatives verify real business scenarios such as NEFT transfer, daily withdrawal limit, failed transaction handling, and statement generation.

Thus, unit testing finds small code defects, integration testing finds interface defects, system testing finds end-to-end defects, and acceptance testing confirms business readiness.

---

## 2. Given a software project scenario, identify and classify the sources of defects and demonstrate how each type can be detected during testing.

Defects can originate from different stages of software development. Identifying sources of defects helps the team prevent similar problems in future projects.

Common sources of defects:

| Source of defect | Example | How to detect |
|---|---|---|
| Requirement defect | Requirement says "fast response" but does not define time | Requirement review, acceptance criteria review |
| Design defect | Payment failure flow is not designed | Design review, architecture review |
| Coding defect | Developer uses wrong formula or condition | Unit testing, code review, white box testing |
| Interface defect | Cart module sends amount as string, payment expects number | Integration testing |
| Data defect | Invalid or missing test data in database | Data validation testing |
| Configuration defect | Wrong API URL in test environment | Configuration testing, smoke testing |
| Environment defect | Application works locally but fails on server | Environment testing |
| Documentation defect | User manual gives wrong steps | Documentation review |

Example: In an online shopping system, if the discount requirement says "apply discount for large orders" but does not define the minimum amount, it is a requirement defect. If the developer writes `amount > 5000` instead of `amount >= 5000`, it is a coding defect. If the cart sends the wrong total to payment gateway, it is an interface defect.

```text
Requirement -> Design -> Code -> Integration -> Deployment
     |          |        |          |             |
 Defects can originate at any development stage
```

Detection requires reviews, unit testing, integration testing, system testing, regression testing, and defect analysis.

---

## 3. Apply different levels of testing (Unit, Integration, System, and Acceptance testing) to a real software system such as a banking or ATM application and demonstrate how each level ensures software quality.

Different levels of testing ensure quality by checking the software at increasing levels of completeness. Consider an ATM application.

Unit testing checks individual program units:

- PIN validation function.
- Balance check function.
- Cash withdrawal calculation.
- Receipt generation function.

Example: If account balance is Rs. 5000 and withdrawal is Rs. 1000, the balance update unit should return Rs. 4000.

Integration testing checks combined modules:

- Card reader with authentication module.
- Authentication with account database.
- Withdrawal module with cash dispenser.
- Transaction module with receipt printer.

Example: After successful authentication, the withdrawal module should receive the correct account number and balance.

System testing checks the whole ATM system:

- Insert card.
- Enter PIN.
- Select withdrawal.
- Enter amount.
- Receive cash.
- Print receipt.
- Update account balance.

Acceptance testing checks whether the ATM satisfies bank requirements and user needs. Bank representatives verify transaction limits, security rules, timeout behavior, wrong PIN lockout, and receipt format.

```text
Unit testing -> Integration testing -> System testing -> Acceptance testing
 Small logic       Interfaces           Full ATM flow        Bank approval
```

Each testing level improves quality by detecting defects at the correct level and reducing the risk of production failure.

---

## 4. How would you approach testing a system that is highly dependent on external APIs or third-party services?

A system dependent on external APIs must be tested carefully because failures may occur due to network issues, wrong API responses, rate limits, authentication errors, or third-party downtime.

Approach:

1. Understand API contract: Study request format, response format, status codes, authentication, rate limits, and error codes.
2. Use mocks and stubs: Replace the external API with a fake service during unit and integration testing.
3. Test success responses: Verify behavior when the API returns valid data.
4. Test failure responses: Check handling of `400`, `401`, `403`, `404`, `429`, and `500` responses.
5. Test timeout and retry logic: Verify that the system does not hang when the API is slow.
6. Test fallback behavior: Check whether user-friendly messages are shown when the service is unavailable.
7. Use sandbox environment: For payment, SMS, email, or map APIs, use official test environments.
8. Monitor logs and reports: Capture request IDs, response times, and failure reasons.
9. Perform regression testing: API changes may break existing flows.

Example: A food delivery app depends on a payment gateway. The tester should check payment success, payment failure, invalid card, timeout, duplicate payment prevention, and refund response.

```text
Application
     |
     v
Mock / Stub API for controlled tests
     |
     v
Sandbox API for realistic tests
     |
     v
Production monitoring after release
```

This approach improves reliability by testing both expected and exceptional API behavior.

---

## 5. Describe a time you had to work with a developer to resolve a complex bug. How did you communicate the issue and ensure it was resolved?

In an exam answer, this can be described as a practical scenario. Suppose I was testing an e-commerce application and found that payment was successful, but the order was not created in the system.

First, I reproduced the bug with clear steps:

1. Login as a customer.
2. Add an item to cart.
3. Proceed to payment.
4. Complete payment using test card.
5. Observe that payment succeeds but order history is empty.

Then I prepared a defect report with:

- Summary of the issue.
- Environment details.
- Test data used.
- Steps to reproduce.
- Expected result: Order should be created after successful payment.
- Actual result: Payment is successful, but no order is created.
- Screenshots, logs, and transaction ID.
- Severity: Critical, because customer money is involved.

I discussed the issue with the developer using evidence instead of blame. The developer checked logs and found that the payment callback was received, but the order service failed due to a database constraint.

After the fix, I performed:

- Retesting of the same payment scenario.
- Regression testing of cart, payment failure, order history, and invoice generation.
- Added a new test case for payment callback handling.

This process ensured that the bug was communicated clearly, fixed correctly, and prevented from reappearing.

---

## 6. Given a software application scenario, identify and classify different defect types with suitable examples from the system.

Defect types classify defects based on their nature. This helps testers report issues clearly and helps teams identify weak areas.

Example system: Online food delivery application.

| Defect type | Example |
|---|---|
| Functional defect | User cannot add food item to cart |
| Calculation defect | Total bill does not include delivery charge correctly |
| Interface defect | Payment module receives wrong order amount from cart |
| Validation defect | User can place order with blank address |
| UI defect | Checkout button overlaps with total amount on mobile |
| Performance defect | Restaurant list takes 20 seconds to load |
| Security defect | User can view another user's order by changing order ID |
| Data defect | Order status in database is different from status shown to user |
| Compatibility defect | App works in Chrome but fails in Safari |
| Recovery defect | App does not recover after payment gateway timeout |

Example classification:

If the system accepts negative quantity for a food item, it is a validation defect. If the wrong bill is generated, it is a calculation defect. If the page crashes under heavy load, it is a performance or reliability defect.

Classifying defects helps assign the right severity, priority, owner, and prevention action.

---

## 7. You've identified a critical bug in a production environment. Describe your process for debugging, reporting, and ensuring it's fixed and doesn't reappear.

A critical production bug affects real users, business operations, data, money, security, or system availability. It must be handled quickly and carefully.

Process:

1. Confirm the issue: Verify whether the reported behavior is real and reproducible.
2. Collect evidence: Gather screenshots, logs, user ID, transaction ID, time, browser/device, and affected environment.
3. Assess severity and impact: Mark the bug critical if it causes data loss, payment failure, security issue, or system crash.
4. Report the defect: Create a clear defect report with summary, steps, expected result, actual result, impact, and evidence.
5. Inform stakeholders: Notify developer, test lead, project manager, support team, and business owner if required.
6. Support debugging: Help developers reproduce the bug in staging or test environment.
7. Verify the fix: Retest the original scenario after the developer fixes it.
8. Perform regression testing: Test related areas that may be affected by the fix.
9. Add prevention checks: Add test cases, update regression suite, review logs, and improve monitoring.
10. Close after confirmation: Close the defect only after the fix works and no related failures are found.

```text
Production bug
      |
      v
Reproduce and collect evidence
      |
      v
Report with severity
      |
      v
Fix and retest
      |
      v
Regression test
      |
      v
Update test cases and close
```

This process ensures that the issue is not only fixed but also prevented from reappearing in future releases.

---

## 8. Illustrate the Defect Life Cycle using a real-time example.

The Defect Life Cycle describes the stages through which a defect passes from discovery to closure. It helps teams track and manage defects systematically.

Common defect states:

```text
New -> Assigned -> Open -> Fixed -> Retest -> Verified -> Closed
              \                         |
               \                        v
                -> Rejected / Deferred / Reopened
```

Example: Login system defect.

Defect: The login system allows access with an incorrect password.

1. New: Tester finds the defect and logs it in the defect tracking tool.
2. Assigned: Test lead assigns the defect to a developer.
3. Open: Developer starts analyzing the defect.
4. Fixed: Developer corrects the authentication logic.
5. Retest: Tester repeats the same failed test case.
6. Verified: Tester confirms that incorrect password is now rejected.
7. Closed: Tester closes the defect.

Alternative states:

- Rejected: Developer rejects the defect if it is not valid.
- Duplicate: Same defect was already reported.
- Deferred: Defect is valid but planned for a later release.
- Reopened: Tester finds that the fix did not work.

The defect life cycle improves tracking, responsibility, communication, and quality control.

---

## 9. How do you handle situations where you disagree with a developer's assessment of a bug or a test case?

Disagreement between tester and developer should be handled with evidence, requirements, and professional communication. The goal is not to win an argument, but to decide whether the software behavior is correct.

Steps:

1. Recheck the requirement: Compare the observed behavior with SRS, user story, acceptance criteria, or business rule.
2. Reproduce the issue: Provide exact steps, data, environment, and screenshots.
3. Use a test oracle: Use requirement document, previous correct behavior, business rule, or customer confirmation.
4. Discuss calmly: Explain the impact and ask the developer to explain their reasoning.
5. Involve the right person: If still unresolved, involve the business analyst, product owner, test lead, or project manager.
6. Update test case or defect: If tester is wrong, correct the test case. If developer is wrong, keep the defect open.
7. Document the decision: Record final decision and reason in the defect repository.

Example: Tester reports that discount is not applied for Rs. 5000 order. Developer says discount applies only above Rs. 5000. The tester checks the requirement, which says "Rs. 5000 and above." Therefore, the defect is valid.

Role clarity and evidence-based communication reduce conflict and improve defect resolution.

---

## 10. Apply the concept of a defect repository and test design process in a real software project and demonstrate how they improve test effectiveness and defect tracking.

A defect repository is a centralized storage system for recording, tracking, analyzing, and managing defects. The test design process converts requirements into test conditions, test cases, test data, and expected results.

Example project: Online banking application.

Defect repository fields:

- Defect ID
- Summary
- Description
- Module
- Steps to reproduce
- Expected result
- Actual result
- Severity
- Priority
- Status
- Assigned developer
- Build version
- Environment
- Attachments
- Root cause
- Closure comments

Test design process:

1. Study requirements.
2. Identify test conditions.
3. Design test cases.
4. Prepare test data.
5. Link test cases to requirements.
6. Execute tests.
7. Log defects in repository.
8. Retest and close defects.

```text
Requirement
    |
    v
Test case
    |
    v
Test execution
    |
    v
Defect repository
    |
    v
Tracking, metrics, retesting, prevention
```

Benefits:

- Improves traceability between requirements, tests, and defects.
- Helps identify defect-prone modules.
- Supports defect metrics such as severity distribution and defect leakage.
- Makes retesting and closure systematic.
- Helps future test design using past defect history.

Thus, a defect repository and good test design improve both defect tracking and test effectiveness.

---

## 11. Given a real software application scenario, classify defects based on their severity levels and justify how severity impacts testing priority and resolution.

Defect severity indicates the impact of a defect on the system. It helps decide how urgently the defect should be fixed.

Example system: Mobile banking application.

| Severity | Meaning | Example | Impact |
|---|---|---|---|
| Critical | System cannot continue or major business loss | Money debited but beneficiary not credited | Must be fixed immediately |
| High | Major feature fails but system partially works | User cannot transfer funds | High priority fix |
| Medium | Feature works incorrectly in some cases | Mini statement shows wrong date format | Fix before release if possible |
| Low | Minor issue with small impact | Typo in help text | Can be fixed later |

Severity affects testing priority because high-severity defects require immediate attention, retesting, and regression testing. Critical defects may block release. Low-severity defects may be deferred if they do not affect core business functions.

Example: If the mobile banking app crashes during fund transfer, it is critical because it affects money and trust. If the profile image is slightly misaligned, it is low severity.

Severity is assigned based on technical and business impact, while priority is assigned based on urgency. A critical severity defect usually has high priority, but priority may also depend on release deadlines and customer needs.

---

## 12. Apply performance testing and recovery testing techniques to a real software system.

Performance testing evaluates how a system behaves under expected workload. Recovery testing checks whether the system can recover after failure.

Example system: Online ticket booking system.

Performance testing application:

1. Identify key operations: login, search trains/events, seat selection, payment, ticket generation.
2. Define workload: number of concurrent users, transactions per minute, expected response time.
3. Execute tests using performance tools.
4. Measure response time, throughput, CPU, memory, database load, and error rate.
5. Identify bottlenecks and retest after tuning.

Example performance test:

| Scenario | Expected outcome |
|---|---|
| 500 users search tickets at same time | Search response should be under 3 seconds |
| 100 users make payment at same time | Payment should complete without duplicate booking |

Recovery testing application:

1. Simulate server crash during booking.
2. Simulate database disconnection.
3. Simulate payment gateway timeout.
4. Restart service and verify data consistency.
5. Check whether incomplete transactions are rolled back or recovered.

```text
Failure occurs
      |
      v
System detects failure
      |
      v
Rollback or recover data
      |
      v
Resume service correctly
```

Performance testing ensures speed and scalability. Recovery testing ensures reliability and data safety after failures.

---

## 13. Given a real-time application, apply load testing and stress testing scenarios and demonstrate how each is performed with suitable examples and expected outcomes.

Load testing and stress testing are types of performance testing. Load testing checks behavior under expected workload, while stress testing checks behavior beyond normal limits.

Example real-time application: Online food delivery system.

Load testing scenario:

- Expected normal peak load: 1000 concurrent users.
- Users browse restaurants, add items to cart, apply coupons, and place orders.
- Measure response time, throughput, error rate, CPU, memory, and database usage.

Expected outcome:

- Restaurant listing loads within 3 seconds.
- Order placement succeeds for normal load.
- Error rate remains within acceptable limit.

Stress testing scenario:

- Increase users beyond expected limit: 1500, 2000, 3000 users.
- Continue increasing load until system slows down or fails.
- Observe how the system fails and recovers.

Expected outcome:

- System should not corrupt orders or payments.
- It should show proper error messages if overloaded.
- It should recover after load is reduced.

```text
Load testing: expected users -> verify stable performance
Stress testing: beyond expected users -> find breaking point
```

Load testing validates readiness for normal business traffic. Stress testing identifies system limits and failure behavior.

---

## 14. Demonstrate Alpha and Beta testing in a real software development scenario and explain how both are conducted before final product release with suitable examples.

Alpha and Beta testing are pre-release testing stages used to collect feedback before final launch.

Alpha testing is performed internally by developers, testers, or internal users in a controlled environment. It is done before releasing the software to external users.

Example: A company develops a hospital management system. Internal testers and hospital domain experts test patient registration, appointment booking, billing, pharmacy, and reports in the company test environment. Defects are fixed before external release.

Beta testing is performed by selected real users in a real or near-real environment. It helps identify usability, compatibility, and real-world defects.

Example: The hospital management system is given to a limited group of doctors, receptionists, and billing staff at one hospital branch. They use it for trial operations and provide feedback.

Comparison:

| Point | Alpha testing | Beta testing |
|---|---|---|
| Performed by | Internal team | Selected external users |
| Environment | Controlled test environment | Real or near-real user environment |
| Timing | Before beta release | Before final release |
| Purpose | Find major defects internally | Collect real user feedback |
| Example defects | Functional defects, crashes | Usability issues, workflow gaps |

```text
Development -> Alpha testing -> Fix defects -> Beta testing -> Final release
```

Both testing stages reduce release risk and improve product quality.

---

## 15. Demonstrate Acceptance and System Testing with example.

System testing tests the complete integrated software system against specified requirements. Acceptance testing checks whether the software satisfies business needs and is acceptable to the customer or end user.

Example system: Library management system.

System testing:

- Test login for librarian and student.
- Test book search.
- Test book issue and return.
- Test fine calculation.
- Test report generation.
- Test performance, security, and compatibility.

System testing is performed by the testing team in a controlled test environment.

Acceptance testing:

- Librarian verifies whether the system supports real library workflow.
- Admin checks whether reports match library rules.
- End users confirm that book issue, return, and fine calculation meet business expectations.

Acceptance testing is usually performed by client, business users, or user representatives.

| Point | System testing | Acceptance testing |
|---|---|---|
| Purpose | Verify complete system against requirements | Validate business acceptance |
| Performed by | Test team | Client/end users |
| Focus | Functional and non-functional correctness | Business needs and user satisfaction |
| Example | Test all library modules | Librarian approves system for deployment |

System testing ensures the software works technically. Acceptance testing ensures the software is useful and acceptable for real business use.

---

## 16. Suppose you are testing a code component and discover a defect: it calculates an output variable incorrectly. A) How would you classify this defect? B) What are the likely causes? C) What steps could have been taken to prevent this defect from propagating to the code?

An incorrect output variable is usually classified as a functional defect or calculation defect. If the incorrect value affects business rules, money, marks, or reports, severity may be high or critical.

A) Classification:

- Defect type: Calculation defect / logic defect.
- Testing level: Usually found in unit testing or system testing.
- Severity: Depends on impact. In banking, wrong interest calculation is critical. In a report label, it may be medium.

B) Likely causes:

- Wrong formula in requirement or code.
- Misunderstanding of business rule.
- Incorrect operator such as `>` instead of `>=`.
- Wrong data type or rounding issue.
- Missing boundary condition.
- Copy-paste error.
- Lack of unit testing.
- Poor code review.

C) Prevention steps:

1. Review requirements and formulas before coding.
2. Create examples with expected outputs.
3. Perform code inspection.
4. Write unit tests for normal, boundary, and invalid values.
5. Use peer review for critical calculations.
6. Trace test cases to requirements.
7. Apply static analysis if possible.

Example: In a student result system, if pass condition is `marks > 40` instead of `marks >= 40`, a student with exactly 40 marks is incorrectly failed. Boundary value test with 40 would prevent this defect from escaping.

---

## 17. Programmer A and Programmer B are working on a group of interfacing modules. Programmer A tends to be a poor communicator and does not get along well with Programmer B. What types of defects are likely to surface in these interfacing modules? What are the likely defect origins?

When programmers working on interfacing modules communicate poorly, integration defects are likely. Interfaces require clear agreement on data format, control flow, error handling, assumptions, and responsibilities.

Likely defect types:

- Interface mismatch: One module sends data in a format another module does not expect.
- Parameter defect: Wrong number, order, or type of parameters.
- Data interpretation defect: One module treats amount as rupees, another as paise.
- Protocol defect: Wrong sequence of calls between modules.
- Error handling defect: One module returns error code, but the other does not handle it.
- Timing defect: One module expects immediate response, another works asynchronously.
- Dependency defect: Module B assumes Module A has already validated data.

Likely origins:

- Poor communication between developers.
- Incomplete interface specification.
- No shared design document.
- No review of module contracts.
- Different assumptions about input and output.
- Lack of integration test cases.
- Personal conflict causing weak collaboration.

Example: In a payment system, Programmer A's cart module sends total amount as a string `"1000"`, but Programmer B's payment module expects numeric value `1000.00`. This can cause integration failure.

Prevention requires interface documentation, design reviews, agreed data contracts, integration testing, and professional communication.

---

## 18. Suppose you are a member of a team designing a defect repository. What information should be associated with each defect? Why is this information useful and who would use it?

A defect repository should store complete and structured information for each defect so that it can be reproduced, assigned, fixed, retested, tracked, and analyzed.

Important defect fields:

| Field | Use | Used by |
|---|---|---|
| Defect ID | Unique identification | Everyone |
| Title / summary | Quick understanding | Testers, developers, managers |
| Description | Detailed explanation | Developers, testers |
| Steps to reproduce | Recreate the defect | Developers, testers |
| Expected result | Defines correct behavior | Testers, developers |
| Actual result | Shows observed failure | Developers |
| Severity | Shows impact | Test lead, manager |
| Priority | Shows urgency | Manager, product owner |
| Module / component | Identifies affected area | Developer, test lead |
| Environment | OS, browser, build, server details | Developer, tester |
| Test data | Inputs used to find defect | Developer, tester |
| Attachments | Screenshots, logs, videos | Developer, support |
| Status | New, assigned, fixed, closed, etc. | Everyone |
| Assigned to | Owner of fix | Developer, manager |
| Root cause | Reason for defect | SQA, team lead |
| Fix version | Build where fix is available | Tester, release manager |
| Closure comments | Final verification details | Tester, auditor |

This information helps testers retest defects, developers debug them, managers track quality, and SQA teams analyze defect trends.

---

## 19. Investigate the defect types commonly found during integration testing and justify their occurrence based on system integration behavior.

Integration testing checks interactions between modules. Defects found here usually occur because modules that work individually may fail when combined.

Common integration defect types:

| Defect type | Example | Reason |
|---|---|---|
| Interface defect | Wrong parameter type passed between modules | Modules have different interface assumptions |
| Data format defect | Date sent as `DD-MM-YYYY`, receiver expects `YYYY-MM-DD` | Inconsistent data contracts |
| Control flow defect | Payment is called before order is created | Wrong sequence of operations |
| Error handling defect | API failure is not handled | One module assumes another always succeeds |
| Database integration defect | Duplicate key or transaction rollback failure | Shared database interaction issue |
| Configuration defect | Wrong endpoint or credentials | Environment setup mismatch |
| Timing defect | Response arrives late and module times out | Asynchronous behavior |
| Dependency defect | Module depends on unavailable service | Missing or unstable dependency |

Example: In an e-commerce system, the cart module may correctly calculate total, and the payment module may work alone. But during integration, payment fails because cart sends amount with currency symbol `"Rs. 500"` while payment expects numeric value `500`.

Integration defects occur because separately tested modules must share data, timing, control, and error responsibilities. Integration testing detects these interaction problems before system testing or production.

---

## 20. In a student management system, illustrate how functions (procedural) and classes (OOP) represent software units during testing.

In unit testing, a software unit is the smallest testable part of the system. In procedural programming, a unit is usually a function or procedure. In object-oriented programming, a unit is usually a class or method.

Student management system in procedural style:

```text
addStudent()
calculateAttendance()
calculateGrade()
generateReport()
```

Each function can be unit tested separately.

Example:

| Function | Unit test |
|---|---|
| `calculateGrade(marks)` | Marks 85 should return Grade A |
| `calculateAttendance(present, total)` | 45/50 should return 90% |
| `validateRollNo(rollNo)` | Blank roll number should be rejected |

Student management system in OOP style:

```text
Class Student
Class AttendanceService
Class ResultService
Class ReportService
```

Each class or method can be treated as a unit.

Example:

| Class / method | Unit test |
|---|---|
| `Student.isEligible()` | Student with required attendance is eligible |
| `ResultService.calculateGrade()` | Marks 40 should return pass grade |
| `ReportService.generateReport()` | Report should include name, roll number, marks |

Thus, unit testing applies to both procedural and OOP systems. The main idea is to isolate the smallest meaningful component and verify its behavior independently.

---

## 21. An air-traffic control system can have one or many users. It interfaces with many hardware devices such as displays, radar detectors, and communications devices. This system can occur in a variety of configurations. Identify how you would carry out configuration tests on this system.

Configuration testing checks whether software works correctly across different hardware, software, network, and user configurations. For an air-traffic control system, this is very important because the system is safety-critical and interacts with many devices.

Configuration test approach:

1. Identify supported configurations:
   - Single-user and multi-user operation.
   - Different radar detectors.
   - Different display units.
   - Communication devices.
   - Backup hardware.
   - Network configurations.

2. Create a configuration matrix:

| Configuration | Users | Radar | Display | Communication | Expected result |
|---|---|---|---|---|---|
| C1 | One | Radar A | Display A | Radio A | Normal operation |
| C2 | Multiple | Radar A | Display B | Radio A | Data shared correctly |
| C3 | Multiple | Radar B | Display A | Radio B | No interface failure |
| C4 | Multiple | Backup radar | Backup display | Radio B | System continues safely |

3. Test hardware interfaces:
   - Radar data input.
   - Display updates.
   - Communication messages.
   - Device failure and reconnect.

4. Test performance under configurations:
   - Multiple users viewing radar data.
   - High traffic data from radar.
   - Communication delays.

5. Test failover and recovery:
   - Radar failure.
   - Display failure.
   - Communication device failure.

Configuration testing ensures that the system works safely and consistently in all supported operational setups.

---

## 22. Identify the types of system tests you would select for the following software: a real-time control system for a new type of laser used for cancer therapy. Some code will control hardware devices. Only qualified technicians can access the system.

A laser therapy control system is safety-critical. Testing must focus on correctness, safety, reliability, security, hardware control, and recovery.

Selected system tests:

| Test type | Objective |
|---|---|
| Functional testing | Verify treatment setup, laser control, dosage calculation, start/stop behavior |
| Safety testing | Ensure unsafe laser output is prevented |
| Performance testing | Verify real-time response within required time limits |
| Recovery testing | Ensure safe recovery after power, hardware, or software failure |
| Security testing | Ensure only qualified technicians can access the system |
| Usability testing | Verify technicians can operate the system without confusion |
| Configuration testing | Check different hardware and device configurations |
| Interface testing | Verify communication between software and laser hardware |
| Regression testing | Ensure changes do not break safety or treatment functions |
| Acceptance testing | Qualified medical/technical users confirm readiness |

Example safety test: If the treatment dose exceeds allowed limit, the system must reject the operation and not activate the laser.

Example recovery test: If power fails during setup, the system should restart in a safe state and not automatically fire the laser.

Because this system affects patient safety, critical defects must block release. Testing should be strict, documented, and reviewed by qualified experts.

---

## 23. Discuss the importance of regression testing when developing a new software release. What items from the previous release would be useful to the regression tester?

Regression testing is important during a new release because changes can unintentionally break existing functionality. A new feature, defect fix, refactoring, database change, or configuration change may affect previously working behavior.

Importance:

- Detects side effects of code changes.
- Protects stable features.
- Reduces production defects.
- Increases release confidence.
- Supports continuous maintenance.

Useful items from previous release:

- Previous test cases and test suites.
- Automation scripts.
- Defect reports and defect history.
- Requirement documents and change requests.
- Traceability matrix.
- Test data.
- User manuals or business workflows.
- Previous release notes.
- Known issues list.
- Test summary reports.
- Production incident reports.

Example: In a banking application, a new release adds UPI transfer. Regression tester should still check login, balance inquiry, fund transfer, transaction history, password reset, and logout from the previous release.

```text
Previous release artifacts
        |
        v
Select regression suite
        |
        v
Run after new changes
        |
        v
Detect broken old features
```

Regression testing ensures that a new release improves the system without damaging existing features.

---

## 24. Design appropriate system testing types for an online fast food restaurant system. For each selected type, specify test objectives, describe the testing approach, and identify the tools required. State any necessary assumptions. *(The system reads customer orders, relays orders to the kitchen, calculates the customer's bill, and gives change. It also maintains inventory information. Each waitperson has a terminal. Only authorized wait-persons and a system administrator can access the system.)*

Assumptions:

- Waitpersons use terminals to enter orders.
- Kitchen receives order details on a kitchen display or printer.
- The system calculates bill and change.
- Inventory is updated after orders.
- Admin manages menu, users, and inventory.

Appropriate system testing types:

| Test type | Objective | Approach | Tools |
|---|---|---|---|
| Functional testing | Verify ordering, billing, change, kitchen relay, inventory update | Execute end-to-end order scenarios | Test cases, defect tracker |
| Security testing | Ensure only authorized users access the system | Test login, roles, admin access, invalid users | Security checklist, browser tools |
| Performance testing | Check response during busy restaurant hours | Simulate many waitpersons entering orders | JMeter or similar load tool |
| Usability testing | Ensure waitpersons can enter orders quickly | Observe users placing common orders | Checklist, feedback form |
| Recovery testing | Check recovery after terminal or network failure | Disconnect terminal during order and verify recovery | Logs, controlled test setup |
| Configuration testing | Check different terminals and printers/displays | Test multiple terminal configurations | Device matrix |
| Regression testing | Ensure changes do not break old functions | Run previous test suite after updates | Automation or regression checklist |

Example functional test:

| Scenario | Expected result |
|---|---|
| Waitperson enters burger and fries order | Order is sent to kitchen, bill is calculated, inventory is reduced |

Example security test:

| Scenario | Expected result |
|---|---|
| Unauthorized user tries admin login | Access denied |

These system tests verify the complete behavior of the restaurant system from order entry to kitchen communication, billing, inventory, and access control.

---

## 25. Using the structure chart below (M1 at root; M2, M3, M4, M5 at level 2; M6, M7 under M2; M8, M9 under M3; M10 under M4; M11 under M5), show the order of module integration for top-down (depth and breadth first) and bottom-up integration approaches. Estimate the number of drivers and stubs needed for each approach.

Structure chart:

```text
                 M1
      +----------+----------+----------+
      |          |          |          |
     M2         M3         M4         M5
   +--+--+    +--+--+      |          |
   |     |    |     |      |          |
  M6    M7   M8    M9    M10        M11
```

Top-down integration starts from root module `M1` and moves downward. Stubs are required for lower modules that are not yet integrated. Drivers are generally not needed because the top module controls execution.

Top-down depth-first order:

```text
M1 -> M2 -> M6 -> M7 -> M3 -> M8 -> M9 -> M4 -> M10 -> M5 -> M11
```

Top-down breadth-first order:

```text
M1 -> M2 -> M3 -> M4 -> M5 -> M6 -> M7 -> M8 -> M9 -> M10 -> M11
```

Stub estimate for top-down:

- Initially, when only `M1` is real, stubs are needed for `M2`, `M3`, `M4`, and `M5`: 4 stubs.
- As lower modules are integrated, stubs are replaced.
- Total stub modules may be up to 10 across the process, but maximum active at the start is 4.
- Drivers needed: 0 or very few.

Bottom-up integration starts from leaf modules and moves upward. Drivers are required to call lower modules before their parent modules are ready. Stubs are generally not needed.

Bottom-up order:

```text
M6, M7 -> M2
M8, M9 -> M3
M10 -> M4
M11 -> M5
M2, M3, M4, M5 -> M1
```

Driver estimate for bottom-up:

- Drivers are needed to test leaf clusters before parents exist.
- Possible drivers: one for each cluster under `M2`, `M3`, `M4`, `M5`, and one final integration driver before `M1`: about 4 to 5 drivers.
- Stubs needed: 0 or very few.

Top-down is useful for early validation of high-level control. Bottom-up is useful for thoroughly testing low-level modules first.

---

## 26. Determine key differences in integrating procedural-oriented systems as compared to object-oriented systems.

Integration in procedural-oriented systems and object-oriented systems differs because their program structures are different.

Procedural systems are organized around functions or procedures. Object-oriented systems are organized around classes, objects, methods, inheritance, and message passing.

| Point | Procedural-oriented integration | Object-oriented integration |
|---|---|---|
| Basic unit | Function or procedure | Class, object, or method |
| Main focus | Function calls and data flow | Object interactions and messages |
| Data handling | Shared data or parameters | Encapsulated object state |
| Integration order | Often based on call hierarchy | Based on class relationships and use cases |
| Defects found | Wrong parameters, wrong call sequence, global data issues | Object state defects, inheritance issues, polymorphism defects |
| Testing support | Drivers and stubs for functions | Drivers, stubs, mocks for objects |
| Complexity | Control flow centered | Interaction and state centered |

Example procedural integration: `calculateBill()` calls `applyDiscount()` and `printBill()`. Testing focuses on correct function calls and returned values.

Example OOP integration: `Order` object interacts with `PaymentService`, `InventoryService`, and `Customer` object. Testing focuses on object state, method calls, and collaboration.

Object-oriented integration must also consider inheritance, overridden methods, constructors, object lifecycle, and dependencies. Procedural integration focuses more on function call structure and data passed between procedures.

---

## 27. Suppose you are testing a code component and you discover a defect: it calculates an output variable incorrectly. A) Classify this defect. B) Identify the likely causes. C) Organize the steps that could have been taken to prevent this defect from propagating to the code.

This defect is an incorrect calculation defect because the output variable does not match the expected result. It is also a functional or logic defect because the component fails to perform its intended function correctly.

A) Classification:

- Defect type: Logic defect / calculation defect.
- Possible origin: Requirement, design, or coding.
- Severity: Depends on impact. Wrong tax, interest, medical dose, or marks calculation may be high or critical.

B) Likely causes:

- Incorrect formula in requirement.
- Developer misunderstood the formula.
- Wrong arithmetic operator.
- Boundary condition missed.
- Incorrect rounding or data type.
- Missing validation.
- No review of calculation logic.
- Weak unit tests.

C) Prevention steps:

```text
Clear requirement
      |
      v
Formula review with examples
      |
      v
Design and code inspection
      |
      v
Unit tests for normal and boundary values
      |
      v
Integration and regression testing
```

Example prevention: For GST calculation, the team should document sample inputs and expected outputs, review the formula, write unit tests for zero amount, normal amount, decimal amount, and boundary values, and perform peer review before integration.

These steps prevent calculation defects from propagating into later testing levels or production.

---

## 28. You are testing a web application and encounter a defect that occurs only when the system is under heavy load. During functional testing, this defect does not appear. What defect type is this and what strategies would you apply to detect such defects earlier?

This is a performance-related defect, load-related defect, or concurrency defect. It appears only when many users or requests use the system at the same time. Functional testing may not reveal it because functional tests usually use limited data and low user load.

Possible causes:

- Database connection pool exhaustion.
- Memory leak.
- Race condition.
- Thread synchronization issue.
- Slow query under high data volume.
- Server resource limit.
- API rate limit.
- Poor caching or inefficient algorithm.

Strategies to detect earlier:

1. Include performance testing early in the test plan.
2. Perform load testing with expected concurrent users.
3. Perform stress testing beyond expected load.
4. Monitor CPU, memory, database, network, and response time.
5. Test with realistic production-like data volume.
6. Use logs and monitoring to identify bottlenecks.
7. Add concurrency tests for shared resources.
8. Include performance checks in regression testing for critical releases.

Example: A ticket booking website works for one user but fails when 1000 users book tickets at the same time. Load testing before release could detect this defect earlier.

---

## 29. Your team observes that many defects originate from code changes in existing functionalities (regression issues). What techniques would you implement to prevent such defects?

Regression issues occur when changes break previously working functionality. To prevent them, the team should improve testing, review, and change control practices.

Techniques:

1. Maintain regression test suite: Keep important old test cases for repeated execution.
2. Automate stable tests: Automate login, payment, order, report, and other critical workflows.
3. Impact analysis: Before changing code, identify affected modules and related test cases.
4. Code review: Review changes for side effects.
5. Unit testing: Developers should update and run unit tests for changed components.
6. Continuous integration: Run tests automatically after every code change.
7. Requirement traceability: Link requirements, code changes, test cases, and defects.
8. Defect analysis: Study repeated regression defects and improve checklists.
9. Version control discipline: Review commits and avoid uncontrolled changes.
10. Smoke testing: Run quick checks after every build.

```text
Code change
    |
    v
Impact analysis
    |
    v
Unit + regression tests
    |
    v
Defect tracking and prevention
```

Example: If a change in coupon logic repeatedly breaks checkout, checkout tests should be added to the automated regression suite and executed after every related change.

---

## 30. During unit testing, coverage reports indicate 100% code coverage, yet multiple defects are still reported during integration testing. What could be the potential causes, and how would you improve your unit testing strategy?

100% code coverage means all statements or branches may have been executed, but it does not guarantee that the tests are strong or that modules work together correctly. Integration defects can still occur.

Potential causes:

- Unit tests have weak assertions.
- Tests execute code but do not verify correct output.
- Interface assumptions between modules are not tested.
- Mock objects behave differently from real dependencies.
- Data format mismatch between modules.
- Error handling paths are not tested properly.
- Boundary and negative cases are missing.
- Code coverage metric measures execution, not correctness.
- Integration contracts are unclear.

Improvements:

1. Strengthen assertions: Check exact expected results, not only whether code runs.
2. Add boundary tests: Include minimum, maximum, and invalid values.
3. Add negative tests: Test failure and exception paths.
4. Use realistic test data.
5. Review mocks and stubs: Ensure they behave like real dependencies.
6. Add contract tests between modules.
7. Include mutation testing to check test strength.
8. Link unit tests to requirements and design assumptions.
9. Add integration tests earlier.

Example: A unit test may cover `sendPayment(amount)` with a mock payment gateway, but integration fails because the real payment gateway expects amount in paise, not rupees. Stronger contract and integration tests would catch this.

---

## 31. Make use of the concept of performance testing and its importance in software systems.

Performance testing evaluates the speed, scalability, stability, and resource usage of a software system under workload. It checks how the system behaves when multiple users, transactions, or large data volumes are present.

Important performance measures:

- Response time.
- Throughput.
- Concurrent users.
- CPU usage.
- Memory usage.
- Database performance.
- Error rate.
- Network usage.

Types related to performance testing:

- Load testing: Tests expected user load.
- Stress testing: Tests beyond expected limits.
- Endurance testing: Tests system for long duration.
- Spike testing: Tests sudden increase in load.

Example: In an online exam system, performance testing checks whether 5000 students can login and submit answers at the same time without timeout or data loss.

Importance:

- Ensures good user experience.
- Finds bottlenecks before release.
- Prevents crashes during peak usage.
- Helps capacity planning.
- Improves reliability and scalability.
- Protects business reputation.

```text
Simulated workload
      |
      v
Measure response and resources
      |
      v
Find bottlenecks
      |
      v
Tune and retest
```

Performance testing is essential for systems where speed, availability, and reliability matter.

---

## 32. Show how defect injection is used in software testing to identify gaps in test coverage.

Defect injection is the intentional insertion of known defects into software or test artifacts to check whether the testing process can detect them. It helps measure the effectiveness of test cases and reviews.

Example: Student result calculation module.

Original rule:

```text
Student passes if marks >= 40
```

Injected defect:

```java
return marks > 40;
```

This defect should be detected by a test case with marks exactly `40`. If the test suite does not fail, it means boundary coverage is missing.

Process:

```text
Select module
      |
      v
Inject known defect
      |
      v
Run existing tests
      |
      v
Check whether tests detect defect
      |
      v
Improve missing tests
```

Examples of injected defects:

- Change `>=` to `>`.
- Remove validation.
- Change formula constant.
- Skip error handling.
- Reverse condition.

Benefits:

- Identifies weak test cases.
- Measures test effectiveness.
- Improves regression suite.
- Supports defect prevention.

Defect injection is related to mutation testing, where small code changes are used to evaluate whether tests can detect faults.

---

## 33. Apply defect prevention techniques in a software development project and demonstrate how they improve software reliability using suitable real-world examples.

Defect prevention means identifying and removing causes of defects before they enter the software or before they reach later stages. It is better than only finding defects after coding.

Defect prevention techniques:

1. Requirement review: Find ambiguous or missing requirements early.
2. Design review: Check architecture, data flow, interfaces, and error handling.
3. Coding standards: Reduce inconsistent and risky coding practices.
4. Code inspection: Find logic errors, missing validation, and poor error handling.
5. Unit testing: Catch defects in small components.
6. Checklists: Use past defect history to prevent repeated mistakes.
7. Root cause analysis: Study why defects occurred.
8. Training: Improve team skills in weak areas.
9. Regression testing: Prevent old defects from reappearing.
10. Defect metrics: Track defect density, leakage, and repeated defect types.

Example 1: In a banking project, many defects occur due to boundary conditions in transaction limits. The team adds a review checklist for minimum and maximum transaction values and writes unit tests for boundary values. Reliability improves because transaction defects reduce.

Example 2: In a hospital system, defects occur due to unclear patient discharge rules. Requirement review with hospital staff clarifies rules before coding, preventing wrong billing and report defects.

```text
Defect data
    |
    v
Root cause analysis
    |
    v
Prevention action
    |
    v
Fewer defects and better reliability
```

Defect prevention improves reliability because the system contains fewer faults and behaves more consistently.

---

## 34. During internal testing, developers find and fix defects in a hospital management system before external release. What type of testing is being conducted? Explain its purpose.

The testing being conducted is Alpha Testing. Alpha testing is performed internally by developers, testers, or internal users before the software is released to external users.

In this scenario, developers are testing a hospital management system inside the organization and fixing defects before external release. This matches alpha testing because it happens before beta testing and final deployment.

Purpose of alpha testing:

- Detect major defects early.
- Check whether core functions work.
- Improve product stability before external users test it.
- Validate workflows in a controlled environment.
- Reduce risk before beta release.

Example hospital management system functions tested:

- Patient registration.
- Doctor appointment scheduling.
- Billing.
- Pharmacy stock update.
- Lab report generation.
- Discharge summary.

```text
Development
    |
    v
Internal alpha testing
    |
    v
Fix major defects
    |
    v
External beta testing or release
```

Alpha testing helps ensure that the system is stable enough before real users or customers evaluate it.

---

## 35. A mobile banking application is released to a limited group of real users outside the organization to collect feedback before final launch. Identify the testing type and explain its significance.

The testing type is Beta Testing. Beta testing is performed by selected real users outside the development organization before final release.

In this scenario, the mobile banking application is given to a limited group of real users to collect feedback. This is beta testing because it happens in a real user environment after internal testing.

Significance of beta testing:

- Collects real user feedback.
- Detects usability issues.
- Finds device, network, and compatibility problems.
- Reveals defects not found in internal testing.
- Builds confidence before final launch.
- Helps improve user experience.

Example issues found during beta testing:

- App crashes on a specific Android version.
- Login works slowly on mobile data.
- Users find fund transfer steps confusing.
- Notification is delayed after transaction.

Beta testing is especially useful for mobile banking because users may have different devices, operating systems, network speeds, and usage patterns.

---

## 36. End users check whether a newly developed library management system satisfies business needs before deployment. What type of testing is being performed? Explain its importance.

The testing being performed is Acceptance Testing. Acceptance testing checks whether the software satisfies business requirements and is acceptable to end users or the client before deployment.

In this scenario, end users are checking whether the library management system meets their business needs. This matches acceptance testing because the focus is not only technical correctness but user approval.

Importance:

- Confirms that the system meets business requirements.
- Gives confidence before deployment.
- Helps users verify real workflows.
- Identifies missing or misunderstood requirements.
- Acts as final approval before release.

Example library acceptance tests:

| Business need | Acceptance test |
|---|---|
| Issue book to student | Librarian issues book and due date is generated |
| Return book | System updates availability |
| Calculate fine | Late return creates correct fine |
| Search book | User finds book by title or author |
| Generate report | Admin gets issued books report |

Acceptance testing is important because a system can pass technical testing but still fail to satisfy real business needs.

---

## 37. Software is tested internally, then by selected users, and finally approved by the client. Identify all testing stages and explain their objectives with examples.

The testing stages are Alpha Testing, Beta Testing, and Acceptance Testing.

1. Alpha Testing:

Alpha testing is performed internally by developers, testers, or internal users before external release.

Objective:

- Find major defects in a controlled environment.
- Improve stability before real users test the product.

Example: Internal team tests a food delivery app for login, restaurant listing, cart, payment, and order tracking.

2. Beta Testing:

Beta testing is performed by selected real users outside the organization before final launch.

Objective:

- Collect real user feedback.
- Detect usability, compatibility, and real-world environment issues.

Example: Selected customers use the food delivery app in their own phones and report issues with payment, notifications, or location.

3. Acceptance Testing:

Acceptance testing is performed by client or end users to decide whether the system satisfies business needs.

Objective:

- Confirm that the software meets agreed requirements.
- Provide final approval before deployment.

Example: The restaurant business owner verifies that order flow, kitchen relay, billing, and reports match business expectations.

```text
Internal testing
      |
      v
Alpha testing
      |
      v
Selected real users
      |
      v
Beta testing
      |
      v
Client approval
      |
      v
Acceptance testing
```

These stages reduce release risk by checking the product internally, then with real users, and finally against business acceptance criteria.
