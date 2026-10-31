# Azure Databricks Compute & Data Transformation Engine

###  Tech Stack Matrix
*  **Compute Engine:** Apache Spark & PySpark (Batch / Streaming)
*  **Storage Fabric:** Delta Lake (Medallion Architecture Layering)
*  **Governance & Lineage:** Unity Catalog
*  **AI Consumption:** Databricks Genie & Genie Agents
*  **Security Boundary:** Azure Key Vault Backed Secret Scopes
*  **Orchestrator Trigger:** Azure Data Factory (ADF) Dynamic Web Hooks

---

##  Executive Summary & Business Impact
This repository hosts the core processing engine running inside the **Azure Databricks Workspace**. It transforms raw transactional data into enterprise-grade analytics assets while maintaining production security standards.

###  Core Frameworks Delivered:
* **Medallion Architecture:** Decouples raw ingestion processing from business logic aggregation using high-throughput PySpark scripts.
* **Unified Governance:** Enforces row/column security access policies and end-to-end data lineage via Unity Catalog.
* **Lakehouse Performance Tuning:** Minimizes analytical cluster latency using Delta Lake Z-Ordering indexing and file compaction metrics.
* **GenAI-Ready Data Analytics:** Embeds structural schema constraints explicitly optimized for Databricks Genie AI Agents natural language processing.

---

##  Transformation Pipeline & Data Topology

```text
             [ Azure Data Factory / Dynamic Ingestion Trigger ]
                                     │
                                     ▼
┌───────────────────────────────── Azure Databricks Compute Workspace ─────────────────────────────────┐
│                                                                                                      │
│  ┌───────────────────────┐       ┌────────────────────────┐       ┌──────────────────────────────┐   │
│  │     Bronze Layer      │       │      Silver Layer      │       │          Gold Layer          │   │
│  │  (Raw / Append-Only)  │ ──💥─►│ (Cleaned / Anonymized) │ ──💥─►│  (Analytical Star Schema)    │   │
│  └───────────────────────┘       └────────────────────────┘       └──────────────────────────────┘   │
│              │                               │                                   │                   │
│              └───────────────────────────────┼───────────────────────────────────┘                   │
│                                              ▼                                                       │
│                                🔓 Unity Catalog Governance Layer                                     │
│                                (Lineage, Security Policies, Auditing)                                │
└──────────────────────────────────────────────┬───────────────────────────────────────────────────────┘
                                               │
                                               ▼
                                🤖 GenAI Consumption Tier
                                (Databricks Genie AI Agents & Dashboards)
```

* **🤎 Bronze Layer (Raw Ingestion):** Captures schemaless historical landing files from ADLS Gen2 with appended extraction metadata.
* **🥈 Silver Layer (Data Cleansing):** Executes schema validation, row de-duplication, and cryptographic SHA-256 PII/PHI masking logic.
* **🥇 Gold Layer (Model Optimization):** Materializes star-schema dimensions optimized with Z-Ordering structures for real-time reporting.

---

##  Key Technical Deliverables
* **Metadata-Driven Scalability:** The PySpark engine consumes structural parameters dynamically from ADF pipelines to handle multi-table routines.
* **ACID Transaction Safeguards:** Leverages Delta transactional logging mechanics to ensure failure-resilient concurrent data operations.
* **Semantic Layer Configuration:** Inject descriptive constraints allowing LLM data models to accurately interpret downstream relational assets.

---

##  Repository Layout
```text
├── config/                 # Environment and cluster configuration manifests
├── notebooks/              # Core transformation code blocks
│   ├── 00_workspace_setup  # Mount points, storage keys initialization setups
│   ├── 01_bronze_to_silver # Data cleansing, masking, deduplication notebooks
│   └── 02_silver_to_gold   # Dimensional modeling, star-schema creation, optimizations
├── tests/                  # PySpark unit tests & quality validation queries
└── README.md               # Compute engine documentation
```

---

##  Deployment & Execution Guide
1. **Repository Synchronization:** Link this repository inside your workspace via the **Databricks Git Integration** interface.
2. **Key Vault Scopes Setup:** Configure an Azure Key Vault-backed secret scope to safely retrieve operational database variables.
3. **Orchestrator Binding:** Point Azure Data Factory notebook execution tasks directly to the files residing in the `/notebooks` index.
