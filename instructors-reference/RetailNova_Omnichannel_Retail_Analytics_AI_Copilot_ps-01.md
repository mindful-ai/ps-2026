# Project 4 --- RetailNova

## Omnichannel Retail Analytics & AI Copilot

### Capstone Structure: ps-01

------------------------------------------------------------------------

# 1. Project Overview

## Objective

Build an end-to-end omnichannel retail intelligence platform that
progressively evolves from data engineering and ML into a
cloud-operated, AI-enabled retail copilot.

The project follows:

**ML → Application + Container → Cloud → Enhance with AI**

## Business Problem

Modern retailers operate across stores, websites, marketplaces and
fulfillment channels. They need unified intelligence to understand:

-   Product demand
-   Sales trends
-   Customer behaviour
-   Promotion impact
-   Inventory risk
-   Stockout risk
-   Product/customer affinity
-   Channel performance
-   Anomalous sales patterns
-   Operational decisions

RetailNova combines these capabilities into a unified omnichannel
analytics platform.

## Core ML Problems

1.  **Demand Forecasting**
    -   Product/store/channel demand
    -   Short-term forecasting
    -   Seasonal demand prediction
2.  **Customer Intelligence**
    -   Customer segmentation
    -   Customer lifetime/value proxy
    -   Churn/retention risk
    -   Product affinity
3.  **Inventory Intelligence**
    -   Stockout-risk prediction
    -   Replenishment recommendations
    -   Slow-moving inventory detection
4.  **Promotion & Sales Analytics**
    -   Promotion impact
    -   Price sensitivity
    -   Sales uplift analysis
5.  **Anomaly Detection**
    -   Unusual sales
    -   Sudden demand changes
    -   Channel-level anomalies

------------------------------------------------------------------------

# 2. Overall Architecture

``` text
POS / Store Sales
        +
E-Commerce Orders
        +
Product Catalog
        +
Inventory Data
        +
Customer Data
        +
Price / Promotion Data
        +
Weather / Regional Context
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
Forecasting + Customer ML + Inventory ML
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
Retail Knowledge Base
        ↓
RAG
        ↓
Multi-Agent System
        ↓
MCP + Guardrails
        ↓
Human Approval
        ↓
RETAILNOVA
OMNICHANNEL RETAIL AI COPILOT
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
Retail Dashboard
+
Forecast APIs
+
Customer Intelligence
+
Inventory Alerts
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

-   Omnichannel retail business problem
-   Target users
-   Functional requirements
-   Non-functional requirements
-   Data architecture
-   ML objectives
-   Dashboard requirements
-   API requirements
-   Evaluation strategy
-   Business KPIs

### Required architecture

``` text
Retail Sources
→ Ingestion
→ Validation
→ Lakehouse
→ SQL Model
→ Features
→ ML
→ Dashboard
```

### Target users

-   Retail analysts
-   Category managers
-   Merchandising teams
-   Supply-chain planners
-   Store operations
-   E-commerce teams
-   Retail executives

### Deliverables

-   Project specification
-   Architecture diagram
-   Data dictionary
-   Git repository
-   Initial API specification
-   KPI definition

------------------------------------------------------------------------

## 2. Data Engineering & EDA

### Recommended primary dataset

**M5 Forecasting Accuracy**

Source:

https://www.kaggle.com/competitions/m5-forecasting-accuracy/data

The M5 dataset provides daily Walmart sales together with calendar,
price and product/store hierarchy information.

### Core data

``` text
sales_train_validation
calendar
sell_prices
sample_submission
```

### Recommended enrichment

-   NOAA weather data
-   U.S. Census regional context
-   Optional Walmart Store Sales dataset

Sources:

https://www.ncei.noaa.gov/cdo-web/

https://www.census.gov/data/developers.html

Optional:

https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting/data

### Recommended combination

``` text
Sales
+
Calendar
+
Prices
+
Product Hierarchy
+
Store Hierarchy
+
Weather
+
Regional Context
```

### Data-engineering rule

Do not force unrelated datasets into row-level joins.

Use defensible keys such as:

``` text
date
store
product
category
department
geography
```

### EDA

Analyze:

-   Daily/weekly/monthly sales
-   Product hierarchy
-   Store performance
-   Channel/store differences
-   Seasonality
-   Promotions/events
-   Price changes
-   Demand volatility
-   Stockout proxies
-   Outliers
-   Missing values

### Deliverables

-   Data acquisition scripts
-   Multi-source ingestion
-   Data-quality report
-   EDA notebook/report
-   Feature engineering pipeline
-   Curated Parquet datasets

------------------------------------------------------------------------

## 3. Dashboard

Build an omnichannel retail intelligence dashboard.

### Required views

1.  Executive sales overview
2.  Product performance
3.  Store/channel performance
4.  Demand forecast
5.  Inventory-risk view
6.  Customer segments
7.  Promotion analysis
8.  Anomaly monitoring
9.  Model performance

### Example product view

``` text
Product
   ↓
