# Project 1 — GridSense AI
## Intelligent Energy Demand Forecasting & Grid Operations Platform

**Objective:** Build an end-to-end energy intelligence platform that starts with ML-based demand forecasting and progressively evolves into a cloud-operated, AI-enabled energy operations copilot.

**Learning progression:**  
**CP1 — ML Product → CP2 — Application + Container → CP3 — Cloud + Operations → CP4 — AI Enhancement**

---

# 1. Overall Product Specification

### Business Problem

Grid operators need to anticipate electricity demand to improve:

- Demand planning
- Generation scheduling
- Peak-load management
- Grid reliability
- Operational decision-making
- Energy efficiency
- Emissions awareness

### Core ML Problem

Predict electricity demand for the next:

- 1 hour
- 6 hours
- 24 hours
- Optional: 7 days

### Example KPIs

| Area | KPI |
|---|---|
| Forecasting | MAE |
| Forecasting | RMSE |
| Forecasting | MAPE / sMAPE |
| Peak prediction | Peak-demand error |
| Application | API latency |
| Data | Data-quality pass rate |
| Operations | Model drift |
| AI | RAG retrieval/groundedness |
| Business | Peak-demand planning accuracy |

---

# 2. Overall Architecture

```text
                    ┌─────────────────────┐
                    │   Public Data       │
                    │                     │
                    │ PJM Load            │
                    │ NOAA Weather        │
                    │ EIA Energy          │
                    │ EPA eGRID           │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Data Ingestion      │
                    │ Python / APIs / CSV │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Data Quality        │
                    │ Validation / Tests   │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Lakehouse           │
                    │ Raw / Bronze        │
                    │ Silver / Curated    │
                    │ Gold / Analytics    │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ SQL + Feature       │
                    │ Engineering         │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ ML Forecasting      │
                    │ XGBoost / LightGBM  │
                    │ / LSTM / TFT        │
                    └──────────┬──────────┘
                               │
                 ┌─────────────┴─────────────┐
                 ▼                           ▼
          ┌──────────────┐           ┌──────────────┐
          │ FastAPI      │           │ Dashboard    │
          │ Inference    │           │              │
          └──────┬───────┘           └──────────────┘
                 │
                 ▼
          ┌──────────────┐
          │ Docker       │
          └──────┬───────┘
                 │
                 ▼
          ┌──────────────┐
          │ Cloud / AWS  │
          └──────┬───────┘
                 │
                 ▼
          ┌──────────────┐
          │ MLOps        │
          │ Monitoring   │
          │ Retraining   │
          │ / Rollback   │
          └──────┬───────┘
                 │
                 ▼
       ┌──────────────────────┐
       │ AI Energy Copilot    │
       │ LLM + RAG + Agents   │
       │ MCP + Guardrails     │
       └──────────────────────┘
```

---

# 3. CP1 — ML Product

### Specification

Build the first working **energy demand forecasting product**.

### Five-point scope

1. **Architecture & Specification** — Understand the complete architecture, define the business problem, prediction target and KPIs, and create a production-ready Git repository structure.
2. **Data Engineering & EDA** — Acquire and combine multiple energy/weather datasets; perform ingestion, cleaning, integration and EDA; identify demand, weather, seasonal and regional patterns.
3. **Dashboard** — Show historical demand, daily/weekly/monthly patterns, peak demand, weather relationships, regional patterns and actual vs predicted demand.
4. **ML Model** — Engineer time-series features, lag features, rolling statistics, calendar features and weather features; train forecasting models.
5. **Evaluation & Deliverables** — Use time-series validation and MAE, RMSE and MAPE/sMAPE; evaluate peak-demand performance and produce the final model artifact.

### CP1 Deliverables

```text
01 Architecture
02 Project Specification
03 Git Repository
04 Data Acquisition Scripts
05 Integrated Dataset
06 EDA Report
07 Feature Engineering
08 ML Models
09 Evaluation Report
10 Interactive Dashboard
11 Key Insights Report
12 Model Artifact
```

**CP1 Exit:** Working ML-based energy forecasting product.

---

# 4. CP2 — Application + Container

### Specification

Convert the ML solution into a **reproducible, tested and deployable application**.

### Five-point scope

