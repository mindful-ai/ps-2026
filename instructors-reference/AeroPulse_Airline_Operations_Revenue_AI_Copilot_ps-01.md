# Project 2 --- AeroPulse

## Airline Operations, Revenue & AI Copilot

### Capstone Structure: ps-01

------------------------------------------------------------------------

# 1. Project Overview

## Objective

Build an end-to-end airline intelligence platform that progressively
evolves from data engineering and ML into a cloud-operated, AI-enabled
airline operations and revenue copilot.

The project follows:

**ML → Application + Container → Cloud → Enhance with AI**

## Business Problem

Airlines operate complex networks involving flights, aircraft, airports,
schedules, weather, passengers, fares and operational disruptions. They
need unified intelligence to understand:

-   Flight delays
-   Cancellation risk
-   Arrival/departure performance
-   Airport congestion
-   Aircraft utilization
-   Route performance
-   Revenue and fare patterns
-   Passenger demand
-   Disruption impact
-   Operational recovery options

AeroPulse combines operational analytics, predictive ML and AI-assisted
decision support.

## Core ML Problems

1.  **Flight Delay Prediction**
    -   Predict departure/arrival delay
    -   Identify high-risk flights
    -   Estimate delay severity
2.  **Cancellation / Disruption Risk**
    -   Predict cancellation risk
    -   Identify operational disruption patterns
    -   Prioritize flights requiring attention
3.  **Revenue & Demand Forecasting**
    -   Forecast passenger demand
    -   Analyze route-level demand
    -   Predict booking/revenue proxies
4.  **Airport / Route Intelligence**
    -   Identify congestion patterns
    -   Compare route performance
    -   Analyze airport operational risk
5.  **Optional Revenue Optimization**
    -   Fare-demand modeling
    -   Price sensitivity
    -   Seat-demand forecasting
    -   What-if revenue analysis

------------------------------------------------------------------------

# 2. Overall Architecture

``` text
Flight Operations Data
        +
Airport / Route Data
        +
Weather Data
        +
Aircraft / Schedule Data
        +
Passenger / Booking Data
        +
Fare / Revenue Data
        +
Aviation Policies / SOPs
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
Delay / Cancellation / Demand ML
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
Aviation Knowledge Base
        ↓
RAG
        ↓
Multi-Agent System
        ↓
MCP + Guardrails
        ↓
Human Approval
        ↓
AEROPULSE
AIRLINE AI COPILOT
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
Airline Operations Dashboard
+
Delay APIs
+
Disruption Alerts
+
Revenue / Demand Analytics
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

-   Airline business problem
-   Target users
-   Operational and revenue use cases
-   Functional requirements
-   Non-functional requirements
-   Data architecture
-   ML target definitions
-   Dashboard requirements
-   API requirements
-   Evaluation strategy
-   Business KPIs

### Required architecture

``` text
Aviation Sources
→ Ingestion
→ Validation
→ Lakehouse
→ SQL Model
→ Features
→ ML
→ Dashboard
```

### Target users

-   Flight operations analysts
-   Network planners
-   Revenue analysts
-   Airport operations teams
-   Airline executives

### Deliverables

-   Project specification
-   Architecture diagram
-   Data dictionary
-   Git repository
-   Initial API specification
-   KPI definition
-   Assumptions and limitations

------------------------------------------------------------------------

## 2. Data Engineering & EDA

### Recommended primary dataset

**U.S. Bureau of Transportation Statistics --- On-Time Performance**

Source:

https://www.transtats.bts.gov/Fields.asp?gnoyr_VQ=FGJ

The BTS on-time performance data provides flight-level operational
information suitable for delay and cancellation analytics.

### Core fields

Typical fields include:

``` text
Flight Date
Airline
Origin
Destination
Scheduled Departure
Actual Departure
Departure Delay
Scheduled Arrival
Actual Arrival
Arrival Delay
Cancelled
Cancellation Code
Air Time
Distance
```

### Recommended enrichment

#### NOAA Climate Data Online

Source:

https://www.ncei.noaa.gov/cdo-web/

Potential variables:

-   Temperature
-   Precipitation
-   Wind
-   Weather events
-   Visibility-related context where available

#### U.S. airport/location information

Use public airport/location metadata to map:

``` text
Airport Code
→ Latitude / Longitude
→ City
→ State
→ Region
```

### Optional revenue/demand dataset

Use a public airline booking/fare dataset if a suitable licensed dataset
is available. For the main capstone, keep the operational prediction
problem independent from any dataset that lacks reliable linkage.

### Recommended combination

``` text
BTS Flight Operations
+
Airport Metadata
+
NOAA Weather
+
Calendar / Holiday Context
```

### Data-engineering rule

Do not invent passenger, booking or revenue values when the operational
dataset does not contain them.

If a revenue dataset cannot be validly joined, treat revenue analytics
as a separate experiment.

### EDA

Analyze:

-   Flights by airline
-   Flights by airport
-   Routes
-   Departure/arrival delay
-   Cancellation rate
-   Delay distributions
-   Time-of-day patterns
-   Day-of-week patterns
-   Seasonal effects
-   Airport effects
-   Route effects
-   Weather relationships
-   Distance
-   Scheduled vs. actual operations
-   Missing values
-   Outliers

### Deliverables

-   Data acquisition scripts
-   Multi-source ingestion
-   Data-quality report
-   EDA notebook/report
-   Feature engineering pipeline
-   Curated Parquet datasets

------------------------------------------------------------------------

## 3. Dashboard

Build an airline intelligence dashboard.

### Required views

1.  Executive operations overview
2.  Flight delay analysis
3.  Cancellation analysis
4.  Airport performance
5.  Route performance
6.  Delay-risk predictions
7.  Weather/operations analysis
8.  Revenue/demand analytics where data permits
9.  Model performance

### Example flight view

``` text
Flight
  ↓
