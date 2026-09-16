# Project --- Meridian FinSight

## Banking Analytics & AI Copilot

### Capstone Structure: ps-01

------------------------------------------------------------------------

# 1. Project Overview

## Objective

Build an end-to-end banking intelligence platform that progressively
evolves from data engineering and ML into a cloud-operated, AI-enabled
banking analytics copilot.

The project follows:

**ML → Application + Container → Cloud → Enhance with AI**

## Business Problem

Banks and financial institutions need data-driven systems to understand:

-   Customer behaviour
-   Credit and repayment risk
-   Transaction patterns
-   Customer value
-   Product usage
-   Fraud/anomaly signals
-   Portfolio performance
-   Operational trends
-   Regulatory and policy requirements

Meridian FinSight combines these capabilities into a unified banking
analytics platform.

## Core ML Problems

1.  **Credit Risk Prediction**
    -   Predict probability of loan default
    -   Customer risk scoring
    -   Portfolio risk segmentation
2.  **Customer Analytics**
    -   Customer segmentation
    -   Product affinity
    -   Customer lifetime/value proxy
    -   Churn/retention risk
3.  **Transaction Anomaly Detection**
    -   Identify unusual transaction behaviour
    -   Detect suspicious patterns
    -   Prioritize cases for investigation
4.  **Optional Revenue/Product Analytics**
    -   Predict product propensity
    -   Identify cross-sell opportunities
    -   Analyze customer/product performance

------------------------------------------------------------------------

# 2. Overall Architecture

``` text
Banking / Loan Dataset
        +
Transaction Data
        +
Customer Data
        +
Economic / Demographic Context
        +
Regulatory / Policy Documents
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
Banking Knowledge Base
        ↓
RAG
        ↓
Multi-Agent System
        ↓
MCP + Guardrails
        ↓
Human Approval
        ↓
MERIDIAN FINSIGHT
BANKING AI COPILOT
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
Banking Dashboard
+
Risk APIs
+
Transaction Alerts
+
Customer Intelligence
+
AI Copilot
+
Agents
+
Recommendations
+
Audit Trail
+
Operations Runbook
```

------------------------------------------------------------------------

# CP1 --- ML Product

## 1. Architecture & Specification

Students define:

-   Banking business problem
-   Target users and personas
-   Functional requirements
-   Non-functional requirements
-   Data architecture
-   ML problem definitions
-   Dashboard requirements
-   API requirements
-   Evaluation strategy
-   Security and privacy assumptions

### Required architecture

``` text
Sources
→ Ingestion
→ Validation
→ Lakehouse
→ SQL Model
→ Features
→ ML
→ Dashboard
```

### Target users

-   Credit analysts
-   Risk managers
-   Relationship managers
-   Fraud/operations analysts
-   Banking executives

### Deliverables

-   Project specification
-   Architecture diagram
-   Data dictionary
-   Git repository
-   Initial API specification
-   Security/privacy assumptions

------------------------------------------------------------------------

## 2. Data Engineering & EDA

### Recommended primary dataset

**Home Credit Default Risk**

Source:

https://www.kaggle.com/competitions/home-credit-default-risk/data

Use the relational banking/credit data to build a realistic
customer-credit analytics pipeline.

Potential tables include:

``` text
application_train
application_test
bureau
bureau_balance
previous_application
POS_CASH_balance
credit_card_balance
installments_payments
```

### Additional public data

Potential enrichment:

-   World Bank indicators
-   U.S. Census demographic context where geographically appropriate
-   Public economic indicators
-   Banking/regulatory documents for the later RAG stage

### Data-engineering challenge

Do not simply train on `application_train`.

Build a relational pipeline that aggregates historical tables into
customer/application-level features.

Example:

``` text
Customer/Application
        +
Previous Applications
        +
Credit Bureau History
        +
Installment Behaviour
        +
Credit Card Behaviour
        ↓
Customer Credit Feature Table
```

### EDA

Analyze:

