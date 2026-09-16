# Project 4 — FactoryGuard AI
## Predictive Quality & Production Intelligence Platform

**Structure:** ps-01  
**Progression:** CP1 — ML Product → CP2 — Application + Container → CP3 — Cloud + Operations → CP4 — AI Enhancement

---

# 1. Overall Product Specification

## Objective

Build an end-to-end industrial quality intelligence platform that predicts rare production failures, identifies sensor/process risk, explains predictions, and evolves into an AI-enabled manufacturing operations copilot.

## Core business problems

- Predict production-line failures before they occur.
- Identify high-risk production conditions.
- Handle highly imbalanced failure data.
- Detect sensor/process anomalies.
- Explain why a production event is considered risky.
- Support proactive quality decisions.
- Provide evidence-backed operational guidance.

## Core ML problems

1. Rare-event failure classification.
2. Production-risk scoring.
3. Sensor/process anomaly detection.
4. Optional defect/root-cause analysis.

## Example KPIs

| Area | KPI |
|---|---|
| Failure prediction | Precision / Recall / F1 |
| Rare-event detection | PR-AUC |
| Risk ranking | Recall@K / Precision@K |
| False negatives | Missed-failure rate |
| Data | Data-quality pass rate |
| Application | API latency / error rate |
| Operations | Drift / retraining rate |
| AI | Retrieval quality / groundedness |
| Business | Prevented-failure opportunity |

---

# 2. Overall Architecture

```text
Manufacturing Production Data
        +
Sensor / Process Features
        +
Production Context
        |
        v
Data Ingestion
        |
        v
Data Quality & Validation
        |
        v
Lakehouse
Raw → Bronze → Silver → Gold
        |
        v
SQL / Analytical Data Model
        |
        v
EDA + Feature Engineering
        |
        v
Failure Prediction
+ Anomaly Detection
+ Explainability
        |
        +------------------+
        |                  |
        v                  v
     FastAPI            Dashboard
        |
        v
      Docker
        |
        v
   CI/CD + MLOps
        |
        v
 AWS Cloud + Monitoring
        |
        v
Manufacturing AI Copilot
LLM + RAG + Agents + MCP
        |
        v
Guardrails + Human Approval + Audit
```

---

# 3. CP1 — ML Product

### Specification

Build the first working **production-failure prediction and quality intelligence product**.

### Five-point scope

1. **Architecture & Specification**
   - Define manufacturing-quality problem, prediction target, users and KPIs.
   - Understand the high-dimensional production-data architecture.
   - Create production-ready Git repository structure.

2. **Data Engineering & EDA**
   - Acquire and process the Bosch Production Line Performance dataset.
   - Profile missingness, cardinality, class imbalance and sensor/process behaviour.
   - Build an initial analytical dataset and identify important production patterns.

3. **Dashboard**
   - Failure-rate analysis.
   - Missing-value patterns.
   - Feature distributions.
   - Production/sensor behaviour.
   - High-risk observations.
   - Model explanations.

4. **ML Models**
   - Engineer numerical, missingness and interaction features.
   - Build baseline classification models.
   - Handle severe class imbalance.
   - Optimize classification thresholds.
   - Add explainability.

5. **Evaluation & Deliverables**
   - Use suitable validation strategy.
   - Evaluate Precision, Recall, F1, PR-AUC and confusion matrix.
   - Analyze false positives and false negatives.
   - Produce model artifacts and quality insights.

### CP1 Deliverables

```text
01 Architecture
02 Project Specification
03 Git Repository
04 Data Acquisition Scripts
05 Integrated Dataset
06 EDA Report
07 Feature Engineering
08 Failure-Prediction Models
09 Imbalance Analysis
10 Threshold Analysis
11 Explainability Report
12 Evaluation Report
13 Dashboard
14 Model Artifacts
```

**CP1 Exit:** Working ML-based **production-failure prediction product**.

---

# 4. CP2 — Application + Container

### Specification

Convert the ML solution into a **reproducible, tested and deployable manufacturing application**.

### Five-point scope

1. **Enhanced Data Pipeline**
   - Identify additional useful production/context data.
   - Build:
     `Raw → Validation → Transformation → Curated Parquet`
   - Use Python + SQL.

2. **Data & Model Engineering**
   - Automated data-quality checks.
   - Missingness validation.
   - Reproducible feature generation.
   - Dataset/model versioning.
   - Risk-score generation.

3. **FastAPI Application**
   - `/predict-failure`
   - `/risk-score`
   - `/explain`
   - `/health`
   - `/ready`
   - Request/response schemas and API documentation.

