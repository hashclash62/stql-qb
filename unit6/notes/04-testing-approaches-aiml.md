# Chapter 4: Testing Approaches for AI/ML Systems

---

## Overview: The Dimensions of AI/ML Testing

Because AI/ML systems have multiple quality dimensions (data quality, model correctness, fairness, robustness, performance), no single testing approach covers everything. You need a *portfolio* of approaches, each targeting a specific dimension.

Think of it like a full health checkup — not just one test, but blood work, ECG, eye test, X-ray — each reveals something different.

---

## 1. Data Validation Testing

**What it is:** Testing the quality, completeness, consistency, and representativeness of the training and evaluation data *before* the model is trained.

**Why it matters:** Bad data = bad model. The model cannot be better than the data it learned from.

**What to test:**

| Data Quality Dimension | What to Check |
|----------------------|---------------|
| Completeness | Are there missing values? In which columns? How many? |
| Consistency | Are values in a valid range? (e.g., age = -5 is invalid) |
| Correctness | Are labels accurate? Any mislabelled examples? |
| Distribution | Is the class distribution balanced? (Or 99:1 skewed?) |
| Representativeness | Does the data represent all real-world subgroups? |
| Freshness | Is the data recent enough for the use case? |
| Duplication | Are there duplicate records that could bias training? |

**Real example:** For a fraud detection model, check that the training dataset contains representative examples of both genuine and fraudulent transactions across different geographies, device types, and time periods — not just from one region or one fraud type.

---

## 2. Model Evaluation Testing

**What it is:** Testing the model's ability to make correct predictions on data it hasn't seen (held-out test set or validation set).

**Standard ML metrics used:**

| Metric | What it measures | Good for |
|--------|-----------------|---------|
| Accuracy | % of all predictions that are correct | Balanced datasets |
| Precision | Of all predicted positives, how many are actually positive? | When false positives are costly (spam filter) |
| Recall (Sensitivity) | Of all actual positives, how many did the model find? | When false negatives are costly (medical diagnosis) |
| F1 Score | Harmonic mean of precision and recall | When you need a balance of both |
| AUC-ROC | Overall ability to distinguish classes | Binary classifiers |
| RMSE / MAE | Average prediction error | Regression models |

**The train/test/validation split:**
```
Full Dataset
    ↓
Training Set (70-80%) ──→ Model learns from this
Validation Set (10-15%) → Tune hyperparameters here
Test Set (10-15%) ──────→ Final evaluation — model never saw this
```

*Important:* The model must NEVER see the test set during training. Contaminating test data with training data is called **data leakage** and gives falsely optimistic results.

---

## 3. Metamorphic Testing

**What it is:** When you can't define the exact correct output (the oracle problem), you test *relationships between outputs for related inputs*.

**The concept:** Define a metamorphic relation — a rule about how the output should change when the input changes in a known way.

**Examples:**

| Domain | Metamorphic Relation |
|--------|---------------------|
| Image classifier | Rotating an image by 10° should not change the label from "cat" to "dog" |
| Sentiment analyser | Replacing "good" with "great" should not change positive sentiment to negative |
| Fraud detector | A transaction identical to a known legitimate one except the amount is slightly different should still be classified similarly |
| Translation system | Translating "Hello, how are you?" and "How are you, hello?" should give semantically equivalent translations |

**Why it works:** Even without knowing the exact correct answer, you know *relative* truths — these relationships must hold for a model that's working correctly.

---

## 4. Adversarial Testing

**What it is:** Deliberately creating inputs designed to confuse or fool the model — inputs that are slightly modified versions of normal inputs but cause the model to make wrong predictions.

**Why it's important:** AI models can be surprisingly fragile. A tiny, imperceptible change to an image can cause a neural network to misclassify completely.

*Classic example:* An image of a panda that looks identical to humans but has tiny pixel-level noise added causes an AI to classify it as a "gibbon" with 99% confidence. The model is vulnerable to adversarial attacks.

**In practice, adversarial testing covers:**
- **Robustness to noise:** Add Gaussian noise to images/audio — does the model still work?
- **Edge cases:** Provide extreme values, unusual combinations, boundary inputs
- **Adversarial examples:** Systematically crafted inputs to probe model weaknesses
- **Out-of-distribution inputs:** Inputs that are nothing like the training data — model should say "I don't know" rather than give confident wrong answers

