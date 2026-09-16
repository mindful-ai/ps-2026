# Project 3 --- MediSphere

## Healthcare Intelligence & AI Copilot

### Capstone Structure: ps-01

------------------------------------------------------------------------

# 1. Project Overview

## Objective

Build an end-to-end healthcare intelligence platform that progressively
evolves from data engineering and ML into a cloud-operated, AI-enabled
healthcare copilot.

The project follows:

**ML → Application + Container → Cloud → Enhance with AI**

## Business Problem

Healthcare organizations generate large volumes of clinical, operational
and patient data. A useful intelligence platform should help authorized
users understand:

-   Patient risk
-   Hospital readmission risk
-   Length of stay
-   Clinical and operational trends
-   Resource utilization
-   Patient cohorts
-   Anomalous patterns
-   Relevant clinical knowledge and procedures

MediSphere combines these capabilities while emphasizing privacy,
safety, explainability and human oversight.

## Core ML Problems

1.  **Readmission Risk Prediction**
    -   Predict risk of readmission
    -   Identify high-risk patient cohorts
    -   Support care-management prioritization
2.  **Length-of-Stay Prediction**
    -   Predict expected hospital stay
    -   Identify operational/resource requirements
3.  **Patient Risk Stratification**
    -   Segment patients using clinical/operational features
    -   Identify cohorts requiring additional attention
4.  **Clinical/Operational Anomaly Detection**
    -   Detect unusual utilization patterns
    -   Identify abnormal operational trends
5.  **Optional Outcome Prediction**
    -   Mortality-risk research task
    -   Complication-risk research task
    -   Use only with appropriate safeguards and clearly defined target
        populations

------------------------------------------------------------------------

# 2. Overall Architecture

``` text
EHR / Clinical Dataset
        +
Hospital Operations Data
        +
Patient Demographics
        +
Public Health / Context Data
        +
Clinical Guidelines / Policies
        ↓
Data Ingestion
        ↓
Data Quality & Validation
        ↓
Lakehouse
        ↓
SQL Data Model
        ↓
EDA & Feature Engineering
        ↓
ML Models
        ↓
Evaluation
        ↓
Model Registry
        ↓
Dashboard + FastAPI
        ↓
Docker
        ↓
CI/CD
        ↓
Cloud / AWS
        ↓
MLOps + Monitoring
        ↓
LLM
        ↓
Healthcare Knowledge Base
        ↓
RAG
        ↓
Multi-Agent System
        ↓
MCP + Guardrails
        ↓
Human / Clinical Approval
        ↓
MEDISPHERE
HEALTHCARE AI COPILOT
```

------------------------------------------------------------------------

# 3. Common Engineering Spine

## Layer 1 --- Data Engineering & ML

``` text
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

## Layer 2 --- Production AI Engineering

``` text
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

## Layer 3 --- AI Engineering