Historical Demand
   ↓
Forecast
   ↓
Price / Promotion
   ↓
Inventory Risk
   ↓
Customer Affinity
   ↓
Recommended Action
```

### Suggested technologies

-   Streamlit
-   Plotly
-   Pandas
-   SQL/DuckDB

------------------------------------------------------------------------

## 4. ML Model

### Demand forecasting progression

``` text
Naive Baseline
→ Seasonal Naive
→ Moving Average
→ Linear Regression
→ Random Forest
→ XGBoost / LightGBM
→ Hierarchical Forecasting
→ Optional LSTM / Transformer
→ Production Forecast
```

### Customer segmentation

``` text
RFM / Behavioural Features
→ Standardization
→ K-Means
→ Hierarchical Clustering
→ Segment Profiling
```

### Customer churn/retention

``` text
Business Baseline
→ Logistic Regression
→ Random Forest
→ XGBoost / LightGBM
→ Threshold Optimization
→ Production Model
```

### Inventory-risk model

``` text
Demand Forecast
+
Demand Volatility
+
Historical Sales
+
Inventory Signals
+
Lead-Time Proxy
        ↓
Stockout Risk
```

### Anomaly detection

``` text
Statistical Baseline
→ Rolling Z-Score
→ Isolation Forest
→ Advanced Detector
```

------------------------------------------------------------------------

## 5. Evaluation & Deliverables

### Forecasting metrics

-   MAE
-   RMSE
-   WAPE
-   sMAPE
-   RMSSE
-   Forecast bias
-   Peak-demand error

### Classification metrics

-   ROC-AUC
-   PR-AUC
-   Precision
-   Recall
-   F1
-   Calibration

### Business metrics

-   Stockout-risk capture
-   Inventory-risk precision
-   Forecast bias
-   Promotion uplift estimate
-   Customer-retention capture

### Required deliverables

-   Model comparison
-   Error analysis
-   Forecast evaluation
-   Customer-segment analysis
-   Inventory-risk analysis
-   Explainability report
-   Dashboard
-   Model artifacts

### CP1 Exit Criteria

A working retail ML product that forecasts demand, identifies
customer/product patterns and highlights inventory or sales risks.

------------------------------------------------------------------------

# CP2 --- Application + Container

## 1. Enhanced Data Pipeline

Extend CP1 into a reproducible retail data platform.

### Requirements

-   Automated ingestion
-   Incremental processing
-   Schema validation
-   Referential-integrity checks
-   Data-quality thresholds
-   Bronze/Silver/Gold layers
-   SQL transformations
-   Feature generation
-   Data freshness monitoring

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

-   Reproducible feature pipelines
-   Feature versioning
-   Model versioning
-   Experiment tracking
-   Configuration management
-   Model artifact storage
-   Evaluation pipeline

### Required lineage

``` text
Source
→ Dataset Version
→ Feature Version
→ Model Version
→ Prediction Version
```

------------------------------------------------------------------------

## 3. FastAPI Application

Expose retail intelligence through APIs.

### Example endpoints

``` text
GET  /health
GET  /metadata

POST /forecast
POST /customer-segment
POST /churn-risk
POST /inventory-risk
POST /sales-anomaly

GET  /product/{product_id}
GET  /store/{store_id}

