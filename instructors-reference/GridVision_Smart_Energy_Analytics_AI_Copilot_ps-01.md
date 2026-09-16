# GridVision -- Smart Energy Analytics & AI Copilot

## Capstone Project Specification --- ps-01

------------------------------------------------------------------------

## 1. Project Objective

Build **GridVision**, an end-to-end smart-energy intelligence platform
that progressively evolves through:

**Machine Learning → Application + Container → Cloud + Operations → AI
Copilot**

The platform should help energy analysts and grid/utility operations
teams understand electricity demand, forecast future load, detect
abnormal consumption, segment customers/consumers, and investigate
operational questions through an AI-powered copilot.

### Core business capabilities

-   Electricity demand forecasting
-   Peak-load prediction
-   Consumption anomaly detection
-   Consumer/load-profile segmentation
-   Load-shape and seasonality analysis
-   Forecast-error and operational monitoring
-   Energy intelligence dashboard
-   RAG-based energy knowledge assistant
-   Multi-agent energy operations copilot
-   MCP-based controlled access to analytics tools

### Engineering progression

``` text
Raw Energy Data
      ↓
Data Engineering + Quality
      ↓
Lakehouse + SQL Data Model
      ↓
EDA + Feature Engineering
      ↓
ML Forecasting + Anomaly Detection
      ↓
FastAPI + Tests
      ↓
Docker + CI/CD
      ↓
Cloud Deployment + Observability
      ↓
RAG + Evaluation
      ↓
Multi-Agent Copilot + MCP
      ↓
Production Energy Intelligence Platform
```

------------------------------------------------------------------------

# CP1 --- ML Product

## 1. Architecture & Specification

### Business problem

Energy operations depend on understanding demand patterns at different
time scales. GridVision should transform historical electricity
measurements into an analytical and predictive product.

### Primary questions

1.  What is the expected electricity demand for the next interval/day?
2.  When are peak-demand periods likely to occur?
3.  Which consumers or load profiles behave similarly?
4.  Which observations represent unusual consumption?
5.  How accurate and reliable are the forecasts?
6.  What factors explain changes in demand?

### Proposed architecture

``` text
Electricity Data
      ↓
Ingestion
      ↓
Data Quality
      ↓
Lakehouse
      ↓
SQL Analytical Model
      ↓
Feature Engineering
      ↓
Forecasting Models
      ├── Demand Forecast
      ├── Peak Risk
      ├── Anomaly Detection
      └── Load Segmentation
      ↓
Model Evaluation
      ↓
Model Artifact
      ↓
Dashboard
```

### Primary dataset

**UCI ElectricityLoadDiagrams20112014**

The dataset contains electricity consumption for **370 clients**,
recorded at **15-minute intervals** from 2011--2014. The UCI description
states that the values are in kW and that the dataset contains no
missing values. It is licensed under **CC BY 4.0**. citeturn0search0

Dataset:
https://archive.ics.uci.edu/dataset/321/electricityloaddiagrams20112014

### Dataset use

Use the dataset to construct:

-   Time-series load observations
-   Consumer/load-profile features
-   Daily and weekly demand profiles
-   Peak-demand indicators
-   Seasonal features
-   Anomaly labels or unsupervised anomaly scores
-   Forecasting targets

### Important data interpretation

The source data is at 15-minute resolution and reports power in kW. If
energy in kWh is required for a 15-minute interval, divide the kW value
by 4. citeturn0search0

Students must preserve the original timestamp semantics and explicitly
document daylight-saving/time-change handling.

------------------------------------------------------------------------

## 2. Data Engineering & EDA

### Ingestion pipeline

``` text
UCI Dataset
    ↓
Raw Zone
    ↓
Schema Validation
    ↓
Timestamp Normalization
    ↓
Long-format Transformation
    ↓
Data Quality Checks
    ↓
Curated Zone
    ↓
Feature Tables
```

### Required transformations

Convert the wide source structure:

``` text
timestamp | client_1 | client_2 | ... | client_370
```

into an analytical long format:

``` text
timestamp | client_id | load_kw
```

### Required derived features

#### Time features

-   Year
-   Month
-   Day
-   Day of week
-   Hour
-   Quarter-hour
-   Weekend indicator
-   Holiday indicator if an external calendar is introduced
-   Seasonal indicator

