# Unit 6 – Mental Model: Emerging Trends in Software Testing (AI/ML)

## How I Mapped the Topics

After reading the syllabus and question bank, here is how the entire unit breaks down into groups of closely related ideas.

---

## Group 1: Role of Software Testing in AI/ML Systems (Foundation)

**Topics:** What testing means in AI/ML, why it's important, contribution to model accuracy, reliability, bias detection, performance evaluation

**Core idea:** AI/ML systems introduce a fundamentally different kind of software — one whose behaviour emerges from data, not just code. Testing in this context is about validating not just "does it run?" but "does it make correct, fair, and reliable predictions?"

**Questions this covers:** Q1, Q2, Q7, Q15, Q18

---

## Group 2: AI/ML Testing vs Traditional Software Testing

**Topics:** Differences in determinism, test oracle problem, input space, output verification, testing lifecycle

**Core idea:** Traditional software has deterministic, logic-driven behaviour — you can predict the exact output for a given input. AI/ML models are probabilistic and data-driven — outputs depend on training data, and there's often no single "correct" answer to compare against.

**Questions this covers:** Q3, Q16, Q31

---

## Group 3: Challenges in Testing AI/ML Systems

**Topics:** Test oracle problem, data dependency, non-determinism, explainability, data drift, bias, model degradation, black-box nature

**Core idea:** The unique properties of AI/ML systems (they learn from data, are probabilistic, and can change over time) create testing challenges that don't exist in traditional software.

**Questions this covers:** Q4, Q10, Q11, Q17, Q22, Q30, Q32

---

## Group 4: Testing Approaches for AI/ML Systems

**Topics:** Data validation, model evaluation, metamorphic testing, adversarial testing, fairness testing, performance testing, regression testing for models

**Core idea:** Because AI/ML testing is different, it requires specialised approaches. Each approach targets a specific dimension of quality (data quality, model accuracy, fairness, robustness, performance).

**Questions this covers:** Q6, Q19, Q21, Q23, Q24, Q25, Q27, Q31, Q32, Q33, Q35

---

## Group 5: Tools for AI/ML Testing

**Topics:** Data validation tools, model evaluation frameworks, performance testing tools, bias detection tools

**Core idea:** Just like traditional software testing has Selenium, JUnit, and JMeter, AI/ML testing has its own toolset — Great Expectations, TensorFlow Model Analysis, Fairlearn, Evidently AI, etc.

**Questions this covers:** Q5, Q13, Q34

---

## Group 6: Real-Time Case Studies & Domain Scenarios

**Topics:** Healthcare AI, fraud detection, autonomous vehicles, chatbots, recommendation systems, image recognition, speech recognition, recruitment AI, IoT systems, e-commerce

**Core idea:** The question bank is heavily scenario-based. Understanding how testing principles apply to real AI/ML systems in specific industries is essential for answering Q8-Q14 and Q20-Q30.

**Questions this covers:** Q8, Q9, Q10, Q12, Q13, Q14, Q20, Q21, Q22, Q23, Q24, Q25, Q26, Q27, Q28, Q29, Q30, Q33

---

## Topic Dependency Map

```
Role of Testing in AI/ML (Group 1)
         |
         +--→ AI/ML vs Traditional Testing (Group 2)
         |              |
         |              ↓
         +--→ Challenges in AI/ML Testing (Group 3)
                        |
                        ↓
              Testing Approaches (Group 4) ←→ Tools (Group 5)
                        |
                        ↓
              Real-Time Case Studies (Group 6)
```

---

## High-Frequency Topics

| Topic | No. of Questions |
|-------|-----------------|
| Real-time domain scenarios (healthcare, fraud, autonomous, chatbot) | 15+ |
| AI/ML vs Traditional testing | 5 |
| Challenges in AI/ML testing | 7 |
| Testing approaches (metamorphic, adversarial, fairness) | 8 |
| Tools for AI/ML testing | 3 |
| Role of testing in AI/ML | 5 |

---

## Must Master vs Good to Know

| Must Master | Good to Know |
|-------------|-------------|
| Why AI/ML testing ≠ traditional testing (core differences) | History of AI testing research |
| Test oracle problem — what it is and why it's a challenge | Formal definitions of metamorphic relations |
| Data drift + model degradation — what they are | Specific mathematical metrics (precision, recall formulas) |
| Bias in AI — what causes it, how to test for it | Full survey of all available AI testing tools |
| Testing dimensions: data, model, performance, fairness | CI/CD pipeline integration for ML models |
| At least 4-5 domain-specific testing considerations | All details of specific cloud ML platforms |
| Metamorphic testing concept | Academic papers on AI testing |
| Adversarial testing concept | GAN-based test generation |
| Key tools: Great Expectations, Fairlearn, Evidently AI | All parameters of TensorFlow Model Analysis |