-   Default distribution
-   Income distribution
-   Loan amount
-   Credit history
-   Payment behaviour
-   Previous applications
-   Installment delays
-   Credit utilization
-   Demographic/business relationships where available
-   Missingness
-   Outliers
-   Class imbalance

### Deliverables

-   Data acquisition scripts
-   Relational ingestion pipeline
-   Data-quality report
-   EDA notebook/report
-   Feature engineering pipeline
-   Curated Parquet datasets

------------------------------------------------------------------------

## 3. Dashboard

Build a banking analytics dashboard.

### Required views

1.  Portfolio overview
2.  Customer risk distribution
3.  Default-risk analysis
4.  Transaction/anomaly overview
5.  Customer segmentation
6.  Product/customer insights
7.  Model performance
8.  Explainability

### Example customer view

``` text
Customer
   ↓
Credit Profile
   ↓
Risk Score
   ↓
Historical Behaviour
   ↓
Anomaly Signals
   ↓
Product Profile
   ↓
Recommended Investigation
```

### Suggested technologies

-   Streamlit
-   Plotly
-   Pandas
-   SQL/DuckDB

------------------------------------------------------------------------

## 4. ML Model

### Credit-risk progression

``` text
Business Rule Baseline
→ Logistic Regression
→ Random Forest
→ XGBoost / LightGBM
→ Class Weighting
→ Threshold Optimization
→ Explainability
→ Production Model
```

### Customer segmentation

``` text
Feature Engineering
→ Standardization
→ K-Means
→ Hierarchical Clustering
→ Segment Profiling
```

### Anomaly detection

``` text
Statistical Baseline
→ Isolation Forest
→ Local Outlier Factor
→ Advanced Anomaly Model
```

### Important banking rule

For credit-risk models, avoid using variables that cause target leakage.

Document:

-   Feature availability time
-   Target definition
-   Observation window
-   Performance window
-   Train/test temporal logic where applicable

------------------------------------------------------------------------

## 5. Evaluation & Deliverables

### Credit-risk metrics

-   ROC-AUC
-   PR-AUC
-   Precision
-   Recall
-   F1
-   Confusion matrix
-   Calibration
-   False-negative rate

### Business/risk metrics

-   Default capture rate
-   Approval/rejection threshold analysis
-   Expected-loss proxy
-   Risk-segment stability

### Anomaly metrics

Where labels exist:

-   Precision
-   Recall
-   F1
-   PR-AUC

Where labels do not exist:

-   Expert review
-   Synthetic anomaly validation
-   False-alert analysis

### Required deliverables

-   Model comparison
-   Error analysis
-   Explainability
-   Threshold analysis
-   Risk dashboard
-   Model artifact
-   Key business insights

### CP1 Exit Criteria

A working banking ML product that predicts credit risk, profiles
customers and identifies anomalous behaviour.

------------------------------------------------------------------------

# CP2 --- Application + Container

## 1. Enhanced Data Pipeline

Extend CP1 into a reproducible banking data platform.

### Requirements

-   Automated ingestion
-   Incremental processing
-   Schema validation
-   Referential-integrity checks
-   Missing-value checks
-   Data-quality thresholds
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
-   SQL transformation scripts
-   Data-quality report

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

### Additional requirements

Document:

-   Model assumptions
-   Feature lineage
-   Training dataset version
-   Model version
-   Evaluation dataset
-   Threshold configuration

------------------------------------------------------------------------

## 3. FastAPI Application

Expose banking analytics through APIs.

### Example endpoints

``` text
GET  /health
GET  /metadata

POST /credit-risk
POST /customer-segment
POST /transaction-anomaly
POST /product-propensity

GET  /customer/{customer_id}
GET  /model-info
GET  /metrics
```

### Example request

``` json
{
  "customer_id": "CUST001",
  "application_id": "APP001"
}
```

### API requirements

-   Pydantic validation
-   Structured responses
-   Error handling
-   Authentication-ready architecture
-   Logging
-   OpenAPI documentation
-   Unit tests
-   Integration tests

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
Banking Dashboard
        ↓
