# Chapter 6: Real-Time Case Studies in AI/ML Testing

---

## Why Case Studies?

The question bank is almost 50% scenario-based questions. The same testing principles apply differently depending on the domain — healthcare has different risk tolerances than e-commerce. This chapter walks through the major domain scenarios in the question bank so you understand how to apply testing knowledge in context.

---

## Case Study 1: Healthcare AI Diagnosis System (Q9, Q26)

**The system:** An AI model that analyses patient symptoms, medical history, and lab results to suggest diagnoses or flag high-risk patients.

**Why testing is critical here:** An error can directly harm or kill a patient. The consequences of a false negative (missing a disease) are far more severe than in most other domains.

### Key Testing Considerations

**1. False Negatives are Dangerous**
- A false negative = the model says "patient is healthy" when they have cancer
- This is worse than a false positive (unnecessary further tests)
- Test with **high recall** as the primary metric: the model must find all actual positives, even at the cost of some false alarms

**2. Subgroup Performance**
- Test separately for different demographics: age, gender, ethnicity, weight, existing conditions
- Medical AI has historically been less accurate for women (trained on male-dominated datasets) and for certain ethnicities

**3. Data Privacy Compliance**
- All patient data used for testing must comply with data protection regulations (HIPAA in the US, local equivalents in India)
- Anonymisation must be tested — no PII should leak

**4. Edge Cases and Rare Conditions**
- Rare diseases are underrepresented in training data
- Specifically test for rare conditions — create synthetic minority-class examples if needed

**5. Integration Testing**
- The AI doesn't work alone — it integrates with hospital information systems, EHRs, PACS systems
- Test the full pipeline: data input → AI prediction → output to doctor interface

**6. Regulatory Compliance**
- Healthcare AI requires approval from regulatory bodies (equivalent of drug approval)
- Testing must generate documented evidence of performance, safety, and fairness

---

## Case Study 2: Banking Fraud Detection System (Q10, Q22, Q28)

**The system:** An AI model that analyses credit card or banking transactions in real-time and flags potential fraud.

**Core challenge:** Transactions happen in milliseconds. The model must respond within 100ms or the transaction is approved by default.

### Key Testing Considerations

**1. Class Imbalance**
- Fraud represents < 1% of all transactions
- A model that always predicts "not fraud" achieves 99%+ accuracy — completely useless
- Test with **precision and recall for the fraud class** specifically, not overall accuracy
- Use **AUC-ROC** to evaluate the model's ability to separate fraud from genuine transactions

**2. Static vs Dynamic Fraud Patterns (Q22)**
- **Static data patterns:** Fraud methods that are consistent (e.g., international transactions from blacklisted IPs)
- **Dynamic data patterns:** Fraud methods that constantly evolve (new social engineering tactics, money mules)
- *Testing challenge:* A model trained on static patterns will degrade as fraud patterns evolve. Need continuous monitoring + frequent retraining.

**3. Real-Time Performance**
- Load test the model API: can it handle peak transaction volume (e.g., Black Friday shopping) at < 100ms latency?
- Test failover: what happens if the ML model is unavailable? (Should default to rule-based fallback)

**4. Regulatory Compliance**
- Financial regulators require explainable decisions (GDPR "right to explanation")
- Test with explainability tools to ensure each fraud flag can be justified

**5. Adversarial Testing**
- Fraudsters actively try to evade detection by slightly modifying transaction patterns
- Adversarial testing simulates this: can a known fraud transaction evade detection with minor modifications?

---

## Case Study 3: Autonomous Vehicle System (Q12, Q27)

**The system:** AI that controls a self-driving car — object detection, path planning, real-time decision making.

**Stakes:** Errors directly cause accidents, injuries, and deaths.

### Key Testing Considerations

**1. Safety-Critical Edge Cases**
- Unusual road scenarios: construction zones, emergency vehicles, extreme weather
- The 99% average case is easy. The 1% edge cases determine safety.
- Use adversarial testing: partially occluded stop signs, unusual pedestrian behaviour

**2. Real-Time Decision Making**
- Latency must be in milliseconds — the car cannot "think" for 2 seconds before braking
- Performance testing under various compute loads (other vehicle systems running simultaneously)

**3. Simulation Testing**
- Exhaustively testing in real vehicles would take decades and cost billions
- Simulation environments (CARLA, SUMO) allow testing millions of scenarios including rare/dangerous ones
- Test whether simulation-to-real gap (sim2real) is acceptable

**4. Sensor Fusion Testing**
- Autonomous vehicles use multiple sensors: cameras, LiDAR, radar
- Test model behaviour when one sensor is degraded or fails
- Robustness: model should handle sensor noise without catastrophic failure

**5. Regulatory and Standards Compliance**
- ISO 26262 (functional safety for road vehicles) and ISO 21448 (Safety of the Intended Functionality — SOTIF)
- Extensive documented testing is required for regulatory approval