``` text
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

``` text
Healthcare Dashboard
+
Risk APIs
+
Patient Cohort Analytics
+
Operational Alerts
+
AI Copilot
+
Agents
+
Evidence Retrieval
+
Audit Trail
+
Operations Runbook
```

------------------------------------------------------------------------

# CP1 --- ML Product

## 1. Architecture & Specification

Students define:

-   Healthcare business problem
-   Authorized user personas
-   Patient/population scope
-   Functional requirements
-   Non-functional requirements
-   Privacy/security assumptions
-   ML target definitions
-   Data architecture
-   Dashboard requirements
-   API requirements
-   Evaluation and safety strategy

### Required architecture

``` text
Healthcare Sources
→ Ingestion
→ Validation
→ Lakehouse
→ SQL Model
→ Features
→ ML
→ Dashboard
```

### Target users

-   Clinical analysts
-   Care-management teams
-   Hospital operations teams
-   Data scientists
-   Healthcare executives

### Deliverables

-   Project specification
-   Architecture diagram
-   Data dictionary
-   Git repository
-   Initial API specification
-   Privacy/security assumptions
-   Model-risk assumptions

------------------------------------------------------------------------

## 2. Data Engineering & EDA

### Recommended primary dataset

**MIMIC-IV**

Source:

https://physionet.org/content/mimiciv/

MIMIC-IV is a de-identified electronic health-record dataset. Access
requires following the dataset's credentialing and data-use
requirements.

### Alternative for students needing simpler access

**UCI Diabetes 130-US Hospitals for Years 1999--2008**

Source:

https://archive.ics.uci.edu/dataset/296/diabetes+130+us+hospitals+for+years+1999+2008

This dataset can be used for readmission-risk modeling and healthcare
data-engineering exercises.

### Recommended project strategy

Use **one primary clinical dataset** for the main capstone and use other
public datasets as separate experiments unless a valid
patient/time/geographic join exists.

### Data-engineering pipeline

``` text
Raw Clinical Data
→ Schema Validation
→ De-identification/Privacy Review
→ Data Cleaning
→ Missingness Analysis
→ Code/Category Normalization
→ Feature Construction
→ Bronze
→ Silver
→ Gold
```

### EDA

Analyze:

-   Patient population
-   Admission patterns
-   Diagnoses
-   Procedures
-   Medication/utilization patterns where available
-   Length of stay
-   Readmission
-   Age distributions
-   Missingness
-   Outliers
-   Class imbalance
-   Temporal patterns

### Important healthcare rule

Do not use information that would not have been available at the
prediction time.

Explicitly define:

``` text
Index Time
→ Observation Window
→ Prediction Time
→ Outcome Window
```

This prevents temporal leakage.

### Deliverables

-   Data acquisition/access instructions
-   Data-quality report
-   EDA notebook/report
-   Feature engineering pipeline
-   Curated Parquet datasets
-   Target-definition document

------------------------------------------------------------------------

## 3. Dashboard

Build a healthcare intelligence dashboard.

### Required views

1.  Population overview
2.  Readmission-risk distribution
3.  Length-of-stay analysis
4.  Patient cohort analysis
5.  Operational utilization
6.  Model performance
7.  Explainability
8.  Data-quality monitoring

### Example patient/cohort view

``` text
Patient/Cohort
      ↓
Clinical/Operational Profile
      ↓
Risk Score
      ↓
Important Factors
      ↓
Historical Pattern
      ↓
Relevant Knowledge
      ↓
Recommended Review
```

### Suggested technologies

-   Streamlit
-   Plotly
-   Pandas
-   SQL/DuckDB

------------------------------------------------------------------------

## 4. ML Model

### Readmission-risk progression

``` text
Clinical Baseline
→ Logistic Regression
→ Random Forest
→ XGBoost / LightGBM
→ Class Weighting
→ Threshold Optimization
→ Calibration
→ Explainability
→ Production Model
```

### Length-of-stay progression

``` text
Mean/Median Baseline
→ Linear Regression
→ Random Forest Regressor
→ Gradient Boosting
→ XGBoost / LightGBM
→ Production Model
```

### Patient segmentation

``` text
Feature Engineering
→ Standardization
→ K-Means
→ Hierarchical Clustering
→ Cohort Profiling
```

### Anomaly detection

``` text
Statistical Baseline
→ Isolation Forest
→ Local Outlier Factor
→ Advanced Detector
```

### Explainability

Use:

-   Feature importance
-   SHAP
-   Local explanations
-   Cohort-level error analysis
-   Calibration analysis

Do not present model explanations as clinical causal conclusions.

------------------------------------------------------------------------

## 5. Evaluation & Deliverables

### Classification metrics

-   ROC-AUC
-   PR-AUC
-   Precision
-   Recall
-   F1
-   Confusion matrix
-   Calibration
-   False-negative rate

### Regression metrics

-   MAE
-   RMSE
-   Median absolute error
-   Error by patient/cohort segment

### Healthcare-specific evaluation

Evaluate performance across relevant subgroups when the dataset permits:

-   Age groups
-   Sex
-   Clinical cohorts
-   Other available demographic/clinical groups

Document limitations and avoid unsupported claims about clinical
effectiveness.

### Required deliverables

-   Model comparison
-   Error analysis
-   Explainability report
-   Threshold analysis
-   Cohort analysis
-   Evaluation report
-   Dashboard
-   Model artifact
-   Safety/limitations document

### CP1 Exit Criteria

A working healthcare ML analytics product that predicts defined outcomes
and provides transparent population-level insights without presenting
predictions as autonomous clinical decisions.

------------------------------------------------------------------------

# CP2 --- Application + Container

## 1. Enhanced Data Pipeline

Extend CP1 into a reproducible healthcare data platform.

### Requirements

-   Automated ingestion
-   Incremental processing
-   Schema validation
-   Data-quality checks
-   Referential-integrity checks
-   Missingness monitoring
-   Temporal consistency checks
-   Bronze/Silver/Gold layers
-   SQL transformations
-   Feature generation

### Suggested technologies

-   Python
-   SQL
-   Pandas / Polars
-   PyArrow
-   DuckDB
-   Great Expectations or equivalent

### Deliverables

-   Automated pipeline
-   Validation framework
-   Curated Parquet
-   SQL transformations
-   Data-quality report
-   Data-lineage documentation

------------------------------------------------------------------------

## 2. Data & Model Engineering

Implement:

-   Reproducible features
-   Feature versioning
-   Model versioning
-   Experiment tracking
-   Configuration management
-   Model artifact storage
-   Evaluation pipeline
-   Dataset/version lineage

### Required model metadata

``` text
Model Version
Training Dataset
Feature Version
Target Definition
Prediction Time
Evaluation Dataset
Threshold
Validation Results
Known Limitations
```

------------------------------------------------------------------------

## 3. FastAPI Application

Expose healthcare analytics through APIs.

### Example endpoints

``` text
GET  /health
GET  /metadata

