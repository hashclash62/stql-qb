# Chapter 5: Ishikawa's Seven Quality Tools

---

## Why These Tools?

Kaoru Ishikawa, a Japanese quality pioneer, identified 7 basic quality tools that can solve the majority of quality problems in any industry without needing advanced statistics. These tools are visual, practical, and team-friendly.

The key idea behind all of them: **make data and problems visible so you can act on them objectively.**

In software, these tools help you answer questions like:
- Why does this module keep having bugs?
- Which defect types should we fix first?
- Is our test process stable or chaotic?
- Is there a relationship between testing effort and defect detection?

---

## Tool 1: Cause-and-Effect Diagram (Fishbone / Ishikawa Diagram)

### What it is
A visual tool to find the **root causes** of a problem. It looks like a fish skeleton — the "head" is the problem, and the "bones" are categories of possible causes.

### Structure

```
                                        EFFECT
                   _____________________|_____
  CAUSE A  ───────/                           \
  CAUSE B  ──────/                             \──→ [PROBLEM/DEFECT]
  CAUSE C  ─────/                             /
  CAUSE D  ────/____________________________/
```

More realistically, for software:

```
          Methods          People
             \               \
              \               \
               ──────────────────────→ HIGH DEFECT RATE
              /               /
             /               /
          Tools           Environment
```

### The 6M Categories (in manufacturing) → Adapted for Software

| Original (Manufacturing) | Software Adaptation |
|--------------------------|---------------------|
| Man (People) | Developers, testers, skill levels |
| Machine | Development tools, hardware |
| Method | Development process, coding standards |
| Material | Requirements documents, design specs |
| Measurement | Metrics, test coverage |
| Environment | Dev/test environment, deadlines, culture |

### How to Build One (Step by Step)

1. Write the problem (effect) on the right side
2. Draw a horizontal arrow pointing to it (the spine)
3. Add the main cause categories as diagonal arrows (the big bones)
4. Brainstorm causes within each category (smaller bones)
5. Keep asking "why?" for each cause to drill deeper
6. Circle the most likely root causes for further investigation

### Real Example: Banking App — High Defect Rate in Production

**Problem:** 40 defects found in production after release

**People branch:**
- Testers untrained on new payment module
- Developer coded without reviewing requirements

**Methods branch:**
- No formal code review process
- Test cases not reviewed by developer

**Tools branch:**
- Old testing framework, doesn't support new API formats

**Environment branch:**
- Production database has more data volume than test database
- Test environment doesn't mirror production configuration

**Root causes identified:** Test environment mismatch + missing code reviews → fix these first.

---

## Tool 2: Pareto Chart

### What it is
A bar chart that ranks causes/defects from most frequent to least frequent. Based on the **Pareto Principle (80/20 rule):** roughly 80% of problems come from 20% of causes.

### Why it's useful
Focus your limited resources on the few causes that create most of the damage. Don't try to fix everything at once.

### Structure

```
      Frequency
         ↑
    50 ──|███
    40 ──|███  ███
    30 ──|███  ███  ███
    20 ──|███  ███  ███  ███
    10 ──|███  ███  ███  ███  ███
         └────────────────────────→ Defect Type
          DB   UI   API  Auth  Misc

(With a cumulative % line overlaid)
```

### How to Read It
- The tallest bars (leftmost) = the biggest contributors
- The cumulative line reaches ~80% at around the 2nd or 3rd bar
- Fix those first 2-3 types and you eliminate ~80% of defects

### Software Example
A software project has 200 defects logged. Breakdown:
- Input validation: 80 (40%)
- Database errors: 60 (30%)
- UI layout: 30 (15%)
- Authentication: 20 (10%)
- Others: 10 (5%)

**Pareto insight:** Fix input validation and database errors first — that addresses 70% of all defects.

---

## Tool 3: Histogram

### What it is
A bar chart that shows the **distribution** (frequency) of a numerical dataset. It reveals the shape, spread, and centre of data.

### Why it's useful in software
- Understand distribution of defects across modules or time
- Identify if a performance metric is normally distributed or skewed
- Spot outliers or unusual patterns

### Structure
```
      Frequency
         ↑
    20 ──|     ███
    15 ──|  ███ ███ ███
    10 ──|  ███ ███ ███ ███
     5 ──|  ███ ███ ███ ███ ███
          └─────────────────────→ Response Time (ms)
           50  100  200  500  1000
```

### Software Example (Q38 scenario)
**Problem:** A web application's response time varies. Is it acceptable?

You measure response times for 100 requests:
- 50-100ms: 40 requests
- 100-200ms: 35 requests
- 200-500ms: 15 requests
- 500ms+: 10 requests

**Histogram interpretation:** Most responses are fast (100ms or less), but there's a tail — 10% are very slow. Investigate why. The histogram makes this pattern visible instantly.

---

## Tool 4: Control Chart

### What it is
A line graph with a **centre line** (average), **Upper Control Limit (UCL)**, and **Lower Control Limit (LCL)**. Used to track a process metric over time and determine if the process is **in control** (stable) or **out of control** (unpredictable).

