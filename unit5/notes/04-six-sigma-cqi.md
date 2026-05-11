# Chapter 4: Six Sigma and Continuous Quality Improvement (CQI)

---

## Six Sigma

### What is Six Sigma?

Six Sigma is a **data-driven methodology** aimed at eliminating defects and reducing variation in processes. The name comes from statistics: "sigma" (σ) is the symbol for standard deviation (how spread out a process's output is).

**The goal:** Achieve **3.4 defects per million opportunities (DPMO)** — which statistically corresponds to 6 standard deviations from the process mean.

In simpler terms: Six Sigma means your process is so well-controlled that you almost never produce a defective output.

### Where Six Sigma Came From

Originally developed at **Motorola in the 1980s**, made famous by **GE (Jack Welch) in the 1990s**. Applied to manufacturing first (reduce defective parts on an assembly line), then adapted to services and software.

### Six Sigma Sigma Levels

| Sigma Level | Defects Per Million | Yield |
|-------------|--------------------|----|
| 1σ | 690,000 | 31% |
| 2σ | 308,000 | 69% |
| 3σ | 66,800 | 93.3% |
| 4σ | 6,210 | 99.4% |
| 5σ | 233 | 99.98% |
| **6σ** | **3.4** | **99.9997%** |

Most software teams operate around 3-4 sigma. Reaching 6 sigma is extremely difficult but the *target* drives continuous improvement.

---

### The DMAIC Cycle — The Heart of Six Sigma

Six Sigma improvements follow the **DMAIC** process:

```
Define → Measure → Analyse → Improve → Control
```

#### Define
- What is the problem? Define it clearly.
- Who are the customers affected?
- What is the goal? (e.g., reduce production defects from 5% to 0.5%)
- Deliverable: Project charter, problem statement

*Example:* "Our payment processing module has a 2% error rate causing transaction failures. Goal: reduce to below 0.01%."

#### Measure
- Collect data about the current process
- Baseline the current performance
- Validate the measurement system (are we measuring the right things?)

*Example:* Track every transaction, classify each failure by type (timeout, validation error, network error), measure frequency.

#### Analyse
- Find the **root causes** of defects using data
- Use tools like fishbone diagrams, scatter plots, regression analysis
- Find the *vital few* causes (usually 20% of causes create 80% of defects — Pareto principle)

*Example:* Analysis shows 70% of failures are timeout errors during peak load → root cause is inefficient database queries.

#### Improve
- Design and implement solutions to the root causes
- Pilot the solution
- Verify it actually improves the metric

*Example:* Optimise database queries + add caching → retest under peak load conditions → error rate drops from 2% to 0.03%.

#### Control
- Put controls in place to ensure the improvement is sustained
- Document the new process
- Monitor with control charts to detect if the process regresses

*Example:* Add automated performance tests to CI pipeline. Alert if response time exceeds threshold.

---

### Six Sigma in Software Testing

How does DMAIC apply to software?

- **Define:** "Our mobile app has high crash rates — define crash as any unhandled exception causing forced closure"
- **Measure:** Instrument the app to log crashes, categorise by module and device
- **Analyse:** Fishbone diagram shows crashes are concentrated in the image loading module on older Android versions
- **Improve:** Fix memory management in image loading, add device-specific handling
- **Control:** Automated crash reporting dashboard with alerts, regression tests for this specific module

---

### Six Sigma Roles (Belt System)

| Belt | Role |
|------|------|
| White/Yellow Belt | Basic awareness and support |
| Green Belt | Leads small improvement projects part-time |
| Black Belt | Full-time Six Sigma project leader |
| Master Black Belt | Mentors Black Belts, org-level strategy |
| Champion | Sponsor (executive level) |

---

## Continuous Quality Improvement (CQI)

### What is CQI?

CQI is the ongoing, systematic effort to improve processes, products, and services over time. It's not a one-time project — it's a **mindset and culture** of always asking "how can we do this better?"

CQI is based on the work of **W. Edwards Deming** and the Japanese concept of **Kaizen** (meaning "change for better" in Japanese).

The famous foundation of CQI is the **PDCA Cycle** (Plan-Do-Check-Act), also called the **Deming Cycle**.

---

### The PDCA Cycle

```
        PLAN
       ↗    ↘
    ACT      DO
       ↖    ↙
        CHECK
```

#### Plan
- Identify an improvement opportunity
- Analyse the current situation
- Set a measurable goal
- Plan the change

#### Do
- Implement the change on a small scale (pilot)
- Collect data during the pilot

#### Check
- Analyse the data from the pilot
- Compare results to the expected goal
- Identify what worked and what didn't

#### Act
- If it worked, roll it out fully and standardise it
- If it didn't, revise the plan and try again
- Start the cycle over with a new improvement target

---

### CQI in Software Engineering

CQI is embedded in modern software development practices:

| CQI Practice | How it appears in software |
|-------------|---------------------------|
| Agile retrospectives | Every sprint: What went well? What can we improve? |
| Post-mortems | After incidents: What caused this? How do we prevent recurrence? |
| Continuous Integration | Automated tests on every commit — quality feedback instantly |
| Code review process | Ongoing peer review improves code quality over time |
| Defect analysis | Regular review of defect data to identify systemic problems |
| Metrics reviews | Regular review of test coverage, defect density, escape rates |

---

### CQI in an E-Commerce Platform (Example)

Imagine a large e-commerce platform like Amazon or Flipkart using continuous integration:

1. **Plan:** "Our checkout page has a 5% error rate during flash sales"
2. **Do:** Add load testing to the CI pipeline, optimise the checkout service, deploy to staging
3. **Check:** Load test results show 0.5% error rate — significant improvement but not ideal yet
4. **Act:** Roll out to production, monitor real traffic. Set up alerting. Start next PDCA cycle: "Reduce checkout errors to below 0.1%"

This cycle never stops. Every deployment, every incident, every customer complaint is an opportunity for the next PDCA loop.

---

### CQI for a Fintech App with High Defect Leakage (Q31 scenario)

**Defect leakage** = defects found by customers that should have been caught during testing.

Priority actions using CQI:
1. **Measure** current leakage rate (how many customer-reported bugs per release)
2. **Classify** leaked defects — which phases missed them? (requirements? testing? code review?)
3. **Find the biggest gap** (Pareto: which defect type accounts for 80% of leakage?)
4. **Plan improvement** for that specific gap (better test case design for that area)
5. **Implement** in the next sprint/release
6. **Measure again** — did leakage reduce?
7. **Repeat**

---

### Six Sigma vs CQI — Comparison

| Aspect | Six Sigma | CQI / PDCA |
|--------|-----------|-----------|
| Approach | Project-based, data-heavy | Continuous cycles, incremental |
| Scope | Targeted at specific big problems | Applies to everything, all the time |
| Tools | DMAIC, statistical analysis | PDCA, basic quality tools |
| Intensity | Intense, structured projects | Lightweight, ongoing |
| Goal | Near-zero defects (3.4 DPMO) | Steady, continuous improvement |
| Best for | Large, recurring, costly defects | Day-to-day process improvement |

**They work well together:** Use CQI/PDCA for regular ongoing improvement and launch a Six Sigma DMAIC project when you identify a significant, persistent, costly problem.

---

## Quick Summary

- **Six Sigma:** Target 3.4 DPMO. Use DMAIC: Define → Measure → Analyse → Improve → Control. Data-driven, project-based.
- **CQI:** Never-ending improvement culture. Use PDCA: Plan → Do → Check → Act. Embedded in daily/sprint/release cycles.
- Both are about reducing defects, but Six Sigma is a surgical strike while CQI is the daily workout.