POST /readmission-risk
POST /length-of-stay
POST /patient-segment
POST /anomaly-score

GET  /patient/{patient_id}
GET  /cohort/{cohort_id}

GET  /model-info
GET  /metrics
```

### Example request

``` json
{
  "patient_id": "PATIENT001",
  "prediction_time": "2026-01-15T10:00:00"
}
```

### API requirements

-   Pydantic validation
-   Structured responses
-   Error handling
-   Authentication/authorization-ready architecture
-   Logging
-   OpenAPI documentation
-   Unit tests
-   Integration tests

### Safety requirement

The API must clearly distinguish:

``` text
Prediction
≠
Diagnosis
≠
Clinical Decision
```

------------------------------------------------------------------------

## 4. Container + UI

Containerize:

``` text
FastAPI
+
ML Models
+
Feature Pipeline
+
Configuration
```

### UI architecture

``` text
Healthcare Dashboard
        ↓
FastAPI
        ↓
Feature Layer
        ↓
ML Models
        ↓
Risk / Forecast / Anomaly Results
```

The UI should communicate through APIs rather than directly invoking
model functions.

### Deliverables

-   Dockerfile
-   Docker Compose where appropriate
-   Containerized application
-   API documentation
-   Dashboard connected to API

------------------------------------------------------------------------

## 5. MLOps

Implement:

-   Automated tests
-   Linting
-   CI pipeline
-   Model validation
-   Reproducible training
-   Artifact versioning
-   Dependency management
-   Security scanning
-   Configuration management
-   Model documentation

### CP2 Exit Criteria

A reproducible, tested and containerized healthcare analytics
application with APIs and dashboard.

------------------------------------------------------------------------

# CP3 --- Cloud + Operations

## 1. Triggers & Automation

Automate:

-   New data ingestion
-   Data validation
-   Feature generation
-   Batch risk scoring
-   Anomaly detection
-   Model training
-   Model evaluation
-   Report generation
-   Alert generation

### Example workflow

``` text
Schedule / Event
→ Ingest
→ Validate
→ Transform
→ Feature Generation
→ Predict
→ Validate Results
→ Store Results
→ Update Dashboard
→ Alert if Required
```

### Suggested orchestration

-   Apache Airflow
-   AWS scheduling/event services
-   Python jobs

------------------------------------------------------------------------

## 2. Production ML Operations

Implement:

-   Model registry
-   Model versions
-   Training pipeline
-   Evaluation gate
-   Deployment pipeline
-   Retraining strategy
-   Rollback strategy
-   Model documentation

### Model promotion

``` text
Candidate Model
→ Validation
→ Performance Comparison
→ Subgroup Analysis
→ Safety Review
→ Approval Gate
→ Production
```

A model should not automatically become production simply because it has
a higher aggregate metric.

------------------------------------------------------------------------

## 3. Telemetry & Reliability

Monitor:

### Application

-   API latency
-   Request rate
-   Error rate
-   Availability

### Data

-   Data freshness
-   Missingness
-   Schema changes
-   Referential integrity
-   Distribution drift
-   Temporal consistency

### Model

-   Performance
-   Prediction drift
-   Feature drift
-   Calibration drift
-   Subgroup performance
-   Error rates

### Healthcare operations

-   High-risk case volume
-   Alert volume
-   False-alert rate
-   Review queue
-   Time to review

### Deliverables

-   Monitoring design
-   Logs
-   Metrics
-   Alerts
-   Monitoring dashboard
-   Incident-response process

------------------------------------------------------------------------

## 4. Safe Model Rollout

Implement:

-   Champion/challenger
-   Shadow deployment
-   Canary deployment where practical
-   Versioned model artifacts
-   Rollback
-   Human approval

### Example

``` text
Production Model
      ↓