**Real-world significance:** In an autonomous vehicle system, adversarial testing checks: can the model still correctly identify a stop sign if someone has stuck a small sticker on it? (Answer for some models before adversarial hardening: no.)

---

## 5. Fairness and Bias Testing

**What it is:** Evaluating whether the model's performance is equitable across different demographic or social groups.

**Why it matters:** A model with 90% overall accuracy might have 95% accuracy for one group and 70% for another — a significant disparity hidden by the aggregate number.

**Key fairness metrics:**

| Fairness Metric | What it means |
|----------------|---------------|
| Demographic Parity | Model makes positive predictions at the same rate for all groups |
| Equal Opportunity | Model has equal true positive rate (recall) for all groups |
| Predictive Parity | Precision is equal across groups |
| Individual Fairness | Similar individuals receive similar predictions |

**How to test:**
1. Identify sensitive attributes (gender, race, age, geography)
2. Slice your test dataset by these attributes
3. Evaluate all metrics *separately* for each slice
4. Flag and investigate significant disparities

**Example — AI Recruitment System (Q33):**
- Run the model on CVs from male and female candidates with equivalent qualifications
- Measure selection rate, precision, recall separately for each gender
- If male candidates are selected at twice the rate of equally qualified female candidates → bias confirmed → investigate training data and model

---

## 6. Performance Testing

**What it is:** Testing the model's response time, throughput, and scalability under realistic and peak load conditions.

**Why AI/ML performance testing is unique:**
- Model inference (making a prediction) can be computationally expensive
- Performance may degrade as batch sizes increase
- Real-time systems (fraud detection, autonomous driving) have strict latency requirements

**What to measure:**
- **Latency:** Time from input to prediction output (should be ms for real-time systems)
- **Throughput:** How many predictions per second can the model handle?
- **Scalability:** Does performance hold up when 10x more requests arrive?
- **Resource consumption:** CPU, GPU, memory usage during inference

*Example:* A banking fraud detection model must evaluate every transaction in under 100ms (before the transaction is processed). If it takes 2 seconds under peak load, it's operationally unusable.

---

## 7. Regression Testing for Models

**What it is:** After retraining or updating a model, verify that it hasn't gotten worse on previously good scenarios.

**The challenge:** Unlike traditional regression testing (re-run the same tests), model regression testing needs a curated **golden dataset** — a fixed set of inputs with known expected outputs (or expected score ranges) that represents important scenarios.

After every model update:
- Run the golden dataset
- Compare new model performance to the baseline
- Flag any regression in accuracy, fairness, or subgroup performance
- Investigate before deploying the new model

---

## 8. Testing for Model Drift (Production Monitoring)

**What it is:** Continuously monitoring deployed model performance using real production data.

**What to monitor:**
- **Prediction drift:** Is the distribution of model outputs shifting? (e.g., suddenly approving far more loans than usual)
- **Feature drift:** Are the input features shifting in distribution? (data drift)
- **Performance drift:** Is accuracy/precision/recall degrading over time?

**Tools used:** Evidently AI, WhyLogs, Fiddler — these generate automated drift reports.

*Example:* An e-commerce recommendation engine should monitor: Are users clicking on recommended products less than they used to? If yes, the model has drifted and needs retraining.

---

## Summary: Which Approach for Which Problem?

| Testing Need | Approach |
|-------------|---------|
| Is the training data good? | Data Validation Testing |
| Is the model accurate? | Model Evaluation Testing (metrics) |
| Is it fair for all groups? | Fairness/Bias Testing |
| Is it robust to noise and edge cases? | Adversarial Testing |
| Is it fast enough for production? | Performance Testing |
| Does it still work after updates? | Regression Testing |
| Is it still working months after deployment? | Drift Monitoring |
| Can't define exact correct output? | Metamorphic Testing |

---

## Quick Summary

- AI/ML testing needs multiple approaches — no single approach covers all quality dimensions
- Data validation must happen *before* model training
- Model evaluation uses statistical metrics (precision, recall, F1, AUC-ROC) not binary pass/fail
- Metamorphic testing solves the oracle problem by testing input-output relationships
- Adversarial testing probes model robustness against unexpected or manipulated inputs
- Fairness testing evaluates performance *per subgroup* to detect hidden bias
- Performance testing checks latency and throughput for real-time deployment readiness
- Drift monitoring in production is essential — testing doesn't end at deployment