Schedule
  ↓
Airport / Route
  ↓
Weather
  ↓
Historical Pattern
  ↓
Delay Risk
  ↓
Operational Explanation
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

### Delay prediction progression

``` text
Historical Average Baseline
→ Logistic Regression
→ Random Forest
→ XGBoost / LightGBM
→ Class Weighting
→ Threshold Optimization
→ Explainability
→ Production Model
```

### Delay regression

``` text
Mean/Median Baseline
→ Linear Regression
→ Random Forest Regressor
→ Gradient Boosting
→ XGBoost / LightGBM
→ Production Model
```

### Cancellation-risk progression

``` text
Business Rule
→ Logistic Regression
→ Random Forest
→ XGBoost / LightGBM
→ Calibration
→ Threshold Optimization
→ Production Model
```

### Demand/revenue progression

Where suitable data is available:

``` text
Historical Demand Baseline
→ Regression
→ Gradient Boosting
→ Time-Series Forecasting
→ Optional Temporal DL
```

### Important rule

Use only information available before the prediction time.

For example, do not use:

``` text
Actual Arrival Delay
Actual Departure Time
```

to predict a flight's departure delay when those values are only known
after departure.

------------------------------------------------------------------------

## 5. Evaluation & Deliverables

### Delay classification metrics

-   ROC-AUC
-   PR-AUC
-   Precision
-   Recall
-   F1
-   Confusion matrix
-   Calibration
-   False-negative rate

### Delay regression metrics

-   MAE
-   RMSE
-   Median absolute error
-   Error by airport
-   Error by route
-   Error by airline

### Cancellation metrics

-   Precision
-   Recall
-   F1
-   PR-AUC
-   False-alert rate

### Business metrics

-   High-risk flight capture
-   Delay-risk precision
-   Cancellation-risk capture
-   Airport-risk detection
-   Operational alert volume

### Required deliverables

-   Model comparison
-   Error analysis
-   Airport/route analysis
-   Explainability
-   Threshold analysis
-   Evaluation report
-   Dashboard
-   Model artifacts

### CP1 Exit Criteria

A working airline ML product that predicts flight delays/cancellation
risk and provides operational intelligence through a dashboard.

------------------------------------------------------------------------

# CP2 --- Application + Container

## 1. Enhanced Data Pipeline

Extend CP1 into a reproducible aviation data platform.

### Requirements

-   Automated ingestion
-   Incremental processing
-   Schema validation
-   Referential-integrity checks
-   Timestamp validation
-   Airport-code validation
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
-   Dataset/version lineage

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

Expose airline intelligence through APIs.

### Example endpoints