FastAPI
        ↓
Feature / Analytics Layer
        ↓
ML Models
        ↓
Risk / Segment / Anomaly Results
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

### CP2 Exit Criteria

A reproducible, tested and containerized banking analytics application
with APIs and dashboard.

------------------------------------------------------------------------

# CP3 --- Cloud + Operations

## 1. Triggers & Automation

Automate:

-   New data ingestion
-   Data validation
-   Feature generation
-   Risk scoring
-   Anomaly scoring
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
→ Risk Scoring
→ Anomaly Detection
→ Store Results
→ Update Dashboard
→ Alert if Required
```

### Suggested orchestration

-   Apache Airflow
-   AWS event/scheduling services
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

### Model promotion

``` text
Candidate Model
→ Validation
→ Performance Comparison
→ Risk/Business Checks
→ Approval Gate
→ Production
```

For financial-risk systems, a newly trained model should not
automatically replace production merely because it has a better single
metric.

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
-   Missing values
-   Schema changes
-   Referential-integrity failures
-   Distribution drift

### Model

-   ROC-AUC/PR-AUC where labels become available
-   Prediction distribution
-   Feature drift
-   Calibration drift
-   Segment stability
-   Error rates

### Banking operations

-   High-risk case volume
-   Anomaly alert volume
-   False-alert rate
-   Manual-review queue
-   Model decision turnaround time

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
Shadow Testing
      ↓
Risk Review
      ↓
Human Approval
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

Students may implement a smaller subset according to the available AWS
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

A cloud-operated banking ML platform with automated data/model
pipelines, monitoring, lifecycle management and safe deployment.

------------------------------------------------------------------------

# CP4 --- AI Enhancement

## 1. AI Product Specification

Transform Meridian FinSight into a **Banking AI Copilot**.

### AI capabilities

The copilot should answer questions such as:

-   Why is this customer considered high risk?
-   What factors contributed to the risk score?
-   What unusual transaction behaviour was detected?
-   What is the customer's financial/product profile?
-   Which banking policy applies to this case?
-   What evidence supports the recommendation?
-   What should an analyst investigate next?

### AI architecture

``` text
User
 ↓
Supervisor Agent
 ↓
 ├── Risk Agent
 ├── Customer Agent
 ├── Transaction Agent
 ├── Data Agent
 ├── Knowledge Agent
 └── Banking Analyst
```

------------------------------------------------------------------------

## 2. Knowledge Base + RAG

Build a banking knowledge base containing publicly usable or
institution-provided documents such as:

-   Banking policies
-   Credit-risk policies
-   Loan product documentation
-   KYC/AML procedures
-   Regulatory guidance
-   Internal SOPs
-   Model-risk documentation
-   Customer-service procedures

For training/demo purposes, use documents that the organization is
permitted to process.

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

Create a banking-specific evaluation dataset.

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
Q1: What documentation is required for this loan process?

Q2: Which policy applies to the identified risk condition?

Q3: What evidence supports the recommended analyst action?

Q4: What is the documented procedure for escalating an unusual transaction?

Q5: Which source supports this KYC/AML requirement?
```

### Deliverables

-   Golden question-answer dataset
-   Retrieval evaluation
-   Answer evaluation
-   Error analysis
-   RAG evaluation report

------------------------------------------------------------------------

## 4. Multi-Agent System

Implement an orchestrated banking-agent system.

### Supervisor Agent

Routes requests and coordinates specialist agents.

### Risk Agent

-   Calls credit-risk model
-   Explains risk factors
-   Produces structured risk summaries

### Customer Agent

-   Retrieves customer profile
-   Analyzes product usage
-   Summarizes behavioural patterns

### Transaction Agent

-   Queries transaction data
-   Detects anomalies
-   Produces evidence for investigation

### Data Agent

-   Queries approved structured data
-   Performs controlled analytical operations
-   Produces numerical evidence

### Knowledge Agent

