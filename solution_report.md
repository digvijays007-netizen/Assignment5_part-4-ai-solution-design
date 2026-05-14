# AI Solution Design: Insurance Claims Fraud Risk Detection

## Dataset source
Shared Google Drive folder: https://drive.google.com/drive/folders/1akV6po4Nrgkc3yQrJkzA6cJlV-wBvUYs?usp=sharing

## 1. Business domain
Insurance

## 2. Business problem
Insurance claim teams must review large volumes of claims and identify cases that may be fraudulent, inconsistent, or unusually risky. The users are claim handlers, fraud investigation teams, compliance teams, and operations leaders.

The current process is usually rule-based and manual. Analysts check claim forms, policy details, customer history, supporting documents, repair invoices, and past claim behavior. This is slow, inconsistent, and may miss complex fraud patterns that are not captured by simple rules.

## 3. AI task type
The recommended task type is **classification**, specifically fraud-risk classification. The model predicts whether a claim is low, medium, or high risk, or whether it is likely legitimate or suspicious. Classification is suitable because the output is a discrete decision category.

## 4. Data requirement plan
Required data includes claim amount, claim type, policy age, customer tenure, past claim count, incident location, time since policy purchase, repair/vendor details, customer profile attributes, document verification signals, and final investigation outcome.

The data is mostly structured, with possible unstructured attachments such as claim notes or documents. The target label can be `fraud_flag`, `risk_level`, or confirmed investigation outcome. Data can be collected from claims management systems, policy systems, CRM tools, document intake systems, and investigation records.

Data quality risks include missing values, inconsistent fraud labels, biased historical decisions, duplicate claims, outdated customer records, and leakage from fields created after investigation.

## 5. Model recommendation
A feed-forward neural network is recommended for structured claim features. It can learn non-linear relationships between policy, customer, claim, and behavioral variables. If claim notes are included, a transformer-based text model can be added to extract signals from unstructured descriptions.

## 6. Evaluation plan
Technical metrics: precision, recall, F1-score, ROC-AUC, confusion matrix, and calibration. Recall is important because missing fraudulent claims is costly. Precision is also important because false accusations create customer harm and operational burden.

Business metrics: reduction in manual review time, fraud detection uplift, investigation productivity, false-positive review rate, claim cycle time, and customer satisfaction.

Possible failure cases include false fraud flags for genuine customers, missed sophisticated fraud, biased predictions against specific customer groups, or model drift after fraud patterns change. High-risk predictions should go to human review before action.

## 7. Responsible AI considerations
The model may inherit bias from historical fraud investigations. Sensitive attributes should be carefully assessed, and proxy variables should be monitored. Incorrect predictions can delay valid claims or allow fraud to pass. Privacy controls are required because insurance data is sensitive. The system should support human oversight, explainability, audit trails, and periodic fairness/drift monitoring.

## 8. One-page final solution summary
**Problem:** Manual insurance claim fraud review is slow and inconsistent.

**Proposed AI solution:** Build a neural-network-based fraud risk scoring system that classifies claims by risk level and routes high-risk claims to specialist review.

**Required data:** Policy details, claim details, customer history, payment/repair information, claim notes, investigation outcomes, and quality-checked labels.

**Model recommendation:** Feed-forward neural network for structured features, with optional transformer text encoder for claim descriptions.

**Expected business impact:** Faster claim triage, better fraud detection, reduced manual workload, improved investigator focus, and more consistent decision-making.

**Risks and mitigation:** Use fairness testing, explainability, human review for high-risk outcomes, privacy controls, monitoring for model drift, and regular retraining with validated labels.

## Architecture diagram
See `diagrams/solution_architecture.png`.