Candidate Model
      ↓
Offline Validation
      ↓
Subgroup Evaluation
      ↓
Shadow Testing
      ↓
Clinical/Operational Review
      ↓
Controlled Promotion
```

------------------------------------------------------------------------

## 5. AWS Transfer

Map the cloud-neutral architecture to AWS.

  Capability           AWS Example
  -------------------- --------------------------------------------
  Object Storage       S3
  Compute              ECS / EC2 / Lambda
  API                  API Gateway + FastAPI
  Database             RDS / Aurora
  Container Registry   ECR
  Workflow             MWAA / Step Functions
  Monitoring           CloudWatch
  Secrets              Secrets Manager
  ML Platform          SageMaker
  CI/CD                CodePipeline / CodeBuild or GitHub Actions

Use only appropriately authorized/de-identified data in the cloud
environment.

### Required deliverables

-   AWS architecture
-   Deployment configuration
-   CI/CD pipeline
-   Cloud deployment
-   Monitoring dashboard
-   Operations runbook
-   Rollback procedure

### CP3 Exit Criteria

A cloud-operated healthcare ML platform with automated pipelines,
monitoring, model lifecycle management and controlled deployment.

------------------------------------------------------------------------

# CP4 --- AI Enhancement

## 1. AI Product Specification

Transform MediSphere into a **Healthcare Intelligence & AI Copilot**.

### AI capabilities

The copilot should support authorized users with questions such as:

-   What factors contributed to this risk score?
-   What patterns are visible in this patient cohort?
-   What does the relevant clinical guideline say?
-   What evidence supports this operational recommendation?
-   What trends are visible across admissions?
-   Which documentation is relevant to this case?
-   What should an authorized analyst review next?

### Important boundary

The copilot is an information and decision-support system.

It should not independently diagnose patients, prescribe treatment, or
execute consequential clinical actions.

### AI architecture

``` text
User
 ↓
Supervisor Agent
 ↓
 ├── Risk Agent
 ├── Patient/Cohort Agent
 ├── Data Agent
 ├── Knowledge Agent
 └── Healthcare Analyst
