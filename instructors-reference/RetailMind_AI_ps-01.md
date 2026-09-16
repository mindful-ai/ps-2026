# Project 3 — RetailMind AI
## AI Demand Forecasting, Customer Intelligence & Replenishment Platform

**Structure:** ps-01  
**Progression:** CP1 — ML Product → CP2 — Application + Container → CP3 — Cloud + Operations → CP4 — AI Enhancement

---

# 1. Overall Product Specification

## Objective

Build an end-to-end retail intelligence platform that forecasts product/store demand, identifies customer and product patterns, supports replenishment decisions, and evolves into an AI-enabled retail copilot.

## Core business problems

- Forecast product demand.
- Identify seasonal and promotional effects.
- Detect demand anomalies.
- Understand product/store performance.
- Support inventory and replenishment decisions.
- Provide customer/product intelligence.
- Generate evidence-backed business recommendations.

## Core ML problems

1. Hierarchical demand forecasting.
2. Product/store demand prediction.
3. Customer segmentation or product affinity.
4. Optional replenishment recommendation.

## Example KPIs

| Area | KPI |
|---|---|
| Forecasting | MAE / RMSE / RMSSE |
| Forecasting | WAPE / sMAPE |
| Inventory | Stockout-risk reduction |
| Recommendation | Precision@K / Recall@K |
| Data | Data-quality pass rate |
| Application | API latency / error rate |
| Operations | Drift / retraining rate |
| AI | Retrieval quality / groundedness |
| Business | Forecast/replenishment impact |

---

# 2. Overall Architecture

```text
M5 Sales
Calendar
Sell Prices
Store/Product Hierarchy
        +
Weather / Economic Context
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
Demand Forecasting
+ Customer/Product Intelligence
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
Retail AI Copilot
LLM + RAG + Agents + MCP
        |
        v
Guardrails + Human Approval + Audit
```

---

# 3. CP1 — ML Product

### Specification

Build the first working **retail demand forecasting and intelligence product**.

### Five-point scope

1. **Architecture & Specification**
   - Define forecasting, customer/product intelligence and replenishment problems.
   - Identify users, targets and KPIs.
   - Create production-ready Git repository structure.

2. **Data Engineering & EDA**
   - Acquire and integrate M5 sales, calendar and sell-price data.
   - Add selected external context such as weather or economic indicators.
   - Perform data profiling, hierarchy checks, EDA and demand analysis.

3. **Dashboard**
   - Sales trends.
   - Store/category/item performance.
   - Seasonality.
   - Price effects.
   - Event/promotion effects.
   - Demand anomalies.
   - Forecast vs actual.

4. **ML Models**
   - Engineer lag, rolling, calendar, price and hierarchy features.
   - Build baseline forecasting models.
   - Build ML forecasting models.
   - Add customer/product intelligence component where data permits.

5. **Evaluation & Deliverables**
   - Use chronological validation.
   - Evaluate forecasts using appropriate metrics.
   - Compare models.
   - Translate forecasts into replenishment insights.

### CP1 Deliverables

```text
01 Architecture
02 Project Specification
03 Git Repository
04 Data Acquisition Scripts
05 Integrated Dataset
06 EDA Report
07 Feature Engineering
08 Forecasting Models
09 Evaluation Report
10 Customer/Product Intelligence
11 Dashboard
12 Key Insights Report
13 Model Artifacts
```

**CP1 Exit:** Working ML-based **retail forecasting and intelligence product**.

---

# 4. CP2 — Application + Container

### Specification

Convert the ML solution into a **reproducible, tested and deployable retail application**.

### Five-point scope

1. **Enhanced Data Pipeline**
   - Identify additional useful retail/context data.
   - Build:
     `Raw → Validation → Transformation → Curated Parquet`
   - Use Python + SQL.

2. **Data & Model Engineering**
   - Automated data-quality checks.
   - Reproducible feature generation.
   - Dataset/model versioning.
   - Forecast generation pipeline.

