# Campus Data Science & AI Engineering — 2026
## Capstone Projects
#### Using progressive methodology

---

# 1. GridSense AI — Intelligent Energy Demand Forecasting & Grid Operations Platform

**Summary:** An end-to-end energy AI platform for demand forecasting, anomaly detection and intelligent grid-operations decision support.

### Abstract

GridSense AI develops a production-grade electricity intelligence platform using large-scale public energy datasets such as PJM historical hourly load data. The project takes students from raw energy data through data engineering, statistical analysis, feature engineering and machine-learning/deep-learning forecasting to a production-ready AI system. Students will compare forecasting approaches, evaluate them using time-series validation, package the selected model and expose it through a production API. The platform will then incorporate MLOps, CI/CD, monitoring, drift detection and controlled retraining. In the final stage, students will build an energy-domain RAG assistant and agent capable of investigating demand anomalies, retrieving supporting evidence and generating operational recommendations under appropriate governance and human-approval controls.

### Objectives

1. Build a scalable ingestion pipeline for large-scale electricity time-series data.
2. Develop a reliable lakehouse and SQL-based analytical data model.
3. Perform EDA covering trends, seasonality, anomalies and regional demand behaviour.
4. Engineer temporal, calendar and contextual features for forecasting.
5. Develop and compare classical ML and deep-learning forecasting models.
6. Evaluate models using appropriate time-series validation and forecasting metrics.
7. Package and deploy the selected forecasting model as a production service.
8. Implement MLOps, CI/CD, monitoring, drift detection and retraining/rollback mechanisms.
9. Build an energy-domain RAG assistant with evaluated retrieval and grounded responses.
10. Develop a controlled agent for energy anomaly investigation and evidence-backed operational decision support.

### Data Set

**Primary:** PJM electricity load and related historical energy-market datasets. PJM provides extensive publicly available electricity-market and operational data suitable for large-scale time-series analysis.
Ref: https://www.pjm.com/

**Optional enrichment:** Public weather, calendar and regional energy datasets.

### Layers

**Layer 1 — Data Engineering & ML**  
`Sources → Ingestion → Data Quality → Lakehouse → SQL/Data Model → EDA → Features → ML/DL → Evaluation → Model Artifact`  
↓  
**Layer 2 — Production AI Engineering**  
`Model Registry → FastAPI → Tests → Docker → CI/CD → Security Scan → Deployment → Observability → Monitoring → Drift → Retraining/Rollback`  
↓  
**Layer 3 — AI Engineering**  
`LLM → Structured Output → RAG → Retrieval Evaluation → Tools → Agent → MCP → Guardrails → Human Approval → LLMOps`  
↓  
**Business Product - MVP/POC**  
`Dashboard + APIs + AI Copilot + Agent + Alerts + Audit Trail + Runbook`

### Deliverables/Checklist

- Complete energy data pipeline
- Lakehouse/analytical data model
- Data-quality framework
- EDA and statistical analysis
- Forecasting feature pipeline
- Multiple forecasting models
- Model evaluation and comparison
- Production model artifact
- Model card
- FastAPI service
- Docker container
- Automated test suite
- CI/CD pipeline
- Model registry
- Monitoring dashboard
- Drift/retraining mechanism
- Energy RAG assistant
- RAG evaluation dataset and results
- Energy operations agent
- MCP/tool integration
- Security/threat model
- Governance documentation
- Incident runbook
- Architecture diagram
- Final technical report
- Business presentation and live demonstration

### Rubrics

| Area | Weight |
|---|---:|
| Data engineering & data quality | 15% |
| EDA, statistics & feature engineering | 10% |
| ML/DL forecasting | 15% |
| Software engineering & testing | 10% |
| Production AI engineering | 10% |
| MLOps, CI/CD & operations | 10% |
| AI Engineering — RAG/Agent/MCP | 15% |
| Security, governance & responsible AI | 5% |
| Monitoring & reliability | 5% |
| Business value & technical defense | 5% |
| **Total** | **100%** |

