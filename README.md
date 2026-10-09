# UDCM — Universal Data Collection & Intelligence Multi-Agent Engine

[![Phase 0: Architecture & Research](https://img.shields.io/badge/Phase-0%20Foundation-blue.svg)](docs/PHASE_0_COMPLETION.md)
[![License: Apache 2.0](https://img.shields.io/badge/License-Apache%202.0-green.svg)](LICENSE)
[![Python: 3.11+](https://img.shields.io/badge/Python-3.11%2B-blue.svg)](pyproject.toml)

> **UDCM** is an autonomous multi-agent system that transforms high-level user data objectives into reliable, structured, validated, and explainable datasets from heterogeneous sources.

---

## 1. Project Identity & Overview

* **Project Name**: UDCM
* **Full Name**: Universal Data Collection & Intelligence Multi-Agent Engine
* **Project Status**: **Phase 0 (Architecture, Specification, and Research Foundation)**

### 1.1 Vision
To pioneer an autonomous data intelligence workforce capable of discovering, ingesting, harmonizing, validating, and explaining open and enterprise data across the internet with zero hand-crafted scrapers or brittle static pipelines.

### 1.2 Mission
To provide researchers, data engineers, and intelligence analysts with a domain-agnostic multi-agent engine that takes a declarative natural-language objective (e.g., *"Collect all railway stations in Tamil Nadu, combine reliable sources, remove duplicates, verify coordinates, and produce a clean GeoJSON dataset"*) and autonomously synthesizes a publication-grade, provenance-backed dataset.

### 1.3 Core Principles
1. **Domain-Agnostic Core**: The core orchestrator and data engines contain zero domain-specific assumptions. All domain rules are supplied through pluggable manifests and interface contracts.
2. **Hybrid Cognitive + Deterministic Execution**: LLMs are strictly reserved for perception, planning, semantic mapping, and ambiguity arbitration. High-volume record filtering, coordinate transformations, spatial indexing, blocking, and aggregations are strictly executed by deterministic, compiled C++/Rust engines (DuckDB, Polars, Shapely).
3. **Evidence-Driven Lineage (W3C PROV)**: Every attribute, cell, and conflict decision is traced to its origin raw byte payload with cryptographic SHA-256 hashes and explicit agent justification logs.
4. **Closed-Loop Quality Feedback**: Downstream validation and conflict detection actively communicate with upstream planners to trigger fallback sources or refine collection strategies.
5. **Ethical & Safe Harvesting**: Mandatory deterministic guardrails for robots.txt compliance, adaptive rate-limiting, and domain throttling.

### 1.4 Long-Term Goals
* Eliminate the human engineering bottleneck required to build bespoke web scrapers and ETL adapters for new domains.
* Create a self-improving data intelligence engine that accumulates episodic knowledge across missions.
* Produce explainable truth discovery that outperforms traditional heuristics on multi-source conflicting records.

### 1.5 Explicit Non-Goals
* **Not a pure web scraper**: UDCM is not merely a tool for dumping raw HTML or downloading pages.
* **Not a static ETL orchestrator**: UDCM does not replace Airflow/Dagster for scheduled, pre-defined warehouse transformations.
* **Not an unconstrained chatbot**: Agents do not engage in open-ended creative conversations; they operate as specialized workers executing discrete contracts within a supervised DAG.
* **Not railway-specific**: While UDCM originated from the railway data collector project (`RI-data-Collector`), all railway logic is strictly sequestered in the `plugins/railway/` domain plugin.

### 1.6 Target Users
* **Data Engineers & Data Scientists**: Needing instant zero-shot dataset bootstrapping without writing custom spiders.
* **Geospatial & Urban Researchers**: Requiring verified, cross-referenced spatial infrastructure datasets.
* **Policy Makers & Academic Researchers**: Requiring fully auditable datasets backed by cryptographic provenance certificates.

### 1.7 Primary Use Cases
* **Infrastructure Asset Harvesting**: Cataloging transportation, healthcare, or municipal infrastructure across regional jurisdictions.
* **Multi-Source Cross-Verification**: Reconciling discrepancies between official governmental portals and crowdsourced registries (e.g., OpenStreetMap).
* **Ad-Hoc Intelligence Research**: Acquiring and harmonizing fragmented public data during crisis response or rapid research investigations.

---

## 2. Conceptual Architecture at a Glance

UDCM is organized into **11 decoupled layers**:

```mermaid
graph TD
    UI[1. User Interface Layer (CLI / API)] --> ML[2. Mission Layer]
    ML --> OL[3. Orchestration Layer]
    OL <--> AL[4. Agent Layer (12 Specialized Agents)]
    AL <--> IL[5. Intelligence Layer (LiteLLM / Embeddings)]
    AL --> SCL[6. Source & Connector Layer]
    AL --> DPL[7. Data Processing Layer (DuckDB / Polars)]
    DPL <--> QTL[8. Quality & Trust Layer]
    AL <--> QTL
    AL <--> MKL[9. Memory & Knowledge Layer]
    QTL --> SOL[10. Storage & Output Layer (Parquet / GeoJSON)]
    DPLG[11. Domain Plugin Layer] -.->|Inversion of Control| ML & DPL & QTL
```

---

## 3. The 12 Specialized Agents

1. **Orchestrator Agent**: Deconstructs objectives into execution DAGs and manages mission state.
2. **Discovery Agent**: Identifies candidate web sources, portals, and endpoints.
3. **Research Agent**: Investigates documentation, licensing (ODbL, CC-BY), and access constraints.
4. **Source Intelligence Agent**: Probes endpoint capabilities, mime-types, and rate limits.
5. **Extraction Agent**: Executes resilient, throttled raw data downloads.
6. **Schema Intelligence Agent**: Infers raw schemas and generates semantic mappings to canonical models.
7. **Normalization Agent**: Deterministically standardizes text, dates, coordinates (EPSG:4326), and datatypes.
8. **Entity Resolution Agent**: Blocks, scores, and clusters duplicate entities across sources.
9. **Validation Agent**: Enforces structural, spatial, and domain-specific integrity constraints.
10. **Conflict Resolution Agent**: Resolves discrepancies across conflicting sources using evidence weights.
11. **Enrichment Agent**: Executes spatial joins and secondary lookups to impute missing fields.
12. **Quality Agent**: Computes composite quality scores and generates W3C PROV lineage certificates.

---

## 4. Phase 0 Documentation Index

The complete architectural, research, and technical specification is documented in the following Phase 0 records:

* [Existing Systems & Prior Art Survey](docs/EXISTING_SYSTEMS.md) — Comprehensive survey of commercial tools, open-source systems, academic literature, and AI research.
* [Research Gap Analysis](docs/RESEARCH_GAP.md) — Exact formulation of the core research problem, central research question, and capability gaps.
* [Novelty & Differentiation Analysis](docs/NOVELTY.md) — Rigorous taxonomy of prior art vs. architectural synthesis vs. unverified novelty hypotheses.
* [System Requirements Specification](docs/REQUIREMENTS.md) — Detailed catalog of Functional (`UDCM-FR-xxx`) and Non-Functional (`UDCM-NFR-xxx`) requirements.
* [System Architecture](docs/ARCHITECTURE.md) — Deep architectural specification of the 11-layer domain-agnostic system.
* [Multi-Agent Architecture](docs/AGENT_ARCHITECTURE.md) — Detailed agent specifications, input/output contracts, and hybrid execution rules.
* [End-to-End Data Lifecycle](docs/DATA_LIFECYCLE.md) — Complete 19-stage state transition and data transformation journey.
* [Technology Stack & ADRs](docs/TECH_STACK.md) — Decision matrices evaluating backend, data processing, LLM gateway, and storage engines.
* [Benchmark & Research Strategy](docs/BENCHMARK_STRATEGY.md) — Evaluation methodology, baselines, quantitative metrics, and domain testbeds.
* [Phase 0 Completion & Architectural Review](docs/PHASE_0_COMPLETION.md) — Verification checklist, identified risks, assumptions, and Phase 1 roadmap.

---

## 5. Repository Structure

```
UDCM/
├── docs/                   # Architecture, requirements, and research specifications
├── research/               # Literature reviews, prior art notes, and comparative studies
│   ├── literature/
│   ├── existing_systems/
│   ├── comparisons/
│   └── notes/
├── architecture/           # Architecture diagrams and Architectural Decision Records (ADRs)
│   ├── diagrams/
│   └── decisions/
├── src/
│   └── udcm/               # Core UDCM domain-agnostic engine (Phase 1+)
├── tests/                  # Unit, integration, and property-based test suites
├── benchmarks/             # Benchmarking suites, evaluation runners, and baselines
├── experiments/            # Exploratory research and ablation studies
├── data/
│   ├── raw/                # Content-addressed raw payload lake (SHA-256)
│   ├── processed/          # Release artifacts (Parquet, GeoJSON, SQLite)
│   └── samples/            # Static fixtures for testing and development
├── plugins/
│   └── railway/            # Reference Domain Plugin: Railway Infrastructure
├── scripts/                # Utility scripts, data generators, and dev tooling
├── .github/                # GitHub Actions workflows and CI configurations
├── pyproject.toml          # PEP 621 Python package configuration and dependencies
├── LICENSE                 # Apache-2.0 Open Source License
└── README.md               # Main project documentation entrypoint
```

---

## 6. Development & Research Roadmap

* **Phase 0: Architecture, Research & Foundation** *(Current)*
  * Project identity, research problem definition, prior art survey, requirements, architecture, multi-agent specifications, tech stack ADRs, and repository scaffolding.
* **Phase 1: Core Domain Plugin & Data Model Foundation** *(Upcoming)*
  * Implement domain plugin contracts, Pydantic canonical schemas, DuckDB staging layer, and the reference Railway domain plugin.
* **Phase 2: Hybrid Multi-Agent Runtime & Ingestion Engine**
  * Implement agent lifecycle, Orchestrator state machine, Extraction Agent with throttling, and Schema Intelligence Agent.
* **Phase 3: Harmonization, Entity Resolution & Quality Engine**
  * Implement deterministic blocking, spatial KD-Tree indexing, Great Expectations validation, and W3C PROV lineage generation.
* **Phase 4: Empirical Evaluation & Benchmarking**
  * Execute comparative benchmark suite against baselines across multiple domains.

---

## 7. License

This project is licensed under the **Apache License 2.0** — see the [LICENSE](LICENSE) file for details.