4. **Container + UI**
   - Build quick Streamlit/React UI.
   - Dockerize the application.
   - Run the complete system locally.

5. **MLOps**
   - Unit/integration tests.
   - Git workflow.
   - CI/CD.
   - Dependency/security checks.
   - Model/data versioning.

### CP2 Deliverables

```text
01 Updated Architecture
02 Additional Data Sources
03 Python/SQL Pipeline
04 Curated Parquet Tables
05 Data Validation
06 Feature Pipeline
07 Versioned Model
08 FastAPI Application
09 API Documentation
10 Quick UI
11 Dockerfile
12 Test Suite
13 CI/CD Pipeline
14 Local Deployment
```

**CP2 Exit:** Containerized **manufacturing quality prediction application**.

---

# 5. CP3 — Cloud + Operations

### Specification

Transform the local application into a **production-oriented cloud ML system**.

### Five-point scope

1. **Triggers & Automation**
   - Define production-data, scheduled and model-performance triggers.
   - Design Airflow:
     `Ingest → Validate → Transform → Features → Train → Evaluate → Register`.

2. **Production ML Operations**
   - Model registry.
   - Model approval.
   - Retraining conditions.
   - Batch and real-time inference.
   - Production-risk scoring.

3. **Telemetry & Reliability**
   - Application logs.
   - API latency/error metrics.
   - Prediction monitoring.
   - Data drift.
   - Model drift.
   - Failure-rate/business KPI monitoring.

4. **Safe Model Rollout**
   - Candidate model validation.
   - Shadow/canary deployment.
   - Rollback conditions.
   - Model version traceability.
   - False-negative monitoring after deployment.

5. **AWS Transfer**
   - Map local architecture to AWS.
   - Deploy containers and pipelines.
   - Configure storage, CI/CD and monitoring.
   - Document operational procedures.

### CP3 Deliverables

```text
01 Cloud Architecture
02 Trigger Specification
03 Airflow DAG
04 Automated ML Pipeline
05 Model Registry
06 CI/CD
07 Telemetry Design
08 Logs + Metrics
09 Serving Design
10 Rollout Strategy
11 Rollback Strategy
12 AWS Architecture
13 AWS Deployment
14 Monitoring Dashboard
15 Operations Runbook
```

**CP3 Exit:** **Cloud-ready production manufacturing ML platform**.

---

# 6. CP4 — AI Enhancement

### Specification

Transform FactoryGuard into an **AI-enabled Manufacturing Quality & Operations Copilot**.

### Five-point scope

1. **AI Product Specification**
   - Define quality engineers, production managers and operations users.
   - Define AI capabilities, tools and permissions.
   - Define guardrails and human approval points.

2. **Knowledge Base + RAG**
   - Quality procedures.
   - Manufacturing SOPs.
   - Inspection procedures.
   - Maintenance procedures.
   - Failure-handling guidelines.
   - Implement ingestion → chunking → embeddings → retrieval → LLM with citations.

3. **RAG Evaluation**
   - Build a manufacturing question/evidence evaluation set.
   - Evaluate retrieval quality, relevance, groundedness, answer quality and citations.
   - Include abstention and unsupported-answer tests.

4. **Multi-Agent System**
   ```text
   User
     ↓
   Supervisor Agent
     ├── Failure Agent
     ├── Sensor/Data Agent
     ├── Root-Cause Agent
     ├── Knowledge Agent
     └── Quality Analyst
             ↓
        Final Response
   ```

5. **Production AI Demonstration**
   - Guardrails.
   - Human approval.
   - Audit trail.
   - AI Copilot UI.
   - Agent workflow.
   - Local/cloud deployment.

### CP4 Deliverables

```text
01 AI Product Specification
02 Knowledge Base Architecture
03 Document Ingestion Pipeline
04 RAG Application
05 RAG Evaluation Dataset
06 RAG Evaluation Report
07 LLM Application
08 Tool Definitions
09 Multi-Agent Architecture
10 Agent Workflow
11 Guardrails
12 Human Approval
13 AI Copilot UI
14 Agent Demonstration
15 Local/Cloud Deployment
16 Final Architecture
17 Technical + Business Presentation
```

**CP4 Exit:** AI-enabled **Manufacturing Quality & Operations Copilot**.

---

# 7. Dataset Specification

The project should combine the core manufacturing dataset with carefully selected contextual sources where useful.

## Dataset 1 — Bosch Production Line Performance