1. **Enhanced Data Pipeline** — Identify additional data sources and build `Raw → Validation → Transformation → Curated Parquet` using Python + SQL.
2. **Data & Model Engineering** — Add automated data-quality checks, feature generation, model versioning and reproducible inference.
3. **FastAPI Application** — Implement `/predict`, `/health`, `/ready`, request/response schemas, API documentation and error handling.
4. **Container + UI** — Build a quick Streamlit/React UI, Dockerize the application and run the complete system locally.
5. **MLOps** — Add unit tests, integration tests, Git workflow, CI/CD, dependency/security checks and model/data versioning.

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
12 Tests
13 CI/CD Pipeline
14 Local Deployment
```

**CP2 Exit:** Containerized **ML application + API + UI**.

---

# 5. CP3 — Cloud + Operations

### Specification

Transform the local application into a **production-oriented cloud ML system**.

### Five-point scope

1. **Triggers & Automation** — Define data-arrival, scheduled and model-performance triggers; design an Airflow pipeline for ingestion → validation → features → training → evaluation → registry.
2. **Production ML Operations** — Define model registry, model approval, retraining conditions, batch serving, real-time serving and scheduled forecasting.
3. **Telemetry & Reliability** — Implement application logs, model metrics, API latency, error rates, forecast accuracy, data drift and model drift monitoring.
4. **Safe Model Rollout** — Define candidate-model validation, approval, shadow/canary deployment and rollback conditions.
5. **AWS Transfer** — Map the local architecture to AWS, including container deployment, cloud storage/database, CI/CD, monitoring and an operational runbook.

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

**CP3 Exit:** **Cloud-ready production ML platform**.

---

# 6. CP4 — AI Enhancement

### Specification

Transform GridSense from an ML forecasting platform into an **AI-enabled Energy Operations Copilot**.

### Five-point scope

1. **AI Product Specification** — Define users, use cases, AI capabilities, tools, permissions, guardrails and human approval points.
2. **Knowledge Base + RAG** — Use energy policies, grid operating procedures, forecasting documentation and regulatory/technical documents; implement ingestion → chunking → embeddings → retrieval → LLM with citations.
3. **RAG Evaluation** — Build an evaluation set and measure retrieval quality, context relevance, groundedness, answer quality, citation correctness and abstention.
4. **Multi-Agent System** — Implement Forecast Agent, Data Agent, Knowledge Agent and Analyst Agent under a Supervisor Agent and workflow orchestrator.
5. **Production AI Demonstration** — Add guardrails, human approval, audit trail, AI Copilot UI, agent workflow and local deployment with optional AWS deployment.

### Example multi-agent workflow

```text
User
  ↓
Supervisor Agent
  ├── Forecast Agent
  ├── Data Agent
  ├── Knowledge Agent
  └── Analyst Agent
          ↓
     Final Response
```

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

**CP4 Exit:** AI-enabled **Energy Operations Copilot** built on the production ML platform.

---

# 7. Dataset Specification

The project should **not depend on a single dataset**. The central data-engineering exercise is to combine datasets with different granularity, frequency, geography, schema, update frequency, data quality and business meaning.

## Dataset 1 — PJM Electricity Load

**Role:** Primary prediction target.

PJM provides publicly available electricity-market and operational data suitable for large-scale time-series analysis.

- [PJM Data Directory](https://www.pjm.com/markets-and-operations/data-dictionary)
- [PJM Load Data & Forecasts](https://www.pjm.com/markets-and-operations/etools/oasis/atc-information)

### Use

```text
timestamp
region
load_MW
```

### ML Target

```text
target_load_MW
```

This becomes the central time-series dataset.

---

## Dataset 2 — NOAA Weather

**Role:** Weather-based demand features.

NOAA Climate Data Online provides historical weather and climate data, including temperature, precipitation, wind and related measurements.

- [NOAA Climate Data Online](https://www.ncei.noaa.gov/cdo-web/)

### Useful variables

```text
timestamp
station
temperature
dew_point
precipitation
wind_speed
humidity
pressure
```

### Derived features

```text
temperature_lag
temperature_rolling_mean
heating_degree_days
cooling_degree_days
extreme_temperature_flag
```

Weather should be mapped to appropriate PJM regions/stations rather than blindly joining every station to every load observation.

---

## Dataset 3 — EIA Electricity Data

**Role:** Additional electricity-system context.

EIA's open-data service provides electricity datasets including hourly balancing-authority data with actual/forecast demand, net generation and power flows.

- [EIA Open Data](https://www.eia.gov/opendata/)

### Potential variables

```text
timestamp
balancing_authority
actual_demand
forecast_demand
net_generation
interchange
generation_by_source
```

### Possible use

```text
PJM Load
     +
EIA Generation / Demand Context
     ↓
