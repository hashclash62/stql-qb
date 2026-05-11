# Chapter 2: Process Maturity Models — CMM, CMMI, and TMMi

---

## Why Do We Need Maturity Models?

Imagine two software companies. Both write code. Both do testing. But Company A delivers reliable software on time, while Company B always has delays, high defect rates, and unpredictable quality.

Why? The difference is **process maturity** — how well-defined, consistent, and continuously improving the development and testing processes are.

Maturity models give organisations a structured way to:
1. Assess where they currently stand (current maturity level)
2. Know what to improve to move to the next level
3. Benchmark themselves against industry standards

---

## CMM — Capability Maturity Model

CMM was developed by the **Software Engineering Institute (SEI) at Carnegie Mellon University** in the late 1980s. It was originally designed to help the US Department of Defense evaluate software contractors.

CMM describes 5 maturity levels. Think of them as a ladder:

### The 5 Levels of CMM

```
Level 5: Optimising   ← Top: Continuous process improvement using data
Level 4: Managed      ← Process is measured and controlled quantitatively
Level 3: Defined      ← Processes are documented and standardised org-wide
Level 2: Repeatable   ← Basic project management, some processes are consistent
Level 1: Initial      ← Chaotic, unpredictable, firefighting mode
```

#### Level 1 — Initial
- No defined processes
- Success depends entirely on individual heroics
- Every project is a fire drill
- *Real-world example:* A startup with 3 developers where everyone does everything differently, bugs are fixed by whoever is free, and no one documents anything.

#### Level 2 — Repeatable
- Basic project management is in place
- Requirements are managed, schedules and costs are tracked
- Similar projects can be repeated with similar results
- *Example:* A company that now has a proper bug tracker (Jira), tracks sprint velocity, and has a release checklist.

#### Level 3 — Defined
- All processes are documented and standardised *across the whole organisation*
- Teams follow the org's standard process, not their own ad-hoc methods
- Training programs exist
- *Example:* A company with a documented "software development lifecycle" that every team follows, including mandatory code review steps, test planning templates, etc.

#### Level 4 — Managed
- Processes are measured using quantitative metrics
- Management uses data to control quality and predict outcomes
- *Example:* "Our target is 95% test coverage and defect density below 0.5 per KLOC. We measure these every sprint and take corrective action if we deviate."

#### Level 5 — Optimising
- Organisation continuously improves processes using data
- Defect prevention is systematic
- New technologies and methods are evaluated and adopted proactively
- *Example:* Google or Microsoft's engineering teams — they have massive automated test infrastructure, measure everything, and constantly experiment with better development practices.

---

## CMMI — Capability Maturity Model Integration

CMMI is the successor to CMM. It was developed to fix a problem: by the 2000s, there were multiple separate CMMs (one for software, one for systems engineering, one for acquisition). Organisations dealing with all these areas had to follow multiple models.

**CMMI integrates them into one unified framework.**

### Key differences from CMM

| Aspect | CMM | CMMI |
|--------|-----|------|
| Scope | Software only | Software + Systems + Services |
| Structure | Single model | Multiple constellations (CMMI-DEV, CMMI-SVC, CMMI-ACQ) |
| Representation | Staged only | Staged + Continuous |
| Focus areas | Process areas per level | Process areas with specific + generic goals |
| Version | Older (1991) | Newer, regularly updated |

### CMMI Representations

**Staged** — Same 5 levels as CMM. Good for comparing organisations.

**Continuous** — You improve specific *process areas* independently, not the whole level at once. More flexible. Good if you want to target specific problem areas.

### CMMI Process Areas (Examples)

Each level in CMMI has specific "Process Areas" (PAs) that must be achieved:

- Level 2: Requirements Management, Project Planning, Project Monitoring, Configuration Management, Measurement and Analysis
- Level 3: Requirements Development, Technical Solution, Product Integration, Verification, Validation, Organisational Training
- Level 4: Quantitative Project Management, Organisational Process Performance
- Level 5: Causal Analysis and Resolution, Organisational Innovation and Deployment

### How CMMI helps with repeated defects

If a company has repeated defects even after multiple testing cycles, the likely root cause is that their processes are at Level 1 or Level 2. CMMI gives them a specific path:
- Move to Level 3: Document and standardise the testing process org-wide
- Move to Level 4: Measure defect rates quantitatively, set targets
- Move to Level 5: Analyse root causes of defects and fix the process itself

---

## TMMi — Test Maturity Model Integration

CMM and CMMI are about the *entire* software development process. But for organisations that want to specifically improve their *testing* processes, TMMi is the dedicated model.

TMMi was developed by the TMMi Foundation and is structured similarly to CMMI but focuses entirely on testing.

### The 5 Levels of TMMi

```
Level 5: Optimisation    ← Defect prevention, quality control, test improvement
Level 4: Managed         ← Advanced testing, peer reviews, statistical quality control
Level 3: Defined         ← Organisation-wide test strategy, test environment, test organisation
Level 2: Phase Definition← Test planning, test monitoring, test design techniques
Level 1: Initial         ← No testing process, ad-hoc, testing = debugging
```

#### Level 1 — Initial
Testing is chaotic. "Testing" just means running the software and hoping nothing breaks. No test plans, no test cases, no metrics.

#### Level 2 — Phase Definition
- Test planning happens as a formal activity
- Test cases are designed using defined techniques
- Test progress is tracked and reported

#### Level 3 — Defined
- A whole test organisation exists with defined roles (test manager, test lead, tester)
- An organisation-wide test strategy guides all projects
- Test environments are properly set up and managed
- Non-functional testing (performance, security) is done formally

#### Level 4 — Managed
- Peer reviews (of test cases, test plans) are systematic
- Advanced test techniques are used
- Statistical quality control: decisions based on data, not gut feel

#### Level 5 — Optimisation
- Defect prevention: root causes of test-missed defects are analysed and processes are improved
- Testing process is continuously measured and optimised

### CMM vs CMMI vs TMMi — Summary

| Model | Focus | Levels | Best For |
|-------|-------|--------|----------|
| CMM | Software development process | 5 | Older baseline understanding |
| CMMI | Development + Systems + Services | 5 (staged) | Overall org process maturity |
| TMMi | Testing process specifically | 5 | Orgs wanting to improve test maturity |

---

## Real-World Scenario: Using These Models

**Scenario:** A company keeps shipping buggy software. After each release, customers report 50+ critical bugs. The team is in constant firefighting mode.

**Using CMMI:**
1. Assess current level — likely Level 1 (Initial)
2. Target Level 2 first: Set up proper requirements management, test planning, defect tracking
3. Target Level 3: Document the entire testing and development process, make everyone follow it
4. At Level 4: Start measuring — track defect density, test coverage, escape rates
5. The data will show where defects are coming from → fix those process gaps

**Using TMMi specifically:**
- If the gap is specifically in testing (not development), TMMi gives more granular guidance
- E.g., "We have good coding practices but our test cases are weak" → TMMi Level 2 improvements: better test design techniques, test planning

---

## Key Things to Remember

- CMM/CMMI/TMMi are not tools or software — they are *frameworks* to guide improvement
- You cannot "skip" levels — each level builds on the previous one
- The goal is NOT to get certified — the goal is to actually improve
- Most commercial software companies operate around Level 2-3; Level 4-5 is rare but exists in defence and aerospace software