**Role:** Primary production-failure prediction dataset.

The Bosch Production Line Performance dataset contains more than one million training observations, hundreds of anonymized features and a highly imbalanced binary response indicating whether a manufacturing process failed.

**Public source:**  
https://www.kaggle.com/competitions/bosch-production-line-performance/data

### Dataset characteristics

```text
train_numeric.csv
train_categorical.csv
train_date.csv
test_numeric.csv
test_categorical.csv
test_date.csv
```

### Important concepts

```text
Id
L#_S#_F#
Response
```

Where the anonymized feature naming represents line/station/feature relationships.

### Primary ML target

```text
Response
```

### Key challenges

```text
High dimensionality
Missing values
Anonymized variables
Severe class imbalance
Potential temporal/process structure
Large data volume
```

---

# 8. Dataset 2 — NASA C-MAPSS

**Role:** Optional secondary dataset for predictive-maintenance comparison.

NASA's Prognostics Center of Excellence provides the C-MAPSS turbofan engine degradation datasets, which are widely used for remaining-useful-life and predictive-maintenance research.

**Public source:**  
https://www.nasa.gov/intelligent-systems-division/discovery-and-systems-health/

### Potential variables

```text
unit
cycle
operational_setting
sensor_measurements
```

### Optional use

Use C-MAPSS as a **separate predictive-maintenance experiment**, not as a direct row-level join with Bosch.

Students can compare:

```text
Bosch → Rare-event classification
C-MAPSS → Degradation / RUL prediction
```

This demonstrates transfer of ML engineering techniques across industrial domains.

---

# 9. Dataset 3 — UCI SECOM

**Role:** Secondary semiconductor manufacturing quality dataset.

The UCI Machine Learning Repository provides the SECOM dataset, containing semiconductor manufacturing process measurements and a binary pass/fail target.

**Public source:**  
https://archive.ics.uci.edu/dataset/179/secom

### Useful characteristics

```text
sensor/process measurements
missing values
high-dimensional features
pass/fail target
```

### Optional use

Use SECOM for:

- Imbalance analysis.
- Feature selection.
- Explainability.
- Model robustness.
- Cross-dataset experimentation.

Again, treat it as a **separate industrial ML dataset**, not a direct join with Bosch.

---

# 10. Dataset 4 — Public Weather / Environmental Context

**Role:** Optional environmental enrichment for manufacturing experiments where a facility/location is explicitly associated with production observations.

**NOAA Climate Data Online:**  
https://www.ncei.noaa.gov/cdo-web/

Potential variables:

```text
temperature
humidity
precipitation
wind
pressure
```

Use only when a defensible facility/date mapping exists. Do not invent a geographical relationship for anonymized Bosch observations.

---

# 11. Recommended Dataset Combination

Because Bosch, C-MAPSS and SECOM have different schemas and grains, the preferred design is **multi-dataset experimentation**, rather than forcing all datasets into one fact table.

| Dataset | Role | Integration approach |
|---|---|---|
| **Bosch** | Primary rare-event production ML | Main project |
| **SECOM** | Semiconductor quality comparison | Separate model/data domain |
| **NASA C-MAPSS** | Predictive maintenance | Separate experiment |
| **NOAA Weather** | Optional environmental context | Join only when geography/time are defensible |

### Recommended architecture

```text
                 Bosch
                   |
                   v
        Primary Manufacturing
             ML Pipeline
                   |
          ┌────────┴────────┐
          |                 |
          v                 v
      Failure ML       Explainability
          |
          v
   Production Product

SECOM ----------------→ Secondary ML Experiment
C-MAPSS --------------→ Predictive Maintenance Experiment
NOAA -----------------→ Optional Context
```

This avoids artificial joins while still giving students a meaningful **data-engineering and multi-dataset integration challenge**.

---

# 12. Lakehouse Structure

```text
data/
│
├── raw/
│   ├── bosch/
│   ├── secom/
│   ├── cmapss/
│   └── weather/
│
├── bronze/
│   ├── bosch_numeric/
│   ├── bosch_categorical/
│   ├── bosch_date/
│   ├── secom/
│   ├── cmapss/
│   └── weather/
│
├── silver/
│   ├── bosch_clean/
│   ├── secom_clean/
│   ├── cmapss_clean/
│   └── weather_clean/
│
└── gold/
    ├── failure_features/
    ├── risk_scores/
    ├── anomaly_features/
    ├── model_predictions/
    └── model_metrics/
```

---

# 13. Recommended SQL/Data Model

