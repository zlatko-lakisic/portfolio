# Local AI & MCP Architecture

[← Back to Main Portfolio](../README.md)

## Overview

![MCP Architecture Blueprint — client, server, and data source request flow](../assets/mcp-architecture.png)

*Standard MCP request/response flow: the client translates AI requests into protocol format; servers fetch from external data sources and return structured context.*

This deep-dive covers self-hosted AI systems that extend enterprise integration thinking into edge inference: model-agnostic orchestration, multi-modal vision pipelines, and MCP tool servers that connect agents to real environments (Home Assistant, documentation, search, and custom catalogs).

Primary repositories:

- [agentic-orchestration](https://github.com/zlatko-lakisic/agentic-orchestration)
- [CodeProjectAI-OmegaOllamaMLLM](https://github.com/zlatko-lakisic/CodeProjectAI-OmegaOllamaMLLM)

---

## System Architecture

### Conceptual MCP flow

How context moves from data sources through MCP into local execution — the pattern this repository implements end to end.

```mermaid
graph TD
    A[Context / Data Sources] -->|Model Context Protocol| B(Agentic Orchestration Layer)
    B -->|Secure Local Payload| C[Ollama Inference Engine]
    C -->|Multi-Modal LLMs| D[Localized Execution Sandbox]
```

### Orchestration blueprint

Detailed component flow across planning, model routing, backends, and MCP tool servers.

```mermaid
flowchart LR
    subgraph Input
        UI[Web UI / YAML Goals]
        API[REST / WebSocket]
    end

    subgraph Orchestration
        Planner[LiteLLM Planner]
        Crew[CrewAI Agent Crew]
        Router[Model Router]
    end

    subgraph Backends
        Ollama[Ollama Local]
        Cloud[OpenAI / Anthropic / HF]
        TPU[vLLM / JetStream]
    end

    subgraph Tools
        MCP[MCP Tool Servers]
        HA[Home Assistant]
        Docs[Docs / Search]
    end

    UI --> API
    API --> Planner
    Planner --> Crew
    Crew --> Router
    Router --> Ollama
    Router --> Cloud
    Router --> TPU
    Crew --> MCP
    MCP --> HA
    MCP --> Docs
```

The orchestration layer separates **planning** (which model and which steps) from **execution** (agent roles and tool calls). MCP servers act as the integration boundary — the same pattern as REST API adapters in enterprise architecture, applied to agent tooling.

---

## Agentic Orchestration

**Repository:** [github.com/zlatko-lakisic/agentic-orchestration](https://github.com/zlatko-lakisic/agentic-orchestration)

### Architectural blueprint

- Natural-language goals and YAML workflows drive coordinated multi-agent crews.
- A LiteLLM-backed planner selects backends per task from a catalog filtered by credentials and hardware capability (CPU, GPU, TPU, VRAM heuristics).
- Optional MCP servers extend agents without hard-coding tool integrations.
- Vertical overlays under `examples/verticals/` add domain-specific orchestrator context without forking core engine code.

### Tech stack

| Layer | Components |
|---|---|
| **Orchestration** | CrewAI, YAML workflow definitions, dynamic planning modes |
| **Model routing** | Ollama, OpenAI-compatible APIs, Anthropic Claude, Hugging Face, vLLM, JetStream |
| **Tooling** | Model Context Protocol (MCP) catalog, Home Assistant, docs/search servers |
| **Interfaces** | CLI tool package, Web UI with local WebSockets, session and learning loops |

### Key outcomes

- **Vendor agnosticism** — Teams adopt on top of existing models, credentials, and MCP tools, then blend commercial APIs when faster or good enough.
- **Short path to POC** — Catalog-driven configuration via environment variables instead of bespoke planner and tool glue.
- **Production-shaped patterns** — Knowledge base, learning loop, VRAM-aware routing, and vertical overlays mirror how enterprise platforms ship domain packs.

### Design lessons

| Challenge | Approach |
|---|---|
| **Latency on local hardware** | Per-task backend selection with VRAM heuristics; prefer smaller models for planning steps |
| **Context window limits** | Session management and knowledge-base retrieval instead of stuffing full history into prompts |
| **Tool sprawl** | MCP catalog as integration hub — same role as an API gateway in distributed systems |
| **Proof-of-concept friction** | YAML + env-var catalogs so teams validate workflows before committing to custom code |

---

## Multi-Modal LLM Integration (CodeProject.AI)

**Repository:** [github.com/zlatko-lakisic/CodeProjectAI-OmegaOllamaMLLM](https://github.com/zlatko-lakisic/CodeProjectAI-OmegaOllamaMLLM)

### Architectural blueprint

Plugin for [CodeProject.AI Server](https://www.codeproject.com/ai/) that routes image and video analysis through **Ollama** vision models. Video is handled via frame sampling and summarization rather than sending full streams to the model.

### Tech stack

Ollama · CodeProject.AI module pipeline · Moondream (default vision model) · containerized execution

### Key outcomes

- Self-hosted multi-modal inferencing inside an existing edge-AI server boundary.
- Data stays local — aligned with privacy-sensitive workloads in enterprise and home-lab contexts.
- Composable with the broader home infrastructure stack documented in [Infrastructure & Home Lab](./Infrastructure.md).

---

## Relationship to Enterprise Work

| Enterprise pattern | Local AI equivalent |
|---|---|
| API gateway / integration bus | MCP catalog and model router |
| Credential-scoped service catalog | Backend catalog filtered by env credentials |
| HLSD and discovery artifacts | YAML workflows and vertical overlays |
| Feedback loop to product roadmap | Learning loop and session history in orchestrator |

The same architectural instincts — bounded integrations, catalog-driven adoption, outcome-first scoping — apply whether the deployment target is a Fortune 500 private network or a Proxmox cluster in a home lab.

---

[← Back to Main Portfolio](../README.md) · [Infrastructure & Home Lab](./Infrastructure.md)
