# Project 2 — SupplyChainIQ
## Predictive Supply Chain Risk & Delivery Intelligence Platform

**Structure:** ps-01  
**Progression:** CP1 — ML Product → CP2 — Application + Container → CP3 — Cloud + Operations → CP4 — AI Enhancement

---

## 1. Overall Product Specification

### Objective

Build an end-to-end supply-chain intelligence platform that predicts delivery time and late-delivery risk, identifies seller/logistics bottlenecks, and progressively evolves into an AI-enabled supply-chain risk copilot.

### Core business problems

- Predict delivery time.
- Predict late-delivery risk.
- Identify high-risk sellers, products and regions.
- Understand freight and geographic drivers.
- Support proactive logistics decisions.
- Provide evidence-backed operational recommendations.

### Core ML problems

1. Delivery-time regression.
2. Late-delivery classification.
3. Seller/risk scoring.
4. Optional customer/product segmentation.

### Example KPIs

| Area | KPI |
|---|---|
| Delivery prediction | MAE / RMSE |
| Late-risk model | Precision / Recall / F1 / PR-AUC |
| Risk ranking | Recall@K / Precision@K |
| Data | Data-quality pass rate |
| Application | API latency / error rate |
| Operations | Drift / retraining rate |
| AI | Retrieval quality / groundedness |
| Business | Late-delivery reduction opportunity |

---

# 2. Overall Architecture

```text
Olist Transactions
Customers / Sellers / Products
Orders / Payments / Reviews
Geolocation
        +
Weather / Holidays / Events
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
ML Risk & Delivery Models
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
Supply-Chain AI Copilot
LLM + RAG + Agents + MCP
        |
        v
Guardrails + Human Approval + Audit
```

---

# 3. CP1 — ML Product

### Specification

Build the first working **supply-chain prediction and risk-analysis product**.

### Five-point scope

1. **Architecture & Specification**
   - Define supply-chain problem, prediction targets, users and KPIs.
   - Understand the relational data architecture.
   - Create production-ready Git repository structure.

2. **Data Engineering & EDA**
   - Acquire and combine Olist orders, customers, sellers, products, payments, reviews and geolocation.
   - Add selected external context such as holidays/events and weather.
   - Perform data profiling, relational validation and EDA.

3. **Dashboard**
   - Order lifecycle.
   - Delivery-time distribution.
   - Late-delivery rate.
   - Seller/product/region risk.
   - Freight patterns.
   - Geographic bottlenecks.

4. **ML Models**
   - Engineer order, seller, product, freight, geography and temporal features.
   - Build delivery-time regression.
   - Build late-delivery classification/risk scoring.

5. **Evaluation & Deliverables**
   - Use appropriate train/validation/test strategy.
   - Evaluate regression and classification models.
   - Analyze feature importance/explainability.
   - Produce model artifacts and business insights.

### CP1 Deliverables

```text
01 Architecture
02 Project Specification
03 Git Repository
04 Data Acquisition Scripts
05 Integrated Dataset
06 EDA Report
07 Feature Engineering
08 Delivery-Time Model
09 Late-Risk Model
10 Evaluation Report
11 Dashboard
12 Key Insights Report
13 Model Artifacts
```

**CP1 Exit:** Working ML-based **delivery prediction and supply-chain risk product**.

---

# 4. CP2 — Application + Container

### Specification

Convert the ML solution into a **reproducible, tested and deployable application**.

### Five-point scope

1. **Enhanced Data Pipeline**
   - Add useful external sources.
   - Build:
     `Raw → Validation → Transformation → Curated Parquet`
   - Use Python + SQL.

2. **Data & Model Engineering**
   - Add automated data-quality checks.
   - Create reproducible feature generation.
   - Version datasets, features and models.

3. **FastAPI Application**
   - `/predict-delivery`
   - `/risk-score`
   - `/seller-risk`
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

**CP2 Exit:** Containerized **supply-chain prediction application**.

---

# 5. CP3 — Cloud + Operations

### Specification

Transform the local application into a **production-oriented cloud ML system**.

### Five-point scope

1. **Triggers & Automation**
   - Define data-arrival, scheduled and model-performance triggers.
   - Design Airflow pipeline:
     `Ingest → Validate → Transform → Features → Train → Evaluate → Register`.

2. **Production ML Operations**
   - Model registry.
   - Model approval.
   - Retraining conditions.
   - Batch and real-time serving.
   - Risk-score generation.

3. **Telemetry & Reliability**
   - Application logs.
   - API latency/error metrics.
   - Prediction monitoring.
   - Data drift.
   - Model drift.
   - Business KPI monitoring.

