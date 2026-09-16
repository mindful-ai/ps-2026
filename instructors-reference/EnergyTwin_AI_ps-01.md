# Project 5 --- EnergyTwin AI

## Industrial Energy Optimization & Predictive Operations Platform

### Capstone Structure: ps-01

------------------------------------------------------------------------

## 1. Project Overview

### Objective

Build an end-to-end industrial energy intelligence platform that:

-   Forecasts energy consumption
-   Detects abnormal energy behaviour
-   Identifies inefficient operating patterns
-   Provides energy-efficiency recommendations
-   Evolves into an AI-enabled energy operations copilot

The project progressively follows:

**ML → Application + Container → Cloud → Enhance with AI**

### Business Problem

Industrial facilities consume large amounts of energy across machines,
production lines, HVAC systems and other equipment. Operations teams
need to understand:

-   How much energy will be consumed?
-   When will demand peak?
-   Which operating periods are abnormal?
-   Which equipment or processes may be inefficient?
-   What operational actions could reduce energy consumption?
-   What evidence supports an energy recommendation?

### Core ML Problems

1.  **Energy Demand Forecasting**
    -   Short-term consumption forecasting
    -   Hourly or sub-hourly prediction
    -   Optional day-ahead forecasting
2.  **Energy Anomaly Detection**
    -   Detect abnormal consumption
    -   Identify unusual operating periods
    -   Detect unexpected spikes or drops
3.  **Energy Efficiency Scoring**
    -   Compare expected vs. actual consumption
    -   Identify inefficient operating periods
    -   Produce equipment/process-level risk scores where data permits
4.  **Optional Optimization**
    -   Recommend lower-energy operating windows
    -   Estimate potential energy savings
    -   Support what-if analysis

------------------------------------------------------------------------

# 2. Overall Architecture