``` text
GET  /health
GET  /metadata

POST /delay-risk
POST /delay-duration
POST /cancellation-risk
POST /airport-risk
POST /route-performance

GET  /flight/{flight_id}
GET  /airport/{airport_code}
GET  /route/{origin}/{destination}

GET  /model-info
GET  /metrics
```

### Example request

``` json
{
  "airline": "XX",
  "origin": "JFK",
  "destination": "ORD",
  "scheduled_departure": "2026-07-15T14:30:00",
  "distance": 740
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
-   Authentication-ready architecture

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
Airline Dashboard
        ↓
FastAPI
        ↓
Feature Layer
        ↓
ML Models
        ↓
Risk / Forecast Results
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

A reproducible, tested and containerized airline analytics application
with APIs and dashboard.

------------------------------------------------------------------------

# CP3 --- Cloud + Operations

## 1. Triggers & Automation

Automate:

-   New flight-data ingestion
-   Weather-data ingestion
-   Data validation
-   Feature generation
-   Delay-risk scoring
-   Cancellation-risk scoring
-   Model training
-   Model evaluation
-   Operations reporting
-   Alert generation

### Example workflow

``` text
Schedule / Event
→ Ingest
→ Validate
→ Transform
→ Feature Generation
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
→ Performance Comparison
→ Airport/Route Evaluation
→ Business KPI Check
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
-   Airport-code validity
-   Timestamp validity
-   Distribution drift

### Model

-   Prediction drift
-   Feature drift
-   Delay prediction error
-   Calibration
-   Airport-level performance
-   Route-level performance

### Airline operations

-   High-risk flight volume
-   Alert volume
-   False-alert rate
-   Airport congestion indicators
-   Delay-risk concentration

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
Airport/Route Evaluation
      ↓
Shadow Testing
      ↓
Operations Review
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

A cloud-operated airline ML platform with automated pipelines,
monitoring, model lifecycle management and controlled deployment.

------------------------------------------------------------------------

# CP4 --- AI Enhancement

## 1. AI Product Specification

Transform AeroPulse into an **Airline Operations & Revenue AI Copilot**.

### AI capabilities

The copilot should answer questions such as:

-   Why is this flight at high delay risk?
-   Which airports are experiencing elevated operational risk?
-   What routes are showing unusual delay patterns?
-   What caused today's operational deterioration?
-   What does the relevant airline procedure recommend?
-   What demand pattern is visible for this route?
-   What evidence supports the recommended operational action?

### AI architecture

``` text
User
 ↓
Supervisor Agent
 ↓
 ├── Flight Risk Agent
 ├── Airport Agent
 ├── Route Agent
 ├── Revenue/Demand Agent
 ├── Data Agent
 ├── Knowledge Agent
 └── Airline Analyst
```

------------------------------------------------------------------------

## 2. Knowledge Base + RAG

Build an aviation knowledge base containing permitted documents such as:

-   Airline SOPs
-   Airport operating procedures
-   Disruption-management procedures
-   Safety procedures
-   Crew/ground-handling procedures
-   Revenue-management documentation
-   Customer-service policies
-   Public aviation regulations and guidance
-   Internal operational documentation

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

Create an aviation-specific evaluation dataset.

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
Q1: What is the documented procedure for handling a major delay?

Q2: Which disruption-management procedure applies to this scenario?

Q3: What operational limits are specified in the relevant documentation?

Q4: What source supports the proposed operational action?

Q5: What is the documented customer-service procedure during a cancellation?
```

### Deliverables

-   Golden question-answer dataset
-   Retrieval evaluation
-   Answer evaluation
-   Error analysis
-   RAG evaluation report

------------------------------------------------------------------------

## 4. Multi-Agent System

Implement an orchestrated airline-agent system.

### Supervisor Agent

Routes requests and coordinates specialist agents.

### Flight Risk Agent

-   Calls delay-risk API
-   Calls cancellation-risk API
-   Explains risk factors
-   Produces flight-risk summaries

### Airport Agent

-   Queries airport performance
-   Identifies congestion patterns
-   Produces airport-risk analysis

### Route Agent

-   Analyzes route history
-   Compares route performance
-   Identifies abnormal patterns

### Revenue/Demand Agent

-   Analyzes demand forecasts
-   Examines fare/revenue data where available
-   Produces demand insights

### Data Agent

-   Queries approved structured data
-   Performs controlled analytics
-   Produces numerical evidence

### Knowledge Agent

-   Retrieves aviation policies/SOPs
-   Provides grounded procedural information

### Airline Analyst

-   Combines model results
-   Combines structured data
-   Combines retrieved knowledge
-   Produces an evidence-backed operational brief

### Example workflow

``` text
User:
"Why is Flight XX123 at high delay risk?"

        ↓

