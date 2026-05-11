# Unit 3 – Mental Model: Levels of Testing and Defect Management

## How I Mapped the Topics

After reading the syllabus and question bank, here is how the entire unit breaks down into groups of closely related ideas.

---

## Group 1: Levels of Testing — Functional (Foundation)

**Topics:** Unit testing, Integration testing, System testing, Acceptance testing (Alpha, Beta, UAT)

**Core idea:** Software is built in layers (functions → modules → full system → deployed product). Testing matches these layers — you validate each layer before combining it with others. Each level catches a different class of defect.

**Questions this covers:** Q1, Q3, Q14, Q15, Q20, Q25, Q26, Q34, Q35, Q36, Q37

---

## Group 2: Levels of Testing — Non-Functional

**Topics:** Performance testing, Load testing, Stress testing, Recovery testing, Regression testing, Configuration testing

**Core idea:** Once the software *works* correctly (functional tests pass), you need to know if it works *well* — fast enough, stable under load, recoverable after failure, consistent across configurations.

**Questions this covers:** Q12, Q13, Q21, Q22, Q23, Q24, Q28, Q29, Q31

---

## Group 3: Test Planning, Monitoring, and Reporting

**Topics:** Test planning, Test reports, Monitoring test effectiveness

**Core idea:** Good testing isn't ad-hoc. It needs a plan (what, when, who, how), execution tracking, and documented reports. Test effectiveness monitoring tells you whether your testing is actually finding defects.

**Questions this covers:** Q10, Q24

---

## Group 4: Defect Origins and Types

**Topics:** Origins of defects (requirements, design, code, communication), Defect types (computational, logic, interface, data, performance)

**Core idea:** Defects don't just appear — they have root causes. Understanding *where* and *why* defects originate helps you design better tests and implement better prevention.

**Questions this covers:** Q2, Q6, Q16, Q17, Q19, Q27, Q28, Q30

---

## Group 5: Defect Lifecycle and Repository

**Topics:** Defect severity, Defect life cycle (New → Open → Fixed → Verified → Closed), Defect repository, Track/Retest/Close

**Core idea:** Every defect goes through a lifecycle from discovery to closure. A defect repository is the organised record of all defects. Together they make defect management systematic rather than chaotic.

**Questions this covers:** Q7, Q8, Q9, Q10, Q11, Q18

---

## Group 6: Defect Prevention and Injection

**Topics:** Defect injection (mutation testing), Defect prevention techniques

**Core idea:** Prevention is better than detection. Defect injection deliberately introduces faults to test your testing process itself. Prevention techniques (reviews, checklists, standards) reduce the rate of defect introduction.

**Questions this covers:** Q32, Q33

---

## Topic Dependency Map

```
Levels of Testing — Functional (Group 1)
        |
        +--→ Levels of Testing — Non-Functional (Group 2)
        |
        +--→ Test Planning & Monitoring (Group 3)
        |
Defect Origins & Types (Group 4)
        |
        ↓
Defect Lifecycle & Repository (Group 5)
        |
        ↓
Defect Prevention & Injection (Group 6)
```

---

## High-Frequency Topics

| Topic | No. of Questions |
|-------|-----------------|
| Levels of testing (unit → acceptance) | 12+ |
| Defect types, origins, classification | 7 |
| Defect lifecycle and repository | 6 |
| Performance / non-functional testing | 5 |
| Defect prevention / injection | 3 |
| Test planning & reporting | 2 |

---

## Must Master vs Good to Know

| Must Master | Good to Know |
|-------------|-------------|
| What each testing level tests and catches | History of V-model |
| Integration strategies: top-down, bottom-up, sandwich | Big-bang integration |
| Alpha vs Beta vs Acceptance testing differences | Specific acceptance criteria frameworks |
| Defect lifecycle: all states and transitions | Tool-specific workflow (Jira states) |
| Defect severity levels (Critical → Low) with examples | Defect priority vs severity detailed nuances |
| Defect types: computational, logic, interface, data | Full taxonomy from IEEE standards |
| Performance testing: load, stress, spike, soak | Specific JMeter configuration |
| Recovery testing concepts | Chaos engineering |
| Regression testing purpose and approach | Test selection algorithms for regression |
| Defect injection / mutation testing concept | Mutation operators math |