``` text
I-BLEND Energy Data
        +
Weather Data
        +
Energy Price / Grid Context
        +
Building / Occupancy Context
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
Forecasting + Anomaly Detection
        ↓
Model Evaluation
        ↓
Model Artifact
        ↓
FastAPI
        ↓
Dashboard / UI
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
RAG Knowledge Base
        ↓
Agents + MCP
        ↓
Guardrails + Human Approval
        ↓
Energy Operations Copilot
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
Energy Dashboard
+
Forecast APIs
+
Anomaly Alerts
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

-   Business problem and target users
-   Functional and non-functional requirements
-   System architecture
-   Data sources
-   Forecasting and anomaly-detection objectives
-   API and dashboard requirements
-   Evaluation strategy
-   Project repository structure

### Required architecture

``` text
Energy Sources
→ Ingestion
→ Data Quality
→ Lakehouse
→ SQL Model
→ Feature Engineering
→ ML Models
→ Dashboard
```

### Deliverables

-   Project specification
-   Architecture diagram
-   Requirements document
-   Git repository
-   Data dictionary
-   Initial API specification

------------------------------------------------------------------------

## 2. Data Engineering & EDA

### Primary dataset

**I-BLEND --- public high-frequency building energy dataset**

Use the dataset as the primary energy-consumption source. Combine it
with contextual datasets where the time/location relationship is
defensible.

### Recommended enrichment

-   Weather
-   Occupancy/contextual information available in the primary dataset
-   Electricity price or grid context
-   Optional building metadata

### Data pipeline

``` text
Raw Sources
→ Ingestion
→ Schema Validation
→ Missing-Value Handling
→ Timestamp Normalization
→ Deduplication
→ Data Quality Checks
→ Bronze
→ Silver
→ Gold
```

### EDA

Students analyze:

-   Energy consumption distribution
-   Hourly/daily/weekly patterns
-   Seasonality
-   Peak demand
-   Consumption by operating period
-   Missing data
-   Outliers
-   Correlation with contextual variables
-   Expected vs. abnormal consumption

### Deliverables

-   Data acquisition scripts
-   Integrated dataset
-   Data-quality report
-   EDA notebook/report
-   Feature engineering pipeline
-   Curated Parquet datasets

------------------------------------------------------------------------

## 3. Dashboard

Build an initial energy intelligence dashboard.

### Required views

1.  Energy consumption trend
2.  Hourly/daily consumption profile
3.  Peak demand analysis
4.  Forecast vs. actual
5.  Anomaly timeline
6.  Energy-efficiency indicators
7.  Key operational insights

### Suggested technologies

-   Streamlit
-   Plotly
-   Pandas
-   Optional SQL-backed dashboard

------------------------------------------------------------------------

## 4. ML Model

### Forecasting progression

``` text
Naive Baseline
→ Seasonal Naive
→ Moving Average
→ Linear Regression
→ Random Forest
→ XGBoost / LightGBM
→ Optional LSTM / Temporal DL
```

### Anomaly detection progression

``` text
Statistical Threshold
→ Rolling Z-Score
→ Isolation Forest
→ Local Outlier Factor
→ Autoencoder (optional)
```

### Feature examples

-   Hour
-   Day of week
-   Weekend
-   Month
-   Holiday
-   Lag consumption
-   Rolling mean
-   Rolling standard deviation
-   Previous-day consumption
-   Previous-week consumption
-   Temperature
-   Occupancy/context
-   Operating-period indicators

### Important rule

Use chronological/time-aware validation. Do **not** randomly shuffle
time-series observations across train and test sets.

------------------------------------------------------------------------

## 5. Evaluation & Deliverables

### Forecasting metrics

-   MAE
-   RMSE
-   MAPE or sMAPE
-   WAPE
-   Peak-demand error

### Anomaly metrics

Where labels exist:

-   Precision
-   Recall
-   F1
-   PR-AUC

Where labels do not exist:

-   Expert review
-   Synthetic anomaly validation
-   Stability analysis
-   False-alert analysis

### Required deliverables

-   Model comparison report
-   Error analysis
-   Forecast plots
-   Anomaly analysis
-   Feature importance/explainability
-   Final model artifact
-   Dashboard
-   Key business insights

### CP1 Exit Criteria

A working ML-based energy intelligence product that can forecast
consumption and identify abnormal energy behaviour.

------------------------------------------------------------------------

# CP2 --- Application + Container

## 1. Enhanced Data Pipeline

Extend CP1 into a reproducible production-style pipeline.

### Requirements

-   Automated ingestion
-   Incremental processing
-   Data validation
-   Schema checks
-   Data-quality thresholds
-   Bronze/Silver/Gold organization
-   SQL transformations
-   Feature generation

### Suggested tools

-   Python
-   SQL
-   Pandas / Polars
-   PyArrow
-   DuckDB
-   Great Expectations or equivalent validation approach

### Deliverables

-   Updated architecture
-   Automated pipeline
-   Validation framework
-   Curated Parquet
-   SQL transformation scripts

------------------------------------------------------------------------

## 2. Data & Model Engineering

Implement:

-   Reproducible feature pipeline
-   Feature versioning
-   Model versioning
-   Experiment tracking
-   Configuration management
-   Model artifact storage
-   Evaluation pipeline

### Deliverables

-   Versioned features
-   Versioned model
-   Training script
-   Evaluation script
-   Configuration files
-   Experiment records

------------------------------------------------------------------------

## 3. FastAPI Application

Expose the energy intelligence system through APIs.

### Example endpoints

``` text
GET  /health
GET  /metadata
POST /forecast
POST /anomaly
POST /efficiency-score
POST /batch-forecast
GET  /model-info
GET  /metrics
```

### Example forecast request

``` json
{
  "building_id": "BLD001",
  "forecast_horizon": 24
}
```

### API requirements

-   Pydantic validation
-   Structured responses
-   Error handling
-   Logging
-   OpenAPI documentation
-   Unit tests
-   Integration tests

------------------------------------------------------------------------

## 4. Container + UI

### Containerize

``` text
FastAPI
+
ML Model
+
Feature Pipeline
+
Configuration
```

using Docker.

### UI

Connect the dashboard to the API rather than directly calling model
functions.

### Demonstration

``` text
Dashboard
→ FastAPI
→ Feature Pipeline
→ Model
→ Forecast / Anomaly
→ Dashboard Visualization
```

### Deliverables

-   Dockerfile
-   docker-compose configuration if needed
-   Containerized application
-   API documentation
-   Dashboard connected to API

------------------------------------------------------------------------

## 5. MLOps

Introduce basic MLOps practices:

-   Automated testing
-   Linting
-   CI pipeline
-   Model validation
-   Reproducible training
-   Artifact versioning
-   Configuration management
-   Dependency management
-   Security scanning

### CP2 Exit Criteria

A reproducible, tested and containerized energy ML application with APIs
and UI.

------------------------------------------------------------------------

# CP3 --- Cloud + Operations

## 1. Triggers & Automation

Design automated workflows for:

-   New data arrival
-   Scheduled ingestion
-   Data validation
-   Feature generation
-   Model training
-   Model evaluation
-   Forecast generation
-   Anomaly detection
-   Alert generation

### Example orchestration

``` text
Schedule / Event
→ Ingest
→ Validate
→ Transform
→ Generate Features
→ Predict
→ Evaluate
→ Store Results
→ Update Dashboard
→ Alert if Required
```

### Suggested orchestration

-   Apache Airflow
-   Cloud scheduler/event service
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
→ Compare with Production
→ Approval Gate
→ Production
```

