# Unit 5: Software Quality Assurance Answers

Subject: Software Testing and Quality
Unit: Software Quality Assurance

---

## 1. Select Software Quality Assurance (SQA) and apply its importance in software development.

Software Quality Assurance (SQA) is a planned and systematic set of activities used to ensure that software processes and products meet specified quality requirements. SQA focuses on preventing defects by improving the development process, not only finding defects after coding.

SQA is important because software quality depends on the complete development process, including requirements, design, coding, testing, reviews, configuration management, and maintenance.

Importance of SQA:

- Ensures that standards and procedures are followed.
- Prevents defects early in the software life cycle.
- Improves customer satisfaction.
- Reduces cost of rework and defect fixing.
- Improves reliability, maintainability, and usability.
- Helps teams follow quality models such as CMM, CMMI, TMMi, and ISO 9001.
- Supports continuous quality improvement.
- Provides quality metrics for management decisions.

Example: In a banking application, SQA ensures that requirement reviews, code reviews, security standards, test planning, defect tracking, and release approvals are followed. This reduces the chance of financial calculation errors or transaction failures.

```text
Good process
    |
    v
Fewer defects
    |
    v
Better software quality
    |
    v
Customer satisfaction
```

Thus, SQA is essential because it builds quality into the process instead of depending only on final testing.

---

## 2. Develop the components of a Software Quality Assurance system.

A Software Quality Assurance system is a structured set of activities, standards, tools, roles, and measurements used to ensure software quality. It supports defect prevention, process control, and continuous improvement.

Main components of an SQA system:

| Component | Purpose |
|---|---|
| Standards and procedures | Define how work should be performed |
| Quality planning | Defines quality goals, responsibilities, schedule, and methods |
| Reviews and audits | Check requirements, design, code, test cases, and processes |
| Testing process | Verifies and validates software behavior |
| Defect management | Records, tracks, retests, and closes defects |
| Configuration management | Controls versions of code, documents, and builds |
| Metrics and measurement | Measures quality using defect density, coverage, leakage, and effort |
| Training | Improves team skill and process awareness |
| Tools and automation | Supports testing, tracking, reporting, and development |
| Process improvement | Uses lessons learned and metrics to improve future work |

SQA system flow:

```text
Quality plan
     |
     v
Standards, reviews, testing, audits
     |
     v
Metrics and defect analysis
     |
     v
Corrective and preventive actions
     |
     v
Improved software process
```

Example: In an e-commerce project, the SQA system includes coding standards, review checklists, automated regression tests, defect repository, release criteria, and quality reports. Together, these components help maintain quality throughout development.

---

## 3. Select and apply Quality Assurance (QA) and Quality Control (QC).

Quality Assurance (QA) and Quality Control (QC) are both related to software quality, but they focus on different aspects.

QA is process-oriented. It ensures that correct processes are followed to prevent defects. QC is product-oriented. It checks the actual software product to detect defects.

| Point | QA | QC |
|---|---|---|
| Focus | Process quality | Product quality |
| Goal | Prevent defects | Detect defects |
| Nature | Proactive | Reactive |
| Activities | Process definition, audits, standards, reviews | Testing, inspection, defect reporting |
| Responsibility | SQA team, managers, process owners | Testers, reviewers, developers |
| Example | Define coding standards | Test login functionality |

Application in a project:

- QA defines requirement review process, coding standards, test strategy, and release criteria.
- QC executes test cases, reports defects, verifies fixes, and checks whether the product meets requirements.

Example: In a food delivery application, QA ensures that every requirement is reviewed and every build follows the release checklist. QC tests actual features such as restaurant search, cart, payment, and order tracking.

```text
QA: Build the process correctly
QC: Check the product correctly
```

Both QA and QC are necessary. QA reduces the number of defects entering the product, while QC detects defects that still remain.

---

## 4. Choose ISO 9001 and its role in software quality management.

ISO 9001 is an international standard for quality management systems. It provides a framework for organizations to consistently deliver products and services that meet customer and regulatory requirements.

In software quality management, ISO 9001 does not prescribe a specific programming or testing method. Instead, it ensures that the organization follows controlled, documented, measurable, and continuously improving processes.

Role of ISO 9001:

- Defines quality management responsibilities.
- Requires documented processes.
- Promotes customer focus.
- Ensures process control and consistency.
- Supports risk-based thinking.
- Requires measurement and monitoring.
- Encourages corrective and preventive actions.
- Supports continuous improvement.

Application in software:

| ISO 9001 concept | Software example |
|---|---|
| Documented process | Defined SDLC, testing, and release process |
| Customer focus | Requirements are reviewed and validated |
| Process monitoring | Defect metrics and test reports are tracked |
| Corrective action | Root cause analysis after production defects |
| Continuous improvement | Process updated based on lessons learned |

Example: A fintech company applying ISO 9001 ensures that requirements, design, code, testing, release approvals, and defect records are properly controlled before deployment.

ISO 9001 improves software quality by making processes repeatable, auditable, and improvement-oriented.

---

## 5. Construct and explain Software Quality Assurance models such as CMM and CMMI.

Software Quality Assurance models provide structured approaches for improving software processes. CMM and CMMI are widely used process maturity models.

CMM stands for Capability Maturity Model. It describes maturity levels of software development processes. The goal is to move from an ad hoc process to a controlled and continuously improving process.

CMM maturity levels:

| Level | Name | Meaning |
|---|---|---|
| 1 | Initial | Processes are informal and unpredictable |
| 2 | Repeatable | Basic project management practices exist |
| 3 | Defined | Organization-wide standard processes are defined |
| 4 | Managed | Processes are measured and controlled |
| 5 | Optimizing | Continuous process improvement is practiced |

CMMI stands for Capability Maturity Model Integration. It is an improved and integrated model that covers software, systems, services, and process improvement. It provides best practices for process areas such as project planning, requirements management, verification, validation, measurement, and process improvement.

```text
Initial -> Managed/Repeatable -> Defined -> Quantitatively Managed -> Optimizing
```