4. **Safe Model Rollout**
   - Candidate model validation.
   - Approval workflow.
   - Shadow/canary deployment.
   - Rollback conditions.
   - Model version traceability.

5. **AWS Transfer**
   - Map local design to AWS.
   - Deploy containers and data pipelines.
   - Configure CI/CD, storage, monitoring and operational controls.

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

**CP3 Exit:** **Cloud-ready production supply-chain ML platform**.

---

# 6. CP4 — AI Enhancement

### Specification

Transform SupplyChainIQ into an **AI-enabled Supply Chain Risk Copilot**.

### Five-point scope

1. **AI Product Specification**
   - Define users, workflows and AI capabilities.
   - Define tools, permissions and risk boundaries.
   - Define human approval points.

2. **Knowledge Base + RAG**
   - Supply-chain policies.
   - Delivery SLAs.
   - Logistics procedures.
   - Seller-management policies.
   - Exception-handling procedures.
   - Implement ingestion → chunking → embeddings → retrieval → LLM with citations.

3. **RAG Evaluation**
   - Build a supply-chain evaluation dataset.
   - Evaluate retrieval quality, context relevance, groundedness, answer quality and citation correctness.
   - Include abstention tests.

4. **Multi-Agent System**
   ```text
   User
     ↓
   Supervisor Agent
     ├── Order Risk Agent
     ├── Seller Risk Agent
     ├── Data Agent
     ├── Knowledge Agent
     └── Logistics Analyst
             ↓
        Final Response
   ```

5. **Production AI Demonstration**
   - Add guardrails.
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

**CP4 Exit:** AI-enabled **Supply Chain Risk Copilot**.

---

# 7. Dataset Specification

The project should deliberately combine **multiple datasets and relational sources** rather than treating Olist as a single flat dataset.

The core Olist dataset contains approximately 100,000 orders from 2016–2018 and includes order status, payment, freight, customer location, product information, sellers, reviews and a separate geolocation dataset. citeturn0search0turn0search2

## Dataset 1 — Olist Brazilian E-Commerce Public Dataset

**Role:** Primary transactional and supply-chain dataset.

**Live source:**  
https://www.kaggle.com/olistbr/brazilian-ecommerce

### Main tables

```text
olist_orders_dataset
olist_order_items_dataset
olist_customers_dataset
olist_sellers_dataset
olist_products_dataset
olist_order_payments_dataset
olist_order_reviews_dataset
olist_geolocation_dataset
product_category_name_translation
```

### Important variables

```text
order_id
customer_id
seller_id
product_id
order_status
order_purchase_timestamp
order_approved_at
order_delivered_carrier_date
order_delivered_customer_date
order_estimated_delivery_date
price
freight_value
product_weight_g
product_dimensions
customer_state
seller_state
review_score
```

### Primary ML targets

```text
delivery_days
late_delivery_flag
delivery_delay_days
seller_risk_score
```

**License note:** The original Olist Kaggle dataset is listed under CC BY-NC-SA 4.0, so students should respect its non-commercial/share-alike terms. citeturn0search0

---

# 8. Dataset 2 — Olist Geolocation

**Role:** Geographic and logistics enrichment.

The Olist release includes a geolocation dataset relating Brazilian ZIP-code prefixes to latitude/longitude coordinates. citeturn0search2

### Useful variables

```text
geolocation_zip_code_prefix
geolocation_lat
geolocation_lng
geolocation_city
geolocation_state
```

### Derived features

```text
seller_customer_distance
seller_region
customer_region
distance_bucket
urban_density_proxy
```

### Example relationship

```text
Seller ZIP
    +
Customer ZIP
    ↓
Geolocation
    ↓
Distance / Region
    ↓
Delivery-risk features
```

---

# 9. Dataset 3 — Brazilian Holidays & Events

**Role:** Calendar effects on orders, fulfillment and delivery.

A currently available Brazilian holiday API provides national, state and municipal holiday data, including API access and 2024–2026 coverage. citeturn0search13turn0search14

**Live source:**  
https://feriados.dev/

### Useful variables

```text
date
holiday_name
holiday_type
state
municipality
```

### Derived features

```text
is_holiday
days_to_holiday
days_after_holiday
holiday_period
long_weekend
```

This can help test whether holidays are associated with longer fulfillment/delivery times.

---

# 10. Dataset 4 — Weather

**Role:** External logistics-risk context.

Recommended source:

**NOAA Climate Data Online:**  
https://www.ncei.noaa.gov/cdo-web/

Potential variables:

```text
date/time
temperature
precipitation
wind
humidity
weather_events
```

Weather observations should be mapped to relevant seller/customer regions and aligned carefully by date/time.

### Example

```text
Order
  +
Seller Location
  +
Customer Location
  +
Weather
  ↓
Weather-adjusted logistics features
```