A model should not automatically replace the production model merely
because it is newly trained.

------------------------------------------------------------------------

## 3. Telemetry & Reliability

Monitor:

### Application

-   API latency
-   Request rate
-   Error rate
-   Availability

### Data

-   Missing values
-   Schema changes
-   Data freshness
-   Volume anomalies
-   Distribution drift

### Model

-   Forecast error
-   Prediction distribution
-   Feature drift
-   Model performance degradation

### Energy product

-   Peak forecast error
-   Anomaly alert volume
-   False-alert rate
-   Recommendation acceptance

### Deliverables

-   Monitoring design
-   Logs
-   Metrics
-   Alerts
-   Monitoring dashboard
-   Incident response process

------------------------------------------------------------------------

## 4. Safe Model Rollout

Implement:

-   Champion/challenger models
-   Shadow deployment
-   Canary deployment where practical
-   Versioned model artifacts
-   Rollback
-   Approval gate

### Example

``` text
Production Model
      ↓
Candidate Model
      ↓
Offline Evaluation
      ↓
Shadow Testing
      ↓
Human Approval
      ↓
Controlled Promotion
```

------------------------------------------------------------------------

## 5. AWS Transfer

Deploy the cloud-neutral design to AWS.

### Possible mapping

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

Students may use a simpler subset depending on the available AWS
environment.

### Required deliverables

-   AWS architecture
-   Deployment scripts/configuration
-   CI/CD pipeline
-   Cloud deployment
-   Monitoring dashboard
-   Operations runbook
-   Rollback procedure

### CP3 Exit Criteria

A cloud-operated energy ML system with automated pipelines, monitoring,
model lifecycle management and safe deployment.

------------------------------------------------------------------------

# CP4 --- AI Enhancement

## 1. AI Product Specification

Transform EnergyTwin into an **Industrial Energy Operations Copilot**.

### AI capabilities

The copilot should answer questions such as:

-   Why did energy consumption increase?
-   What caused the latest anomaly?
-   What is tomorrow's expected demand?
-   Which operating periods are inefficient?
-   What historical evidence supports this conclusion?
-   What actions could reduce energy consumption?
-   What is the expected impact of a proposed action?

### AI architecture

``` text
User
 ↓
Supervisor Agent
 ↓
 ├── Forecast Agent
 ├── Anomaly Agent
 ├── Data Agent
 ├── Knowledge Agent
 ├── Optimization Agent
 └── Energy Analyst
```

------------------------------------------------------------------------

## 2. Knowledge Base + RAG

Build a domain knowledge base containing:

-   Energy-management policies
-   Equipment operating manuals
-   SOPs
-   Maintenance procedures
-   Energy-efficiency guidelines
-   Internal operating procedures
-   Historical incident reports
-   Relevant technical documentation

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

Create a formal evaluation dataset.

### Evaluation dimensions

-   Retrieval relevance
-   Context precision
-   Context recall
-   Answer correctness
-   Groundedness
-   Citation/source accuracy
-   Hallucination rate
-   Latency

### Example evaluation questions

``` text
Q1: What is the recommended operating procedure for an abnormal energy spike?

Q2: Which maintenance procedure applies to the identified equipment?

Q3: What operating limits are specified in the equipment documentation?

Q4: Which document supports the recommended corrective action?
```

### Deliverables

-   Golden question-answer dataset
-   Retrieval evaluation
-   Answer evaluation
-   Error analysis
-   RAG evaluation report

------------------------------------------------------------------------

## 4. Multi-Agent System

Implement an orchestrated multi-agent system.

### Agents

#### Supervisor Agent