---

# 2. SupplyChainIQ — Predictive Supply Chain Risk & Delivery Intelligence Platform

**Summary:** An AI-powered supply-chain platform that predicts delivery risk, identifies operational bottlenecks and provides intelligent logistics decision support.

### Abstract

SupplyChainIQ transforms a large public e-commerce dataset into an enterprise supply-chain intelligence platform. Using the Olist Brazilian E-Commerce Public Dataset, students integrate orders, customers, sellers, products, payments, freight and geographic information into a reliable analytical data product. They will perform EDA and feature engineering before developing models for delivery-time prediction, late-delivery risk and seller-level risk analysis. The solution then progresses into production model serving, containerization, CI/CD and MLOps. The final AI engineering layer introduces supply-chain RAG and a controlled agent that can investigate high-risk orders and sellers using approved tools, evidence and human-approval mechanisms.

### Objectives

1. Integrate multiple relational supply-chain datasets into a unified analytical model.
2. Establish data-quality, grain, key and reconciliation controls.
3. Analyze seller, customer, product, freight and geographic delivery behaviour.
4. Engineer features for delivery-time and delivery-risk prediction.
5. Develop a delivery-time regression model.
6. Develop a late-delivery classification and risk-scoring model.
7. Apply explainability to operational risk predictions.
8. Deploy the predictive system using production engineering and MLOps practices.
9. Build an evaluated supply-chain RAG assistant over policies and operational knowledge.
10. Develop an agentic workflow for supply-chain risk investigation and decision support.

### Data Set

**Primary:** Olist Brazilian E-Commerce Public Dataset — approximately 100,000 orders with multiple relational tables covering orders, products, sellers, customers, payments, freight and reviews.
Ref: https://github.com/duygut/Brazilian_E-Commerce_Data_Analysis

**Optional enrichment:** Olist geolocation and marketing-funnel datasets.

### Layers

**Layer 1 — Data Engineering & ML**  
`Sources → Ingestion → Data Quality → Lakehouse → SQL/Data Model → EDA → Features → ML/DL → Evaluation → Model Artifact`  
↓  
**Layer 2 — Production AI Engineering**  
`Model Registry → FastAPI → Tests → Docker → CI/CD → Security Scan → Deployment → Observability → Monitoring → Drift → Retraining/Rollback`  
↓  
**Layer 3 — AI Engineering**  
`LLM → Structured Output → RAG → Retrieval Evaluation → Tools → Agent → MCP → Guardrails → Human Approval → LLMOps`  
↓  
**Business Product - MVP/POC**  
`Dashboard + APIs + AI Copilot + Agent + Alerts + Audit Trail + Runbook`

### Deliverables/Checklist

- Multi-source ingestion pipeline
- Supply-chain lakehouse
- SQL analytical data model
- Data-quality framework
- EDA report
- Delivery-time model
- Late-delivery risk model
- Seller-risk model
- Explainability analysis
- Model cards
- Prediction APIs
- Docker image
- Automated tests
- CI/CD
- Model registry
- Monitoring dashboard
- Drift detection
- Supply-chain RAG assistant
- RAG evaluation suite
- Risk-investigation agent
- MCP/tool integration
- Security controls
- Audit trail
- Governance documentation
- Operations runbook
- Architecture diagram
- Business-impact analysis
- Final report and presentation

### Rubrics

| Area | Weight |
|---|---:|
| Data engineering & data modelling | 15% |
| EDA & analytical reasoning | 10% |
| Predictive modelling | 15% |
| Software engineering & testing | 10% |
| Production AI engineering | 10% |
| MLOps, CI/CD & operations | 10% |
| AI Engineering — RAG/Agent/MCP | 15% |
| Security, governance & responsible AI | 5% |
| Monitoring & reliability | 5% |
| Business value & technical defense | 5% |
| **Total** | **100%** |

---

# 3. RetailMind — AI Demand Forecasting, Customer Intelligence & Replenishment Platform

