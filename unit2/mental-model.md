# Unit 2 – Mental Model: Testing Techniques

## How I Mapped the Topics

After reading the syllabus and question bank, here is how the entire unit breaks down into groups of closely related ideas.

---

## Group 1: Black Box Testing — Specification-Based Techniques

**Topics:** Random testing, Equivalence Class Partitioning (ECP), Boundary Value Analysis (BVA), Cause-Effect Graphing, State Transition Testing, Decision Table Testing, Requirement-Based Testing

**Core idea:** Black box testing treats the software as a sealed box — you only know the inputs and expected outputs from the specification. You don't care about the code inside. These techniques help you choose *which inputs* to test to maximise defect detection without exhaustive testing.

**Questions this covers:** Q2, Q4, Q5, Q6, Q8, Q11, Q14, Q19, Q24, Q29, Q30, Q31, Q32

---

## Group 2: White Box Testing — Structural/Code-Based Techniques

**Topics:** Control flow graphs, Cyclomatic complexity, Code coverage criteria (statement, branch, condition, MC/DC), Path testing, Data flow testing, Loop testing, Test adequacy criteria

**Core idea:** White box testing looks *inside* the code. You design tests based on the internal structure — to ensure every statement, branch, path, or data-flow interaction is exercised at least once.

**Questions this covers:** Q7, Q9, Q17, Q18, Q20, Q21, Q23, Q25

---

## Group 3: Black Box vs White Box vs Gray Box

**Topics:** Comparison of testing approaches, when to use each

**Core idea:** These are not competing approaches — they're complementary. Black box finds functional gaps; white box finds structural gaps. Gray box combines both.

**Questions this covers:** Q3, Q16

---

## Group 4: Mutation Testing

**Topics:** Mutants, mutation operators, killing mutants, equivalent mutants, mutation score

**Core idea:** Mutation testing evaluates the *quality of your test suite* by deliberately introducing small code faults and checking whether your tests detect them. If they don't, your tests have gaps.

**Questions this covers:** Q22, Q33, Q34

---

## Group 5: Regression Testing and Re-testing

**Topics:** Regression testing purpose, when it's needed, re-testing vs regression testing

**Core idea:** Re-testing checks that a specific fixed defect is gone. Regression testing checks that fixing that defect didn't break anything else.

**Questions this covers:** Q12, Q13

---

## Group 6: JUnit Testing

**Topics:** JUnit test structure, annotations (@Test, @Before, @After, @BeforeClass, @AfterClass), assertions, writing test cases for code coverage

**Core idea:** JUnit is the standard framework for writing automated unit tests in Java. Understanding its structure and annotations is a practical, hands-on skill.

**Questions this covers:** Q26, Q27, Q28

---

## Topic Dependency Map

```
Black Box Techniques (Group 1)
        |
        +--→ BB vs WB vs Gray Box (Group 3)
        |
White Box Techniques (Group 2)
        |
        +--→ Mutation Testing (Group 4) ← Tests the quality of any test suite
        |
Regression / Re-testing (Group 5)
        |
JUnit (Group 6) ← Practical implementation of unit-level white box tests
```

---

## High-Frequency Topics

| Topic | No. of Questions |
|-------|-----------------|
| ECP + BVA (Black Box) | 5 |
| Cause-Effect Graphing | 4 |
| White box / CFG / Cyclomatic complexity | 4 |
| JUnit | 3 |
| Mutation Testing | 3 |
| Data flow testing | 2 |
| State transition testing | 2 |

---

## Must Master vs Good to Know

| Must Master | Good to Know |
|-------------|-------------|
| ECP: valid/invalid classes, how to derive test cases | Formal ECP notation |
| BVA: boundaries of ranges, all 3 values per boundary | Modified BVA (robust BVA) |
| Decision table: conditions, actions, rules | Minimising decision tables |
| Cause-effect graphing: causes, effects, graph, table | Constraint notation in CEG |
| State transition diagram: states, transitions, test paths | State explosion problem |
| Control Flow Graph: nodes, edges, decision nodes | All formal path coverage criteria |
| Cyclomatic complexity: V(G) = E - N + 2P formula | McCabe's original paper |
| What code coverage criteria mean (statement, branch, condition) | MC/DC (used in aviation) |
| Data flow testing: definition, use, def-use paths | All-defs vs all-uses difference |
| Loop testing: all test cases for a loop | Formal loop testing theory |
| Mutation score formula and interpretation | All mutation operator types |
| JUnit: @Test, @Before, @After, assertions | Parameterised tests, test suites |
| Re-testing vs Regression testing difference | Test selection algorithms |