Routes requests and coordinates agents.

#### Forecast Agent

-   Calls forecasting API
-   Produces future energy demand
-   Explains forecast trends

#### Anomaly Agent

-   Detects abnormal consumption
-   Investigates historical patterns
-   Produces anomaly evidence

#### Data Agent

-   Queries structured energy data
-   Runs approved analytical tools
-   Produces numerical evidence

#### Knowledge Agent

-   Retrieves relevant documents
-   Provides grounded technical information

#### Optimization Agent

-   Evaluates possible efficiency actions
-   Estimates potential savings
-   Produces what-if analysis

#### Energy Analyst

-   Combines model predictions
-   Combines structured data
-   Combines retrieved knowledge
-   Produces an executive analysis

### Example workflow

``` text
User:
"Why was yesterday's energy consumption unusually high?"

        ↓

Supervisor
        ↓
Anomaly Agent
        ↓
Data Agent
        ↓
Forecast Agent
        ↓
Knowledge Agent
        ↓
Energy Analyst
        ↓
Evidence-backed Explanation
        ↓
Recommended Action
        ↓
Human Approval
```

------------------------------------------------------------------------

## 5. Production AI Demonstration

The final demonstration should show:

### Scenario 1 --- Forecast

``` text
User asks:
"What is tomorrow's expected energy consumption?"
```

System:

-   Calls forecast API
-   Returns forecast
-   Shows uncertainty/error information
-   Explains important drivers

### Scenario 2 --- Anomaly Investigation

``` text
User asks:
"Why did energy consumption spike yesterday?"
```

System:

-   Detects anomaly
-   Queries structured data
-   Retrieves relevant knowledge
-   Generates evidence-backed explanation

### Scenario 3 --- Efficiency Recommendation

``` text
User asks:
"How can we reduce energy consumption during peak periods?"
```

System:

-   Analyzes historical demand
-   Identifies peak periods
-   Retrieves relevant operating guidance
-   Generates candidate actions
-   Estimates potential impact
-   Requests human approval before operational action

### Scenario 4 --- MCP Integration

Expose approved capabilities through MCP tools/resources.

Example tools:

``` text
get_energy_forecast()
detect_energy_anomaly()
query_energy_history()
get_equipment_status()
retrieve_energy_policy()
calculate_savings()
create_energy_report()
```

### Guardrails

Implement:

-   Tool allow-list
-   Input validation
-   Output validation
-   Access control
-   Retrieval grounding
-   Human approval for operational actions
-   Audit logging
-   Prompt-injection defenses
-   Sensitive-data controls

### CP4 Exit Criteria

A production-style AI Energy Operations Copilot that combines ML
forecasting, anomaly detection, RAG, tools, multi-agent reasoning, MCP
and human approval.

------------------------------------------------------------------------

# 4. Dataset Strategy

## Primary Dataset

### I-BLEND

Use I-BLEND as the principal high-frequency energy dataset for the
project.

Students should document:

-   Dataset source
-   License/usage terms
-   Sampling frequency
-   Time coverage
-   Available contextual variables
-   Target variable
-   Missing-data characteristics
-   Limitations

## Recommended External Enrichment

### NOAA Climate Data Online

Use weather data where a defensible time/location mapping exists.

Source:

https://www.ncei.noaa.gov/cdo-web/

Potential variables:

-   Temperature
-   Precipitation
-   Humidity
-   Wind
-   Weather events

### Optional Energy/Grid Context

Use an appropriate public electricity-price or grid-context dataset when
it can be joined reliably by time and geography.

### Important Data Engineering Rule

Do not force unrelated datasets into a row-level join merely to increase
the number of sources.

A valid multi-source design may use:

``` text
Energy Consumption
+
Weather
+
Occupancy
+
Price/Grid Context
```

with carefully documented keys such as:

``` text
timestamp
building_id
location_id
```

and appropriate aggregation windows.

------------------------------------------------------------------------

# 5. Lakehouse Structure

``` text
data/
│
├── raw/
│   ├── iblend/
│   ├── weather/
│   ├── energy_price/
│   └── building_context/
│
├── bronze/
│   ├── energy/
│   ├── weather/
│   └── context/
│
├── silver/
│   ├── energy_clean/
│   ├── weather_clean/
│   └── context_clean/
│
└── gold/
    ├── energy_features/
    ├── forecasting_dataset/
    ├── anomaly_features/
    ├── efficiency_scores/
    ├── predictions/
    └── model_metrics/
```

