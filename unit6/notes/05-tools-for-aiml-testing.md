# Chapter 5: Tools for AI/ML Testing

---

## Why Specialised Tools?

You wouldn't use a hammer to tighten a screw. Similarly, you can't use Selenium or JUnit to validate a machine learning model's fairness or detect data drift. AI/ML testing requires its own toolset.

These tools are grouped by what they test: data, models, fairness, or production monitoring.

---

## Category 1: Data Validation Tools

### Great Expectations
**What it does:** Defines and validates "expectations" (rules) about your data. Think of it as writing test cases for your dataset.

**How it works:**
- You define expectations like: "Column `age` should be between 0 and 120", "Column `email` should never be null", "Distribution of `fraud_label` should be between 1-3% positive"
- Run validations on new data batches
- Get pass/fail reports with detailed statistics

**Real example:** In a banking fraud detection pipeline, Great Expectations validates every new transaction batch before it's used for model retraining — ensuring no corrupted data enters the training loop.

### Pandas Profiling / ydata-profiling
**What it does:** Generates an automated HTML report summarising a dataset — distributions, missing values, correlations, outliers.

Useful for initial data exploration and catching obvious quality problems quickly.

---

## Category 2: Model Evaluation Frameworks

### TensorFlow Model Analysis (TFMA)
**What it does:** Evaluates TensorFlow models on large datasets with the ability to slice results by feature values.

**Key capability:** Slice-based evaluation — you can compute accuracy, precision, recall separately for each age group, gender, or geography. This is the foundation of bias detection in TF pipelines.

### Scikit-learn metrics module
For classical ML models, scikit-learn provides all standard evaluation metrics: `accuracy_score`, `precision_score`, `recall_score`, `f1_score`, `roc_auc_score`, `confusion_matrix`.

### MLflow
**What it does:** Tracks experiments — logs parameters, metrics, and model versions. Useful for comparing multiple model training runs.

**Testing relevance:** Lets you compare new model performance to baseline. If new model has lower recall on a critical subgroup → don't deploy.

---

## Category 3: Fairness and Bias Testing Tools

### Fairlearn (Microsoft)
**What it does:** Assesses and improves fairness in AI models.

**Key features:**
- Compute fairness metrics (demographic parity, equalized odds) across sensitive groups
- Provides a "fairness dashboard" to visualise disparities
- Offers mitigation algorithms to reduce bias

**Example use:** In a recruitment AI, Fairlearn can compare model performance for male vs female candidates and flag if the false negative rate is significantly higher for one group.

### IBM AI Fairness 360 (AIF360)
**What it does:** A comprehensive toolkit with 70+ fairness metrics and 11 bias mitigation algorithms.

Useful for thorough fairness audits in regulated industries.

### What-If Tool (Google)
**What it does:** A visual interface for exploring model behaviour across different inputs and subgroups without writing code.

Allows testers to manually probe the model: "What if this loan applicant was female instead of male — would the decision change?"

---

## Category 4: Adversarial Testing Tools

### CleverHans
An open-source library for benchmarking AI models against adversarial attacks. Generates adversarial examples (slightly modified inputs designed to fool the model).

### Foolbox
A Python toolbox to create adversarial examples for neural networks. Supports many different attack methods (FGSM, PGD, etc.).

**Use case:** Testing an autonomous vehicle's object detection model — use Foolbox to generate adversarially perturbed images of stop signs and check if the model still classifies them correctly.

---

## Category 5: Performance Testing Tools

### Locust / Apache JMeter
Traditional load testing tools adapted for model serving endpoints.

**How:** Make HTTP requests to the model's prediction API endpoint. Simulate thousands of concurrent users. Measure response time and throughput.

**Example:** Test a fraud detection REST API: can it handle 10,000 transactions per second while keeping response time under 50ms?

### NVIDIA Triton Inference Server Benchmarking
For models deployed on GPU, Triton provides performance benchmarking — measures GPU utilisation, batching efficiency, and latency.

---

## Category 6: Production Monitoring and Drift Detection Tools

### Evidently AI
**What it does:** Generates automated data and model quality reports. Detects data drift, prediction drift, and data quality issues in production.

**How it works:**
- Compare reference dataset (training data) against production data
- Generate visual drift reports
- Integrate with CI/CD pipelines for automated monitoring

**Example:** E-commerce recommendation engine — Evidently monitors weekly whether the feature distributions of user clickstream data have drifted from the training data. Alerts when drift exceeds a threshold.

### WhyLogs
Lightweight data logging library for ML pipelines. Logs statistical summaries of data at every stage — useful for debugging where in the pipeline data quality degraded.

### Fiddler AI
Enterprise-grade model monitoring platform. Tracks model performance, fairness, and explainability in production with dashboards and alerts.

---

## Tool Summary Table

| Tool | Category | Primary Use | Open Source? |
|------|----------|-------------|-------------|
| Great Expectations | Data Validation | Define and run data quality rules | ✅ Yes |
| ydata-profiling | Data Validation | Automated data quality reports | ✅ Yes |
| TFMA | Model Evaluation | Slice-based model evaluation | ✅ Yes |
| MLflow | Model Tracking | Experiment tracking, model registry | ✅ Yes |
| Scikit-learn metrics | Model Evaluation | Standard ML metrics | ✅ Yes |
| Fairlearn | Fairness | Fairness metrics + mitigation | ✅ Yes |
| AIF360 | Fairness | Comprehensive bias detection | ✅ Yes |
| What-If Tool | Fairness | Visual model exploration | ✅ Yes |
| CleverHans | Adversarial | Adversarial example generation | ✅ Yes |
| Foolbox | Adversarial | Adversarial attacks on neural nets | ✅ Yes |
| Evidently AI | Production Monitoring | Drift detection, data quality | ✅ Yes |
| WhyLogs | Production Monitoring | Statistical data logging | ✅ Yes |
| Fiddler AI | Production Monitoring | Enterprise model monitoring | ❌ Commercial |
| JMeter | Performance | Load testing model API | ✅ Yes |

---

## Quick Summary

- AI/ML testing has a dedicated toolset covering data validation, model evaluation, fairness, adversarial testing, and production monitoring
- Great Expectations validates data quality before training
- TF Model Analysis and Fairlearn are key for bias/fairness evaluation
- Evidently AI and WhyLogs handle production drift monitoring
- Traditional performance tools (JMeter, Locust) still apply for model serving APIs
- Most important tools are open-source and widely used in the industry
