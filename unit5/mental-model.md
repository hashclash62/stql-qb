# Unit 5 – Mental Model: Software Quality Assurance

## How I Mapped the Topics

After reading the syllabus and question bank, here is how the entire unit breaks down into groups of closely related ideas.

---

## Group 1: What is SQA? (Foundation)

**Topics:** SQA basics, QA vs QC, Importance of SQA

**Core idea:** SQA is not just testing. It is a *process-level* discipline — you build quality in from the start instead of hunting for bugs at the end. Understanding the difference between QA (process-focused, preventive) and QC (product-focused, detective) is fundamental.

**Questions this covers:** Q1, Q3, Q18, Q19, Q22, Q23

---

## Group 2: SQA System Architecture

**Topics:** Components of an SQA system

**Core idea:** An SQA system is made up of several moving parts — standards, reviews, audits, metrics, tools, training, defect tracking. Think of it like the internal machinery that keeps quality running inside an organisation.

**Questions this covers:** Q2, Q20

---

## Group 3: Maturity & Process Models

**Topics:** CMM, CMMI, TMMi

**Core idea:** These models are like "level-up" systems for an organisation. They tell you *how mature* your software process is and give you a roadmap to improve. CMM → CMMI evolved the framework; TMMi focuses specifically on testing maturity.

**Questions this covers:** Q5, Q10, Q24, Q26, Q30, Q33, Q34

---

## Group 4: International Standards

**Topics:** ISO 9001

**Core idea:** ISO 9001 is an internationally recognised quality management standard. For software, it means having documented processes, consistent execution, and evidence of compliance. Important for regulated industries like fintech and healthcare.

**Questions this covers:** Q4, Q16, Q27

---

## Group 5: Quality Improvement Methodologies

**Topics:** Six Sigma, Continuous Quality Improvement (CQI)

**Core idea:** Six Sigma is a data-driven approach targeting near-zero defects (3.4 defects per million opportunities). CQI is the ongoing organisational habit of measuring, analysing, and improving processes in small increments (like Kaizen).

**Questions this covers:** Q6, Q7, Q14, Q17, Q27, Q31, Q32

---

## Group 6: Defect Analysis Tools (Ishikawa's 7 Tools)

**Topics:** Fishbone diagram, Pareto chart, Histogram, Control chart, Scatter diagram, Check sheet, Flowchart/Stratification

**Core idea:** These are visual, analytical tools for understanding *why* defects happen and *where* to focus improvement efforts. Very practical in real scenarios.

**Questions this covers:** Q8, Q11, Q21, Q32, Q35, Q36, Q37, Q38, Q39, Q40

---

## Group 7: CASE Tools

**Topics:** CASE tools and their effect on software quality

**Core idea:** CASE (Computer-Aided Software Engineering) tools automate repetitive engineering tasks — design, code generation, testing, documentation. They reduce human error and improve consistency.

**Questions this covers:** Q9, Q13, Q25, Q29

---

## Topic Dependency Map

```
SQA Foundation (Group 1)
        |
        +---> SQA System Components (Group 2)
        |
        +---> Process Maturity Models (Group 3) -----> ISO 9001 (Group 4)
        |
        +---> Quality Improvement (Group 5) <-------> Defect Analysis Tools (Group 6)
        |
        +---> CASE Tools (Group 7)
```

---

## High-Frequency Topics (appear in many questions)

| Topic | No. of Questions |
|-------|-----------------|
| CMM/CMMI/TMMi | 7 |
| Ishikawa's 7 tools | 7 |
| SQA basics / QA vs QC | 6 |
| Six Sigma | 3 |
| ISO 9001 | 3 |
| CASE Tools | 4 |
| CQI | 3 |

---

## What to Master vs What to Know

| Must Master (exam-critical) | Good to Know |
|-----------------------------|--------------|
| CMM 5 levels + what each means | History of CMM origin (SEI) |
| CMMI vs CMM differences | CMMI appraisal methods |
| TMMi 5 levels | TMMi vs TPI comparison |
| All 7 Ishikawa tools + how to draw/read them | Statistical math behind control charts |
| Six Sigma DMAIC cycle | Six Sigma belt system |
| QA vs QC table | Full ISO 9001 clause numbers |
| ISO 9001 key requirements | ISO 9001 certification process steps |
| CASE tool categories + examples | Specific tool vendor names |
| CQI cycle (PDCA) | Detailed Kaizen methodology |
