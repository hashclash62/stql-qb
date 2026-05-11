# Chapter 4: Defect Lifecycle, Repository, and Reporting

---

## The Defect Lifecycle

A defect is not just "found and fixed". It goes through a series of states from the moment it's discovered to the moment it's permanently closed. This is the **Defect Lifecycle** (also called Bug Lifecycle or Defect Management Workflow).

Think of it like a customer complaint in a company — it's logged, assigned to the right person, investigated, resolved, verified by the customer, and then formally closed.

---

## Defect States and Transitions

```
               [New]
                 |
                 ↓ (Assigned to developer by Test Lead)
              [Open]
                 |
           ┌─────┴────────┐
           ↓              ↓
        [Fixed]      [Rejected] → (Not a defect / Cannot reproduce)
           |              |
           ↓              ↓
       [Verified]    [Deferred] → (Valid but fix postponed)
           |
     ┌─────┴──────┐
     ↓            ↓
  [Closed]   [Reopened] → (Fix didn't work → back to Open)
```

### Each State Explained

| State | Meaning | Who is responsible |
|-------|---------|-------------------|
| **New** | Defect just logged by tester | Tester |
| **Open** | Assigned to developer for investigation | Test Lead → Developer |
| **In Progress** | Developer actively working on fix | Developer |
| **Fixed** | Developer has implemented a fix and updated the code | Developer |
| **Verified** | Tester re-tests the fix and confirms it's resolved | Tester |
| **Closed** | Verified fix, no issues, defect formally closed | Test Lead / QA Manager |
| **Rejected** | Developer determines it's not a real defect (by design, wrong test, etc.) | Developer |
| **Deferred** | Valid defect but fix is postponed to a later release | Product Manager / Test Lead |
| **Reopened** | Fix was verified to be incorrect — defect resurfaces | Tester |

---

## Real-Time Example: Defect in a Banking App (Q8)

1. **Tester discovers:** When transferring ₹0 to another account, the system shows a success message but charges a ₹50 processing fee.

2. **New:** Tester logs the defect in Jira with:
   - Title: "Zero amount transfer incorrectly charges processing fee"
   - Steps to reproduce
   - Expected result: "Transaction rejected or fee = ₹0"
   - Actual result: "Success message + ₹50 fee charged"
   - Severity: Critical
   - Screenshots

3. **Open:** Test Lead assigns to backend developer.

4. **Fixed:** Developer finds the fee calculation doesn't check for zero amount. Adds the check. Marks as Fixed.

5. **Verified:** Tester re-tests: zero amount now correctly rejected with "Invalid amount" message. No fee charged. Marks as Verified.

6. **Closed:** Test Lead confirms and closes.

**Alternative path:** If developer disagrees ("this is expected business behaviour — you can't transfer ₹0"), they mark it **Rejected** with justification. Tester can appeal. If agreed upon, it might be reclassified as a business rule change request.

---

## Handling a Critical Production Bug (Q7)

**Scenario:** A critical bug is found in production. Here's the systematic process:

1. **Triage:** Assess impact. How many users affected? Is data corrupted? Can it be temporarily worked around?

2. **Log immediately:** Create a defect report with all known details and severity = Critical/Blocker.

3. **Isolate:** Reproduce in a controlled environment (staging). If only production, gather logs.

4. **Debug:** Work with developer to trace root cause. Share exact steps, logs, environment details.

5. **Fix:** Developer implements hotfix in a branch.

6. **Test the fix:** Tester verifies the fix in staging. Also runs regression tests to ensure the fix didn't break anything.

7. **Deploy:** Hotfix deployed to production through an expedited process.

8. **Verify in production:** Confirm fix works in production.

9. **Close + Post-mortem:** Close the defect. Conduct a post-mortem: How did this escape all testing? What process change prevents recurrence?

10. **Close the gap:** Update test cases, add regression tests for this scenario.

---

## The Defect Repository

### What it is (Q10, Q18)
A **defect repository** is a centralised database or system where all defects are stored, tracked, and managed throughout their lifecycle.

It's not just a list of bugs — it's a structured, searchable, analysable record that the entire team uses.

### What Information Should Each Defect Record Contain? (Q18)

