# Projects

[← Back to Main Portfolio](./README.md)

Project highlights from [LinkedIn](https://www.linkedin.com/in/zlatko-lakisic/details/projects/), expanded with portfolio context and repository links where available.

---

## Omega CMS

**Jan 2017 – Present** · [omegacms.io](https://omegacms.io) · [GitHub](https://github.com/zlatko-lakisic/omegacms)

OmegaCMS is a new type of content management system that redefines what it means to help companies and individuals organize and manage their content. It reads and integrates data from multiple systems, runs on existing infrastructure or as a serverless service, and helps users make use of their content with very little overhead.

### Architectural highlights

- **Database-agnostic data layer** — SQL Server, MySQL, Oracle, document stores, and flat-file sources through pluggable data access.
- **Decoupled / headless delivery** — Management UI plus APIs and client libraries (C#, JavaScript, TypeScript) for web, mobile, and internal tools.
- **Serverless deployment** — AWS Lambda, Azure Functions, and Google Cloud targets for bursty or globally distributed workloads.
- **Content-first modeling** — Visual content designer drives generated structures rather than page-builder lock-in.

### Role

Co-Founder and Solutions Architect at [Omega Content Management Services](https://www.linkedin.com/company/omega-cms). Led customer blueprinting, architecture documentation, .NET Core services, federated data integration, and AWS migration playbooks for enterprise clients.

**Deep dive** → [OmegaCMS on GitHub](https://github.com/zlatko-lakisic/omegacms) · [Technical Strategy & Career](./Technical-Strategy.md#founder--omega-it-llc-new-york-ny)

---

## Walmart Inventory Automation

**Genpact · Walmart & Sam's Club · 11/2018 – 11/2019**

![Walmart Inventory Automation — enterprise integration mesh unifying 50+ legacy and modern systems across global supply chain operations](./assets/walmart-project.png)

Architectural strategy, re-engineering, and automation of a highly fragmented global supply chain and inventory accounting ecosystem. At enterprise scale, the initiative unified 50+ disparate legacy and modern systems into a resilient dual-mode integration bridge — replacing a brittle manual workflow built on multi-layered spreadsheet networks with a right-first-time data pipeline that secured financial fidelity for metrics directly tied to corporate P&L.

### The challenge

The baseline infrastructure was extreme technical debt in a fully siloed operating model:

- **Systemic scale** — 50+ disconnected platforms, from SAP and Salesforce to mainframe green-screen terminals, independent file shares, and legacy email data streams.
- **Geospatial gaps** — No unified mapping; logistics teams relied on static paper atlases instead of centralized GIS.
- **Spreadsheet dependency** — Frontline staff tracked inventory through a fragile Excel matrix fed by 50 individual data-dump sheets into an unstable master VLOOKUP system.
- **P&L exposure** — Inventory metrics feed corporate profit-and-loss statements; teams reran identical calculation cycles three to four times per period to manually verify integrity.

### Architectural highlights

#### 1. Dual-mode integration bridge

Orchestration layer supporting synchronous and asynchronous processing so low-performance legacy systems could not drag down modern cloud applications:

- **Synchronous streams** — Low-latency API transactions for interactive endpoints (SAP, Salesforce).
- **Asynchronous pipelines** — Stateful, queue-driven workers for bulk FTP drops, file-share exchanges, and structured email payloads without blocking upstream workflows.
- **Legacy mainframe adapters** — Custom programmatic wrappers and terminal emulators to extract and integrate siloed green-screen data layers.

#### 2. Operational discovery and workflow optimization

Before automation code shipped, ground-level technical discovery mapped undocumented manual processes and systematic failure points. Edge-case exceptions were diagnosed and proactive error-reconciliation algorithms were built into the software layer — optimizing the operational flow before automation took over.

#### 3. Cognitive document-matching mesh (3-stage HITL ML pipeline)

Physical Bills of Lading from truck drivers often arrived months — or up to a year — before corresponding vendor invoices. A Human-in-the-Loop machine learning system reconciled that temporal friction:

- **Stage 1 — Imitation learning** — Models ingested historical processing patterns to capture implicit matching heuristics used by human operators.
- **Stage 2 — Assisted inference** — Interactive suggestion layer with live operator feedback loops to continuously tune model confidence scores.
- **Stage 3 — Autonomous execution** — Full autonomy with human operators out of the active loop except for randomized QA and statistical sanity checks.

### Business outcomes

- **Spreadsheet eradication** — Eliminated the manual 50-tab Excel ecosystem and its performance lags and corruption vectors.
- **Right-first-time fidelity** — Automated validation delivered reliable metrics on the first run, removing 3×–4× operational rework cycles.
- **Supply chain visibility** — Transformed batch-oriented tracking into a continuous, event-driven data stream across 5,500 retail locations.
- **P&L integrity** — Executive leadership gained high-fidelity, near-real-time inventory assets tied to financial reporting.

### Tech stack

Event-driven architecture · synchronous/asynchronous microservices · enterprise application integration (EAI) · SAP · Salesforce API · custom mainframe terminal emulators · FTP/SFTP · applied ML · HITL pipelines · operator feedback loops · .NET · SQL Server · Sequence platform

### Role

Principal Consultant — Lead architect and delivery director. Led a team of 15 through discovery, HLSD, and deployment. Directed backend discovery architecture for the inventory automation initiative across Walmart and Sam's Club.

**Related experience** → [Technical Strategy & Career — Genpact](./Technical-Strategy.md#principal-consultant--genpact-new-york-ny)

---

## ALSTOM — Global Enterprise Web Platform

**Green River Media** · Ektron CMS · ASP.NET WebForms

An enterprise website developed on the Ektron CMS platform with an ASP.NET WebForms front end. The solution is distributed not only by environment but geographically — hosted across North America, South America, Europe, and Asia.

### Architectural highlights

- **Multi-region content delivery** — Global enterprise presence with continent-level deployment topology.
- **Ektron CMS foundation** — Content governance, versioning, and template structures on the .NET stack.
- **High-availability digital performance** — Part of a broader portfolio of Ektron implementations including Eurotunnel and Emco Wheaton (Gardner Denver).

### Role

Lead Developer and later Product Director at Green River Media. Designed and implemented web application architecture, on-site client delivery, and server infrastructure for global manufacturing and infrastructure clients.

**Related experience** → [Technical Strategy & Career — Green River Media](./Technical-Strategy.md#product-director--green-river-media-london-uk)

---

## Video Promotions (ViewBooster)

**Zoomin.TV** · YouTube Multi-Channel Network

A system designed to run concurrent advertising campaigns across the YouTube platform. Zoomin.TV deployed it across 60,000+ channels. In minutes, a campaign can be created and placed on each video of each selected channel.

### Architectural highlights

- **High-velocity campaign engine** — Angular and Material UI communicating with Web API services; campaigns propagated across massive channel fleets in minutes.
- **ML-driven channel matching** — Back-end Windows service matches channels to advertising campaigns and monitors click-through performance in real time.
- **Massive data orchestration** — Daily ingestion and analysis of Google API statistics across millions of channels; proprietary promotion logic for ~100,000 managed channels.
- **Revenue impact** — Contributed to new revenue streams with multi-million-dollar business impact while Zoomin was among the largest YouTube MCNs globally.

### Tech stack

C# .NET · Google APIs · AngularJS / Angular Material · Web API · ColdFusion (merchandising interfaces) · AWS · automated campaign optimization

### Role

Director, Solutions Architecture and Head of Development. Led a global team of 27; defined platform strategy for creator monetization and merchandising revenue streams.

**Related experience** → [Technical Strategy & Career — ZoominTV](./Technical-Strategy.md#director-solutions-architecture--zoomintv-amsterdam-netherlands)

---

## Related Open-Source & Lab Projects

These active GitHub repositories extend the project work above into local AI, agent orchestration, and hands-on infrastructure — not listed separately on LinkedIn but part of the same engineering narrative.

| Project | Repository |
|---|---|
| Agentic Orchestration | [agentic-orchestration](https://github.com/zlatko-lakisic/agentic-orchestration) |
| Ollama MultiModal LLM (CodeProject.AI) | [CodeProjectAI-OmegaOllamaMLLM](https://github.com/zlatko-lakisic/CodeProjectAI-OmegaOllamaMLLM) |
| My Futuristic Home (home lab) | [My-Futuristic-Home](https://github.com/zlatko-lakisic/My-Futuristic-Home) |

---

[← Back to Main Portfolio](./README.md)