------------------------------------------------------------------------

# 6. SQL Data Model

Recommended analytical model:

``` text
dim_time
dim_building
dim_equipment
dim_location
dim_energy_source
dim_weather_station

fact_energy_consumption
fact_weather
fact_occupancy
fact_energy_price
fact_operating_event

feature_energy_forecast
feature_energy_anomaly
feature_efficiency

prediction_energy_forecast
prediction_anomaly
prediction_efficiency

model_metrics
```

### Example relationships

``` text
dim_time
   ↓
fact_energy_consumption
   ↓
feature_energy_forecast
   ↓
prediction_energy_forecast
```

and:

``` text
fact_energy_consumption
+
fact_weather
+
fact_occupancy
+
fact_operating_event
        ↓
feature_energy_anomaly
        ↓
prediction_anomaly
```

------------------------------------------------------------------------

# 7. Feature Engineering

## Temporal

-   Hour
-   Day
-   Week
-   Month
-   Quarter
-   Day of week
-   Weekend
-   Holiday
-   Season

## Lag Features

-   1-hour lag
-   3-hour lag
-   6-hour lag
-   12-hour lag
-   24-hour lag
-   7-day lag

## Rolling Features

-   Rolling mean
-   Rolling median
-   Rolling standard deviation
-   Rolling minimum
-   Rolling maximum

## Contextual

-   Temperature
-   Humidity
-   Occupancy
-   Operating period
-   Production/activity indicator
-   Energy price

## Derived

-   Expected consumption
-   Consumption deviation
-   Peak indicator
-   Energy intensity
-   Efficiency score
-   Anomaly score

------------------------------------------------------------------------

# 8. ML Progression

``` text
Business Baseline
        ↓
Seasonal Naive
        ↓
Linear Regression
        ↓
Random Forest
        ↓
XGBoost / LightGBM
        ↓
Temporal Deep Learning
        ↓
Model Comparison
        ↓
Production Model
```

### Anomaly pipeline

``` text
Statistical Baseline
        ↓
Rolling Threshold
        ↓
Isolation Forest
        ↓
Advanced Anomaly Model
        ↓
Expert Validation
        ↓
Production Detector
```

------------------------------------------------------------------------

# 9. Key KPIs

  Category      KPI
  ------------- --------------------------
  Forecasting   MAE
  Forecasting   RMSE
  Forecasting   sMAPE
  Forecasting   WAPE
  Forecasting   Peak-demand error
  Anomaly       Precision
  Anomaly       Recall
  Anomaly       F1
  Anomaly       False-alert rate
  Data          Data-quality pass rate
  Data          Data freshness
  API           Latency
  API           Error rate
  Model         Drift
  Operations    Retraining frequency
  AI            Retrieval relevance
  AI            Groundedness
  AI            Hallucination rate
  AI            Tool success rate
  Business      Estimated energy savings

------------------------------------------------------------------------

# 10. Suggested Repository Structure

``` text
energy-twin-ai/
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
├── requirements/
└── README.md
```

------------------------------------------------------------------------

# 11. Final Capstone Deliverables

## CP1

-   Architecture
-   Project specification
-   Data acquisition scripts
-   Integrated dataset
-   Data-quality report
-   EDA
-   Feature pipeline
-   ML models
-   Evaluation report
-   Dashboard
-   Model artifact

## CP2

-   Enhanced data pipeline
-   SQL data model
-   Versioned features
-   Versioned model
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
-   Knowledge base
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

The final EnergyTwin AI demonstration should present the complete
journey:

``` text
DATA
  ↓
Energy Data Engineering
  ↓
ML
  ↓
Forecasting
  ↓
Anomaly Detection
  ↓
FastAPI
  ↓
Docker
  ↓
Cloud
  ↓
MLOps
  ↓
Monitoring
  ↓
RAG
  ↓
Agents
  ↓
MCP
  ↓
Guardrails
  ↓
Human Approval
  ↓
ENERGY OPERATIONS COPILOT
```

## Final Student Outcome

By completing EnergyTwin AI, students demonstrate an integrated
capability across:

**Data Science → Data Engineering → ML Engineering → Production AI
Engineering → Cloud → MLOps → RAG → Agentic AI → MCP → Enterprise AI**