3. **FastAPI Application**
   - `/forecast`
   - `/product-insights`
   - `/store-insights`
   - `/replenishment`
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
07 Versioned Models
08 FastAPI Application
09 API Documentation
10 Quick UI
11 Dockerfile
12 Test Suite
13 CI/CD Pipeline
14 Local Deployment
```

**CP2 Exit:** Containerized **retail prediction and decision-support application**.

---

# 5. CP3 — Cloud + Operations

### Specification

Transform the local application into a **production-oriented cloud retail ML system**.

### Five-point scope

1. **Triggers & Automation**
   - Define data-arrival, scheduled and model-performance triggers.
   - Design Airflow:
     `Ingest → Validate → Transform → Features → Train → Evaluate → Register`.

2. **Production ML Operations**
   - Model registry.
   - Forecast-generation jobs.
   - Batch and real-time serving where appropriate.
   - Retraining conditions.
   - Model approval.

3. **Telemetry & Reliability**
   - Application logs.
   - API latency/error metrics.
   - Forecast-quality monitoring.
   - Data drift.
   - Model drift.
   - Business KPI monitoring.

4. **Safe Model Rollout**
   - Candidate model validation.
   - Shadow/canary deployment.
   - Rollback conditions.
   - Model version traceability.
   - Forecast comparison before promotion.

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

**CP3 Exit:** **Cloud-ready production retail ML platform**.

---

# 6. CP4 — AI Enhancement

### Specification

Transform RetailMind into an **AI-enabled Retail Intelligence & Replenishment Copilot**.

### Five-point scope

1. **AI Product Specification**
   - Define business users and AI workflows.
   - Define AI capabilities and tools.
   - Define permissions, guardrails and human approval points.

2. **Knowledge Base + RAG**
   - Retail policies.
   - Inventory procedures.
   - Pricing/promotion policies.
   - Replenishment rules.
   - Store-operation documentation.
   - Implement ingestion → chunking → embeddings → retrieval → LLM with citations.

3. **RAG Evaluation**
   - Build retail question/evidence evaluation set.
   - Evaluate retrieval quality, relevance, groundedness, answer quality and citations.
   - Include abstention tests.

4. **Multi-Agent System**
   ```text
   User
     ↓
   Supervisor Agent
     ├── Forecast Agent
     ├── Inventory Agent
     ├── Product Agent
     ├── Customer Agent
     ├── Knowledge Agent
     └── Retail Analyst
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

**CP4 Exit:** AI-enabled **Retail Intelligence & Replenishment Copilot**.

---

# 7. Dataset Specification

The project should deliberately combine **multiple datasets** and preserve the retail hierarchy.

## Dataset 1 — M5 Forecasting Accuracy

**Role:** Primary sales, calendar, store and price dataset.

The M5 dataset contains hierarchical daily Walmart sales data, with product/store information, calendar information and sell prices. The public Kaggle data page currently lists `calendar.csv`, `sales_train_validation.csv`, `sales_train_evaluation.csv`, `sell_prices.csv` and the submission file. citeturn0search0turn0search1

**Live source:**  
https://www.kaggle.com/competitions/m5-forecasting-accuracy/data

### Main files

```text
calendar.csv
sales_train_validation.csv
sales_train_evaluation.csv
sell_prices.csv
```

### Main dimensions

```text
item_id
dept_id
cat_id
store_id
state_id
date
wm_yr_wk
```

### Important variables

```text
sales
sell_price
event_name_1
event_type_1
event_name_2
event_type_2
snap_CA
snap_TX
snap_WI
```

### Primary ML target

```text
unit_sales
```

The original M5 challenge forecasts daily unit sales for products/stores over 28-day horizons and covers stores in California, Texas and Wisconsin. citeturn0search15

---

# 8. Dataset 2 — NOAA Weather

**Role:** Weather-driven demand enrichment.

NOAA Climate Data Online provides historical weather and climate data, including temperature, precipitation, wind and degree-day measurements. citeturn0search3

**Live source:**  
https://www.ncei.noaa.gov/cdo-web/

### Useful variables

```text
date
station
temperature
precipitation
wind
degree_days
```

### Derived features

```text
temperature
temperature_lag
temperature_rolling_mean
heating_degree_days
cooling_degree_days
extreme_weather_flag
```

Weather should be mapped to the relevant Walmart store state/region and aligned to the M5 calendar.

---

# 9. Dataset 3 — U.S. Census Data

**Role:** Store-region demographic and economic context.

The U.S. Census Data API provides public statistical data associated with geographic areas, while Census TIGERweb provides geographic boundaries and the Census Geocoder provides location-to-coordinate services. citeturn0search9turn0search14

**Live source:**  
https://www.census.gov/data/developers.html

### Potential variables

```text
population
household_count
median_income
population_density
age_distribution
employment_context
```

### Derived features

```text
population_density
income_band
market_size_proxy
demographic_segment
```

Use the geographic level appropriate to the store-location information available to the student.

---

# 10. Dataset 4 — Optional Walmart Store Forecasting Dataset

A second public Walmart competition dataset contains historical weekly department/store sales plus store, temperature, fuel price, markdown, CPI and unemployment variables. citeturn0search16