-   Retrieves banking policies
-   Provides grounded regulatory/procedural information

### Banking Analyst

-   Combines model results
-   Combines structured data
-   Combines retrieved knowledge
-   Produces an evidence-backed analysis

### Example workflow

``` text
User:
"Why is this customer classified as high risk?"

        ↓

Supervisor
        ↓
Risk Agent
        ↓
Data Agent
        ↓
Customer Agent
        ↓
Knowledge Agent
        ↓
Banking Analyst
        ↓
Evidence-backed Explanation
        ↓
Recommended Investigation
        ↓
Human Approval
```

------------------------------------------------------------------------

## 5. Production AI Demonstration

### Scenario 1 --- Credit Risk

``` text
User:
"Explain this customer's risk score."
```

System:

-   Calls risk model
-   Identifies important factors
-   Retrieves applicable policy information
-   Produces a structured explanation
-   Shows supporting evidence

### Scenario 2 --- Transaction Investigation

``` text
User:
"Investigate unusual transactions for this customer."
```

System:

-   Queries transaction data
-   Detects anomalies
-   Summarizes relevant events
-   Retrieves applicable procedures
-   Produces an investigation brief

### Scenario 3 --- Policy Question

``` text
User:
"What procedure should an analyst follow for this case?"
```

System:

-   Retrieves relevant policy/SOP documents
-   Cites supporting sources
-   Generates a grounded response
-   Does not invent policy requirements

### Scenario 4 --- MCP Integration

Expose approved capabilities through MCP tools/resources.

Example tools:

``` text
get_customer_profile()
get_credit_risk()
get_transaction_history()
detect_transaction_anomaly()
query_portfolio()
retrieve_banking_policy()
get_model_explanation()
create_risk_report()
```

### Guardrails

Implement:

-   Tool allow-list
-   Input validation
-   Output validation
-   Authentication/authorization architecture
-   Retrieval grounding
-   Prompt-injection defenses
-   Sensitive-data controls
-   Human approval for consequential actions
-   Audit logging
-   Model/version traceability

### Important Banking Principle

The AI copilot should support analysts rather than silently making
consequential financial decisions.

High-impact actions should follow an explicit human-review workflow.

### CP4 Exit Criteria

A production-style Banking AI Copilot that combines ML risk analytics,
customer intelligence, anomaly detection, RAG, tools, multi-agent
orchestration, MCP, guardrails and human approval.

------------------------------------------------------------------------

# 4. Dataset Strategy

## Primary Dataset

### Home Credit Default Risk

Source:

https://www.kaggle.com/competitions/home-credit-default-risk/data

Use the dataset as the main credit-risk and relational-data-engineering
challenge.

### Recommended relational integration

``` text
Application
+
Previous Applications
+
Credit Bureau
+
Credit Bureau Balance
+
POS/Cash Balance
+
Credit Card Balance
+
Installment Payments
        ↓
Customer Credit Feature Store
```

## Additional Context

Potential public sources may include:

-   World Bank indicators
-   Public economic indicators
-   Census/demographic data where geographic mapping is defensible
-   Public banking/regulatory documents

### Data-engineering rule

Do not force unrelated datasets into a row-level join.

Use a documented relationship such as:

``` text
customer/application
+
time
+
geography
+
product
```

only when the relationship is valid.

------------------------------------------------------------------------

# 5. Lakehouse Structure

``` text
data/
│
├── raw/
│   ├── home_credit/
│   ├── economic/
│   ├── demographic/
│   └── policies/
│
├── bronze/
│   ├── applications/
│   ├── bureau/
│   ├── payments/
│   ├── credit_cards/
│   └── previous_applications/
│
├── silver/
│   ├── applications_clean/
│   ├── bureau_clean/
│   ├── payments_clean/
│   └── customer_history/
│
└── gold/
    ├── customer_credit_features/
    ├── customer_segments/
    ├── transaction_features/
    ├── anomaly_features/
    ├── risk_scores/
    ├── predictions/
    └── model_metrics/
```