#### Lag features

-   Lag 1
-   Lag 4
-   Lag 24
-   Lag 96
-   Lag 672

#### Rolling features

-   Rolling mean
-   Rolling standard deviation
-   Rolling minimum
-   Rolling maximum
-   Rolling median

### Load-profile features

For each client:

-   Mean load
-   Maximum load
-   Minimum load
-   Load variance
-   Peak-to-average ratio
-   Load factor
-   Daily variability
-   Weekly variability
-   Night/day ratio
-   Weekend/weekday ratio

### EDA requirements

Students must investigate:

-   Overall demand trends
-   Client-level demand patterns
-   Daily load curves
-   Weekly load curves
-   Seasonal effects
-   Peak periods
-   Low-demand periods
-   Correlation between clients
-   Highly variable consumers
-   Similar load profiles
-   Abnormal observations

### Data-quality checks

Implement automated checks for:

-   Duplicate timestamps
-   Invalid timestamps
-   Unexpected client IDs
-   Negative load values where not expected
-   Impossible intervals
-   Missing observations
-   Constant-value periods
-   Extreme outliers
-   Time-order violations

------------------------------------------------------------------------

## 3. Dashboard

Build a first-generation GridVision dashboard using **Streamlit** or an
equivalent framework.

### Dashboard pages

#### Page 1 --- Grid Overview

Display:

-   Total load
-   Average load
-   Peak load
-   Peak timestamp
-   Current/latest observed load
-   Daily/weekly/monthly trends

#### Page 2 --- Demand Analysis

Visualize:

-   Load curve
-   Daily profile
-   Weekly profile
-   Monthly profile
-   Seasonal comparison

#### Page 3 --- Consumer Intelligence

Display:

-   Consumer ranking by consumption
-   Load factor
-   Peak-to-average ratio
-   Consumer clusters
-   Consumer profiles

#### Page 4 --- Anomaly Analysis

Display:

-   Anomaly count
-   Anomaly timeline
-   Highest-severity anomalies
-   Affected consumers
-   Anomaly score distribution

#### Page 5 --- Forecasting

Display:

-   Actual vs predicted demand
-   Forecast horizon
-   Prediction intervals where available
-   Forecast error
-   Peak prediction

------------------------------------------------------------------------

## 4. ML Model

### A. Demand Forecasting

Start with simple baselines:

``` text
Naive Forecast
      ↓
Seasonal Naive
      ↓
Moving Average
      ↓
Linear Regression
      ↓
Random Forest
      ↓
Gradient Boosting
      ↓
XGBoost / LightGBM
      ↓
Optional Temporal Deep Learning
```

### Recommended features

-   Recent load
-   Same interval previous day
-   Same interval previous week
-   Rolling statistics
-   Hour
-   Day of week
-   Month
-   Weekend
-   Consumer ID/profile features

### Forecast horizons

Students should demonstrate at least:

-   Short horizon: next 1--4 hours
-   Day-ahead: next 24 hours
-   Optional week-ahead forecasting

### Forecast metrics

Use:

-   MAE
-   RMSE
-   MAPE where appropriate
-   sMAPE
-   WAPE
-   Peak-load error

Do not rely on a single metric.

------------------------------------------------------------------------

### B. Peak-Demand Prediction

Define a peak event using a documented threshold, such as:

``` text
load > historical percentile threshold
```

Then build:

``` text
Feature Engineering
      ↓
Logistic Regression
      ↓
Random Forest
      ↓
Gradient Boosting
      ↓
XGBoost / LightGBM
```

Evaluate:

-   Precision
-   Recall
-   F1
-   PR-AUC
-   Confusion matrix
-   Calibration

------------------------------------------------------------------------

### C. Consumption Anomaly Detection

Implement at least two approaches:

#### Statistical baseline

``` text
Rolling Mean
+
Rolling Standard Deviation
```

#### ML approach

``` text
Isolation Forest
```

Optional:

-   Local Outlier Factor
-   One-Class SVM
-   Autoencoder

Compare anomaly detection approaches and explain the operational meaning
of detected anomalies.

------------------------------------------------------------------------

