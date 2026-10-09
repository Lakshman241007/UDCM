# Research Gap Analysis

## 1. Context and Problem Statement

Data engineering workflows historically require human practitioners to write, debug, and maintain rigid, brittle pipelines. When faced with a new data objective—such as acquiring all geographical assets, administrative records, or entity registries for an under-served region—the process entails:
1. Manually searching search engines, data portals, and APIs.
2. Manually assessing data terms of service, rate limits, and reliability.
3. Writing custom extractors (HTTP scrapers, API clients, file format unpackers).
4. Inspecting undocumented raw schemas and hand-crafting transformation code.
5. Manually resolving duplicate entities with ad-hoc heuristics.
6. Hand-crafting validation checks and reconciling conflicting source values.

While specialized tools exist for isolated steps (e.g., dbt for transformation, Airflow for orchestration, Great Expectations for validation), the end-to-end cognitive synthesis required to transform a natural language objective into a verified, publication-grade dataset remains an open, unautomated challenge.

---

## 2. Research Problem & Central Research Question

### 2.1 The Core Research Problem
> **How can an autonomous, domain-agnostic computational architecture translate a high-level natural language data objective into an end-to-end data acquisition, harmonization, and validation mission, while minimizing human engineering effort and guaranteeing data integrity, provenance, and explainability?**

### 2.2 Central Research Question (CRQ)
> **Can a multi-agent, adaptive architecture autonomously transform an underspecified, high-level data objective into a validated, harmonized, and conflict-resolved dataset across heterogeneous, uncoordinated web sources with significantly reduced human configuration compared to traditional static ETL/ELT pipelines?**

### 2.3 Secondary Research Questions (SRQs)
* **SRQ-1 (Planning & Adaptability)**: Can cognitive agents decompose a declarative goal into a directed acquisition plan that dynamically adapts when candidate sources fail, experience schema drift, or return corrupt data?
* **SRQ-2 (Hybrid Semantic & Deterministic Resolution)**: How can LLM-based semantic reasoning be combined with deterministic blocking, string metrics, and spatial algorithms to achieve high entity resolution precision without prohibitive computational or token expense?
* **SRQ-3 (Truth Discovery & Evidence Attribution)**: How can multi-agent systems arbitrate conflicting records across heterogeneous sources without producing untraceable hallucinations or black-box selections?
* **SRQ-4 (Episodic Knowledge Retention)**: Can an autonomous multi-agent engine retain structural knowledge across consecutive missions (e.g., source reliability metrics, known schema mappings, rate-limit policies) to measurably improve future collection speed and accuracy?

---

## 3. Systematic Evaluation of Research Dimensions

The table below categorizes key technical capabilities according to their current scientific standing, distinguishing established prior art from genuine open research gaps.

| Capability Dimension | Classification | State of the Art | The Unresolved Gap |
| :--- | :--- | :--- | :--- |
| **High-level objective $\rightarrow$ automatic collection plan** | **Potential Gap** | LangChain / AutoGPT decompose general tasks; Text-to-SQL generates database queries. | No system decomposes a zero-shot data harvesting mission into multi-source extraction, validation contracts, and entity graphs automatically. |
| **Adaptive source selection** | **Potential Gap** | Web search APIs rank pages by relevance; source selection in databases relies on pre-computed cost models. | Autonomous agents evaluating uncoordinated source endpoints based on freshness, completeness, authority, and API constraints on-the-fly. |
| **Dynamic extraction strategy selection** | **Partially Explored** | Scrapy provides fixed spiders; Headless browser frameworks (Playwright) execute pre-written scripts. | Dynamic runtime selection: determining whether to download a raw dump, query a REST endpoint, or trigger DOM extraction based on source response. |
| **Multi-agent data acquisition** | **Partially Explored** | Multi-agent swarms for web browsing exist (e.g., CrewAI, AutoGen web scrapers). | Cooperative agent swarms with transactional boundaries, backpressure, rate-limit governance, and schema awareness. |
| **Agent-based schema understanding** | **Partially Explored** | LLM-based column classification (Narayan et al. 2022); schema matching algorithms (COMA++). | Zero-shot mapping of opaque, foreign-language, or heavily abbreviated schemas into unified canonical models without predefined ontologies. |
| **Cross-source entity resolution** | **Partially Explored** | Machine learning ER (Tamr, DeepMatcher); LLM pair matching (MatchGPT). | Hybrid agentic entity resolution combining deterministic blocking with LLM reasoning solely for edge-case arbitration in ad-hoc domains. |
| **Agent-based conflict resolution** | **Potential Gap** | Statistical truth discovery (Dong et al.); rule-based precedence matrices. | Contextual, evidence-driven multi-agent debate and provenance verification to arbitrate discrepancies across conflicting sources. |
| **Evidence-driven data decisions** | **Potential Gap** | Data provenance models (W3C PROV); auditing logs in enterprise tools. | Granular cell-level attribution linking each final record attribute back to the raw payload, agent reasoning log, and confidence score. |
| **Autonomous data-quality assessment** | **Partially Explored** | Great Expectations, Soda Core (declarative rules); automated data profiling (Pandas Profiling). | Autonomous synthesis of domain-appropriate validation rules derived dynamically from the user's objective without manual rule writing. |
| **Mission-level orchestration** | **Potential Gap** | Workflow engines (Airflow, Temporal) execute static DAGs. | Adaptive, self-healing orchestration graphs that branch, retry, or switch fallback sources based on data quality feedback. |
| **Persistent source/schema knowledge** | **Requires Further Investigation** | Knowledge graphs, vector stores (RAG). | Cross-mission episodic memory that compiles successful extraction blueprints, endpoint reliability profiles, and schema equivalences. |
| **Self-improving collection strategies** | **Requires Further Investigation** | Reinforcement learning for web crawling; active learning in Tamr. | Agentic reinforcement learning from validation failures to refine crawler policies and selector heuristics over time. |
| **Domain-agnostic core architecture** | **Potential Gap** | Vertical scrapers (real estate, e-commerce, flights) hardcode domain assumptions. | A strictly domain-agnostic execution engine that loads specialized domain plugins (e.g. railway, healthcare, environmental) via clean interfaces. |

---

## 4. Why Prior Systems Fall Short

1. **The Hand-Crafted Pipeline Bottleneck**: Traditional data engineering assumes that sources are static and human engineers are available to build custom ingestion adapters. When facing dynamic, uncoordinated global sources, this model fails due to linear engineering cost.
2. **The LLM Hallucination & Scalability Trap**: Naive AI agent frameworks attempt to send raw tables directly into LLM prompts. This causes:
   - High token consumption and prohibitive cost.
   - Severe latency.
   - Hallucination of factual data and coordinates.
   - Non-deterministic, unrepeatable results.
3. **The Disconnect Between Extraction and Validation**: Existing web scrapers do not evaluate data quality during extraction, and existing quality frameworks (e.g., Great Expectations) do not direct the scraper when data fails assertions.

---

## 5. Preliminary Novelty Hypothesis

> **Novelty Hypothesis**: By separating the collection engine into an autonomous multi-agent planning and arbitration layer and a deterministic execution runtime, and connecting them via an evidence ledger (W3C PROV compliant), UDCM can achieve higher source coverage and schema harmonization accuracy than traditional static ETL pipelines, while avoiding the hallucination, latency, and cost penalties of naive LLM-only systems.

*Note: This hypothesis represents a research direction to be validated empirically through the benchmarks established in Phase 0.11.*