Supervisor
        ↓
Flight Risk Agent
        ↓
Airport Agent
        ↓
Route Agent
        ↓
Data Agent
        ↓
Knowledge Agent
        ↓
Airline Analyst
        ↓
Evidence-backed Explanation
        ↓
Recommended Review
        ↓
Human Approval
```

------------------------------------------------------------------------

## 5. Production AI Demonstration

### Scenario 1 --- Flight Risk

``` text
User:
"Why is this flight at high delay risk?"
```

System:

-   Calls delay-risk model
-   Analyzes airport and route history
-   Incorporates available weather/context
-   Explains important model factors
-   Provides evidence

### Scenario 2 --- Airport Investigation

``` text
User:
"Which airports have elevated operational risk today?"
```

System:

-   Queries approved operational data
-   Computes risk indicators
-   Identifies unusual patterns
-   Produces an operational summary

### Scenario 3 --- Disruption Procedure

``` text
User:
"What is the documented procedure for a major cancellation?"
```

System:

-   Retrieves relevant SOP/policy documents
-   Cites sources
-   Produces a grounded summary
-   Escalates when the documentation is ambiguous

### Scenario 4 --- Revenue/Demand

``` text
User:
"What is the expected demand pattern for this route?"
```

System:

-   Calls demand model where available
-   Analyzes historical route data
-   Provides forecast/context
-   Explains limitations of the underlying data

### Scenario 5 --- MCP Integration

Expose approved capabilities through MCP tools/resources.

Example tools:

``` text
get_flight_delay_risk()
get_cancellation_risk()
get_airport_performance()
get_route_performance()
query_flight_history()
get_weather_context()
get_demand_forecast()
retrieve_airline_policy()
create_operations_report()
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
-   Human approval for consequential operational actions
-   Audit logging
-   Model/version traceability

### Important Aviation Principle

The AI copilot should support authorized airline personnel rather than
independently executing safety-critical or operationally consequential
actions.

------------------------------------------------------------------------

### CP4 Exit Criteria

A production-style Airline Operations & Revenue AI Copilot that combines
predictive ML, operational analytics, RAG, tools, multi-agent
orchestration, MCP, guardrails and human approval.

------------------------------------------------------------------------

# 4. Dataset Strategy

## Primary Dataset

### U.S. BTS On-Time Performance

Source:

https://www.transtats.bts.gov/Fields.asp?gnoyr_VQ=FGJ

Use this as the main flight-operations dataset.

## Recommended Enrichment

### NOAA Climate Data Online

Source:

https://www.ncei.noaa.gov/cdo-web/

Use weather information only where airport/time mapping is defensible.

### Airport Metadata

Use public airport metadata for:

-   Airport coordinates
-   Geographic region
-   Airport type
-   Location

### Optional Revenue/Demand Dataset

A separate public fare/booking dataset can be used for revenue analytics
when licensing and joinability are appropriate.

### Data-engineering rule

Do not manufacture:

-   Passenger counts
-   Revenue
-   Fare
-   Booking information

when those variables are absent from the primary dataset.

If valid revenue data cannot be integrated, implement revenue analytics
as a separate experiment.

------------------------------------------------------------------------

# 5. Lakehouse Structure

``` text
data/
│
├── raw/
│   ├── bts_flights/
│   ├── airport_metadata/
│   ├── weather/
│   ├── calendar/
│   └── optional_revenue/
│
├── bronze/
│   ├── flights/
│   ├── airports/
│   ├── weather/
│   └── revenue/
│
├── silver/
│   ├── flights_clean/
│   ├── airport_clean/
│   ├── weather_clean/
│   └── revenue_clean/
│
└── gold/
    ├── flight_features/
    ├── airport_features/
    ├── route_features/
    ├── delay_features/
    ├── cancellation_features/
    ├── demand_features/
    ├── predictions/
    └── model_metrics/
```