```

------------------------------------------------------------------------

## 2. Knowledge Base + RAG

Build a healthcare knowledge base using permitted documents such as:

-   Clinical guidelines
-   Hospital SOPs
-   Patient-care procedures
-   Medication information approved for the use case
-   Infection-control procedures
-   Operational policies
-   Public-health guidance
-   Model documentation

For educational projects, use public or explicitly authorized documents.

### RAG pipeline

``` text
Documents
→ Parsing
→ Chunking
→ Embeddings
→ Vector Store
→ Retrieval
→ Reranking
→ Context
→ LLM
→ Grounded Answer
```

### Example technologies

-   LangChain
-   LangGraph
-   Chroma / Pinecone
-   Hugging Face embeddings
-   OpenAI / Anthropic / Groq or equivalent LLMs

------------------------------------------------------------------------

## 3. RAG Evaluation

Create a healthcare-specific evaluation dataset.

### Evaluation dimensions

-   Retrieval relevance
-   Context precision
-   Context recall
-   Answer correctness
-   Groundedness
-   Citation/source accuracy
-   Hallucination rate
-   Latency

### Example questions

``` text
Q1: What does the referenced guideline recommend for this scenario?

Q2: Which hospital procedure applies to this operational case?

Q3: What source supports this recommendation?

Q4: What documentation should an authorized analyst review?

Q5: What limitations are stated in the relevant clinical guidance?
```

### Required safeguards

-   Source citations
-   Confidence/uncertainty communication
-   No unsupported clinical claims
-   Escalation for ambiguous questions
-   Human review for consequential outputs

### Deliverables

-   Golden question-answer dataset
-   Retrieval evaluation
-   Answer evaluation
-   Error analysis
-   RAG evaluation report

------------------------------------------------------------------------

## 4. Multi-Agent System

Implement an orchestrated healthcare-agent system.

### Supervisor Agent

Routes requests and coordinates specialist agents.

### Risk Agent

-   Calls approved prediction APIs
-   Explains model factors
-   Produces structured risk summaries

### Patient/Cohort Agent

-   Summarizes authorized patient/cohort data
-   Identifies trends
-   Performs cohort comparisons

### Data Agent

-   Queries approved structured datasets
-   Performs controlled analytics
-   Produces numerical evidence

### Knowledge Agent

-   Retrieves relevant clinical/operational documents
-   Provides grounded information
-   Cites sources

### Healthcare Analyst

-   Combines model outputs
-   Combines structured data
-   Combines retrieved knowledge
-   Produces an evidence-backed analytical brief

### Example workflow

``` text
User:
"What factors contributed to the high-risk score?"

        ↓

Supervisor
        ↓
Risk Agent
        ↓
Data Agent
        ↓
Patient/Cohort Agent
        ↓
Knowledge Agent
        ↓
Healthcare Analyst
        ↓
Evidence-backed Explanation
        ↓