---

# 11. Recommended Dataset Combination

| Dataset | Role | Grain |
|---|---|---|
| **Olist Orders** | Order lifecycle | Order |
| **Olist Items** | Products/sellers/freight | Order item |
| **Olist Customers** | Destination | Customer |
| **Olist Sellers** | Origin | Seller |
| **Olist Products** | Product characteristics | Product |
| **Olist Geolocation** | Distance/location | ZIP prefix |
| **Brazil Holidays** | Calendar effects | Date/location |
| **NOAA Weather** | Weather/logistics context | Station/time |

### Integrated architecture

```text
                 OLIST
       ┌──────────┼───────────┐
       ↓          ↓           ↓
    Orders      Items     Customers
       ↓          ↓           ↓
    Sellers    Products   Geolocation
       └──────────┼───────────┘
                  ↓
          Core Supply Chain
             Data Model
                  +
        ┌─────────┴─────────┐
        ↓                   ↓
   Holidays              Weather
        └─────────┬─────────┘
                  ↓
        Integrated Features
                  ↓
       ML Delivery + Risk
```

---

# 12. Lakehouse Structure

```text
data/
│
├── raw/
│   ├── olist/
│   ├── geolocation/
│   ├── holidays/
│   └── weather/
│
├── bronze/
│   ├── orders/
│   ├── order_items/
│   ├── customers/
│   ├── sellers/
│   ├── products/
│   ├── payments/
│   ├── reviews/
│   ├── geolocation/
│   ├── holidays/
│   └── weather/
│
├── silver/
│   ├── orders_clean/
│   ├── logistics_clean/
│   ├── customer_location/
│   ├── seller_location/
│   └── external_context/
│
└── gold/
    ├── order_features/
    ├── seller_features/
    ├── delivery_risk/
    ├── regional_risk/
    └── model_predictions/
```

---

# 13. Recommended SQL/Data Model

```text
dim_date
dim_customer
dim_seller
dim_product
dim_location
dim_holiday

fact_order
fact_order_item
fact_payment
fact_review
fact_weather

feature_order_risk
feature_seller_risk
prediction_delivery
prediction_risk
model_metrics
```

### Main analytical feature table

```text
order_id
seller_id
customer_id
product_id

order_purchase_timestamp
estimated_delivery_date

price
freight_value
product_weight
product_volume

seller_state
customer_state
distance_km

day_of_week
month
is_weekend
is_holiday

temperature
precipitation
wind_speed

seller_historical_delay_rate
seller_order_volume
seller_avg_delivery_days

product_category
product_historical_delay_rate

delivery_days
late_delivery_flag
```

---

# 14. ML Progression

Students should progress from interpretable baselines to stronger models:

```text
Business Baseline
       ↓
Rule-based Risk Score
       ↓
Linear / Logistic Regression
       ↓
Random Forest
       ↓
XGBoost / LightGBM
       ↓
Explainability
       ↓
Threshold Optimization
       ↓
Production Model
```

### Regression

Predict:

```text
delivery_days
```

Metrics:

```text
MAE
RMSE
MAPE / sMAPE
```

### Classification

Predict:

```text
late_delivery_flag
```

Metrics:

```text
Precision
Recall
F1
PR-AUC
ROC-AUC
Confusion Matrix
```

For operational risk, threshold selection should reflect the relative cost of missing a genuinely late order versus investigating a false alarm.

---

# 15. Final Product

By Day 27 the student should demonstrate:

```text
Olist + External Data
        ↓
Data Engineering
        ↓
Validated Lakehouse
        ↓
SQL Data Model
        ↓
EDA + Dashboard
        ↓
Delivery Prediction
        ↓
Late-Risk Prediction
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
AI Supply Chain Risk Copilot
```

## Final demonstration scenario

**User:**

> "Which orders are at high risk of late delivery, what are the likely reasons, and what action should the logistics team consider?"

The system should combine:

- **Risk Agent** → ML prediction
- **Data Agent** → order/seller/customer data
- **Knowledge Agent** → RAG over logistics policies
- **Logistics Analyst** → evidence-based analysis
- **Supervisor Agent** → workflow orchestration and response validation

The final response should provide **evidence, model-derived risk, relevant policy citations, uncertainty and appropriate human approval**, rather than allowing the agent to autonomously execute high-impact logistics actions.

---

# 16. Engineering Spine

SupplyChainIQ follows the same **ps-01 engineering spine** as GridSense:

**Layer 1 — Data Engineering + ML**

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

**Layer 2 — Production AI Engineering**

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

**Layer 3 — AI Engineering**

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

**Business Product**

```text
Dashboard
+ APIs
+ AI Copilot
+ Risk Alerts
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