### Key Concept: Common Cause vs Special Cause Variation
- **Common cause variation:** Normal, expected random variation. Process is stable.
- **Special cause variation:** Something unusual happened. Investigate.

### What "Out of Control" looks like on a chart
- A data point above UCL or below LCL
- 8 consecutive points on the same side of the centre line (run rule)
- A trend of 6 or more consecutive increasing/decreasing points

### Structure
```
        UCL ─────────────────────────────────────
             •         •
             •  •   •  •      •
Avg ─────────────────────────────────────────────
                  •      •  •
                       •
        LCL ─────────────────────────────────────

        ← Time / Sprint Number →
```

### Software Example (Q39 scenario)
**Problem:** Track defects found per testing sprint over 10 sprints.

If the points stay within UCL and LCL with no unusual patterns → process is **in control** (predictable).

If Sprint 7 shows a spike above UCL → special cause. Investigate Sprint 7: was it a new developer? A new module? A rushed release?

---

## Tool 5: Scatter Diagram (Scatter Plot)

### What it is
A graph that plots two variables against each other to look for a **relationship (correlation)** between them.

### Types of Correlation
- **Positive:** As X increases, Y increases (e.g., more testing hours → more defects found)
- **Negative:** As X increases, Y decreases (e.g., more code reviews → fewer defects in production)
- **No correlation:** Points are randomly spread

### Structure
```
    Defects
    Found
      ↑  •  •
         •  •  •
         •  •
         •  •  •
         ──────────────→ Testing Hours
```

### Software Example (Q40 scenario)
**Question:** Is there a relationship between testing effort and number of defects found?

Plot: X axis = testing hours per module, Y axis = defects found per module

**Result:** Positive correlation → Modules where more testing time was spent had more defects found. This suggests either (a) those modules are inherently complex and need more testing, or (b) defects existed but weren't being found in under-tested modules.

**Insight:** Increase testing effort in modules that have historically been under-tested.

---

## Tool 6: Check Sheet

### What it is
A simple structured form for systematically **collecting and recording data** in real time at the place where the data is generated.

### Why it's useful
Makes data collection easy, consistent, and minimally prone to error. Think of it as a tally sheet.

### Software Example
```
Defect Type            Mon  Tue  Wed  Thu  Fri  Total
─────────────────────────────────────────────────────
Input Validation        ||   |   |||   ||    |    9
Database Error          |   |||   |    |    ||    8
UI Bug                  |    |    |   |||    |    7
Authentication Issue    |    |         |         3
Performance Problem          |    |              2
─────────────────────────────────────────────────────
Total                   5    6    6    7    5   29
```

This becomes the raw data for Pareto charts and other analyses.

---

## Tool 7: Flowchart / Stratification

### Flowchart
A visual representation of a process — steps, decisions, loops. In quality, it's used to:
- Understand the current process (as-is)
- Identify where defects are most likely to be introduced
- Design an improved process (to-be)

### Stratification
Separating/stratifying data by category to find patterns. Example: instead of looking at total defects, stratify by developer, module, day of week, or release version to see where the pattern lies.

**Example:** Total defects = 100. But stratified by module:
- Payment module: 60 defects
- User management: 25 defects
- Reporting: 15 defects

The payment module needs urgent attention — the overall number hides this fact.

---

## How the 7 Tools Work Together

In practice, these tools are used in sequence:

```
Check Sheet       → Collect raw defect data
Histogram         → See the distribution of that data
Pareto Chart      → Identify the vital few causes
Fishbone Diagram  → Drill into root causes of those vital few
Scatter Diagram   → Verify suspected relationships
Control Chart     → Monitor the process over time
Flowchart         → Redesign the process to fix root causes
```

---

## Applying to a Real Scenario: Defects in a Banking App (Q11)

The team is struggling to identify root causes of defects.

**Step 1:** Use a **Check Sheet** — start logging every defect with type, location, time found.

**Step 2:** Use a **Pareto Chart** — rank defect types. Find that 75% of defects are in transaction processing.

**Step 3:** Use a **Fishbone Diagram** — take "transaction processing defects" as the effect. Brainstorm causes:
- People: testers not trained on transaction flows
- Methods: no integration tests between payment gateway and core banking
- Tools: mock server doesn't simulate actual bank API responses
- Environment: test uses dummy data, production has complex real transaction history

**Step 4:** Use **Scatter Diagram** — check: do more defects appear when testing is rushed (hours < X)?

**Step 5:** Fix the root causes. Then use **Control Chart** to monitor if defect rate drops and stays low.

---

## Quick Reference: All 7 Tools

| Tool | Purpose | Output |
|------|---------|--------|
| Fishbone (Cause-Effect) | Find root causes | Visual cause map |
| Pareto Chart | Prioritise causes | Ranked bar chart with 80/20 insight |
| Histogram | Show data distribution | Frequency distribution shape |
| Control Chart | Monitor process stability over time | In/out of control signal |
| Scatter Diagram | Find relationships between variables | Correlation visible |
| Check Sheet | Systematic data collection | Tally/frequency table |
| Flowchart / Stratification | Visualise process / split data by category | Process map / stratified data |