Human Review
```

------------------------------------------------------------------------

## 5. Production AI Demonstration

### Scenario 1 --- Risk Explanation

``` text
User:
"Explain the factors behind this risk score."
```

System:

-   Calls approved ML model
-   Identifies important model features
-   Presents limitations
-   Retrieves relevant documentation if needed
-   Produces a structured explanation

### Scenario 2 --- Cohort Analysis

``` text
User:
"What patterns are visible in the high-risk cohort?"
```

System:

-   Queries approved data
-   Performs cohort analysis
-   Produces statistics and trends
-   Clearly distinguishes correlation from causation

### Scenario 3 --- Knowledge Question

``` text
User:
"What does the relevant guideline say about this situation?"
```

System:

-   Retrieves authoritative permitted documents
-   Cites sources
-   Produces a grounded summary
-   Escalates when the question is ambiguous

### Scenario 4 --- MCP Integration

Expose approved capabilities through MCP tools/resources.

Example tools:

``` text
get_patient_profile()
get_cohort_summary()
get_readmission_risk()
get_length_of_stay_prediction()
query_healthcare_data()
retrieve_clinical_guideline()
get_model_explanation()
create_analyst_report()
```

### Guardrails

Implement:

-   Tool allow-list
-   Input validation
-   Output validation
-   Authentication/authorization
-   Retrieval grounding
-   Prompt-injection defenses
-   Sensitive-data controls
-   Audit logging
-   Model/version traceability
-   Human approval
-   Clinical escalation path

### Important Healthcare Principle

The AI copilot should support authorized professionals and analysts
rather than silently replacing clinical judgment.

Consequential clinical decisions require appropriate human oversight and
organizational governance.

### CP4 Exit Criteria

A production-style Healthcare Intelligence & AI Copilot that combines
ML, healthcare analytics, RAG, tools, multi-agent orchestration, MCP,
guardrails, privacy controls and human oversight.

------------------------------------------------------------------------

# 4. Dataset Strategy

## Primary Dataset Option 1 --- MIMIC-IV

Source:

https://physionet.org/content/mimiciv/

Use for advanced healthcare data engineering and clinical analytics.

Requirements include appropriate credentialing and data-use compliance.

## Primary Dataset Option 2 --- UCI Diabetes 130-US Hospitals

Source:

https://archive.ics.uci.edu/dataset/296/diabetes+130+us+hospitals+for+years+1999+2008

Use for a more accessible readmission-risk project.

## Optional Public Context

Possible sources:

-   WHO
-   World Bank
-   CDC
-   Government health statistics
-   Public clinical guidelines

Use external data only when the join keys and time/geographic
relationships are defensible.

### Healthcare data-engineering rule

Do not create artificial patient-level joins between unrelated datasets.

Use valid relationships such as:

``` text
patient
+
encounter
+
timestamp
+
clinical event
```

or:

``` text
facility
+
time
+
geography
```

where supported by the source data.

------------------------------------------------------------------------

# 5. Lakehouse Structure

``` text
data/
│
├── raw/
│   ├── mimic/
│   ├── diabetes/
│   ├── public_health/
│   └── guidelines/
│
├── bronze/
│   ├── patients/
│   ├── admissions/
│   ├── diagnoses/
│   ├── procedures/
│   ├── medications/
│   └── measurements/
│
├── silver/
│   ├── patients_clean/
│   ├── encounters_clean/
│   ├── clinical_events/
│   └── derived_history/
│
└── gold/
    ├── patient_features/
    ├── cohort_features/
    ├── readmission_features/
    ├── los_features/
    ├── anomaly_features/
    ├── predictions/
    └── model_metrics/
```

------------------------------------------------------------------------

# 6. SQL Data Model

Recommended model:

``` text
dim_patient
dim_encounter
dim_provider
dim_facility
dim_diagnosis
dim_procedure
dim_medication
dim_time
dim_cohort

fact_admission
fact_diagnosis
fact_procedure
fact_medication
fact_measurement
fact_patient_event

feature_readmission_risk
feature_length_of_stay
feature_patient_cohort
feature_anomaly

prediction_readmission
prediction_los
prediction_anomaly

model_metrics
```

### Example relationships

``` text
dim_patient
      ↓
fact_admission
      ↓
feature_readmission_risk
      ↓
prediction_readmission
```

and:

``` text
dim_patient
      ↓
fact_patient_event
      ↓
feature_anomaly
      ↓
prediction_anomaly
```

------------------------------------------------------------------------

# 7. Feature Engineering

## Patient Features

-   Age
-   Demographic variables where appropriate
-   Historical admissions
-   Prior readmissions
-   Diagnosis counts
-   Procedure counts
-   Medication/utilization features where available

## Encounter Features

-   Admission type
-   Length of stay
-   Previous encounter interval
-   Number of diagnoses
-   Number of procedures
-   Utilization indicators

## Temporal Features

-   Hour
-   Day
-   Week
-   Month
-   Season
-   Time since previous admission

## Clinical/Utilization Features

-   Diagnosis categories
-   Procedure categories
-   Medication categories
-   Measurement summaries
-   Recent utilization
-   Historical utilization

## Derived Features

-   Readmission history
-   Utilization intensity
-   Risk score
-   Cohort assignment
-   Anomaly score

### Leakage Prevention

Only include features available before the prediction timestamp.

------------------------------------------------------------------------

# 8. ML Progression

``` text
Clinical / Operational Baseline
        ↓
Logistic Regression
        ↓
Random Forest
        ↓
XGBoost / LightGBM
        ↓
Class Weighting
        ↓
Threshold Optimization
        ↓
Calibration
        ↓
Explainability
        ↓