Example: A company with repeated production defects may be at a low maturity level because it lacks standard reviews, metrics, and defect prevention. By adopting CMMI, it can introduce requirement management, process measurement, verification, validation, and root cause analysis.

CMM and CMMI improve quality by making processes predictable, measurable, and continuously improving.

---

## 6. Apply Six Sigma approach in improving software quality.

Six Sigma is a quality improvement methodology that aims to reduce defects and process variation. In software, Six Sigma can be used to reduce defect rate, improve process capability, and increase customer satisfaction.

The common Six Sigma method is DMAIC:

| Phase | Meaning | Software application |
|---|---|---|
| Define | Define problem and customer needs | High defect leakage in payment module |
| Measure | Measure current performance | Count defects, failure rate, rework effort |
| Analyze | Find root causes | Use Pareto chart, fishbone diagram, defect analysis |
| Improve | Implement solutions | Add reviews, automation, better test data |
| Control | Maintain improvement | Monitor metrics and control charts |

Example: A banking application has frequent transaction defects. The team applies Six Sigma:

1. Define: Transaction defects are causing customer complaints.
2. Measure: 40% defects are from incorrect validation.
3. Analyze: Root cause is unclear requirements and weak boundary testing.
4. Improve: Add requirement reviews, validation checklist, and automated boundary tests.
5. Control: Track defect density and defect leakage every release.

```text
Define -> Measure -> Analyze -> Improve -> Control
```

Six Sigma improves software quality by using data-based decisions instead of assumptions. It is useful for reducing recurring defects and improving process stability.

---

## 7. Apply Continuous Quality Improvement (CQI) and its importance in software engineering.

Continuous Quality Improvement (CQI) is an ongoing effort to improve software processes, products, and services. It is based on the idea that quality can always be improved through measurement, feedback, and corrective action.

CQI in software engineering involves:

- Collecting defect and process data.
- Identifying repeated problems.
- Finding root causes.
- Improving process steps.
- Monitoring results.
- Repeating the improvement cycle.

Common CQI cycle:

```text
Plan -> Do -> Check -> Act
```

Application example: An e-commerce team observes that checkout defects occur in every release.

1. Plan: Decide to improve checkout testing.
2. Do: Add automated regression tests and review payment requirements.
3. Check: Measure reduction in checkout defects.
4. Act: Make the new process standard if it works.

Importance of CQI:

- Reduces repeated defects.
- Improves process maturity.
- Supports Agile and DevOps practices.
- Increases customer satisfaction.
- Improves productivity.
- Helps teams learn from mistakes.
- Supports long-term software reliability.

CQI is important because software development changes continuously. Without continuous improvement, the same defects and process weaknesses repeat across projects.

---

## 8. Apply Ishikawa's seven quality tools and their use in defect analysis.

Ishikawa's seven quality tools are basic tools used to analyze quality problems, identify root causes, and improve processes. They are useful in software defect analysis.

The seven quality tools are:

| Tool | Use in defect analysis |
|---|---|
| Cause-and-effect diagram / Fishbone diagram | Identifies root causes of defects |
| Check sheet | Collects defect data systematically |
| Pareto chart | Identifies major causes contributing most defects |
| Histogram | Shows distribution of data such as response time or defect count |
| Control chart | Checks whether process is stable over time |
| Scatter diagram | Shows relationship between two variables |
| Flow chart | Shows process steps and identifies weak points |

Example: A banking application has repeated login defects. The team uses:

- Check sheet to count login defect types.
- Pareto chart to find that 70% defects come from password reset.
- Fishbone diagram to identify causes such as unclear requirements, weak testing, and API failures.
- Control chart to monitor whether login defects reduce over future releases.

```text
Defect data
    |
    v
Quality tools
    |
    v
Root cause and priority
    |
    v
Corrective action
```

These tools help teams move from guessing to data-based defect analysis.

---

## 9. Make use of the role of CASE tools in improving software quality.

CASE stands for Computer-Aided Software Engineering. CASE tools support software development and testing activities using automation. They improve quality by reducing manual errors, improving consistency, and supporting traceability.

Role of CASE tools:

- Requirement management.
- Design modeling.
- Code generation.
- Test case management.
- Defect tracking.
- Configuration management.
- Documentation generation.
- Static analysis.
- Version control.
- Project monitoring.

Examples:

| CASE tool area | Quality improvement |
|---|---|
| Requirement tool | Maintains requirement traceability |
| Modeling tool | Improves design clarity |
| Static analysis tool | Finds coding defects early |
| Test management tool | Tracks test cases and coverage |
| Defect tracking tool | Manages defect life cycle |
| Version control tool | Prevents uncontrolled code changes |

Example: In an e-commerce project, a test management CASE tool links requirements to test cases and defects. This helps ensure that every requirement is tested and every defect is tracked to closure.

CASE tools do not guarantee quality by themselves. They improve quality when used with proper processes, trained people, and review practices.

---

## 10. A software company faces repeated defects even after multiple testing cycles. Which SQA model (CMM/CMMI/TMMi) can help improve the process? Justify your answer.

If a company faces repeated defects even after multiple testing cycles, CMMI or TMMi can help improve the process. The best choice depends on whether the weakness is in the overall software process or mainly in the testing process.

CMMI improves the complete software development process, including requirements, design, coding, project management, verification, validation, measurement, and process improvement. TMMi focuses specifically on improving testing maturity.

Recommended approach:

- Use CMMI if repeated defects originate from unclear requirements, poor design, weak project planning, coding issues, and lack of process control.
- Use TMMi if the main problem is weak test planning, poor test design, incomplete regression testing, and lack of test metrics.

Justification:

| Problem | Suitable model |
|---|---|
| Defects due to poor requirements and design | CMMI |
| Defects due to poor test process | TMMi |
| Organization-wide process weakness | CMMI |
| Testing maturity weakness | TMMi |

Example: If production defects occur because requirements are unclear and code reviews are missing, CMMI is more suitable. If defects occur because test cases are weak and regression testing is not systematic, TMMi is more suitable.

