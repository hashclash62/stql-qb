# Chapter 5: Reviews as a Testing Activity

## The Analogy Before the Definition

Before submitting your final year project report, you ask a classmate to read it. They point out that you used the wrong formula in Chapter 3, and there's a logical contradiction in your methodology. You fix both before submission.

That's a review. You didn't run any tests — but you caught real problems.

Reviews are one of the most cost-effective defect removal techniques because they find problems **before code is even written**.

---

## What is a Review?

A review is a **manual examination of a software work product** (document, design, code, test plan) by one or more people other than its author.

Reviews can be applied to:
- Requirements documents
- Design documents
- Source code
- Test plans and test cases
- User manuals

**Key insight:** You don't need runnable software to do a review. A review is a **static testing** technique — the product is examined, not executed.

---

## Types of Reviews

### 1. Walkthrough (Informal Review)

**Who leads it:** The **author** of the document/code
**Formality:** Low — informal, collaborative
**Purpose:** Share understanding, gather feedback, educate team

**How it works:**
1. Author invites peers to a meeting
2. Author walks the group through the document/code
3. Participants ask questions and suggest improvements
4. Notes are taken (but no formal defect logging required)
5. Author decides which suggestions to incorporate

**Best for:**
- Early designs that are still changing
- New team members getting up to speed
- When the author wants informal feedback

**Analogy:** A developer presents their new database schema to the team on a whiteboard. "Here's what I'm thinking — any concerns?" This is a walkthrough.

---

### 2. Inspection (Formal Review)

**Who leads it:** A trained **moderator** (not the author)
**Formality:** High — structured, documented, formal process
**Purpose:** Find defects systematically using checklists

**How it works:**
1. **Planning:** Moderator prepares checklist, distributes materials
2. **Individual review:** Each reviewer studies the document independently
3. **Inspection meeting:** Reviewers report defects found; each is logged
4. **Rework:** Author fixes all logged defects
5. **Follow-up:** Moderator verifies defects are fixed

**Key rules:**
- Each reviewer uses a **checklist** (e.g., "Is every input validated?")
- Defects are logged with type, location, description
- The author does NOT defend their work during inspection
- Defects found ≠ criticism of the author

**Best for:**
- Critical code (security, payments, medical systems)
- High-risk modules where defects would be costly
- When there's time and resources for a formal process

**Analogy:** A building inspector visits with a checklist. They don't ask the builder to explain anything — they independently check each item on the list and log every issue. This is an inspection.

---

### 3. Other Review Types (briefly)

| Type | Formality | Notes |
|------|-----------|-------|
| Informal review / Peer review | Very low | Ad hoc — "hey can you look at this?" |
| Technical review | Medium | Technical experts check for correctness |
| Walkthrough | Low | Author-led, educational |
| Inspection | High | Moderator-led, checklist-driven, formal output |
| Audit | Formal | External or internal — checks process compliance |

---

## Walkthrough vs Inspection (Q11)

| | Walkthrough | Inspection |
|-|-------------|-----------|
| Led by | Author | Moderator (not author) |
| Formality | Informal | Formal |
| Checklist | No | Yes |
| Defect logging | Optional | Required |
| Rework required | Author decides | Mandatory |
| Best for | Early feedback, education | Critical defect finding |
| Documentation | Minimal | Formal defect reports |

### Q11 Scenario: "Team needs to review code with limited time"

If time is limited:
- Use a **walkthrough** — faster, less overhead, still catches obvious issues
- Author can quickly explain and get feedback from 2-3 key people in under an hour

If the code is critical (e.g., payment processing, security authentication):
- Use an **inspection** — more time upfront, but catches more defects; worth the investment

---

## Need for Review Policies

A review policy is a documented set of rules that defines **when and how reviews must be conducted** in a project.

### Why have review policies?
- Without a policy, reviews are optional and often skipped under pressure
- Policy ensures consistency — every module reviewed the same way
- Provides evidence for audits (proof that reviews happened)
- Sets expectations — developers know review is part of the process

### What a review policy includes:
- Which work products require review (code? requirements? test cases?)
- Which type of review to use at each stage (walkthrough for requirements, inspection for critical code)
- Minimum number of reviewers
- Entry and exit criteria for reviews
- How defects are logged and tracked

---

## Components of a Review Plan

A review plan is a document that describes how a specific review will be conducted.

| Component | Description |
|-----------|-------------|
| Objectives | What the review aims to achieve |
| Work product | What is being reviewed (e.g., Module X source code) |
| Participants | Who is reviewing (names and roles) |
| Roles | Moderator, recorder, reviewers |
| Schedule | Meeting date, duration |
| Checklist | Questions reviewers will answer |
| Entry criteria | Conditions before review can start (e.g., code must compile) |
| Exit criteria | Conditions that mean review is complete (e.g., all major defects fixed) |

---

## Review Metrics

After reviews, you collect metrics to measure their effectiveness and improve the process.

### Key Review Metrics

| Metric | Formula / Description | Purpose |
|--------|----------------------|---------|
| Defect Density | Defects found / Size of document | How buggy is it? (per page or per KLOC) |
| Defect Detection Rate | Defects found in review / Total defects | How effective was the review? |
| Review Coverage | % of work products reviewed | Are we reviewing enough? |
| Preparation Rate | Pages/hour reviewed by each reviewer | Are reviewers spending enough time? |
| Inspection Rate | Lines of code / Hours spent | Speed of inspection (not too fast) |
| Rework Effort | Hours spent fixing defects found | Cost of review-found defects |

### Why metrics matter
- If a module has very high defect density → invest more time in review / rework
- If defect detection rate is low → reviews are not effective → improve checklist or training
- If inspection rate is too high (too fast) → reviewers are skimming → slow down

### Example

A code inspection of 500 lines of code takes 5 hours. 20 defects are found.

- Inspection Rate = 500 / 5 = 100 LOC/hour (acceptable; ISTQB recommends 100–200 LOC/hour)
- Defect Density = 20 / 500 = 0.04 defects/LOC = 40 defects/KLOC (high — this module needs rework)

---

## Quick Summary

| Concept | One-liner |
|---------|-----------|
| Review | Static examination of work products by people other than the author |
| Walkthrough | Author-led, informal, educational, quick feedback |
| Inspection | Moderator-led, formal, checklist-driven, defects logged and fixed |
| Review policy | Rules mandating when/how reviews must be done |
| Review plan | Document specifying who, what, when, how for a specific review |
| Defect density | Defects per unit size — shows how buggy a product is |
| Inspection rate | LOC per hour — should not be too fast or too slow |
