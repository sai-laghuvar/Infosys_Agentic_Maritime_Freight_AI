# 🚢 FreightQuote AI — Milestone 4

## Agentic AI for Maritime Freight Pricing & Route Optimization

**Infosys Springboard 7.0 — Batch 1**  
**Milestone:** 4  
**Domain:** Maritime / Ocean Freight + Agentic AI  
**Application:** Streamlit  
**Backend:** FastAPI  
**Database:** SQLite  
**LLM:** Qwen 2.5  
**Translation:** NLLB-200  
**RAG:** FAISS + BM25  
**Weather:** Open-Meteo  
**Deployment/Preview:** Google Colab + Cloudflare Tunnel / Docker-ready architecture

---

## 📌 Table of Contents

1. [Project Overview](#1-project-overview)
2. [Problem Statement](#2-problem-statement)
3. [Objectives](#3-objectives)
4. [Proposed Solution](#4-proposed-solution)
5. [Key Features](#5-key-features)
6. [System Architecture](#6-system-architecture)
7. [Nine AI Agents](#7-nine-ai-agents)
8. [Shared Platform Features](#8-shared-platform-features)
9. [AI Copilot](#9-ai-copilot)
10. [RAG and Document Intelligence](#10-rag-and-document-intelligence)
11. [Machine Learning](#11-machine-learning)
12. [Route Optimization](#12-route-optimization)
13. [Security and RBAC](#13-security-and-rbac)
14. [Admin Dashboard](#14-admin-dashboard)
15. [Database and Seed Data](#15-database-and-seed-data)
16. [Technology Stack](#16-technology-stack)
17. [Project Structure](#17-project-structure)
18. [Running the Project](#18-running-the-project)
19. [Cloudflare Public Preview](#19-cloudflare-public-preview)
20. [M4 Screenshots](#20-m4-screenshots)
21. [Testing and Validation](#21-testing-and-validation)
22. [Limitations](#22-limitations)
23. [Future Scope](#23-future-scope)
24. [Conclusion](#24-conclusion)

---

# 1. Project Overview

FreightQuote AI is an **agentic maritime intelligence and predictive-operations platform** designed to support ocean-freight decisions. The system brings route intelligence, freight pricing, carrier analysis, weather risk, margin prediction, customs and tariff analysis, document processing, translation and document-based retrieval into a single Streamlit workspace.

The Milestone 4 notebook is a self-contained project generator and launcher. It recreates the `freight_app` application modules, installs the required Python dependencies, initializes and seeds the SQLite database, starts the FastAPI model service, launches Streamlit and can expose the Streamlit application through a Cloudflare Tunnel.

The platform is organized around **nine numbered agents** plus shared platform capabilities. The current navigation explicitly contains Agent 1 through Agent 9, with Notifications treated as a shared feature rather than an additional numbered agent.

The core design principle is to use specialized tools, structured data, machine-learning outputs, APIs and document retrieval as the source of operational evidence, while the language model provides natural-language reasoning and explanation over that evidence.

---

# 2. Problem Statement

Maritime freight decisions are affected by many changing signals and are often handled through disconnected operational tools.

Major problems addressed by FreightQuote AI include:

- **Freight-price uncertainty:** Quotes depend on base freight, fuel/BAF and additional charges.
- **Route uncertainty:** Distance, port congestion, dwell time and operational risk influence route selection.
- **Weather disruption:** Severe weather can affect port and vessel operations.
- **Carrier selection:** Teams need reliability, on-time performance, cost and risk information.
- **Margin pressure:** A commercially attractive quote may still produce poor profitability.
- **Customs complexity:** HS codes, duties, taxes and required documentation affect clearance.
- **Document overhead:** Bills of Lading and other shipping documents require extraction and validation.
- **Distributed knowledge:** Important maritime information exists in PDFs, manuals, contracts and policies.
- **Language barriers:** Maritime documents and operational instructions may need multilingual support.
- **Operational alerts:** Incidents and risks require a centralized notification surface.

FreightQuote AI addresses these problems by creating a connected intelligence layer instead of isolated operational views.

---

# 3. Objectives

The Milestone 4 objectives are:

1. Build an integrated maritime decision-support workspace.
2. Implement nine specialized AI-agent modules.
3. Connect structured operational data with ML, APIs and documents.
4. Provide a natural-language AI Copilot.
5. Support document retrieval through FAISS and BM25.
6. Provide route, port and congestion intelligence.
7. Provide freight pricing and margin intelligence.
8. Provide carrier and weather-risk analysis.
9. Provide customs, tariff and document intelligence.
10. Provide multilingual translation.
11. Provide operational notifications and monitoring.
12. Provide Knowledge Graph, Digital Twin and anomaly-analysis capabilities.
13. Implement authentication, JWT sessions and RBAC.
14. Provide an administrative command center.
15. Support reproducible execution from the Milestone 4 notebook.
16. Support public preview through Cloudflare Tunnel.

---

# 4. Proposed Solution

The platform follows the general decision-support flow:

```text
User Request
    ↓
Authentication / RBAC
    ↓
AI Copilot or Direct Agent
    ↓
Intent / Module Selection
    ↓
SQL + ML + Route Solver + API + RAG
    ↓
Evidence / Results
    ↓
Qwen 2.5 Reasoning
    ↓
Grounded Natural-Language Response
```

The overall intelligence workflow is:

```text
Retrieve → Calculate → Predict → Reason → Respond
```

The language model is therefore not intended to independently invent operational numbers. It receives information from the relevant application components and turns that information into a human-readable answer.

---

# 5. Key Features

| Feature | Purpose |
|---|---|
| AI Copilot | Natural-language maritime decision support |
| Agent 1 — Route AI | Route, port, congestion and sailing intelligence |
| Agent 2 — Spot Quotes | Freight quotation and cost analysis |
| Agent 3 — Carriers | Carrier reliability and performance analysis |
| Agent 4 — Weather Risk | Weather, storm and port-risk analysis |
| Agent 5 — Margin Predictor | Margin and profitability intelligence |
| Agent 6 — Customs & Tariff | HS-code, duty and clearance analysis |
| Agent 7 — Docs (OCR) | Bill of Lading/document extraction and validation |
| Agent 8 — Translation | Multilingual maritime translation |
| Agent 9 — PDF RAG Studio | Custom document indexing and Q&A |
| Notifications | Centralized operational alerts/incidents |
| Knowledge Graph | Maritime relationship visualization |
| Digital Twin | Port/network scenario simulation |
| Anomaly Scanner | Detection of unusual operational patterns |
| Data Feed Center | Data/system feed visibility |
| Admin Dashboard | Platform administration and telemetry |
| Authentication/RBAC | Secure role-aware access |

---

# 6. System Architecture

```text
┌─────────────────────────────────────────────────────────┐
│                    USER / OPERATOR                      │
└──────────────────────────┬──────────────────────────────┘
                           ↓
┌─────────────────────────────────────────────────────────┐
│ EXPERIENCE                                               │
│ Streamlit UI • AI Copilot • Dashboards • Navigation    │
└──────────────────────────┬──────────────────────────────┘
                           ↓
┌─────────────────────────────────────────────────────────┐
│ MULTI-AGENT ORCHESTRATION                              │
│ Intent Routing • Agent Selection • Result Aggregation   │
└──────────────────────────┬──────────────────────────────┘
                           ↓
┌─────────────────────────────────────────────────────────┐
│ NINE SPECIALIZED AGENTS                                 │
│ Route • Pricing • Carrier • Weather • Margin            │
│ Customs • Docs • Translation • PDF RAG                  │
└──────────────────────────┬──────────────────────────────┘
                           ↓
┌─────────────────────────────────────────────────────────┐
│ DATA & INTELLIGENCE                                     │
│ SQLite • ML Models • FAISS • BM25 • Open-Meteo         │
│ Documents • Knowledge Graph • Digital Twin             │
└──────────────────────────┬──────────────────────────────┘
                           ↓
┌─────────────────────────────────────────────────────────┐
│ GENERATION                                               │
│ Qwen 2.5 • NLLB-200 • Grounded Response                │
└─────────────────────────────────────────────────────────┘
```

### Five conceptual layers

1. **Authentication & Access** — bcrypt/JWT/RBAC.
2. **FreightQuote Platform** — Copilot and nine agents.
3. **Multi-Agent Orchestration** — routing and coordination.
4. **Data & Intelligence** — SQLite, ML, RAG and external signals.
5. **Generation** — Qwen 2.5 and NLLB-200.

---

# 7. Nine AI Agents

## Agent 1 — Route Intelligence & Eco-Speed AI

Agent 1 provides maritime route and port intelligence.

Capabilities include:

- Port network information
- Port congestion index
- Average port dwell time
- Active-vessel indicators
- Haversine geographic distance
- Sailing-time estimation
- Route-risk analysis
- Candidate route comparison
- Port network mapping
- Vessel sailing simulation
- Bunker/fuel cost simulation
- Eco-speed/slow-steaming analysis
- Route-delay prediction/advisory

The notebook includes a route model comparison view and a ten-parameter sailing simulator.

### Route concept

```text
Origin + Destination
       ↓
Port Coordinates
       ↓
Distance Calculation
       ↓
Congestion + Dwell + Risk
       ↓
Route Scoring
       ↓
Recommended / Ranked Route
```

---

## Agent 2 — Spot Freight Quote & Cost Engine

Agent 2 calculates and analyzes container freight quotes.

Capabilities include:

- Spot freight quote calculation
- Base freight analysis
- Fuel/BAF surcharge analysis
- Insurance and customs-fee components
- Final-price calculation
- Pricing sensitivity
- Quote comparison
- Pricing regression analysis
- Quote explanation

Conceptually:

```text
Base Freight
+ Fuel / BAF
+ Insurance
+ Customs / Fees
+ Other Charges
        ↓
Final Quote
```

---

## Agent 3 — Ocean Carrier Intelligence & Audit

Agent 3 analyzes carrier performance.

Capabilities include:

- Carrier reliability
- Rating comparison
- On-time delivery benchmarks
- Average cost index
- Risk-level analysis
- Carrier scorecards
- Fleet/capacity allocation simulation
- Performance-oriented decision support

A carrier with strong reliability and on-time performance can be identified through the carrier comparison views.

---

## Agent 4 — Weather Risk & Typhoon Predictor

Agent 4 provides weather and operational-risk intelligence.

Capabilities include:

- Open-Meteo weather telemetry
- Port weather analysis
- Weather severity rating
- Wind and wave analysis
- Storm/typhoon indicators
- Potential delay risk
- Cyclone rerouting/simulation concepts
- Weather visualization
- AI weather advisory

The agent can combine current API information with application risk logic.

---

## Agent 5 — Freight Margin Predictor & Yield Engine

Agent 5 evaluates quote profitability.

Capabilities include:

- Freight margin prediction
- Margin percentage analysis
- Cost/revenue relationships
- BAF impact simulation
- Rate sensitivity
- Carrier yield comparison
- Margin distribution analysis
- Margin optimization support

The purpose is to avoid optimizing only for the lowest freight quote when that quote may produce poor commercial margins.

---

## Agent 6 — Customs & Tariff Compliance Engine

Agent 6 supports customs and tariff decisions.

Capabilities include:

- HS-code analysis
- Tariff lookup within the application dataset
- Basic Customs Duty (BCD)
- IGST calculation
- Customs clearance-risk estimation
- Required-document awareness
- Regulatory advisory
- High-risk lane identification

Typical workflow:

```text
Cargo
  ↓
HS Code
  ↓
Origin / Destination
  ↓
Duty + Tax
  ↓
Required Documents
  ↓
Clearance Risk
```

---

## Agent 7 — Bill of Lading & Document OCR Studio

Agent 7 processes shipping documents.

Capabilities include:

- Bill of Lading information extraction
- OCR/text extraction
- Field extraction
- Document validation
- Shipping-document generation
- Document anomaly/fraud-analysis concepts

Typical flow:

```text
Document Upload
      ↓
OCR / Text Extraction
      ↓
Field Extraction
      ↓
Validation
      ↓
Structured Information
```

---

## Agent 8 — Multilingual Maritime Translator

Agent 8 uses **NLLB-200** for multilingual translation.

Capabilities include:

- Maritime text translation
- Document translation
- Copilot-response translation
- Multilingual workflows
- Maritime glossary handling
- Numerical-integrity checks
- Protection of domain terminology

Important values such as currency, measurements, HS codes and maritime terminology should remain intact during translation.

---

## Agent 9 — PDF Vector RAG Studio

Agent 9 is the custom document knowledge workbench.

Supported uploads include:

- PDF
- TXT
- Markdown

The workflow is:

```text
Upload Document
      ↓
Text Extraction
      ↓
Chunking
      ↓
Embeddings
      ↓
FAISS + BM25
      ↓
Relevant Evidence
      ↓
Grounded Q&A
```

The UI includes document Q&A, an active knowledge-base manager, document filtering/isolation and citation/evidence information.

---

# 8. Shared Platform Features

The nine agents are supported by common platform services.

### Notifications

Central operational alert and incident stream. This is **not Agent 10**.

### Knowledge Graph

Interactive relationships between monitored ports, carriers and shipping corridors.

### Digital Twin

Scenario-oriented simulation of port congestion, vessel queues and corridor flow.

### Anomaly Scanner

Highlights unusual patterns in operational data.

### Data Feed Center

Provides visibility into the application's data and system feeds.

### Admin Dashboard

Provides platform-wide administration, user management, database maintenance, GPU/VRAM telemetry and chat monitoring.

### Profile

Provides the user-facing profile/session area.

---

# 9. AI Copilot

The AI Copilot is the primary natural-language interface.

A user can ask a combined question such as:

> What will it cost to ship a 20ft container from Chennai to Rotterdam next week, and are there any weather risks on the route?

The intended reasoning flow is:

```text
User Query
   ↓
Intent / Agent Selection
   ↓
Pricing Agent ──────────┐
Route Agent ────────────┼──→ Combined Context
Weather Agent ──────────┘
   ↓
Grounding / Validation
   ↓
Qwen 2.5
   ↓
Natural-Language Answer
```

For structured values, the application can obtain evidence from SQL/data tables, calculations and ML outputs. For weather questions it can use weather data. For document questions it can use RAG retrieval.

### Hallucination note

The architecture is designed to **reduce hallucination risk through grounding**. It should not be described as a mathematical guarantee of zero hallucination.

---

# 10. RAG and Document Intelligence

The RAG design combines semantic and lexical retrieval.

### FAISS

FAISS is used for vector similarity retrieval. It helps find semantically relevant document chunks even when the query wording differs from the source.

### BM25

BM25 provides lexical retrieval and is useful for exact maritime terminology, identifiers and phrases.

### Hybrid Retrieval

```text
                User Query
                 /       \
                /         \
        Dense Embedding   BM25 Query
              ↓               ↓
            FAISS           BM25
              \               /
               \             /
                ↓           ↓
                  Hybrid Ranking
                        ↓
                 Top Evidence Chunks
                        ↓
                    Grounding
                        ↓
                     Qwen
```

The RAG Builder used during development is conceptually separate from the application runtime: it creates searchable artifacts, while Agent 9/application RAG consumes retrieval resources and exposes them through the UI.

---

# 11. Machine Learning

The project uses classical ML for prediction and analytics.

Typical algorithms used across different tasks include:

- Random Forest
- Gradient Boosting
- Decision Tree
- Linear Regression
- Ridge Regression
- Lasso Regression
- Logistic Regression
- SVC / SVR
- Isolation Forest for anomaly detection

### General ML pipeline

```text
Dataset
  ↓
Cleaning / Preprocessing
  ↓
Feature Preparation
  ↓
Train / Validation
  ↓
Multiple Candidate Models
  ↓
Evaluation
  ↓
Best Candidate
  ↓
Serialized Model
  ↓
Agent Inference
```

### Important interpretation note

Some training workflows include fallback/synthetic data when suitable real datasets or target columns are unavailable. Metrics produced from synthetic fallback data must not be presented as real-world production accuracy.

---

# 12. Route Optimization

Agent 1 uses geographic and operational factors rather than relying only on straight-line distance.

### Haversine Distance

Haversine distance estimates great-circle distance between two latitude/longitude coordinates.

The application combines distance-related information with operational indicators such as:

- Congestion
- Dwell time
- Risk
- Sailing speed
- Bunker/fuel assumptions

The route simulator also exposes configurable sailing parameters and calculates voyage-time and operating-cost effects.

---

# 13. Security and RBAC

The application includes authentication and role-based access control.

### Authentication

- Password hashing with bcrypt
- JWT-based session handling
- Login/session verification
- Account lock/unlock handling
- Role-aware navigation

### Roles implemented in the M4 RBAC module

- **Admin** — full platform access, including Data Feed Center and Admin Dashboard.
- **Operations Manager** — operational access plus Data Feed Center, without Admin Dashboard.
- **Freight Broker** — operational access without administrative/data-feed controls.
- **Auditor** — read-oriented operational access plus Admin Dashboard for oversight.
- **Customer** — restricted access to Copilot, Spot Quotes, Weather Risk, Notifications and Translation.

The navigation is dynamically filtered according to the authenticated role, and sensitive branches also use access checks.

### Secrets

Credentials and sensitive values should be supplied through environment variables, Colab Secrets or an equivalent secret-management mechanism. Secrets must not be committed to the repository.

---

# 14. Admin Dashboard

The Admin Dashboard is the FreightQuote command center.

Current M4 functionality includes five major areas:

1. **Platform KPIs** — monitored ports, shipments, pending alerts and accelerator status.
2. **GPU & VRAM Telemetry** — CUDA availability, GPU device and VRAM information.
3. **User Management** — user listing, role management, account lock/unlock and administration.
4. **Database Maintenance** — administrative data operations.
5. **Chat Monitor** — recent Copilot activity for oversight.

The M4 notebook also contains GPU diagnostics for the FastAPI model server.

---

# 15. Database and Seed Data

The application uses SQLite for structured project data.

The M4 seed process creates operational demo records for areas including:

- Ports
- Users
- Shipments
- Weather risks
- Alerts
- Carriers
- Customers
- Freight quotes
- Customs tariffs
- Operational tables used by the broader platform

The seeded port network includes major ports such as Mumbai/JNPT, Mundra, Chennai, Singapore, Shanghai, Rotterdam, Antwerp, Hamburg, Los Angeles and other global locations.

The seed data is intended for demonstration and application testing. It should not be treated as live maritime operational data.

---

# 16. Technology Stack

| Layer | Technology |
|---|---|
| Language | Python |
| UI | Streamlit |
| Navigation | streamlit-option-menu |
| API | FastAPI / Uvicorn |
| Database | SQLite |
| LLM | Qwen 2.5 |
| Translation | NLLB-200 |
| Embeddings | Sentence Transformers / transformer embeddings |
| Dense Retrieval | FAISS |
| Sparse Retrieval | BM25 |
| ML | scikit-learn |
| PDF / Docs | pdfplumber, ReportLab, FPDF |
| Visualization | Plotly, Folium, streamlit-folium |
| Weather | Open-Meteo REST API |
| Authentication | bcrypt + PyJWT |
| Graph | NetworkX / graph visualization |
| GPU | PyTorch + CUDA where available |
| Environment | Google Colab / Python runtime |
| Public Preview | Cloudflare Tunnel |
| Containerization | Docker / Docker Compose |

The M4 notebook's generated `requirements.txt` includes the core runtime packages for Streamlit, Streamlit option menu, Folium, translation, Transformers, PyTorch, SentencePiece, Accelerate, PDF tooling, ReportLab, FPDF, bcrypt, Flask and Plotly.

---

# 17. Project Structure

The notebook generates the application under `freight_app/`.

```text
FreightQuote_AI/
│
├── Milestone4.ipynb
├── README.md
│
├── freight_app/
│   ├── app.py
│   ├── model_server.py
│   ├── admin_dash.py
│   ├── auth.py
│   ├── config.py
│   ├── db.py
│   ├── rbac.py
│   ├── seed_data.py
│   │
│   ├── ai_copilot.py
│   ├── intent_router.py
│   ├── llm_engine.py
│   ├── rag_engine.py
│   ├── translation_engine.py
│   ├── weather_context.py
│   │
│   ├── agent1_route.py
│   ├── agent2_freight.py
│   ├── agent3_freight.py
│   ├── agent4_weather_freight.py
│   ├── agent5_margin.py
│   ├── agent6_customs_freight.py
│   ├── agent7_docs.py
│   ├── agent8_translation.py
│   ├── agent9_pdf_rag.py
│   │
│   ├── notifications.py
│   ├── knowledge_graph.py
│   ├── digital_twin.py
│   ├── anomaly_scanner.py
│   ├── data_feed_center.py
│   ├── profile.py
│   └── ui_theme.py
│
├── runtime_data/
│   ├── models/
│   ├── metrics/
│   ├── faiss_indexes/
│   ├── bm25_indexes/
│   └── documents/
│
├── screenshots-M4/
└── tests/
```

The exact generated directory contents can vary with the final notebook/runtime version. The important application boundary is the `freight_app/` module set and its runtime data.

---

# 18. Running the Project

## Google Colab

The Milestone 4 notebook is designed to recreate and launch the project.

### General flow

```text
Open Milestone4.ipynb
        ↓
Run cells from top to bottom
        ↓
Create freight_app/
        ↓
Install dependencies
        ↓
Initialize SQLite
        ↓
Seed demonstration data
        ↓
Start FastAPI model service
        ↓
Start Streamlit
        ↓
Optional Cloudflare Tunnel
```

The notebook launches Streamlit on port **8501** and the FastAPI model service on port **8000**.

### Local Streamlit command

```bash
streamlit run freight_app/app.py
```

### FastAPI command

```bash
python -m uvicorn model_server:app --host 0.0.0.0 --port 8000
```

Run the FastAPI command from the `freight_app` application directory when using the generated notebook layout.

---

# 19. Cloudflare Public Preview

The M4 notebook contains a Cloudflare Tunnel launch step.

Conceptually:

```text
Public Browser
      ↓
Cloudflare Tunnel
      ↓
Streamlit :8501
      ↓
FastAPI :8000
```

The notebook downloads `cloudflared` when required and starts a temporary Quick Tunnel against the Streamlit port.

Example:

```bash
cloudflared tunnel --url http://localhost:8501
```

A Quick Tunnel URL is temporary and should be used for development/demo purposes. For persistent hosting, use a managed Cloudflare Tunnel on a cloud VM/server together with Docker Compose and persistent storage.

---

# 20. M4 Screenshots

The supplied screenshot folder contains the following captured application views:

```text
screenshots-M4/
├── login.jpg
├── knowledge_graph.jpg
├── digital_twin.jpg
├── data_feed_center.jpg
├── anomaly_scanner.jpg
├── ai_copilot.jpg
├── agent9_pdf_rag.jpg
├── agent8_alerts.jpg
├── agent7_docs.jpg
├── agent6_customs.jpg
├── agent5_margin.jpg
├── agent4_weather.jpg
├── agent3_carrier.jpg
├── agent2_pricing.jpg
├── agent1_route.jpg
└── admin_dashboard.jpg
```

## Login

![Login](screenshots-M4/login.jpg)

The login screenshot documents the authentication entry point.

## Admin Dashboard

![Admin Dashboard](screenshots-M4/admin_dashboard.jpg)

Shows the administrative command-center interface.

## Agent 1 — Route AI

![Route AI](screenshots-M4/agent1_route.jpg)

Shows route and port intelligence.

## Agent 2 — Pricing

![Spot Pricing](screenshots-M4/agent2_pricing.jpg)

Shows spot freight quotation and pricing analysis.

## Agent 3 — Carrier Intelligence

![Carrier Intelligence](screenshots-M4/agent3_carrier.jpg)

Shows carrier performance and comparison.

## Agent 4 — Weather Risk

![Weather Risk](screenshots-M4/agent4_weather.jpg)

Shows weather and maritime risk information.

## Agent 5 — Margin Predictor

![Margin Predictor](screenshots-M4/agent5_margin.jpg)

Shows margin and profitability analysis.

## Agent 6 — Customs

![Customs](screenshots-M4/agent6_customs.jpg)

Shows customs and tariff analysis.

## Agent 7 — Docs / OCR

![Docs OCR](screenshots-M4/agent7_docs.jpg)

Shows document/OCR functionality.

## Agent 8 / Alerts Screenshot

![Alerts](screenshots-M4/agent8_alerts.jpg)

This filename reflects the captured screenshot. In the **final architecture, Alerts/Incidents is the shared Notifications module; Agent 8 is Translation**.

## Agent 9 — PDF RAG

![PDF RAG](screenshots-M4/agent9_pdf_rag.jpg)

Shows custom document retrieval and Q&A.

## AI Copilot

![AI Copilot](screenshots-M4/ai_copilot.jpg)

Shows the natural-language Copilot interface.

## Anomaly Scanner

![Anomaly Scanner](screenshots-M4/anomaly_scanner.jpg)

Shows anomaly-analysis functionality.

## Data Feed Center

![Data Feed Center](screenshots-M4/data_feed_center.jpg)

Shows the data/system feed interface.

## Digital Twin

![Digital Twin](screenshots-M4/digital_twin.jpg)

Shows maritime scenario simulation.

## Knowledge Graph

![Knowledge Graph](screenshots-M4/knowledge_graph.jpg)

Shows maritime entity/network relationships.

---

# 21. Testing and Validation

Recommended M4 validation checklist:

### Authentication

- [ ] Signup works.
- [ ] Login works.
- [ ] Invalid credentials are rejected.
- [ ] Session/JWT state is maintained.
- [ ] Logout returns to authentication.
- [ ] RBAC hides unauthorized modules.

### Agent Validation

- [ ] Agent 1 Route AI loads.
- [ ] Agent 2 Spot Quotes loads.
- [ ] Agent 3 Carriers loads.
- [ ] Agent 4 Weather Risk loads.
- [ ] Agent 5 Margin Predictor loads.
- [ ] Agent 6 Customs & Tariff loads.
- [ ] Agent 7 Docs/OCR loads.
- [ ] Agent 8 Translation loads.
- [ ] Agent 9 PDF RAG loads.

### Copilot

- [ ] Query is accepted.
- [ ] Appropriate module/tool is selected.
- [ ] Structured values come from application evidence.
- [ ] RAG questions retrieve supporting content.
- [ ] Unsupported questions fail safely rather than inventing business facts.

### RAG

- [ ] Document upload works.
- [ ] Text extraction works.
- [ ] Indexing works.
- [ ] FAISS retrieval works.
- [ ] BM25 retrieval works.
- [ ] Evidence/citation information is displayed.

### API / Model Server

- [ ] FastAPI starts on port 8000.
- [ ] `/health` responds.
- [ ] Qwen model loading is verified.
- [ ] NLLB loading is verified when translation is used.
- [ ] GPU is used when CUDA is available.

### Application

- [ ] Streamlit starts on port 8501.
- [ ] Database initializes.
- [ ] Seed data is available.
- [ ] Notifications load.
- [ ] Knowledge Graph loads.
- [ ] Digital Twin loads.
- [ ] Anomaly Scanner loads.
- [ ] Data Feed Center loads for authorized roles.
- [ ] Admin Dashboard loads for authorized roles.

---

# 22. Limitations

FreightQuote AI is an **academic/internship prototype** and should not be treated as a production maritime control or regulatory system.

### Demo/Seed Data

The notebook creates demonstration records. They are not equivalent to continuously updated production data.

### ML Data

Where fallback/synthetic data is used, its metrics should not be presented as real-world performance.

### Live Maritime Telemetry

The project does not establish a universal live AIS/vessel-tracking system by default. Real-time AIS and richer port telemetry are future integration areas.

### Carrier Rates

Direct production carrier-rate/schedule APIs are not guaranteed by the notebook and should be separately integrated for real operations.

### Customs

Tariff and customs decisions must be checked against current authoritative regulations before real-world use.

### Weather

Weather APIs and risk logic are decision-support inputs, not guarantees of future conditions.

### LLM Hallucination

Grounding reduces hallucination risk but cannot guarantee zero hallucinations.

### SQLite

SQLite is appropriate for the prototype. A production, highly concurrent deployment may require PostgreSQL or another enterprise database.

### Digital Twin

The Digital Twin is a simulation/decision-support capability rather than a complete synchronized replica of the physical maritime world.

---

# 23. Future Scope

## Advanced ML

- XGBoost
- LightGBM
- Ensemble models
- Model drift monitoring
- Automated retraining

## Real-Time Maritime Data

- AIS vessel positions
- Live ETA feeds
- Real port congestion telemetry
- Carrier APIs
- Live freight-rate APIs

## Production Data Layer

- PostgreSQL
- Redis
- Cloud object storage
- Enterprise vector databases

## Advanced RAG

- Neural reranking
- Better retrieval evaluation
- Document versioning
- Citation verification
- RAG evaluation datasets

## Agentic AI

- More advanced multi-step planning
- Tool execution loops
- Agent evaluation
- Human feedback
- Confidence/uncertainty reporting

## Digital Twin

- Real-time synchronization
- Monte Carlo scenarios
- Predictive disruption simulation
- Corridor-level optimization

## Deployment

- Docker Compose production setup
- Managed Cloudflare Tunnel
- Kubernetes
- CI/CD
- Centralized logging
- Monitoring and observability
- Enterprise secret management

---

# 24. Conclusion

FreightQuote AI demonstrates how **Agentic AI can combine specialized operational agents, structured maritime data, machine learning, document retrieval, weather information, simulation and natural-language reasoning in a single decision-support platform**.

The nine-agent architecture is:

```text
1. Route AI
2. Spot Quotes
3. Carriers
4. Weather Risk
5. Margin Predictor
6. Customs & Tariff
7. Docs (OCR)
8. Translation
9. PDF RAG Studio
```

The platform is complemented by:

```text
AI Copilot
Notifications
Knowledge Graph
Digital Twin
Anomaly Scanner
Data Feed Center
Admin Dashboard
Authentication
RBAC
```

The key architectural idea is:

```text
Operational Data
      +
Calculations / Route Solver
      +
Machine Learning
      +
RAG
      +
External APIs
      +
Specialized Agents
      ↓
Grounded Context
      ↓
Qwen 2.5
      ↓
Human-Readable Decision Support
```

This makes the project a practical demonstration of an end-to-end Agentic AI workflow for maritime freight operations while keeping domain-specific evidence and calculations separate from natural-language generation.

---

## 🎓 Project Information

**Project:** FreightQuote AI  
**Theme:** Agentic AI for Maritime Freight Pricing & Route Optimization  
**Program:** Infosys Springboard 7.0  
**Batch:** 1  
**Milestone:** 4  
**UI:** Streamlit  
**API:** FastAPI  
**Database:** SQLite  
**LLM:** Qwen 2.5  
**Translation:** NLLB-200  
**RAG:** FAISS + BM25  
**Weather:** Open-Meteo  
**ML:** scikit-learn  
**Public Preview:** Cloudflare Tunnel  

---

## ⚠️ Disclaimer

This project is developed for internship/academic demonstration, learning and experimentation. It should not replace authoritative maritime, customs, financial, contractual, safety or regulatory systems. Real-world decisions should be validated against current authoritative sources and operational professionals.