Thus, CMMI can improve the overall process, while TMMi can specifically strengthen testing activities.

---

## 11. A team is struggling with identifying root causes of defects in a banking application. How can Ishikawa's quality tools be applied in this scenario?

Ishikawa's quality tools can help the team analyze banking defects systematically and identify root causes using data.

Scenario: A banking application has repeated transaction failures.

Application of seven quality tools:

| Tool | Application |
|---|---|
| Check sheet | Record defect type, module, severity, date, and cause |
| Pareto chart | Identify which defect category contributes most failures |
| Fishbone diagram | Analyze root causes under categories such as people, process, tools, requirements, environment |
| Flow chart | Map transaction process and locate weak steps |
| Histogram | Analyze distribution of response time or transaction failures |
| Control chart | Monitor defect rate across releases |
| Scatter diagram | Check relationship between transaction volume and failures |

Fishbone example:

```text
                 Transaction defects
People -------- unclear ownership
Process ------- weak reviews
Requirements -- unclear validation rules
Tools --------- poor monitoring
Environment --- unstable test server
Data ---------- incorrect test accounts
```

Example result: Pareto chart may show that 60% of banking defects are from fund transfer validation. The team can then focus improvement efforts on requirement clarification, boundary tests, and validation automation.

Quality tools help the team identify root causes instead of only fixing symptoms.

---

## 12. In an Agile project, frequent requirement changes are affecting product quality. How can SQA practices help manage this situation?

In Agile projects, requirement changes are common. SQA practices help manage changes without losing product quality by introducing discipline, traceability, reviews, and continuous testing.

SQA practices:

1. Requirement review: Review user stories and acceptance criteria before development.
2. Change impact analysis: Identify which modules, tests, and risks are affected by a change.
3. Definition of Done: Include testing, review, and documentation criteria.
4. Traceability: Link user stories to test cases and defects.
5. Continuous testing: Run automated unit, API, and regression tests in every sprint.
6. Regression testing: Ensure changes do not break existing features.
7. Defect tracking: Record defects and analyze repeated issues.
8. Metrics: Track defect leakage, escaped defects, story rejection rate, and test coverage.
9. Retrospective improvement: Use sprint retrospectives to improve quality practices.

Example: If a payment requirement changes in an Agile e-commerce project, SQA ensures that cart, coupon, checkout, payment, and invoice test cases are updated and regression tests are executed.

```text
Requirement change
      |
      v
Impact analysis
      |
      v
Update tests and acceptance criteria
      |
      v
Continuous testing
      |
      v
Quality feedback
```

SQA does not stop requirement changes. It controls their quality impact.

---

## 13. A project uses CASE tools for development and testing. How do these tools improve software quality in real-time development?

CASE tools improve software quality in real-time development by supporting automation, consistency, traceability, and faster feedback.

Examples of CASE tools in development and testing:

| CASE tool type | Quality benefit |
|---|---|
| Requirement management tool | Maintains clear and traceable requirements |
| Design modeling tool | Helps visualize architecture and interfaces |
| Code editor/static analyzer | Detects coding defects early |
| Version control tool | Tracks code changes and supports rollback |
| Test management tool | Organizes test cases and coverage |
| Automation tool | Runs regression tests quickly |
| Defect tracking tool | Tracks defects from reporting to closure |
| CI/CD tool | Builds and tests software automatically |

Real-time example: In a food delivery project, developers commit code to version control. CI tools build the application and run automated tests. Defects are logged in a defect tracking tool. Test management tools show which requirements are covered.

Benefits:

- Reduces manual errors.
- Improves communication between teams.
- Provides faster test feedback.
- Supports continuous integration.
- Improves documentation and traceability.
- Helps managers monitor quality.

CASE tools improve quality when integrated with a disciplined SQA process.

---

## 14. A company wants to reduce defect rate to near-zero using Six Sigma. How can this methodology be applied in software testing?

Six Sigma can be applied in software testing to reduce defect rate by using measurement, root cause analysis, process improvement, and control.

Use DMAIC:

1. Define: Define the quality problem. Example: Too many production defects in login and payment modules.
2. Measure: Collect data such as defect count, defect density, severity, leakage, and test coverage.
3. Analyze: Identify root causes using Pareto chart, fishbone diagram, and defect trend analysis.
4. Improve: Improve test design, automation, reviews, test data, and regression coverage.
5. Control: Monitor defect rates and ensure improvements continue.

Example: A company finds that most defects are caused by missed boundary values. It improves testing by adding boundary value test cases, review checklists, and automation scripts.

Six Sigma metrics:

- Defects per module.
- Defects per thousand lines of code.
- Defect leakage percentage.
- Test case failure rate.
- Rework effort.

```text
Defect data
    |
    v
Analyze root cause
    |
    v
Improve testing process
    |
    v
Monitor with metrics
```

Six Sigma does not mean no defects instantly. It creates a disciplined, data-driven method to reduce defects continuously.

---

## 15. In a healthcare application, errors in data processing can lead to critical failures. How can SQA models ensure reliability in such real-time systems?

Healthcare applications are safety-critical because errors in patient data, diagnosis, dosage, reports, or billing can cause serious harm. SQA models help ensure reliability by enforcing disciplined processes, reviews, testing, measurement, and continuous improvement.

Applicable SQA models:

- CMMI for improving overall development process maturity.
- TMMi for improving testing process maturity.
- ISO 9001 for quality management and documented processes.
- Six Sigma for reducing defects and variation.

Application:

1. Requirement management: Clearly define patient data rules, report formats, access control, and safety constraints.
2. Verification and validation: Review requirements, design, and code; test actual system behavior.
3. Testing maturity: Use TMMi practices for planned, measured, and controlled testing.
4. Defect tracking: Maintain complete defect repository and root cause analysis.
5. Metrics: Track defect leakage, severity, reliability, and response time.
6. Continuous improvement: Improve process using defect trends.