### D. Load Segmentation

Use:

``` text
Feature Engineering
      ↓
Standardization
      ↓
K-Means
      ↓
Cluster Profiling
```

Optional:

-   Hierarchical clustering
-   DBSCAN
-   PCA/UMAP visualization

Expected profiles may include:

-   Stable consumers
-   High-peak consumers
-   Night-heavy consumers
-   Day-heavy consumers
-   Highly variable consumers

Students must avoid presenting cluster labels as externally defined
categories; they are model-generated profiles.

------------------------------------------------------------------------

## 5. Evaluation & Deliverables

### Evaluation framework

#### Forecasting

``` text
Baseline
   ↓
Candidate Models
   ↓
Backtesting
   ↓
Error Analysis
   ↓
Final Model
```

Use time-based splits rather than random train/test splitting for
forecasting.

### Required model artifacts

``` text
models/
├── demand_forecaster/
├── peak_classifier/
├── anomaly_detector/
└── load_segmenter/
```

### Required deliverables

-   Architecture diagram
-   Data dictionary
-   Data-quality report
-   SQL schema
-   EDA notebook/report
-   Feature engineering pipeline
-   Forecasting model
-   Peak-risk model
-   Anomaly detector
-   Load segmentation model
-   Evaluation report
-   Streamlit dashboard
-   README
-   Unit tests
-   Model artifacts

### CP1 acceptance criteria

The student must demonstrate:

-   Reproducible ingestion
-   Validated analytical dataset
-   Time-aware feature engineering
-   At least one production-quality forecasting model
-   Anomaly detection
-   Consumer/load segmentation
-   Evaluation against baselines
-   Working dashboard

------------------------------------------------------------------------

# CP2 --- Application + Container

## 1. Enhanced Data Pipeline

Convert the notebook-based workflow into a reusable pipeline.

``` text
Raw Dataset
    ↓
Extract
    ↓
Validate
    ↓
Transform
    ↓
Feature Engineering
    ↓
Train / Validate
    ↓
Model Artifact
```

### Pipeline requirements

-   Configuration-driven execution
-   Logging
-   Error handling
-   Data-quality checks
-   Reproducible runs
-   Versioned datasets
-   Versioned features
-   Model metadata

### Suggested project structure

``` text
gridvision/
├── app/
├── api/
├── data/
├── pipelines/
├── features/
├── models/
├── training/
├── evaluation/
├── tests/
├── dashboard/
├── docker/
├── configs/
├── docs/
└── scripts/
```

------------------------------------------------------------------------

## 2. Data & Model Engineering

Create reusable components for:

-   Feature generation
-   Forecast generation
-   Peak-risk scoring
-   Anomaly scoring
-   Consumer segmentation
-   Model loading
-   Model versioning
-   Prediction logging

### Model registry metadata

Store:

-   Model name
-   Model version
-   Training dataset version
-   Feature version
-   Training timestamp
-   Algorithm
-   Metrics
-   Hyperparameters
-   Approval status

------------------------------------------------------------------------

## 3. FastAPI Application

Expose GridVision through REST APIs.

### Required endpoints

``` text
GET  /health

GET  /api/v1/grid/summary

GET  /api/v1/load/history

GET  /api/v1/load/forecast

POST /api/v1/forecast

GET  /api/v1/peak-risk

GET  /api/v1/anomalies

GET  /api/v1/consumers/{client_id}/profile

GET  /api/v1/segments

GET  /api/v1/models

GET  /api/v1/metrics
```

### API requirements

-   Pydantic schemas
-   Input validation
-   Structured errors
-   OpenAPI documentation
-   Authentication-ready design
-   Request IDs
-   Logging
-   Unit and integration tests

------------------------------------------------------------------------

## 4. Container + UI

Create Docker images for:

``` text
GridVision API
GridVision Dashboard
```

Optional:

``` text
GridVision Worker
GridVision Scheduler
```

### Docker requirements

-   Multi-stage build where appropriate
-   Non-root user
-   Environment-based configuration
-   Health checks
-   Small runtime image
-   No secrets in image
-   Reproducible dependency installation

### UI integration

The dashboard must call the FastAPI service rather than directly loading
model files.

------------------------------------------------------------------------

