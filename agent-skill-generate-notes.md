# AI Agent Skill: Generate Study Notes for a Unit

## Skill Name
`generate-unit-notes`

## Purpose
Given a subject unit's syllabus file and question bank file, this skill generates:
1. A mental model file grouping related topics
2. Comprehensive, plain-English study notes (split into chapters)
3. A notes index with a syllabus checklist and quick-revision cheat sheet

---

## How to Invoke This Skill

When you want notes for a new unit, paste the following prompt into GitHub Copilot Chat (or any AI assistant), replacing the `[UNIT NUMBER]` and attaching the two files:

---

## The Prompt (Copy and use this)

```
I want to generate study notes for Unit [UNIT NUMBER] of my subject.

I have attached:
- The syllabus file: unit[X]-syllabus.md
- The question bank file: unit[X]-questions.md

Please follow these steps exactly:

---

STEP 1 — BUILD A MENTAL MODEL
Read both files carefully. Group all topics that are closely related together.
For each group:
- Give the group a clear name
- Explain the core idea of the group in 1-2 sentences
- List which question bank questions this group covers (by Q.No.)

Also produce:
- A topic dependency map (how the groups relate to each other)
- A "High-Frequency Topics" table (which topics appear in the most questions)
- A "Must Master vs Good to Know" table

Save this as: unit[X]/mental-model.md

---

STEP 2 — GENERATE NOTES (one file per topic group)
For each topic group identified in Step 1, create a separate notes file.

Rules for writing notes:
1. Write in natural, plain English. No jargon without explanation.
2. Always introduce a concept with a real-world analogy before giving the technical definition.
3. Include at least one concrete, realistic example per concept (use domains like banking, e-commerce, healthcare, fintech, IoT where relevant — to match the question bank scenarios).
4. For any model/framework with numbered levels (like CMM, TMMi), describe each level with a real-world equivalent.
5. For any methodology (like DMAIC, PDCA), walk through each step with a software example.
6. For any tool or diagram (like fishbone, Pareto), explain:
   - What it is
   - When to use it
   - How to build/read it (step by step)
   - A worked example using software data
7. Include comparison tables where two or more concepts are commonly confused (e.g., QA vs QC, CMM vs CMMI vs TMMi, Six Sigma vs CQI).
8. End each file with a "Quick Summary" or "Key Takeaways" section (5-8 bullet points).
9. Do NOT write direct answers to the question bank. Write notes that build the knowledge needed to answer those questions independently.
10. Each file should cover enough depth that a student can answer a 5-7 mark exam question on any topic in that file.

Save notes as: unit[X]/notes/01-[topic].md, 02-[topic].md, etc.

---

STEP 3 — CREATE AN INDEX FILE
Create unit[X]/notes/README.md with:
- A table mapping each notes file to the topic and question bank questions it covers
- A syllabus coverage checklist (checkboxes for each syllabus item)
- A "Key Diagrams to Draw in Exam" section listing visual structures the student should be able to draw
- A "Quick-Revision Cheat Sheet" with ultra-condensed summaries (lists, tables) of all key models and frameworks

---

FORMATTING GUIDELINES:
- Use Markdown with headers (##, ###)
- Use tables for comparisons
- Use code blocks for diagrams (ASCII art is fine)
- Use bold for key terms when first introduced
- Keep paragraphs short (3-5 sentences max)
- Prefer bullet points over dense paragraphs for lists
- Write at a level appropriate for a 3rd-year engineering student studying for exams

---

OUTPUT LOCATION:
All files go into: /[workspace-root]/unit[X]/ directory
Structure:
unit[X]/
  mental-model.md
  notes/
    README.md
    01-[topic-name].md
    02-[topic-name].md
    ...
```

---

## Parameter Reference

When using the prompt above, replace:

| Placeholder | Replace with |
|-------------|-------------|
| `[UNIT NUMBER]` | The unit number, e.g., `3` |
| `[X]` | Same unit number |
| `unit[X]-syllabus.md` | Path to the syllabus file |
| `unit[X]-questions.md` | Path to the question bank file |
| `/[workspace-root]/unit[X]/` | Your actual workspace path + unit folder |

---

## Quality Checklist (Review Generated Notes Against This)

After the AI generates the notes, check:

- [ ] Every syllabus topic is covered (use the README checklist)
- [ ] Every question in the QB maps to at least one section in the notes
- [ ] Each chapter has at least 1 real-world example
- [ ] Comparison tables exist for commonly confused topics
- [ ] The mental model clearly shows topic groupings and relationships
- [ ] Each chapter ends with a quick summary
- [ ] The README cheat sheet covers all key models and their levels/steps

---

## Tips for Best Results

1. **Attach both files explicitly** — don't just reference them by name. Paste their content or use the file attachment feature.

2. **Specify your domain context** — if your subject has a specific focus (e.g., "this is a Software Testing subject"), mention it so the AI uses relevant examples.

3. **Iterate on weak sections** — if a generated chapter feels too shallow, ask: *"Expand chapter [X] with more depth on [specific concept]. Add a worked example using a [domain] application."*

4. **Ask for exam-focused additions** — after generating notes, prompt: *"Based on the question bank, which 5 topics are most likely to appear in a 10-mark exam question? Give me a structured answer framework for each."*

5. **Request diagrams separately** — if you need a specific diagram drawn in detail: *"Draw a complete fishbone diagram for the scenario in Q35 of the question bank using ASCII art."*

---

## Example Invocation

> "I want to generate study notes for Unit 3. I've attached unit3-syllabus.md and unit3-questions.md. Please follow the generate-unit-notes skill steps exactly and create all files in the /notes/unit3/ directory."

---

## File Naming Convention

```
unit{N}/
├── mental-model.md
└── notes/
    ├── README.md
    ├── 01-[first-topic-group].md
    ├── 02-[second-topic-group].md
    ├── 03-[third-topic-group].md
    └── ...
```

Topic file names should be lowercase, hyphen-separated, descriptive. Examples:
- `01-sqa-basics.md`
- `02-cmm-cmmi-tmmi.md`
- `03-iso9001.md`
- `04-six-sigma-cqi.md`