```text
dim_process
dim_station
dim_feature
dim_time
dim_dataset

fact_production_observation
fact_sensor_measurement
fact_failure_event
fact_weather

feature_failure_risk
feature_anomaly
prediction_failure
prediction_risk
model_metrics
```

### Main analytical feature table

```text
observation_id
timestamp
line_id
station_id

feature_count
missing_feature_count
missing_feature_ratio

sensor_features
process_features

rolling_statistics
interaction_features

failure_history
station_failure_rate
feature_missingness_rate

failure_target
risk_score
```

For anonymized datasets, retain the original feature identifiers and document any feature-group interpretation instead of inventing business meanings.

---

# 14. ML Progression

Students should progress from simple baselines to imbalance-aware production models:

```text
Rule-Based Baseline
       ↓
Logistic Regression
       ↓
Random Forest
       ↓
XGBoost / LightGBM
       ↓
Class Weighting
       ↓
Sampling / Imbalance Strategies
       ↓
Threshold Optimization
       ↓
Explainability
       ↓
Production Model
```

### Classification metrics

```text
Precision
Recall
F1
PR-AUC
ROC-AUC
Confusion Matrix
False-Negative Rate
```

### Critical industrial consideration

Accuracy should **not** be the primary metric for a severely imbalanced failure-prediction problem.

Students should explicitly investigate:

```text
False Positive Cost
        vs
False Negative Cost
```

and select an operating threshold accordingly.

---

# 15. Explainability

Required techniques may include:

```text
Feature Importance
SHAP
Local Explanation
Global Explanation
Error Analysis
Threshold Analysis
```

Example:

```text
Prediction:
HIGH FAILURE RISK

Evidence:
- Feature group A unusually high
- Missingness pattern detected
- Process feature B outside normal range

Risk:
0.87

Model:
Version 1.4

Action:
Escalate for human quality review
```

The system should distinguish model evidence from operational recommendations.

---

# 16. Final Product

By Day 27 the student should demonstrate:

```text
Bosch Manufacturing Data
        +
Optional Industrial Datasets
        ↓
Data Engineering
        ↓
Validated Lakehouse
        ↓
SQL Data Model
        ↓
EDA + Dashboard
        ↓
Rare-Event ML
        ↓
Failure Risk Prediction
        ↓
Explainability
        ↓
FastAPI
        ↓
Docker
        ↓
CI/CD
        ↓
Airflow
        ↓
MLOps
        ↓
AWS
        ↓
RAG
        ↓
LLM
        ↓
Multi-Agent System
        ↓
MCP
        ↓
Guardrails
        ↓
AI Manufacturing Copilot
```

## Final demonstration scenario

**User:**

> "Why is this production observation considered high risk, what evidence supports the prediction, and which approved procedure should the quality engineer review?"

The system should combine:

- **Failure Agent** → ML risk prediction.
- **Data Agent** → production/sensor evidence.
- **Root-Cause Agent** → interprets relevant model signals.
- **Knowledge Agent** → retrieves approved procedures through RAG.
- **Quality Analyst** → synthesizes evidence.
- **Supervisor Agent** → orchestrates and validates the response.

The final response should provide **model evidence, confidence/uncertainty, relevant procedure citations and human approval**, rather than autonomously changing production settings.

---

# 17. Engineering Spine

FactoryGuard follows the same **ps-01 engineering spine**:

## Layer 1 — Data Engineering + ML

```text
Sources
→ Ingestion
→ Data Quality
→ Lakehouse
→ SQL/Data Model
→ EDA
→ Features
→ ML/DL
→ Evaluation
→ Model Artifact
```

## Layer 2 — Production AI Engineering

```text
Model Registry
→ FastAPI
→ Tests
→ Docker
→ CI/CD
→ Security Scan
→ Deployment
→ Observability
→ Monitoring
→ Drift
→ Retraining/Rollback
```

## Layer 3 — AI Engineering

```text
LLM
→ Structured Output
→ RAG
→ Retrieval Evaluation
→ Tools
→ Agent
→ MCP
→ Guardrails
→ Human Approval
→ LLMOps
```

## Business Product

```text
Dashboard
+ APIs
+ AI Copilot
+ Failure Alerts
+ Risk Scores
+ Agent
+ Audit Trail
+ Runbook
```

## CP progression

**CP1:** Build the **ML product**  
↓  
**CP2:** Build the **application + container**  
↓  
**CP3:** Transfer it to **cloud + operations**  
↓  
**CP4:** Enhance it with **RAG + LLM + multi-agent AI**