Example: If a lab report system sometimes maps results to the wrong patient, SQA models require root cause analysis, process correction, review of data mapping design, regression testing, and preventive controls.

SQA models improve reliability by making quality activities systematic instead of informal.

---

## 16. A fintech application must comply with ISO 9001 standards before deployment. How does this standard ensure software quality in real-world usage?

ISO 9001 ensures software quality by requiring a controlled quality management system. For a fintech application, this is important because the software handles financial transactions, customer data, compliance, and security-sensitive operations.

How ISO 9001 supports quality:

- Requires documented development and testing processes.
- Ensures customer and regulatory requirements are understood.
- Promotes risk-based thinking.
- Requires process monitoring and measurement.
- Requires corrective action for defects and failures.
- Encourages continuous improvement.
- Ensures responsibility and accountability.
- Supports auditability.

Application to fintech:

| ISO 9001 practice | Fintech example |
|---|---|
| Requirement control | Transaction rules and compliance needs are documented |
| Process control | Coding, review, testing, and release steps are followed |
| Measurement | Defect rate, test coverage, and incident trends are monitored |
| Corrective action | Payment failure root causes are analyzed and fixed |
| Customer focus | User complaints and feedback are considered |

Example: Before deployment, the fintech company verifies that fund transfer, KYC, transaction history, and error handling requirements are reviewed, tested, documented, and approved.

ISO 9001 ensures real-world quality by making processes consistent, traceable, and auditable.

---

## 17. In a large-scale e-commerce platform, continuous integration is used. How does Continuous Quality Improvement help maintain software quality in real-time deployment?

Continuous Quality Improvement (CQI) helps maintain software quality in real-time deployment by continuously measuring, analyzing, and improving the development and testing process.

In a large e-commerce platform, continuous integration means code changes are frequently built and tested. CQI ensures that the process improves based on feedback from builds, tests, defects, and production monitoring.

CQI application:

1. Collect data from CI builds, automated tests, defects, and production logs.
2. Identify repeated failures such as checkout defects or payment timeouts.
3. Analyze root causes using quality tools.
4. Improve process by adding tests, improving reviews, or fixing deployment issues.
5. Monitor whether defect rate reduces in later releases.

```text
CI feedback
    |
    v
Quality metrics
    |
    v
Root cause analysis
    |
    v
Process improvement
    |
    v
Better releases
```

Example: If CI frequently fails due to cart module defects, the team adds better unit tests, API tests, code reviews, and regression tests for cart behavior.

CQI is important in real-time deployment because frequent releases need fast feedback and continuous process correction.

---

## 18. Choose and apply Software Quality Assurance models used in industry.

Industry uses different SQA models depending on quality goals, process maturity, domain, and testing needs.

Important SQA models:

| Model | Purpose | Application |
|---|---|---|
| CMM | Measures software process maturity | Improve organization process level |
| CMMI | Integrated process improvement model | Improve development, management, verification, validation |
| TMMi | Test process maturity model | Improve test planning, test design, metrics, automation |
| ISO 9001 | Quality management standard | Ensure documented, controlled, auditable quality process |
| Six Sigma | Defect and variation reduction | Reduce high defect rate using DMAIC |
| CQI | Continuous improvement | Improve quality based on ongoing feedback |

Application example: A banking company can use ISO 9001 for quality management, CMMI for process maturity, TMMi for testing maturity, and Six Sigma for reducing transaction defects.

Selection:

- Use CMMI for overall process improvement.
- Use TMMi when testing process is weak.
- Use ISO 9001 for standardization and audit compliance.
- Use Six Sigma when defect reduction requires data-driven improvement.
- Use CQI for ongoing improvement in Agile/DevOps environments.

These models improve quality by making processes defined, measured, controlled, and continuously improved.

---

## 19. Apply Software Quality Assurance (SQA) on any application.

Consider applying SQA to an online food delivery application.

SQA activities:

1. Requirement quality: Review requirements for restaurant search, cart, coupon, payment, order tracking, and cancellation.
2. Quality plan: Define quality goals, test strategy, standards, roles, and exit criteria.
3. Design review: Check architecture for UI, backend, payment gateway, map service, and database.
4. Coding standards: Ensure consistent, readable, and maintainable code.
5. Testing process: Perform unit, integration, system, regression, performance, and acceptance testing.
6. Defect management: Record defects with severity, priority, steps, screenshots, and status.
7. Metrics: Track defect density, test coverage, defect leakage, and test execution status.
8. Configuration management: Control versions of builds, code, and test data.
9. Release audit: Verify that release checklist and exit criteria are satisfied.
10. Continuous improvement: Analyze repeated defects and improve process.

```text
Requirements -> Reviews -> Testing -> Metrics -> Improvement
```

Example: If wrong delivery charges are repeatedly found, SQA performs root cause analysis. The solution may include clearer requirements, boundary tests, code review checklist, and automated regression tests.

SQA ensures that the application is built using a controlled and quality-focused process.

---

## 20. Make use of components of a Software Quality Assurance system.

The components of an SQA system can be used in a software project to control quality from planning to release.

Example project: Library management system.

Use of SQA components:

| SQA component | Use in project |
|---|---|
| Quality plan | Defines quality goals, test scope, schedule, and responsibilities |
| Standards | Defines coding, documentation, and testing standards |
| Reviews | Reviews requirements, design, code, and test cases |
| Testing | Verifies book issue, return, fine calculation, and reports |
| Defect management | Tracks defects from new to closed |
| Metrics | Measures defects, test coverage, and progress |
| Configuration management | Controls versions of code, database scripts, and documents |
| Audits | Checks whether the team follows the defined process |
| Training | Improves team knowledge of tools and quality practices |
| Process improvement | Uses defect data to improve future releases |

Example: If fine calculation defects are found repeatedly, the SQA system uses defect reports and metrics to identify the root cause. Then it improves the review checklist and adds automated tests.

Using SQA components ensures that quality is not dependent only on final testing. It becomes part of the complete development process.

---