**Summary:** A large-scale retail AI platform combining demand forecasting, customer intelligence, recommendations and inventory decision support.

### Abstract

RetailMind uses the large-scale M5 Walmart forecasting dataset to create a complete retail AI product. Students will process hierarchical product-store sales data together with calendar and pricing information, build scalable analytical datasets and investigate demand patterns across products, departments and stores. The project progresses from forecasting baselines to advanced ML/deep-learning models and can incorporate customer/product affinity and recommendation capabilities. The resulting models are operationalized through APIs, Docker, CI/CD, MLOps and monitoring. The final AI engineering layer adds a retail RAG assistant and an agent capable of investigating demand anomalies, explaining business drivers and generating evidence-backed replenishment recommendations.

### Objectives

1. Build a scalable retail data-ingestion and transformation pipeline.
2. Develop hierarchical retail data models and analytical datasets.
3. Analyze demand, seasonality, pricing, promotions and store behaviour.
4. Engineer temporal, lag, rolling and contextual demand features.
5. Develop and compare multiple retail demand-forecasting models.
6. Develop customer segmentation, product affinity or recommendation capabilities.
7. Translate predictions into inventory/replenishment decision support.
8. Operationalize models through APIs, CI/CD, MLOps and production monitoring.
9. Build an evaluated retail RAG assistant for business users.
10. Develop an agent for demand investigation and evidence-backed retail recommendations.

### Data Set

**Primary:** M5 Forecasting Accuracy — Walmart historical daily sales, calendar and pricing data across products and stores.
Ref: https://www.kaggle.com/competitions/m5-forecasting-accuracy/data

**Optional:** Instacart Market Basket Analysis dataset for customer and basket intelligence.

### Layers

**Layer 1 — Data Engineering & ML**  
`Sources → Ingestion → Data Quality → Lakehouse → SQL/Data Model → EDA → Features → ML/DL → Evaluation → Model Artifact`  
↓  
**Layer 2 — Production AI Engineering**  
`Model Registry → FastAPI → Tests → Docker → CI/CD → Security Scan → Deployment → Observability → Monitoring → Drift → Retraining/Rollback`  
↓  
**Layer 3 — AI Engineering**  
`LLM → Structured Output → RAG → Retrieval Evaluation → Tools → Agent → MCP → Guardrails → Human Approval → LLMOps`  
↓  
**Business Product - MVP/POC**  
`Dashboard + APIs + AI Copilot + Agent + Alerts + Audit Trail + Runbook`

### Deliverables/Checklist

- Retail data pipeline
- Lakehouse/data model
- SQL analytical datasets
- Data-quality framework
- EDA
- Forecasting features
- Demand models
- Forecast comparison
- Customer/product intelligence component
- Recommendation/replenishment component
- Model cards
- Production APIs
- Docker image
- Tests
- CI/CD pipeline
- MLflow/model registry
- Monitoring and drift detection
- Retail RAG assistant
- RAG evaluation framework
- Retail intelligence agent
- MCP integration
- Guardrails
- Governance documentation
- Operations runbook
- Architecture diagram
- Business case
- Final report
- Live demonstration

### Rubrics

| Area | Weight |
|---|---:|
| Data engineering & scalability | 15% |
| EDA & feature engineering | 10% |
| Forecasting/ML/recommendation | 15% |
| Software engineering & testing | 10% |
| Production AI engineering | 10% |
| MLOps, CI/CD & operations | 10% |
| AI Engineering — RAG/Agent/MCP | 15% |
| Security, governance & responsible AI | 5% |
| Monitoring & reliability | 5% |
| Business value & technical defense | 5% |
| **Total** | **100%** |

---

# 4. FactoryGuard AI — Predictive Quality & Production Intelligence Platform

**Summary:** An industrial AI platform that predicts rare manufacturing failures, explains production risks and supports proactive quality management.

### Abstract