## 5. MLOps

Implement:

``` text
Data
 ↓
Validation
 ↓
Training
 ↓
Evaluation
 ↓
Model Registration
 ↓
API Deployment
```

### CI/CD

Pipeline stages:

``` text
Lint
 ↓
Unit Tests
 ↓
Integration Tests
 ↓
Data/Schema Checks
 ↓
Build
 ↓
Security Scan
 ↓
Deploy
```

### Required testing

-   Unit tests
-   API tests
-   Feature tests
-   Model inference tests
-   Data-quality tests
-   Container health test

------------------------------------------------------------------------

# CP3 --- Cloud + Operations

## 1. Triggers & Automation

Implement automated workflows for:

-   Data arrival
-   Scheduled feature generation
-   Scheduled forecasting
-   Model retraining
-   Anomaly detection
-   Report generation

Example:

``` text
Scheduled Trigger
      ↓
Data Validation
      ↓
Feature Pipeline
      ↓
Prediction
      ↓
Store Results
      ↓
Update Dashboard
      ↓
Generate Alerts
```

------------------------------------------------------------------------

## 2. Production ML Operations

Implement:

### Batch prediction

Generate forecasts for:

-   Next 4 hours
-   Next 24 hours
-   Optional next 7 days

### Online inference

Allow API clients to submit a request and receive:

-   Forecast
-   Peak probability
-   Anomaly score

### Retraining

Trigger retraining when:

-   Scheduled interval is reached
-   Data volume threshold is reached
-   Model performance degrades
-   Data drift is detected

------------------------------------------------------------------------

## 3. Telemetry & Reliability

Monitor:

### Application metrics

-   Request count
-   Latency
-   Error rate
-   Throughput

### ML metrics

-   MAE
-   RMSE
-   Forecast bias
-   Peak prediction performance
-   Anomaly rate

### Data metrics

-   Missing values
-   Schema changes
-   Feature distribution
-   Timestamp gaps
-   Volume changes

### Drift

Monitor:

-   Feature drift
-   Prediction drift
-   Load-profile drift
-   Segment distribution drift

------------------------------------------------------------------------

## 4. Safe Model Rollout

Implement:

``` text
Candidate Model
      ↓
Offline Evaluation
      ↓
Shadow / Canary
      ↓
Performance Monitoring
      ↓
Approval
      ↓
Production
```

Maintain:

-   Model version
-   Rollout status
-   Previous production version
-   Rollback procedure

### Rollback condition

A rollback may be triggered by documented operational thresholds such
as:

-   Excessive forecast error
-   API failure
-   Data-quality failure
-   Significant drift
-   Invalid prediction output

------------------------------------------------------------------------

## 5. AWS Transfer

The architecture should remain cloud-neutral.

### Suggested AWS mapping

  GridVision Component          AWS Option
  ----------------------------- -------------------------------
  Object storage                S3
  Relational/analytical store   RDS / Aurora / Redshift
  Containers                    ECS / EKS
  API                           ECS / EKS / API Gateway
  Scheduler                     EventBridge
  Workflow                      Step Functions
  Model registry                SageMaker
  Monitoring                    CloudWatch
  Secrets                       Secrets Manager
  Container registry            ECR
  CI/CD                         CodePipeline / GitHub Actions

Students should explain the mapping rather than simply deploy without
architectural justification.

------------------------------------------------------------------------

# CP4 --- AI Enhancement

## 1. AI Product Specification

Transform GridVision into an **Energy Intelligence Copilot**.

### User questions

Examples:

> What is tomorrow's expected peak load?

> Which consumers show unusual consumption this week?

> Why did demand increase yesterday?

> Which load profiles are most volatile?

> Compare this week's demand with the previous week.

> What are the largest forecast errors?

> Show the operational risks for tomorrow.

> Explain this anomaly for client 117.

The AI must answer using tools and grounded data rather than inventing
analytical results.

------------------------------------------------------------------------

## 2. Knowledge Base + RAG

Create an energy knowledge base containing appropriate
public/organizational material such as:

-   Energy operations procedures
-   Forecasting documentation
-   Data dictionary
-   Model documentation
-   Energy terminology
-   Grid operational policies
-   Internal runbooks
-   Model cards
-   Alert-response procedures
-   Regulatory or standards documentation where licensing permits