## 21. Make use of Ishikawa's seven quality tools used in software quality analysis.

Ishikawa's seven quality tools are used to collect, analyze, and improve quality data in software projects.

The seven tools and their use:

| Tool | Software quality use |
|---|---|
| Check sheet | Collect defect counts by module or type |
| Pareto chart | Identify top defect causes |
| Fishbone diagram | Find root causes of quality problems |
| Histogram | Show distribution of response times or defect counts |
| Control chart | Monitor process stability over time |
| Scatter diagram | Study relationship between effort and defects |
| Flow chart | Understand and improve process steps |

Example: A project has many production defects.

1. Use check sheet to collect defect data.
2. Use Pareto chart to find that 80% defects come from 20% modules.
3. Use fishbone diagram to identify causes such as unclear requirements, poor reviews, weak testing, and unstable environment.
4. Use control chart to check if defect rate is improving over releases.

```text
Collect data -> Analyze pattern -> Find root cause -> Improve process
```

These tools help teams make quality decisions based on evidence instead of assumptions.

---

## 22. Summarize Quality Assurance and Quality Control differences in software projects.

Quality Assurance and Quality Control are both required in software projects, but they differ in focus.

Quality Assurance is process-oriented and aims to prevent defects. Quality Control is product-oriented and aims to detect defects.

| Point | Quality Assurance | Quality Control |
|---|---|---|
| Focus | Process | Product |
| Goal | Prevent defects | Find defects |
| Timing | Throughout development | During product evaluation/testing |
| Nature | Proactive | Reactive |
| Activities | Standards, audits, process improvement, reviews | Testing, inspection, defect reporting |
| Output | Improved process | Defect reports and product quality status |
| Example | Define test process | Execute test cases |

Example: In an online exam system, QA ensures that requirements are reviewed, coding standards are followed, and test plans are prepared. QC tests login, exam timer, question display, answer submission, and result calculation.

Both are complementary:

```text
QA prevents defects
QC detects remaining defects
```

A good software project needs both QA and QC to deliver reliable software.

---

## 23. Apply Software Quality Assurance and its role in software development.

SQA plays a major role in software development by ensuring that processes are defined, followed, measured, and improved.

Role of SQA:

- Define quality standards.
- Prepare quality plans.
- Review requirements and design.
- Ensure coding and documentation standards.
- Monitor testing activities.
- Audit process compliance.
- Track quality metrics.
- Analyze defects and root causes.
- Support process improvement.
- Ensure release readiness.

Application example: Student management system.

SQA ensures that admission, attendance, marks, result, and report requirements are reviewed. It checks that developers follow coding standards, testers prepare test cases, defects are tracked properly, and release criteria are satisfied before deployment.

SQA flow:

```text
Plan quality
    |
    v
Define standards
    |
    v
Monitor development and testing
    |
    v
Analyze defects
    |
    v
Improve process
```

SQA helps the development team produce software that is reliable, maintainable, and aligned with user expectations.

---

## 24. Plan TMMi model contribution in improving testing maturity.

TMMi stands for Test Maturity Model integration. It is a model used to assess and improve the maturity of testing processes in an organization.

TMMi maturity levels:

| Level | Name | Meaning |
|---|---|---|
| 1 | Initial | Testing is informal and unpredictable |
| 2 | Managed | Test planning, monitoring, and basic control exist |
| 3 | Defined | Organization-wide test process is defined |
| 4 | Measured | Testing is measured using metrics |
| 5 | Optimization | Continuous test process improvement is performed |

Contribution of TMMi:

- Improves test planning.
- Defines testing roles and responsibilities.
- Introduces test design techniques.
- Improves defect tracking.
- Uses test metrics for decision making.
- Supports test automation.
- Reduces defect leakage.
- Improves regression testing.
- Promotes continuous improvement.

Example: A company where testers execute cases without planning may be at TMMi Level 1. By adopting Level 2 practices, it introduces test plans, test monitoring, defect tracking, and controlled execution. Higher levels add standard processes, metrics, and optimization.

TMMi improves testing maturity by moving testing from an ad hoc activity to a managed and continuously improving process.

---

## 25. Identify the role of CASE tools in improving software quality.

CASE tools improve software quality by supporting automation and discipline in development, testing, documentation, and maintenance.

Roles of CASE tools:

- Support requirement traceability.
- Create design diagrams and models.
- Generate code or templates.
- Detect coding issues using static analysis.
- Manage test cases.
- Track defects.
- Control versions.
- Automate builds and tests.
- Generate reports.

Example:

| CASE tool | Quality role |
|---|---|
| Requirement management tool | Prevents missed requirements |
| UML modeling tool | Improves design understanding |
| Static analysis tool | Finds code quality issues |
| Test management tool | Tracks test coverage |
| Defect tracking tool | Ensures defects are fixed and closed |
| Version control tool | Maintains change history |

In a large e-commerce application, CASE tools help connect requirements to test cases and defects. This improves traceability and helps ensure every business rule is tested.

CASE tools improve quality most effectively when combined with proper SQA practices.

---

## 26. Apply a software project where repeated defects are found after release and categorize the possible gaps in the SQA process using CMM/CMMI model.

Repeated defects after release indicate weak process maturity. CMM/CMMI can be used to categorize gaps and improve the software process.

Example: A mobile banking application has repeated production defects in login, fund transfer, and transaction history.

Possible SQA gaps using CMM/CMMI:

| Gap | CMM/CMMI area affected | Explanation |
|---|---|---|
| Requirements are unclear | Requirements management | Business rules are not controlled |
| No formal reviews | Verification | Requirement, design, and code defects escape |
| Weak testing process | Validation | Test cases do not cover important scenarios |
| No metrics | Measurement and analysis | Team cannot identify repeated defect patterns |
| Poor change control | Configuration management | Fixes introduce new defects |
| No root cause analysis | Process improvement | Same defects repeat |
| Informal project planning | Project planning | Testing time and resources are insufficient |

Maturity interpretation:

- If processes are ad hoc and defect fixing is reactive, the organization may be near CMM Level 1.
- To improve, it should adopt managed practices such as planning, tracking, configuration control, reviews, and metrics.

Improvement steps:

```text
Identify gaps -> Define process -> Measure quality -> Analyze root causes -> Improve
```

CMMI helps convert repeated production defects into structured process improvement actions.

---

## 27. Apply differentiation between ISO 9001 compliance and Six Sigma approach in improving software quality for a real-time banking application.

ISO 9001 and Six Sigma both improve quality, but their focus is different. ISO 9001 focuses on a quality management system, while Six Sigma focuses on reducing defects and variation using data.

Comparison:

| Point | ISO 9001 | Six Sigma |
|---|---|---|
| Focus | Quality management process | Defect reduction and process variation |
| Nature | Standard compliance | Improvement methodology |
| Main concern | Are processes defined and followed? | Are defects reduced statistically? |
| Method | Documentation, audits, corrective action | DMAIC: Define, Measure, Analyze, Improve, Control |
| Output | Certified quality management system | Reduced defects and improved process capability |
| Example | Banking release process is documented and audited | Transaction failure rate is reduced |

Application to banking:

- ISO 9001 ensures that banking requirements, testing, approvals, release, and defect handling follow documented processes.
- Six Sigma analyzes defects such as failed transfers, wrong balance updates, and payment delays to reduce their frequency.

Example: If fund transfer defects occur, ISO 9001 checks whether process steps were followed. Six Sigma measures defect data, finds root cause, improves the process, and monitors whether defects reduce.

Both can be used together: ISO 9001 provides process discipline, while Six Sigma provides data-driven improvement.

---

## 28. Examine a scenario where a healthcare system shows frequent failures due to poor requirement handling and identify appropriate SQA improvements.

Poor requirement handling causes serious defects in healthcare systems because patient data, diagnosis, reports, dosage, and billing must be accurate.

Scenario: A hospital system frequently fails because patient discharge rules are unclear. Sometimes wrong bills are generated and lab reports are not linked correctly.

Likely causes:

- Ambiguous requirements.
- Missing acceptance criteria.
- No requirement review with doctors and hospital staff.
- Poor traceability from requirements to test cases.
- Frequent uncontrolled changes.
- Weak validation testing.

SQA improvements:

1. Requirement review: Involve doctors, billing staff, lab staff, and testers.
2. Requirement traceability matrix: Link each requirement to design, code, and test cases.
3. Acceptance criteria: Define measurable expected behavior.
4. Change control: Approve and document requirement changes.
5. Prototyping: Validate workflows with users before coding.
6. Risk-based testing: Give high priority to patient safety and billing rules.
7. Defect root cause analysis: Study repeated failures and update process.
8. Compliance audits: Ensure process is followed.

```text
Poor requirements
      |
      v
Review, traceability, change control
      |
      v
Better tests and fewer failures
```

These SQA improvements reduce requirement-related defects and improve healthcare system reliability.

---

## 29. Criticize the effectiveness of CASE tools in reducing defects in a large-scale e-commerce application and justify your view.

CASE tools are effective in reducing defects, but they are not a complete solution by themselves. Their effectiveness depends on how well they are selected, integrated, and used by the team.

How CASE tools reduce defects:

- Requirement tools reduce missed or unclear requirements.
- Modeling tools improve design understanding.
- Static analysis tools detect coding issues early.
- Test management tools improve test coverage.
- Automation tools catch regression defects.
- Defect tracking tools ensure defects are not forgotten.
- CI tools give fast feedback after code changes.

Example: In a large e-commerce platform, automated regression tools can quickly test login, cart, coupon, checkout, and payment after every change. This reduces repeated manual effort and catches defects early.

Limitations:

- Tools cannot fix poor requirements automatically.
- Tools need skilled users.
- Automation scripts require maintenance.
- Incorrect tool configuration can create false confidence.
- Tools may not detect usability or business logic issues.
- High cost and training may be required.

Justified view: CASE tools are valuable and can significantly reduce defects, but only when supported by strong SQA processes, reviews, skilled people, and continuous improvement.

Thus, CASE tools support quality; they do not replace engineering judgment.

---

## 30. Apply a software development organization using TMMi model and determine its current maturity level based on given quality issues.

TMMi can be used to assess the maturity of an organization's testing process based on observed quality issues.

Scenario: A software organization has the following issues:

- Test planning is informal.
- Test cases are created late.
- Defects are tracked inconsistently.
- Regression testing is incomplete.
- No test metrics are collected.
- Testing depends on individual tester experience.

TMMi assessment:

These issues show that testing is mostly ad hoc and not well controlled. The organization is likely at TMMi Level 1: Initial.

Reason:

| Issue | TMMi interpretation |
|---|---|
| Informal testing | Level 1 behavior |
| No metrics | Not Level 4 |
| No standard process | Not Level 3 |
| Weak planning and tracking | Not fully Level 2 |
| Individual-dependent testing | Low maturity |

Improvement plan:

1. Move toward Level 2 by introducing test planning, monitoring, test design, and defect tracking.
2. Define organization-wide test process for Level 3.
3. Collect test metrics for Level 4.
4. Use continuous improvement and defect prevention for Level 5.

```text
Initial testing -> Managed testing -> Defined testing -> Measured testing -> Optimized testing
```

TMMi helps the organization understand its current level and plan realistic improvements.

---

## 31. Prioritize quality improvement actions for a fintech application facing high defect leakage using Continuous Quality Improvement (CQI) approach.

Defect leakage means defects escape from testing and reach production or later stages. For a fintech application, high defect leakage is serious because it may affect money, security, and customer trust.

CQI approach:

1. Collect data: Gather production defects, test defects, modules affected, severity, root causes, and release history.
2. Analyze leakage: Identify where defects escaped and why.
3. Prioritize actions based on risk and impact.
4. Implement improvements.
5. Monitor results in future releases.

Prioritized actions:

| Priority | Improvement action | Reason |
|---|---|---|
| 1 | Strengthen requirement reviews | Many fintech defects come from unclear rules |
| 2 | Add risk-based test planning | Critical payment and transaction modules need focus |
| 3 | Improve regression automation | Frequent releases need fast repeatable testing |
| 4 | Add code reviews and static analysis | Prevent coding defects early |
| 5 | Improve test data | Financial edge cases need realistic data |
| 6 | Analyze root causes | Prevent repeated leakage |
| 7 | Track metrics | Monitor defect leakage trend |
| 8 | Improve release gate | Stop release if critical tests fail |

CQI cycle:

```text
Measure leakage
    |
    v
Analyze root cause
    |
    v
Improve process
    |
    v
Monitor leakage reduction
```

This approach reduces leakage gradually through continuous, data-based improvement.

---

## 32. Propose a quality improvement strategy for an IoT-based real-time system using Ishikawa's quality tools and Six Sigma principles.

An IoT-based real-time system includes sensors, devices, networks, cloud services, and user applications. Quality problems may occur due to hardware failures, network delay, data loss, timing issues, or software defects.

Quality improvement strategy:

1. Define the problem using Six Sigma:
   - Example: Sensor data is delayed or incorrect in 8% of cases.

2. Measure:
   - Collect defect data using check sheets.
   - Measure latency, packet loss, device failures, and incorrect readings.

3. Analyze using Ishikawa tools:
   - Fishbone diagram for root causes.
   - Pareto chart to identify major causes.
   - Histogram for response time distribution.
   - Control chart for process stability.
   - Scatter diagram for relationship between network strength and delay.

Fishbone categories:

```text
                 IoT data failure
Device -------- sensor calibration issue
Network ------- packet loss
Software ------ parsing defect
Cloud --------- slow processing
Environment --- temperature/noise
People -------- poor configuration
Process ------- weak testing
```

4. Improve:
   - Add sensor validation.
   - Improve network retry logic.
   - Add real-time monitoring.
   - Perform performance and recovery testing.
   - Add automated regression tests.

5. Control:
   - Track latency, failure rate, and defect leakage using dashboards and control charts.

This strategy combines Six Sigma's DMAIC method with Ishikawa's tools for practical root cause analysis and continuous improvement.

---

## 33. Contribution of TMMi model in enhancing testing process quality.

TMMi enhances testing process quality by providing a structured maturity model for improving testing practices. It helps organizations move from informal testing to managed, defined, measured, and optimized testing.

TMMi levels:

| Level | Contribution |
|---|---|
| Level 1 Initial | Shows testing is informal and needs improvement |
| Level 2 Managed | Introduces test planning, monitoring, design, and defect tracking |
| Level 3 Defined | Establishes organization-wide standard testing process |
| Level 4 Measured | Uses metrics to control and improve testing |
| Level 5 Optimization | Focuses on defect prevention and continuous improvement |

Contribution to testing quality:

- Improves test planning.
- Defines clear testing roles.
- Encourages formal test design techniques.
- Improves defect reporting and tracking.
- Supports regression testing and automation.
- Uses metrics for decision making.
- Reduces defect leakage.
- Improves test process consistency.
- Supports continuous improvement.

Example: A company with inconsistent regression testing can use TMMi to define regression strategy, maintain test suites, collect execution metrics, and improve automation.

TMMi is valuable because it treats testing as a mature engineering process rather than an informal activity at the end.

---

## 34. Function of CMM and CMMI models in improving software process maturity.

CMM and CMMI models improve software process maturity by helping organizations assess, define, measure, and improve their software development processes.

CMM focuses on software process maturity. CMMI is an integrated and improved model that covers broader process improvement areas.

Main functions:

- Assess current process maturity.
- Identify process weaknesses.
- Define standard processes.
- Improve project planning and tracking.
- Improve requirement management.
- Strengthen verification and validation.
- Introduce measurement and analysis.
- Promote defect prevention.
- Support continuous improvement.

Maturity levels:

```text
Initial -> Managed -> Defined -> Quantitatively Managed -> Optimizing
```

Example: At a low maturity level, a company may depend on individual effort and informal testing. With CMMI, it introduces standard requirements management, reviews, test planning, configuration management, and metrics. Over time, the process becomes predictable and measurable.

Benefit:

- Fewer repeated defects.
- Better schedule control.
- Improved product quality.
- Better customer satisfaction.
- Reduced rework.

CMM and CMMI help organizations move from chaotic processes to disciplined and continuously improving processes.

---

## 35. Apply a situation where a software project shows a high number of defects in the production phase and identify possible root causes using a Fishbone diagram.

Fishbone diagram, also called cause-and-effect diagram, is used to identify possible root causes of a quality problem.

Problem: A software project shows a high number of production defects.

Fishbone diagram:

```text
                         High production defects
                                   |
   ----------------------------------------------------------------
   |          |            |            |            |             |
 People     Process      Requirements  Testing      Tools       Environment
   |          |            |            |            |             |
 Lack of    No reviews    Ambiguous    Poor         No static    Unstable
 training   Weak change   Missing      regression   analysis     staging
 Poor       control       acceptance   Low test     No CI        Config
 communication            criteria     coverage                  mismatch
```

Possible root causes:

- Requirements were unclear or incomplete.
- Code reviews were skipped.
- Test cases did not cover edge cases.
- Regression testing was weak.
- Test environment differed from production.
- Developers and testers lacked domain knowledge.
- Defect trends were not analyzed.
- Release was approved despite open high-severity defects.

Corrective actions:

- Improve requirement reviews.
- Add test coverage for critical modules.
- Strengthen regression testing.
- Use defect metrics and root cause analysis.
- Improve staging environment.
- Add release exit criteria.

Fishbone diagram helps organize causes clearly and guides the team toward prevention.

---

## 36. A development team faces repeated delays in project delivery. Identify the contributing factors and organize them using a Fishbone diagram.

Repeated project delays can occur due to people, process, requirements, tools, technology, and management factors. A Fishbone diagram helps organize these causes.