------------------------------------------------------------------------

# 6. SQL Data Model

Recommended model:

``` text
dim_customer
dim_application
dim_product
dim_branch
dim_time
dim_geography
dim_risk_segment

fact_loan_application
fact_credit_account
fact_payment
fact_transaction
fact_customer_product

feature_credit_risk
feature_customer_segment
feature_transaction_anomaly
feature_product_propensity

prediction_credit_risk
prediction_anomaly
prediction_propensity

model_metrics
```

### Example relationships

``` text
dim_customer
      ↓
fact_loan_application
      ↓
feature_credit_risk
      ↓
prediction_credit_risk
```

and:

``` text
dim_customer
      ↓
fact_transaction
      ↓
feature_transaction_anomaly
      ↓
prediction_anomaly
```

------------------------------------------------------------------------

# 7. Feature Engineering

## Credit Features

-   Income
-   Credit amount
-   Annuity
-   Loan-to-income ratio
-   Credit-to-income ratio
-   Previous loan count
-   Previous approval rate
-   Previous rejection rate
-   Average previous loan amount
-   Payment delay
-   Installment history
-   Credit utilization

## Customer Behaviour

-   Number of products
-   Product tenure
-   Transaction frequency
-   Average transaction amount
-   Transaction volatility
-   Recent activity
-   Customer segment

## Anomaly Features

-   Transaction amount deviation
-   Frequency deviation
-   Time-of-day deviation
-   Rolling transaction statistics
-   Customer baseline deviation
-   Velocity indicators

## Temporal

-   Day
-   Week
-   Month
-   Quarter
-   Weekend
-   Holiday
-   Recency

------------------------------------------------------------------------

# 8. ML Progression

``` text
Business Baseline
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
Production Risk Model
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

  Category          KPI
  ----------------- -----------------------------
  Credit Risk       ROC-AUC
  Credit Risk       PR-AUC
  Credit Risk       Recall
  Credit Risk       Precision
  Credit Risk       F1
  Credit Risk       Calibration
  Risk Operations   High-risk capture rate
  Risk Operations   False-negative rate
  Anomaly           Precision
  Anomaly           Recall
  Anomaly           F1
  Data              Data-quality pass rate
  Data              Data freshness
  API               Latency
  API               Error rate
  Model             Feature drift
  Model             Prediction drift
  AI                Retrieval relevance
  AI                Groundedness
  AI                Hallucination rate
  AI                Tool success rate
  Operations        Manual-review volume
  Business          Risk-review turnaround time

------------------------------------------------------------------------

# 10. Suggested Repository Structure

``` text
meridian-finsight/
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
├── requirements/
└── README.md
```

------------------------------------------------------------------------

# 11. Final Capstone Deliverables

## CP1

-   Architecture
-   Project specification
-   Data acquisition scripts
-   Integrated relational dataset
-   Data-quality report
-   EDA
-   Feature pipeline
-   Credit-risk model
-   Anomaly model
-   Customer segmentation
-   Evaluation report
-   Dashboard
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
-   Banking knowledge base
-   RAG pipeline
-   RAG evaluation dataset
-   RAG evaluation report
-   Multi-agent system
-   MCP tools
-   Guardrails
-   Human approval workflow
-   Audit trail
-   Final AI demonstration

------------------------------------------------------------------------

# 12. Final Demonstration

The final Meridian FinSight demonstration should show:

``` text
BANKING DATA
     ↓
DATA ENGINEERING
     ↓
SQL / LAKEHOUSE
     ↓
CREDIT RISK
     ↓
CUSTOMER INTELLIGENCE
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
HUMAN APPROVAL
     ↓
MERIDIAN FINSIGHT
BANKING AI COPILOT
```

## Final Student Outcome

Students demonstrate an integrated capability across:

**Data Science → Data Engineering → ML Engineering → Production AI
Engineering → Cloud → MLOps → RAG → Agentic AI → MCP → Enterprise
Banking AI**