### RAG pipeline

``` text
Documents
   ↓
Parsing
   ↓
Chunking
   ↓
Metadata
   ↓
Embeddings
   ↓
Vector Store
   ↓
Retriever
   ↓
Reranking
   ↓
Context
   ↓
LLM
```

### Required metadata

``` text
document_id
document_type
source
version
effective_date
topic
section
access_level
```

------------------------------------------------------------------------

## 3. RAG Evaluation

Build a test set covering:

### Retrieval

-   Recall@K
-   Precision@K
-   MRR
-   NDCG

### Answer quality

-   Groundedness
-   Correctness
-   Completeness
-   Citation/source accuracy

### Safety

-   Prompt injection
-   Unauthorized information requests
-   Unsupported operational claims
-   Missing context
-   Tool misuse

### Required evaluation categories

``` text
Easy
Medium
Complex
Ambiguous
Adversarial
Out-of-scope
```

The system should explicitly say when evidence is insufficient.

------------------------------------------------------------------------

## 4. Multi-Agent System

Implement an orchestrated GridVision multi-agent architecture.

``` text
                    ┌──────────────────┐
                    │ Supervisor Agent │
                    └────────┬─────────┘
                             │
       ┌─────────────────────┼──────────────────────┐
       ↓                     ↓                      ↓
 Forecast Agent       Anomaly Agent          Load Agent
       │                     │                      │
       └──────────────┬──────┴──────────────┬───────┘
                      ↓                     ↓
                Data Agent            Knowledge Agent
                      │                     │
                      └──────────┬──────────┘
                                 ↓
                       Energy Analyst Agent
```

### Agents

#### 1. Supervisor Agent

-   Understand user intent
-   Select specialist agent
-   Coordinate multi-step tasks
-   Enforce policy

#### 2. Forecast Agent

-   Retrieve forecasts
-   Compare forecast horizons
-   Analyze forecast error
-   Explain demand patterns

#### 3. Anomaly Agent

-   Query anomaly results
-   Rank anomalies
-   Investigate historical context
-   Explain anomaly scores

#### 4. Load Intelligence Agent

-   Analyze consumer/load profiles
-   Compare segments
-   Identify high-variability profiles

#### 5. Data Agent

-   Execute approved analytical queries
-   Validate data availability
-   Return structured results

#### 6. Knowledge Agent

-   Retrieve policies
-   Retrieve runbooks
-   Retrieve model documentation
-   Provide grounded explanations

#### 7. Energy Analyst Agent

-   Combine evidence
-   Produce executive summaries
-   Generate operational reports

------------------------------------------------------------------------

## 5. Production AI Demonstration

### MCP tools

Expose controlled GridVision capabilities through MCP.

Example tools:

``` text
get_grid_summary()

get_load_history(client_id, start_time, end_time)

get_demand_forecast(horizon)

get_peak_risk(date)

get_anomalies(start_time, end_time)

get_consumer_profile(client_id)

get_load_segments()

get_forecast_error(start_time, end_time)

compare_periods(period_a, period_b)

query_energy_metrics(metric, filters)

retrieve_energy_policy(topic)

create_energy_report(scope)
```

### Example interaction

``` text
User
 ↓
Supervisor
 ↓
Forecast Agent
 ↓
get_demand_forecast()
 ↓
Peak Risk Agent
 ↓
get_peak_risk()
 ↓
Knowledge Agent
 ↓
retrieve_energy_policy()
 ↓
Energy Analyst
 ↓
Grounded Response
```

### Guardrails

Implement:

-   Tool allow-list
-   Schema validation
-   Authentication and authorization
-   Parameter validation
-   Rate limiting
-   Prompt-injection defense
-   Retrieval grounding
-   Source attribution
-   Sensitive-data controls
-   Human approval for consequential actions
-   Audit logging
-   Full tool-call traceability

### Important operational boundary

GridVision is an **analytics and decision-support copilot**.

It must not independently execute safety-critical grid-control actions,
switch equipment, change protection settings, or issue consequential
operational commands without an authorized human and appropriate
operational controls.

------------------------------------------------------------------------

# Final System Architecture