GET  /model-info
GET  /metrics
```

### Example request

``` json
{
  "store_id": "STORE001",
  "product_id": "PRODUCT001",
  "forecast_horizon": 14
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
Retail Dashboard
        ↓
FastAPI
        ↓
Feature Layer
        ↓
ML Models
        ↓
Forecast / Risk / Customer Results
```

The dashboard should communicate through APIs rather than directly
invoking model functions.

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

A reproducible, tested and containerized omnichannel retail analytics
application with APIs and dashboard.

------------------------------------------------------------------------

# CP3 --- Cloud + Operations

## 1. Triggers & Automation

Automate:

-   New sales-data ingestion
-   Inventory-data ingestion
-   Data validation
-   Feature generation
-   Demand forecasting
-   Inventory-risk scoring
-   Customer scoring
-   Anomaly detection
-   Report generation
-   Alert generation

### Example workflow

``` text
Schedule / Event
→ Ingest
→ Validate
→ Transform
→ Feature Generation
→ Forecast
→ Risk Scoring
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
→ Business KPI Check
→ Performance Comparison
→ Approval Gate
→ Production
```

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
-   Referential integrity
-   Distribution drift

### Forecasting

-   MAE
-   WAPE
-   Forecast bias
-   Prediction drift
-   Feature drift

### Retail operations

-   Stockout-risk alerts
-   Inventory-risk volume
-   Forecast exceptions
-   Anomaly volume
-   Recommendation volume

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
Business KPI Evaluation
      ↓
Shadow Testing
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

### Required deliverables

-   AWS architecture
-   Deployment configuration
-   CI/CD pipeline
-   Cloud deployment
-   Monitoring dashboard
-   Operations runbook
-   Rollback procedure

### CP3 Exit Criteria

A cloud-operated retail ML platform with automated data/model pipelines,
monitoring, model lifecycle management and controlled deployment.

------------------------------------------------------------------------

# CP4 --- AI Enhancement

## 1. AI Product Specification

Transform RetailNova into an **Omnichannel Retail AI Copilot**.

### AI capabilities

The copilot should answer questions such as:

-   Why did sales change?
-   What is the expected demand for a product?
-   Which products have elevated stockout risk?
-   Which stores/channels are underperforming?
-   Which customer segments are changing?
-   What promotion patterns are associated with demand changes?
-   What evidence supports a recommended action?

### AI architecture

``` text
User
 ↓
Supervisor Agent
 ↓
 ├── Forecast Agent
 ├── Inventory Agent
 ├── Customer Agent
 ├── Product Agent
 ├── Data Agent
 ├── Knowledge Agent
 └── Retail Analyst
```

------------------------------------------------------------------------

## 2. Knowledge Base + RAG

Build a retail knowledge base containing:

-   Product policies
-   Pricing policies
-   Promotion guidelines
-   Inventory SOPs
-   Store operating procedures
-   Merchandising guidelines
-   Supplier documentation
-   Return/refund policies
-   Customer-service procedures
-   Internal business documentation

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

Create a retail-specific evaluation dataset.

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
Q1: What is the documented process for handling a stockout?

Q2: Which promotion policy applies to this product category?

Q3: What evidence supports this inventory recommendation?

Q4: What is the documented return procedure?

Q5: Which source supports this merchandising recommendation?
```

### Deliverables

-   Golden question-answer dataset
-   Retrieval evaluation
-   Answer evaluation
-   Error analysis
-   RAG evaluation report

------------------------------------------------------------------------

## 4. Multi-Agent System

Implement an orchestrated retail-agent system.

### Supervisor Agent

Routes requests and coordinates specialist agents.

### Forecast Agent

-   Calls demand-forecasting API
-   Explains demand trends
-   Produces forecast summaries

### Inventory Agent

-   Queries inventory/risk data
-   Identifies stockout risk
-   Produces replenishment candidates

### Customer Agent

-   Analyzes customer segments
-   Identifies product affinity
-   Summarizes retention/churn signals

### Product Agent

-   Analyzes product performance
-   Compares categories
-   Identifies product anomalies

### Data Agent

-   Queries approved structured data
-   Performs controlled analytics
-   Produces numerical evidence

### Knowledge Agent

-   Retrieves relevant retail documentation
-   Provides grounded procedural information

### Retail Analyst

-   Combines model results
-   Combines structured data
-   Combines retrieved knowledge
-   Produces an evidence-backed business analysis

### Example workflow

``` text
User:
"Why are sales of Product X falling?"

        ↓

Supervisor
        ↓
Forecast Agent
        ↓
Product Agent
        ↓
Customer Agent
        ↓
Data Agent
        ↓
Knowledge Agent
        ↓
Retail Analyst
        ↓
Evidence-backed Explanation
        ↓
Recommended Action
        ↓
Human Approval
```

------------------------------------------------------------------------

## 5. Production AI Demonstration

### Scenario 1 --- Demand Forecast

``` text
User:
"What is the expected demand for Product X next week?"
```

System:

-   Calls forecast API
-   Returns forecast
-   Shows historical context
-   Explains important drivers
-   Displays uncertainty/error information

### Scenario 2 --- Inventory Risk

``` text
User:
"Which products are at high stockout risk?"
```

System:

-   Queries inventory-risk model
-   Retrieves product/store information
-   Ranks investigation candidates
-   Provides supporting evidence

### Scenario 3 --- Sales Investigation

``` text
User:
"Why did sales decline last week?"
```

System:

-   Queries sales history
-   Analyzes product/store/channel trends
-   Checks price/promotion context
-   Retrieves relevant business documentation
-   Produces an evidence-backed analysis

### Scenario 4 --- MCP Integration

Expose approved capabilities through MCP tools/resources.

Example tools:

``` text
get_sales_forecast()
get_inventory_risk()
get_product_performance()
get_customer_segment()
query_sales_history()
detect_sales_anomaly()
retrieve_retail_policy()
calculate_promotion_impact()
create_retail_report()
```

### Guardrails

Implement:

-   Tool allow-list
-   Input validation
-   Output validation
-   Access control
-   Retrieval grounding
-   Prompt-injection defenses
-   Sensitive-data controls
-   Human approval for consequential actions
-   Audit logging
-   Model/version traceability

### CP4 Exit Criteria

A production-style Omnichannel Retail AI Copilot that combines
forecasting, customer intelligence, inventory analytics, RAG, tools,
multi-agent orchestration, MCP, guardrails and human approval.

------------------------------------------------------------------------

# 4. Dataset Strategy

## Primary Dataset

### M5 Forecasting Accuracy

Source:

https://www.kaggle.com/competitions/m5-forecasting-accuracy/data

Use M5 as the principal forecasting and retail data-engineering
challenge.

## Recommended Enrichment

### NOAA Climate Data Online

Source:

https://www.ncei.noaa.gov/cdo-web/

Use weather only where store/location/time mapping is defensible.

### U.S. Census Data API

Source:

https://www.census.gov/data/developers.html

Use regional demographic/economic context where geographic mapping is
valid.

### Optional Walmart Store Sales

Source:

https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting/data

Use as a separate comparative forecasting experiment rather than forcing
an artificial join with M5.

### Data-engineering rule

A multi-source architecture is encouraged, but every join must have a
documented business meaning.

------------------------------------------------------------------------

# 5. Lakehouse Structure

``` text
data/
│
├── raw/
│   ├── m5/
│   ├── weather/
│   ├── census/
│   └── optional_walmart/
│
├── bronze/
│   ├── sales/
│   ├── prices/
│   ├── calendar/
│   ├── stores/
│   ├── products/
│   └── context/
│
├── silver/
│   ├── sales_clean/
│   ├── price_clean/
│   ├── calendar_clean/
│   ├── store_clean/
│   └── context_clean/
│
└── gold/
    ├── demand_features/
    ├── customer_features/
    ├── inventory_features/
    ├── promotion_features/
    ├── anomaly_features/
    ├── forecasts/
    ├── recommendations/
    └── model_metrics/
```

------------------------------------------------------------------------

# 6. SQL Data Model

Recommended model:

``` text
dim_date
dim_store
dim_product
dim_category
dim_department
dim_channel
dim_geography
dim_promotion
dim_customer

fact_sales
fact_price
fact_inventory
fact_promotion
fact_customer_order
fact_weather

feature_demand
feature_customer
feature_inventory_risk
feature_promotion
feature_anomaly

prediction_forecast
prediction_churn
prediction_inventory_risk
prediction_anomaly

model_metrics
```

### Example relationships

``` text
dim_product
      ↓
fact_sales
      ↓
feature_demand
      ↓
prediction_forecast
```

and:

``` text
dim_store
+
dim_product
+
fact_sales
+
fact_inventory
      ↓
feature_inventory_risk
      ↓
prediction_inventory_risk
```

------------------------------------------------------------------------

# 7. Feature Engineering

## Demand Features

-   Lag sales
-   Rolling mean
-   Rolling standard deviation
-   Previous-week demand
-   Previous-month demand
-   Demand trend
-   Demand volatility

## Product Features

-   Category
-   Department
-   Price
-   Price change
-   Product popularity
-   Historical sales
-   Product lifecycle proxy

## Store/Channel Features

-   Store
-   Geography
-   Channel
-   Store historical demand
-   Channel demand
-   Regional characteristics

## Promotion Features

-   Promotion indicator
-   Event indicator
-   Price discount
-   Promotion duration
-   Historical promotion response

## Customer Features

Where customer-level data is available:

-   Recency
-   Frequency
-   Monetary value
-   Product affinity
-   Category affinity
-   Purchase frequency
-   Customer tenure

## Inventory Features

-   Recent demand
-   Demand volatility
-   Inventory level
-   Stockout proxy
-   Replenishment interval
-   Forecast demand

------------------------------------------------------------------------

# 8. ML Progression

``` text
Business Baseline
        ↓
Seasonal Naive
        ↓
Moving Average
        ↓
Linear Regression
        ↓
Random Forest
        ↓
XGBoost / LightGBM
        ↓
Hierarchical Forecasting
        ↓
Optional Temporal Deep Learning
        ↓
Model Comparison
        ↓
Production Forecast
```

### Customer intelligence

``` text
RFM / Behavioural Features
→ Clustering
→ Segment Profiling
→ Churn Model
→ Product Affinity
```

### Inventory risk

``` text
Forecast
+
Inventory
+
Volatility
+
Historical Patterns
        ↓
Risk Score
        ↓
Threshold Optimization
        ↓
Production Model
```

------------------------------------------------------------------------

# 9. Key KPIs

  Category      KPI
  ------------- -------------------------
  Forecasting   MAE
  Forecasting   RMSE
  Forecasting   WAPE
  Forecasting   sMAPE
  Forecasting   RMSSE
  Forecasting   Forecast Bias
  Inventory     Stockout-risk precision
  Inventory     Stockout-risk recall
  Customer      ROC-AUC
  Customer      PR-AUC
  Customer      F1
  Promotion     Uplift estimate
  Data          Data-quality pass rate
  Data          Data freshness
  API           Latency
  API           Error rate
  Model         Feature drift
  Model         Prediction drift
  AI            Retrieval relevance
  AI            Groundedness
  AI            Hallucination rate
  AI            Tool success rate
  Operations    Alert volume
  Business      Forecast error
  Business      Inventory-risk capture

------------------------------------------------------------------------

# 10. Suggested Repository Structure

``` text
retailnova/
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
-   Integrated retail dataset
-   Data-quality report
-   EDA
-   Feature pipeline
-   Demand forecasting models
-   Customer analytics
-   Inventory-risk model
-   Anomaly model
-   Evaluation report
-   Dashboard
-   Model artifacts

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
-   Retail knowledge base
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

The final RetailNova demonstration should show:

``` text
RETAIL DATA
     ↓
DATA ENGINEERING
     ↓
SQL / LAKEHOUSE
     ↓
DEMAND FORECASTING
     ↓
CUSTOMER INTELLIGENCE
     ↓
INVENTORY RISK
     ↓
SALES ANOMALY DETECTION
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
RETAILNOVA
OMNICHANNEL RETAIL AI COPILOT
```

## Final Student Outcome

Students demonstrate an integrated capability across:

**Data Science → Data Engineering → ML Engineering → Production AI
Engineering → Cloud → MLOps → RAG → Agentic AI → MCP → Enterprise Retail
AI**