**Live source:**  
https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting/data

### Potential use

Use this as an **optional comparative/secondary retail dataset** for:

- External validation of feature-engineering techniques.
- Promotion/markdown analysis.
- Economic-context analysis.
- Model transferability experiments.

Do not mix it directly into the M5 target without documenting the different business periods, grains and schemas.

---

# 11. Recommended Dataset Combination

| Dataset | Role | Grain |
|---|---|---|
| **M5 Sales** | Primary demand target | Item × Store × Day |
| **M5 Calendar** | Events/calendar | Day |
| **M5 Prices** | Price features | Item × Store × Week |
| **NOAA Weather** | Weather context | Station × Day |
| **Census** | Regional context | Geographic area |
| **Walmart Store Sales** | Optional secondary experiment | Store × Dept × Week |

### Integrated architecture

```text
                  M5
       ┌──────────┼───────────┐
       ↓          ↓           ↓
     Sales      Calendar     Prices
       └──────────┼───────────┘
                  ↓
           Retail Core Model
                  +
       ┌──────────┴──────────┐
       ↓                     ↓
    NOAA Weather          Census
       └──────────┬──────────┘
                  ↓
        Integrated Features
                  ↓
     Forecast + Intelligence
```

---

# 12. Lakehouse Structure

```text
data/
│
├── raw/
│   ├── m5/
│   ├── weather/
│   ├── census/
│   └── walmart_optional/
│
├── bronze/
│   ├── sales/
│   ├── calendar/
│   ├── prices/
│   ├── weather/
│   └── regional_context/
│
├── silver/
│   ├── sales_clean/
│   ├── calendar_clean/
│   ├── prices_clean/
│   ├── weather_clean/
│   └── geography_clean/
│
└── gold/
    ├── demand_features/
    ├── item_store_features/
    ├── forecast_dataset/
    ├── replenishment_features/
    └── model_predictions/
```

---

# 13. Recommended SQL/Data Model

```text
dim_date
dim_store
dim_product
dim_category
dim_department
dim_geography
dim_event

fact_daily_sales
fact_weekly_price
fact_weather
fact_regional_context

feature_demand
feature_customer_proxy
feature_product_affinity
prediction_forecast
prediction_replenishment
model_metrics
```

### Main analytical feature table

```text
date
store_id
state_id
item_id
dept_id
cat_id

unit_sales
sell_price

price_change_pct
price_rolling_mean

day_of_week
week_of_year
month
year
is_weekend
is_event
event_type

temperature
precipitation
degree_days

population
population_density
income_context

lag_1
lag_7
lag_14
lag_28
lag_364

rolling_mean_7
rolling_mean_28
rolling_std_28

forecast_target
```

---

# 14. ML Progression

Students should progress from forecasting baselines to scalable ML:

```text
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
Optional LSTM / Transformer
      ↓
Model Comparison
      ↓
Production Forecast Model
```

### Forecasting metrics

```text
MAE
RMSE
WAPE
sMAPE
RMSSE
```

The original M5 competition used Weighted Root Mean Squared Scaled Error (WRMSSE), so students can study the metric and compare it with simpler business-facing measures. citeturn0search15

### Optional intelligence components

```text
Customer/Product Segmentation
        ↓
Product Affinity
        ↓
Recommendation
        ↓
Replenishment Decision Support
```

---

# 15. Final Product

By Day 27 the student should demonstrate:

```text
M5 + Weather + Regional Data
        ↓
Data Engineering
        ↓
Validated Lakehouse
        ↓
SQL Data Model
        ↓
EDA + Dashboard
        ↓
Demand Forecasting
        ↓
Product/Store Intelligence
        ↓
Replenishment Support
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
AI Retail Copilot
```

## Final demonstration scenario

**User:**

> "Which products and stores are likely to experience unusually high demand next week, why, and what replenishment action should we consider?"

The system should combine:

- **Forecast Agent** → demand forecast.
- **Inventory Agent** → replenishment/risk analysis.
- **Product Agent** → product/category patterns.
- **Data Agent** → current data and contextual features.
- **Knowledge Agent** → retail policies through RAG.
- **Retail Analyst** → evidence-based explanation.
- **Supervisor Agent** → workflow orchestration and response validation.

The final response should provide **forecast evidence, assumptions, uncertainty, relevant policy citations and human approval for consequential inventory actions**.

---

# 16. Engineering Spine

RetailMind follows the same **ps-01 engineering spine**:

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
+ Forecast Alerts
+ Replenishment Recommendations
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
