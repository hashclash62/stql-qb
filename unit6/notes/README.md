# Unit 6: Emerging Trends in Software Testing (AI/ML) — Notes Index

## How to Use These Notes

Start with Chapter 1 and 2 to build the conceptual foundation. Then read Chapters 3-5 for depth on challenges, approaches, and tools. Use Chapter 6 as your "scenario response guide" when practicing question bank answers.

---

## Reading Order

| File | Topic | Covers QB Questions |
|------|-------|---------------------|
| [mental-model.md](../mental-model.md) | Topic grouping + study guide | All |
| [01-role-of-testing-in-ai-ml.md](./01-role-of-testing-in-ai-ml.md) | Why testing matters in AI/ML, testing lifecycle, real applications | Q1, Q2, Q7, Q15, Q18 |
| [02-aiml-vs-traditional-testing.md](./02-aiml-vs-traditional-testing.md) | Full comparison, determinism, test oracle problem, failure modes | Q3, Q16, Q31 |
| [03-challenges-in-aiml-testing.md](./03-challenges-in-aiml-testing.md) | 9 major challenges: oracle, data, drift, bias, black-box | Q4, Q10, Q11, Q17, Q22, Q30, Q32 |
| [04-testing-approaches-aiml.md](./04-testing-approaches-aiml.md) | Data validation, metamorphic, adversarial, fairness, performance, drift monitoring | Q6, Q19, Q21, Q23, Q24, Q25, Q27, Q31, Q32, Q33, Q35 |
| [05-tools-for-aiml-testing.md](./05-tools-for-aiml-testing.md) | Great Expectations, Fairlearn, Evidently AI, TFMA, adversarial tools | Q5, Q13, Q34 |
| [06-real-time-case-studies.md](./06-real-time-case-studies.md) | Healthcare, fraud detection, autonomous vehicles, chatbots, e-commerce, IoT | Q8, Q9, Q10, Q12, Q14, Q20, Q22, Q26, Q28, Q29, Q30, Q33 |

---

## Syllabus Coverage Checklist

- [x] Key roles of Software Testing in AI/ML
- [x] How AI/ML testing is different from Traditional Software Testing
- [x] Challenges in testing AI/ML systems
- [x] Tools used for AI/ML testing
- [x] Real-time case studies

---

## Key Concepts to Explain Clearly in Exam Answers

1. **Test Oracle Problem** — no single "correct" output in AI/ML; use statistical thresholds or metamorphic relations
2. **Data Drift vs Concept Drift** — input distribution changes vs. input-output relationship changes
3. **Metamorphic Testing** — test relationships between inputs/outputs when exact output is unknown
4. **Adversarial Testing** — deliberately crafted inputs to probe model robustness
5. **Fairness metrics** — demographic parity, equal opportunity, equalized odds
6. **Data Leakage** — test set contamination leading to falsely optimistic results
7. **Model Degradation** — performance decay over time without model updates
8. **Slice-based evaluation** — evaluating metrics per subgroup to detect hidden bias

---

## Key Diagrams to Draw in Exam

1. **ML Testing Lifecycle** — a pipeline diagram from data collection through production monitoring, with testing activities at each stage
2. **Train/Validation/Test Split** — show 70/15/15 split, explain why test set must never be seen during training
3. **Confusion Matrix** — 2x2 table with True Positive, False Positive, True Negative, False Negative; derive precision and recall from it
4. **AI/ML vs Traditional Testing Comparison Table** — cover determinism, oracle, input space, failure modes, tools
5. **Data Drift concept** — two distributions (reference vs current) shifting apart over time

---

## Quick-Revision Cheat Sheet

### AI/ML Testing vs Traditional Testing

| | Traditional | AI/ML |
|-|------------|-------|
| Behaviour | Deterministic | Probabilistic |
| Oracle | Exact spec | Statistical / ambiguous |
| Inputs | Finite, discrete | Infinite, continuous |
| Failures | Obvious crashes/errors | Silent, subgroup-specific |
| Testing end | Pre-deployment | Never — continuous monitoring |

### 9 Challenges in AI/ML Testing
1. Test Oracle Problem
2. Data Dependency
3. Non-Determinism
4. Data Drift
5. Model Degradation
6. Bias and Fairness
7. Black-Box Nature
8. Infinite Input Space
9. Dynamic Environments (IoT)

### 8 Testing Approaches
1. Data Validation Testing
2. Model Evaluation Testing (metrics)
3. Metamorphic Testing
4. Adversarial Testing
5. Fairness/Bias Testing
6. Performance Testing
7. Regression Testing for Models
8. Drift Monitoring

### Key ML Metrics
- **Accuracy** = (TP + TN) / Total
- **Precision** = TP / (TP + FP) → minimise false alarms
- **Recall** = TP / (TP + FN) → minimise missed cases (critical in healthcare)
- **F1** = 2 × (Precision × Recall) / (Precision + Recall)
- **AUC-ROC** = Overall discrimination ability

### Key Tools at a Glance
| Tool | Purpose |
|------|---------|
| Great Expectations | Data quality validation |
| Fairlearn | Bias/fairness metrics |
| Evidently AI | Production drift monitoring |
| TFMA | Slice-based model evaluation |
| Foolbox / CleverHans | Adversarial testing |
| MLflow | Experiment tracking |
| What-If Tool | Visual bias exploration |

### Domain-Specific Primary Concern
| Domain | #1 Testing Priority |
|--------|-------------------|
| Healthcare AI | High recall — never miss a real case |
| Fraud Detection | Precision-recall balance + real-time latency |
| Autonomous Vehicles | Safety edge cases + adversarial robustness |
| Chatbot | Intent accuracy + graceful failure handling |
| E-commerce | Relevance + diversity + cold start |
| Recruitment AI | Bias/fairness — counterfactual testing |
| IoT | Sensor noise tolerance + real-time performance |