Production Model
```

### Length-of-stay

``` text
Median Baseline
→ Linear Regression
→ Random Forest
→ Gradient Boosting
→ XGBoost / LightGBM
→ Production Model
```

### Anomaly pipeline

``` text
Statistical Rules
        ↓
Isolation Forest
        ↓
Local Outlier Factor
        ↓
Advanced Detector
        ↓
Expert Validation
        ↓
Production Detector
```

------------------------------------------------------------------------

# 9. Key KPIs

  Category         KPI
  ---------------- ------------------------
  Readmission      ROC-AUC
  Readmission      PR-AUC
  Readmission      Recall
  Readmission      Precision
  Readmission      F1
  Readmission      Calibration
  Length of Stay   MAE
  Length of Stay   RMSE
  Anomaly          Precision
  Anomaly          Recall
  Anomaly          F1
  Data             Data-quality pass rate
  Data             Data freshness
  API              Latency
  API              Error rate
  Model            Feature drift
  Model            Prediction drift
  Model            Subgroup performance
  AI               Retrieval relevance
  AI               Groundedness
  AI               Hallucination rate
  AI               Tool success rate
  Operations       Alert volume
  Operations       Review turnaround time

------------------------------------------------------------------------

# 10. Suggested Repository Structure

``` text
medisphere/
│
├── data/
├── notebooks/
├── src/
│   ├── ingestion/
│   ├── validation/
│   ├── transformation/
│   ├── features/
│   ├── models/
│   ├── evaluation/
│   ├── api/
│   ├── agents/
│   ├── rag/
│   └── tools/
│
├── sql/
├── dashboard/
├── tests/
├── configs/
├── docs/
├── pipelines/
├── deployment/
├── docker/
├── monitoring/
├── governance/
├── security/
├── requirements/
└── README.md
```

------------------------------------------------------------------------

# 11. Final Capstone Deliverables

## CP1

-   Architecture
-   Project specification
-   Data acquisition/access documentation
-   Integrated clinical dataset
-   Data-quality report
-   EDA
-   Feature pipeline
-   Readmission-risk model
-   Length-of-stay model
-   Anomaly model
-   Evaluation report
-   Dashboard
-   Explainability report
-   Safety/limitations document
-   Model artifact

## CP2

-   Enhanced data pipeline
-   SQL data model
-   Versioned features
-   Versioned models
-   FastAPI
-   API documentation
-   Tests
-   Docker
-   CI/CD
-   Containerized UI

## CP3

-   Cloud architecture
-   Automated orchestration
-   Model registry
-   Training pipeline
-   Monitoring
-   Telemetry
-   Deployment
-   Rollback
-   AWS implementation
-   Operations runbook

## CP4

-   AI product specification
-   Healthcare knowledge base
-   RAG pipeline
-   RAG evaluation dataset
-   RAG evaluation report
-   Multi-agent system
-   MCP tools
-   Guardrails
-   Privacy/security controls
-   Human approval workflow
-   Audit trail
-   Final AI demonstration

------------------------------------------------------------------------

# 12. Final Demonstration

The final MediSphere demonstration should show:

``` text
HEALTHCARE DATA
      ↓
DATA ENGINEERING
      ↓
SQL / LAKEHOUSE
      ↓
PATIENT & COHORT ANALYTICS
      ↓
RISK PREDICTION
      ↓
LENGTH-OF-STAY PREDICTION
      ↓
ANOMALY DETECTION
      ↓
FASTAPI
      ↓
DOCKER
      ↓
CLOUD
      ↓
MLOps
      ↓
MONITORING
      ↓
RAG
      ↓
MULTI-AGENT AI
      ↓
MCP
      ↓
GUARDRAILS
      ↓
HUMAN / CLINICAL OVERSIGHT
      ↓
MEDISPHERE
HEALTHCARE AI COPILOT
```

## Final Student Outcome

Students demonstrate an integrated capability across:

**Data Science → Data Engineering → ML Engineering → Production AI
Engineering → Cloud → MLOps → RAG → Agentic AI → MCP → Responsible
Healthcare AI**