FactoryGuard AI addresses a realistic industrial manufacturing problem using the Bosch Production Line Performance dataset, which contains approximately 1.18 million training observations and an extremely imbalanced failure target. Students will build a robust industrial data pipeline, conduct high-dimensional EDA, investigate missing and anomalous sensor measurements and develop models for rare production failures. The project emphasizes industry-standard considerations such as class imbalance, cost-sensitive classification, threshold optimization and explainability. The selected solution will be deployed through a production API and operated using CI/CD, MLOps, monitoring and rollback practices. The final AI engineering layer introduces manufacturing RAG and a controlled production-investigation agent.

### Objectives

1. Process and validate a million-plus-row manufacturing dataset.
2. Build a scalable lakehouse and manufacturing analytical model.
3. Analyze missingness, sensor behaviour and production anomalies.
4. Engineer features for rare-event failure prediction.
5. Develop baseline and advanced classification models.
6. Handle severe class imbalance and optimize decision thresholds.
7. Explain individual and global model predictions.
8. Deploy the predictive quality system using production AI engineering.
9. Build manufacturing RAG over quality procedures and operational documentation.
10. Develop a controlled agent for production anomaly investigation and decision support.

### Data Set

**Primary:** Bosch Production Line Performance dataset — approximately 1.18 million training observations with hundreds of anonymized production features and a highly imbalanced failure target.
Ref: https://www.kaggle.com/c/bosch-production-line-performance

Ref: 

### Layers

**Layer 1 — Data Engineering & ML**  
`Sources → Ingestion → Data Quality → Lakehouse → SQL/Data Model → EDA → Features → ML/DL → Evaluation → Model Artifact`  
↓  
**Layer 2 — Production AI Engineering**  
`Model Registry → FastAPI → Tests → Docker → CI/CD → Security Scan → Deployment → Observability → Monitoring → Drift → Retraining/Rollback`  
↓  
**Layer 3 — AI Engineering**  
`LLM → Structured Output → RAG → Retrieval Evaluation → Tools → Agent → MCP → Guardrails → Human Approval → LLMOps`  
↓  
**Business Product - MVP/POC**  
`Dashboard + APIs + AI Copilot + Agent + Alerts + Audit Trail + Runbook`

### Deliverables/Checklist

- Large-scale manufacturing data pipeline
- Lakehouse
- Data-quality framework
- EDA
- Feature pipeline
- Failure-prediction models
- Imbalance analysis
- Threshold/cost analysis
- Explainability report
- Model card
- FastAPI service
- Docker container
- Test suite
- CI/CD pipeline
- Model registry
- Monitoring dashboard
- Drift detection
- Manufacturing RAG
- RAG evaluation suite
- Production investigation agent
- MCP/tool layer
- Threat model
- Governance controls
- Audit trail
- Incident runbook
- Architecture diagram
- Business-impact assessment
- Final technical report
- Live technical defense

### Rubrics

| Area | Weight |
|---|---:|
| Data engineering & data quality | 15% |
| EDA & feature engineering | 10% |
| Rare-event ML & explainability | 20% |
| Software engineering & testing | 10% |
| Production AI engineering | 10% |
| MLOps, CI/CD & operations | 10% |
| AI Engineering — RAG/Agent/MCP | 10% |
| Security, governance & responsible AI | 5% |
| Monitoring & reliability | 5% |
| Business value & technical defense | 5% |
| **Total** | **100%** |

---

# 5. EnergyTwin AI — Industrial Energy Optimization & Predictive Operations Platform

**Summary:** An industrial energy AI system that forecasts consumption, detects abnormal behaviour and provides intelligent operational recommendations.

### Abstract

EnergyTwin AI develops an industrial energy intelligence platform using high-frequency public energy datasets such as I-BLEND. The project combines energy consumption, occupancy and contextual information to understand operational patterns and identify opportunities for improved efficiency. Students will construct time-series pipelines, perform EDA, engineer temporal and contextual features and develop forecasting and anomaly-detection models using classical ML and deep-learning techniques. These capabilities will be operationalized through APIs, containers, CI/CD, MLOps and production monitoring. The final stage introduces energy-management RAG and a controlled AI agent that investigates abnormal energy events, retrieves relevant operating procedures and generates evidence-backed efficiency recommendations subject to human approval.