---

## Case Study 4: AI Chatbot / NLP System (Q14, Q20)

**The system:** An AI-powered customer service chatbot (like a banking assistant or e-commerce support bot).

### Key Testing Considerations

**1. Intent Recognition Testing**
- Test that the chatbot correctly identifies user intent across varied phrasings
- "What's my account balance?" / "Show me how much money I have" / "Balance check" → all same intent
- Use metamorphic testing: different phrasing → same intent classification

**2. Handling Out-of-Scope Queries**
- Test the bot's response to questions outside its domain
- Should gracefully say "I can't help with that" — not give wrong or hallucinated answers

**3. Edge Cases and Adversarial Inputs**
- What if the user types gibberish? Emojis? SQL injection attempts?
- What if the user is angry or uses offensive language?

**4. Contextual Continuity**
- In a multi-turn conversation, the bot should remember earlier messages
- Test: "Book a flight to Delhi" → "Change departure date to next Friday" → does it remember the earlier context?

**5. Language and Accent Variability**
- Test in multiple languages if the bot serves multilingual users
- Test regional dialects, slang, abbreviations

**6. Failure Recovery**
- If the bot misunderstands, does it offer to connect to a human agent?
- Test the escalation path: bot confidence below threshold → escalate to human

---

## Case Study 5: E-Commerce Recommendation Engine (Q29)

**The system:** An AI that recommends products to users based on browsing history, purchases, and preferences.

### Key Testing Considerations

**1. Relevance Testing**
- Test that recommendations are actually related to user interests
- Use precision@K metric: of the top K recommendations, how many did the user interact with?

**2. Diversity and Filter Bubble Testing**
- Recommending only similar items creates a filter bubble (user never discovers new categories)
- Test that recommendations have diversity beyond the user's immediate history

**3. Cold Start Problem**
- What does the system recommend to a brand new user with no history?
- Test the cold-start strategy: use popular items, demographic-based suggestions, etc.

**4. Bias Testing**
- Are high-margin products being recommended unfairly? (revenue bias)
- Are recommendations fair regardless of user demographics?

**5. Real-Time Performance**
- Recommendations must be generated quickly for good UX
- Test latency under peak load (sale events, new product launches)

---

## Case Study 6: AI-Based Recruitment System (Q33)

**The system:** AI that screens CVs and ranks candidates.

### Bias Testing Focus

This is almost entirely a fairness/bias testing scenario.

**1. Protected Attribute Testing**
- Remove gender, age, name (which may signal ethnicity) from test CVs
- Test: does removing these attributes change the ranking? If yes, the model has learned proxy biases.

**2. Counterfactual Testing**
- Create identical CVs differing only in one sensitive attribute (e.g., same qualification, one with female name, one with male name)
- Compare predictions — they should be identical or very close

**3. Historical Bias in Training Data**
- If the training data is "successful past hires", and past hires were historically biased, the model learns that bias
- Audit the training data for demographic imbalances

**4. Disparate Impact Analysis**
- Measure selection rate for each group
- A rule of thumb: if selection rate for one group is less than 80% of the highest-selected group → legal risk (the 4/5ths rule in US employment law)

---

## Case Study 7: IoT-Based Real-Time AI System (Q30)

**The system:** AI for predictive maintenance in a factory, smart grid management, or environmental monitoring.

### Key Testing Considerations

**1. Sensor Data Quality**
- Sensors fail, produce noise, or go offline
- Test model behaviour: missing sensor values, sudden spikes, gradual drift in baseline readings

**2. Real-Time Constraints**
- Decisions must happen within strict time windows
- A predictive maintenance alert arriving 10 minutes late is useless if the machine already failed

**3. Data Volume and Velocity**
- IoT systems generate massive data streams
- Performance test the full pipeline: ingestion → preprocessing → model inference → alert generation

**4. Concept Drift**
- Machine behaviour changes over time (wear and tear, seasonal variations)
- The model trained on "normal" data from 6 months ago may flag perfectly normal current behaviour as anomalous

---

## Quick Summary

| Domain | Primary Testing Concern | Key Metric |
|--------|------------------------|-----------|
| Healthcare AI | False negatives, subgroup fairness | Recall, per-subgroup accuracy |
| Fraud Detection | Class imbalance, evolving patterns, real-time performance | Precision/Recall for fraud class, latency |
| Autonomous Vehicles | Safety edge cases, sensor fusion, simulation | Coverage of rare scenarios |
| Chatbots/NLP | Intent accuracy, out-of-scope handling, context | Intent classification accuracy, escalation rate |
| E-commerce Recommendation | Relevance, diversity, cold start | Precision@K, diversity metrics |
| Recruitment AI | Bias, counterfactual fairness | Selection rate parity, counterfactual consistency |
| IoT AI | Sensor noise, real-time, concept drift | Latency, drift detection |