| Field | Why it's important | Who uses it |
|-------|--------------------|-------------|
| **Defect ID** | Unique identifier for tracking and reference | Everyone |
| **Title / Summary** | Quick identification | Everyone |
| **Description** | What the defect is | Developer, tester |
| **Steps to Reproduce** | How to trigger the defect reliably | Developer |
| **Expected Result** | What should happen | Developer, tester |
| **Actual Result** | What actually happens | Developer, tester |
| **Severity** | How bad is the impact | Test Lead, PM, Developer |
| **Priority** | How urgently it needs fixing | Product Manager, Test Lead |
| **Status** | Current lifecycle state | Everyone |
| **Assigned To** | Who is responsible for it now | Developer, Test Lead |
| **Reported By** | Who found it | Accountability |
| **Date Reported** | When it was found | Metrics, SLAs |
| **Date Fixed** | When the fix was implemented | Metrics, SLAs |
| **Build/Version** | Which software version has the defect | Developer, Release Manager |
| **Environment** | OS, browser, device, network conditions | Developer (for reproduction) |
| **Attachments** | Screenshots, log files, videos | Developer |
| **Root Cause** | Why the defect occurred (filled after fix) | Process improvement, management |
| **Regression Status** | Did the defect reappear? | Tester, Release Manager |

**Why is this useful?**
- Enables tracking and accountability — no defect gets lost
- Generates metrics: defect density, average fix time, defect escape rate
- Root cause data feeds into defect prevention
- Management uses it for release go/no-go decisions
- Historical data helps estimate future defect rates in similar projects

---

## Test Planning (Q10)

A **test plan** is the document that describes the *what*, *when*, *who*, *how*, and *why* of testing for a project.

### Key Contents of a Test Plan

| Section | Content |
|---------|---------|
| **Scope** | What will and won't be tested |
| **Test Strategy** | Levels of testing, techniques, tools |
| **Entry/Exit Criteria** | Conditions to start and stop testing |
| **Test Schedule** | Timeline for each testing phase |
| **Resources** | Testers, tools, environments |
| **Risk Assessment** | What could go wrong, mitigation |
| **Defect Management** | How defects will be tracked |
| **Test Deliverables** | Test cases, reports, sign-offs |

A good test plan + defect repository together form the foundation of the SQA system at the project level. The test plan tells everyone what to do; the defect repository tracks what was found.

---

## Monitoring Test Effectiveness

How do you know if your testing is actually *working*? You measure it.

**Key metrics:**

| Metric | What it measures |
|--------|-----------------|
| **Defect Detection Efficiency (DDE)** | % of defects found before release vs total defects (found before + after release) |
| **Defect Density** | Number of defects per module or per 1000 lines of code |
| **Test Coverage** | % of requirements covered by test cases |
| **Defect Removal Rate** | % of known defects fixed per sprint/release cycle |
| **Escape Rate** | % of defects that reach production despite testing |
| **Reopened Defects Rate** | % of defects reopened after being marked fixed |

---

## Resolving Disagreements with Developers (Q5, Q9)

In practice, testers and developers often disagree about defects:
- "That's not a bug, that's a feature"
- "I can't reproduce it on my machine"
- "That's extremely edge-case, not worth fixing"

**How to handle it professionally:**
1. **Provide clear, reproducible evidence:** Log the exact steps, environment, screenshots, logs
2. **Refer to the requirements:** "The requirement says X. The current behaviour is Y. These differ."
3. **Escalate constructively:** If still disagreed, bring in the Test Lead or Product Manager for a neutral decision
4. **Avoid personal conflict:** Focus on the product, not personalities
5. **Document the outcome:** Whatever is decided, record it in the defect tracker (Rejected with reason, or Deferred with justification)

---

## Quick Summary

- The defect lifecycle: New → Open → Fixed → Verified → Closed (with Rejected, Deferred, Reopened states)
- A defect repository records all defects with rich structured data for tracking, metrics, and improvement
- Every defect record should contain: steps to reproduce, severity, status, environment, root cause
- Test planning defines scope, strategy, schedule, and criteria for testing
- Test effectiveness is measured via metrics: DDE, defect density, escape rate
- Disagreements with developers are resolved by evidence, requirements reference, and constructive escalation