Problem: Repeated delays in project delivery.

Fishbone diagram:

```text
                           Project delivery delays
                                      |
  ------------------------------------------------------------------------
  |          |             |             |             |                  |
 People     Process       Requirements  Tools         Technology         Management
  |          |             |             |             |                  |
 Skill gap  Poor planning  Frequent     Slow build    Complex           Unrealistic
 Absences   No tracking    changes      tools         architecture      deadline
 Poor       Weak reviews   Unclear      Poor test     Integration       Poor risk
 communication             scope        automation    issues            management
```

Contributing factors:

- Requirements change frequently.
- Estimates are unrealistic.
- Developers lack required skills.
- Testing starts late.
- Defects cause rework.
- Tools are slow or poorly configured.
- Integration issues are found late.
- Management does not track risks properly.

Corrective actions:

- Improve requirement clarification.
- Use realistic planning and estimation.
- Track progress regularly.
- Start testing early.
- Use automation for regression.
- Improve communication.
- Monitor risks and dependencies.

Using a Fishbone diagram helps the team identify that delays are usually caused by multiple factors, not only one person or one activity.

---

## 37. Apply a defect dataset in a software project and prioritize the major causes using a Pareto chart.

A Pareto chart is a quality tool used to identify the most significant causes of defects. It is based on the 80/20 principle, which says that a small number of causes often produce most defects.

Example defect dataset:

| Defect cause | Number of defects |
|---|---|
| Requirement ambiguity | 40 |
| Coding error | 30 |
| Weak regression testing | 15 |
| Environment issue | 8 |
| UI issue | 5 |
| Documentation issue | 2 |

Total defects = 100.

Pareto table:

| Cause | Defects | Percentage | Cumulative percentage |
|---|---:|---:|---:|
| Requirement ambiguity | 40 | 40% | 40% |
| Coding error | 30 | 30% | 70% |
| Weak regression testing | 15 | 15% | 85% |
| Environment issue | 8 | 8% | 93% |
| UI issue | 5 | 5% | 98% |
| Documentation issue | 2 | 2% | 100% |

Pareto interpretation:

```text
Requirement ambiguity:    ####################
Coding error:             ###############
Weak regression testing:  #######
Environment issue:        ####
UI issue:                 ##
Documentation issue:      #
```

Priority actions:

1. Improve requirement reviews.
2. Strengthen code reviews and unit testing.
3. Improve regression testing.

The Pareto chart shows that focusing on the top three causes can address 85% of the defects.

---

## 38. Apply variation in response time of a web application and categorize the performance behavior using a histogram.

A histogram is a quality tool that shows the distribution of data. In software performance analysis, it can show how response times are spread across ranges.

Example response time data from a web application:

```text
0.8, 1.0, 1.2, 1.4, 1.8, 2.0, 2.1, 2.4, 2.8, 3.0,
3.5, 4.0, 4.5, 5.2, 6.0
```

Histogram categories:

| Response time range | Number of requests |
|---|---:|
| 0-1 sec | 1 |
| 1-2 sec | 4 |
| 2-3 sec | 5 |
| 3-4 sec | 2 |
| 4-5 sec | 2 |
| 5-6 sec | 1 |
| Above 6 sec | 0 |

Text histogram:

```text
0-1 sec   : #
1-2 sec   : ####
2-3 sec   : #####
3-4 sec   : ##
4-5 sec   : ##
5-6 sec   : #
>6 sec    :
```

Interpretation:

- Most responses are between 1 and 3 seconds.
- Some responses are slower than 4 seconds.
- The system may need optimization if the required response time is under 3 seconds.

Histogram helps categorize performance behavior and identify whether response time is consistent or widely variable.

---

## 39. Apply testing performance metrics over time and identify whether the process is under control using control chart techniques.

A control chart is used to monitor whether a process is stable over time. In software testing, it can track metrics such as defects found per day, test execution rate, build failure rate, or response time.

Example metric: Defects found per test cycle.

| Test cycle | Defects found |
|---|---:|
| 1 | 12 |
| 2 | 14 |
| 3 | 11 |
| 4 | 13 |
| 5 | 12 |
| 6 | 30 |
| 7 | 13 |
| 8 | 12 |

Assume:

- Center line (average) = 15
- Upper control limit (UCL) = 25
- Lower control limit (LCL) = 5

Control chart interpretation:

```text
UCL 25  -------------------------
Cycle 6 defect count = 30  <-- out of control
CL  15  -------------------------
LCL 5   -------------------------
```

Since cycle 6 has 30 defects, which is above the upper control limit, the process is not fully under control. The team should investigate special causes such as a major code change, weak requirements, unstable build, or poor test data.

Use in testing:

- Detect abnormal defect spikes.
- Monitor process stability.
- Identify special causes.
- Support continuous quality improvement.

Control charts help teams distinguish normal variation from unusual quality problems.

---

## 40. Analyze the relationship between testing effort and number of defects found using a scatter diagram.

A scatter diagram is used to study the relationship between two variables. In software testing, it can show whether testing effort is related to the number of defects found.

Example data:

| Testing effort in hours | Defects found |
|---:|---:|
| 5 | 3 |
| 8 | 5 |
| 10 | 7 |
| 12 | 9 |
| 15 | 11 |
| 18 | 12 |
| 20 | 13 |

Scatter diagram idea:

```text
Defects
 14 |                         *
 12 |                    *  *
 10 |               *
  8 |          *
  6 |       *
  4 |    *
  2 |
    +------------------------------
      5   10   15   20   Effort
```

Interpretation:

- As testing effort increases, defects found also increase.
- This shows a positive relationship.
- After some point, the increase may become smaller, meaning most major defects may already be found.

Possible conclusions:

- More testing effort can improve defect detection.
- If effort increases but defects do not increase, the module may be stable or test cases may be weak.
- If defects increase sharply with little effort, the module may be highly defective.

Scatter diagrams help teams understand relationships between effort, defects, complexity, experience, and quality.