Energy Feature Dataset
```

---

## Dataset 4 — EPA eGRID

**Role:** Generation mix and environmental context.

eGRID contains generation, emissions, emission rates, resource mix and other electricity-system attributes.

- [EPA eGRID](https://www.epa.gov/egrid)
- [eGRID Detailed Data](https://www.epa.gov/egrid/detailed-data)
- [eGRID Mapping Files](https://www.epa.gov/egrid/egrid-mapping-files)

### Useful variables

```text
subregion
generation
resource_mix
CO2
CO2e
NOx
SO2
emission_rate
```

### Important design decision

eGRID is primarily annual/regional contextual data, so it should not be treated as an hourly demand dataset. Use it as a slowly changing enrichment:

```text
PJM hourly data
        +
NOAA hourly/daily weather
        +
EIA electricity context
        +
EPA eGRID regional characteristics
        ↓
Integrated Energy Dataset
```

---

# 8. Recommended Dataset Combination

| Dataset | Frequency | Primary role |
|---|---|---|
| **PJM Load** | Hourly | ML target |
| **NOAA Weather** | Hourly/Daily | Demand predictors |
| **EIA Electricity** | Hourly/Monthly | Grid context |
| **EPA eGRID** | Annual | Generation/emissions enrichment |

### Integrated data model

```text
                    PJM
              Hourly Load Data
                    │
                    ▼
             ┌─────────────┐
             │   Time      │
             │   Dimension │
             └──────┬──────┘
                    │
       ┌────────────┼────────────┐
       │            │            │
       ▼            ▼            ▼
    NOAA           EIA         eGRID
   Weather      Electricity    Regional
    Data          Data        Attributes
       │            │            │
       └────────────┼────────────┘
                    ▼
          Integrated Energy
             Data Model
                    │
                    ▼
             Feature Tables
                    │
                    ▼
             ML Forecasting
```

---

# 9. Suggested Lakehouse Structure

```text
data/
│
├── raw/
│   ├── pjm/
│   ├── noaa/
│   ├── eia/
│   └── egrid/
│
├── bronze/
│   ├── pjm_load/
│   ├── weather/
│   ├── electricity/
│   └── grid_emissions/
│
├── silver/
│   ├── hourly_load/
│   ├── weather_clean/
│   ├── electricity_clean/
│   └── grid_context/
│
└── gold/
    ├── energy_features/
    ├── forecasting_dataset/
    ├── regional_summary/
    └── model_predictions/
```

---

# 10. Core SQL/Data Model

Recommended tables:

```text
dim_time
dim_region
dim_weather_station
dim_grid_region

fact_energy_load
fact_weather
fact_generation
fact_grid_environment

feature_energy_demand
forecast_results
model_metrics
```

The main ML table could contain:

```text
timestamp
region
load_MW
temperature
humidity
wind_speed
precipitation
hour
day_of_week
month
is_weekend
is_holiday
lag_1h
lag_24h
lag_168h
rolling_mean_24h
rolling_mean_168h
generation_context
grid_emission_factor
```

---

# 11. Recommended ML Progression

Students should not jump directly to deep learning.

```text
Baseline
   ↓
Naive / Seasonal Naive
   ↓
Linear Regression
   ↓
Random Forest
   ↓
XGBoost / LightGBM
   ↓
LSTM / Temporal Deep Learning
   ↓
Model Comparison
   ↓
Production Model
```

### Required evaluation

Use chronological validation:

```text
Historical Data
       │
       ├── Train
       │
       ├── Validation
       │
       └── Test
```

**Do not randomly shuffle the time-series data.**

---

# 12. Final Product

By the end of Day 27, the student should be able to demonstrate:

```text
Multiple Public Data Sources
          ↓
Data Engineering
          ↓
Validated Lakehouse
          ↓
SQL Data Model
          ↓
EDA + Dashboard
          ↓
Demand Forecasting ML
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
AI Energy Operations Copilot
```

### Final demonstration scenario

> **User:** “What is the expected demand for tomorrow evening, what factors are driving it, and are there any operational concerns?”

The system should combine:

- **Forecast Agent → ML model**
- **Data Agent → current/forecast data**
- **Knowledge Agent → RAG knowledge base**
- **Analyst Agent → analysis**
- **Supervisor → orchestrates and validates response**

with **citations, confidence/uncertainty, auditability and human approval where required**.

---

# 13. Checkpoint Progression Summary

| Checkpoint | Focus | Exit Product |
|---|---|---|
| **CP1** | ML Product | Energy demand forecasting product |
| **CP2** | Application + Container | API + UI + Dockerized ML application |
| **CP3** | Cloud + Operations | Cloud-ready production ML platform |
| **CP4** | AI Enhancement | AI-enabled Energy Operations Copilot |

**Overall progression:**

**Traditional ML → Data Engineering → Production Software → MLOps/Cloud → RAG → LLM → Agentic AI → Enterprise AI**

---

**Reference label:** `ps-01`