``` text
                    ┌───────────────────────┐
                    │      Users / Ops      │
                    └───────────┬───────────┘
                                │
                        Dashboard / API
                                │
                    ┌───────────▼───────────┐
                    │    GridVision API     │
                    └───────────┬───────────┘
                                │
        ┌───────────────────────┼────────────────────────┐
        │                       │                        │
        ▼                       ▼                        ▼
   ML Services             Data Services            AI Layer
        │                       │                        │
 Forecasting              SQL / Lakehouse          RAG
 Peak Risk                Feature Store            Agents
 Anomaly                  Prediction Store         MCP
 Segmentation             Model Registry           Guardrails
        │                       │                        │
        └───────────────────────┼────────────────────────┘
                                │
                         Observability
                                │
                     Cloud + MLOps Platform
```

------------------------------------------------------------------------

# Final Capstone Deliverables

## Engineering

-   Complete source repository
-   Architecture documentation
-   Data pipeline
-   SQL analytical model
-   Feature pipelines
-   ML models
-   Model evaluation
-   Model registry
-   FastAPI service
-   Docker images
-   CI/CD pipeline
-   Cloud deployment
-   Monitoring
-   Drift detection
-   Retraining workflow
-   Rollback mechanism

## AI

-   Energy knowledge base
-   RAG pipeline
-   RAG evaluation suite
-   Supervisor agent
-   Specialist agents
-   MCP server
-   MCP tools
-   Guardrails
-   AI evaluation
-   Audit trail

## Product

-   GridVision dashboard
-   Energy analyst API
-   AI copilot
-   Forecast visualization
-   Anomaly investigation
-   Consumer/load segmentation
-   Operational reporting
-   Runbook/documentation

------------------------------------------------------------------------

# Final Demonstration Scenario

Students should demonstrate the complete lifecycle:

``` text
1. Ingest electricity data
        ↓
2. Validate and transform
        ↓
3. Build analytical SQL model
        ↓
4. Explore demand patterns
        ↓
5. Train forecasting model
        ↓
6. Detect anomalies
        ↓
7. Segment load profiles
        ↓
8. Evaluate models
        ↓
9. Package models
        ↓
10. Expose through FastAPI
        ↓
11. Containerize
        ↓
12. Deploy to cloud
        ↓
13. Monitor predictions
        ↓
14. Detect drift
        ↓
15. Retrieve energy knowledge
        ↓
16. Evaluate RAG
        ↓
17. Invoke specialist agents
        ↓
18. Use MCP tools
        ↓
19. Produce grounded analysis
        ↓
20. Present GridVision
```

------------------------------------------------------------------------

# Technical Defense Questions

Students should be able to explain:

### Data Engineering

-   Why was the source transformed from wide to long format?
-   How were timestamps normalized?
-   How were time gaps detected?
-   How was data leakage prevented?

### ML

-   Why was the forecasting baseline selected?
-   Why is random splitting inappropriate for time-series forecasting?
-   Why was the final model selected?
-   How were peak events defined?
-   How were anomalies validated?

### MLOps

-   How is a model versioned?
-   How is drift detected?
-   What triggers retraining?
-   How does rollback work?

### RAG

-   Why was the chunking strategy selected?
-   How was retrieval evaluated?
-   How are unsupported answers handled?
-   How is prompt injection mitigated?

### Agents

-   Why use multiple agents?
-   Which tasks are deterministic tools versus LLM reasoning?
-   How does the supervisor prevent incorrect routing?
-   How are tool calls validated?

### MCP

-   Why expose energy analytics through MCP?
-   Which tools are read-only?
-   Which operations require human approval?
-   How are tool calls audited?

### Production

-   What happens when the forecasting service fails?
-   What happens when data quality fails?
-   How does the dashboard behave during model downtime?
-   How is the previous model restored?

------------------------------------------------------------------------

# Final Outcome

**GridVision** should demonstrate that a student can move from raw
electricity time-series data to a production-oriented smart-energy
intelligence platform:

**Data Engineering → ML → API → Docker → Cloud → MLOps → RAG → Agents →
MCP → Enterprise AI**

The final system should be explainable, testable, observable, secure,
and suitable for human-in-the-loop energy operations.