### Objectives

1. Build a high-frequency energy data ingestion and processing pipeline.
2. Develop scalable time-series storage and analytical models.
3. Analyze energy consumption against occupancy and contextual variables.
4. Engineer temporal and operational features.
5. Develop short-term energy forecasting models.
6. Detect abnormal energy-consumption patterns.
7. Develop data-driven energy-efficiency recommendations.
8. Operationalize the system using APIs, CI/CD, MLOps and monitoring.
9. Build an evaluated energy-management RAG assistant.
10. Develop a controlled agent for energy-event investigation and operational recommendations.

### Data Set

**Primary:** I-BLEND — a public high-frequency building energy dataset containing long-duration electricity measurements and contextual/occupancy information.
Ref: https://www.nature.com/articles/sdata201915

**Optional enrichment:** Public weather, energy-price and building datasets.

### Layers

**Layer 1 — Data Engineering & ML**  
`Sources → Ingestion → Data Quality → Lakehouse → SQL/Data Model → EDA → Features → ML/DL → Evaluation → Model Artifact`  
↓  
**Layer 2 — Production AI Engineering**  
`Model Registry → FastAPI → Tests → Docker → CI/CD → Security Scan → Deployment → Observability → Monitoring → Drift → Retraining/Rollback`  
↓  
**Layer 3 — AI Engineering**  
`LLM → Structured Output → RAG → Retrieval Evaluation → Tools → Agent → MCP → Guardrails → Human Approval → LLMOps`  
↓  
**Business Product - MVP/POC**  
`Dashboard + APIs + AI Copilot + Agent + Alerts + Audit Trail + Runbook`

### Deliverables/Checklist

- High-frequency energy ingestion pipeline
- Time-series lakehouse
- SQL/analytical model
- Data-quality framework
- EDA
- Feature engineering pipeline
- Forecasting models
- Anomaly-detection model
- Energy-efficiency recommendation component
- Model cards
- FastAPI APIs
- Docker image
- Automated tests
- CI/CD
- Model registry
- Monitoring dashboard
- Drift/retraining mechanism
- Energy RAG assistant
- RAG evaluation suite
- Energy operations agent
- MCP/tool integration
- Guardrails
- Human-approval workflow
- Governance documentation
- Audit trail
- Incident/runbook
- Architecture diagram
- Business-impact analysis
- Final report
- Live demonstration

### Rubrics

| Area | Weight |
|---|---:|
| Data engineering & time-series processing | 15% |
| EDA & feature engineering | 10% |
| Forecasting/anomaly/optimization | 15% |
| Software engineering & testing | 10% |
| Production AI engineering | 10% |
| MLOps, CI/CD & operations | 10% |
| AI Engineering — RAG/Agent/MCP | 15% |
| Security, governance & responsible AI | 5% |
| Monitoring & reliability | 5% |
| Business value & technical defense | 5% |
| **Total** | **100%** |

---

# Capstone Design Principle

The five projects share the **same engineering spine**:

**Layer 1:** Data Engineering + ML  
↓  
**Layer 2:** Production AI Engineering  
↓  
**Layer 3:** AI Engineering  
↓  
**Business Product - MVP/POC**

The five domain problems provide different technical challenges:

- **GridSense → Forecasting**
- **SupplyChainIQ → Risk & relational analytics**
- **RetailMind → Forecasting + recommendation**
- **FactoryGuard → Rare-event industrial ML**
- **EnergyTwin → Forecasting + anomaly detection + optimization**

All five ultimately converge on:

**RAG → Agents → MCP → Guardrails → Human Approval → LLMOps**

This creates a complete **Data Science → ML Engineering → AI Engineering → Enterprise AI** progression.