------------------------------------------------------------------------

# 6. SQL Data Model

Recommended model:

``` text
dim_date
dim_airline
dim_airport
dim_route
dim_aircraft
dim_weather
dim_time
dim_flight

fact_flight_operation
fact_flight_delay
fact_cancellation
fact_weather

feature_delay_risk
feature_cancellation_risk
feature_airport_risk
feature_route_performance
feature_demand

prediction_delay
prediction_cancellation
prediction_demand

model_metrics
```

### Example relationships

``` text
dim_flight
      ↓
fact_flight_operation
      ↓
feature_delay_risk
      ↓
prediction_delay
```

and:

``` text
dim_airport
+
dim_route
+
fact_flight_operation
+
fact_weather
      ↓
feature_airport_risk
      ↓
prediction_cancellation / delay
```

------------------------------------------------------------------------

# 7. Feature Engineering

## Flight Features

-   Airline
-   Origin
-   Destination
-   Distance
-   Scheduled departure
-   Scheduled arrival
-   Departure hour
-   Arrival hour
-   Day of week
-   Month
-   Season

## Airport Features

-   Historical average delay
-   Historical cancellation rate
-   Flight volume
-   Hourly congestion proxy
-   Recent delay trend

## Route Features

-   Historical route delay
-   Historical route cancellation
-   Flight frequency
-   Average distance
-   Recent route performance

## Weather Features

-   Temperature
-   Precipitation
-   Wind
-   Weather events
-   Other available airport-relevant conditions

## Temporal Features

-   Hour
-   Day
-   Week
-   Month
-   Holiday
-   Weekend
-   Season

## Derived Features

-   Airport delay score
-   Route delay score
-   Recent delay rate
-   Rolling delay statistics
-   Disruption score
-   Delay-risk score

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
Production Model
```

### Delay regression

``` text
Mean/Median Baseline
→ Linear Regression
→ Random Forest
→ Gradient Boosting
→ XGBoost / LightGBM
→ Production Model
```

### Demand forecasting

Where suitable data exists:

``` text
Historical Baseline
→ Moving Average
→ Regression
→ Gradient Boosting
→ Time-Series Model
→ Optional Temporal DL
```

------------------------------------------------------------------------

# 9. Key KPIs

  Category               KPI
  ---------------------- --------------------------
  Delay Classification   ROC-AUC
  Delay Classification   PR-AUC
  Delay Classification   Precision
  Delay Classification   Recall
  Delay Classification   F1
  Delay Regression       MAE
  Delay Regression       RMSE
  Cancellation           Precision
  Cancellation           Recall
  Cancellation           F1
  Operations             High-risk flight capture
  Operations             False-alert rate
  Airport                Delay-rate error
  Route                  Delay-rate error
  Data                   Data-quality pass rate
  Data                   Data freshness
  API                    Latency
  API                    Error rate
  Model                  Feature drift
  Model                  Prediction drift
  AI                     Retrieval relevance
  AI                     Groundedness
  AI                     Hallucination rate
  AI                     Tool success rate
  Operations             Alert volume

------------------------------------------------------------------------

# 10. Suggested Repository Structure

``` text
aeropulse/
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
-   Integrated flight dataset
-   Data-quality report
-   EDA
-   Feature pipeline
-   Delay-risk model
-   Delay-duration model
-   Cancellation-risk model
-   Airport/route analytics
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
-   Aviation knowledge base
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

The final AeroPulse demonstration should show:

``` text
FLIGHT & AVIATION DATA
        ↓
DATA ENGINEERING
        ↓
SQL / LAKEHOUSE
        ↓
DELAY PREDICTION
        ↓
CANCELLATION RISK
        ↓
AIRPORT & ROUTE INTELLIGENCE
        ↓
DEMAND / REVENUE ANALYTICS
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
AEROPULSE
AIRLINE OPERATIONS & REVENUE AI COPILOT
```

## Final Student Outcome

Students demonstrate an integrated capability across:

**Data Science → Data Engineering → ML Engineering → Production AI
Engineering → Cloud → MLOps → RAG → Agentic AI → MCP → Enterprise
Aviation AI**
