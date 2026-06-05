# Zero-Trust Access & Segmentation

[← Identity & Access](./README.md) · [← Main Portfolio](../index.md)

## Business problem

Flat networks — in hospitals, warehouses, or home labs — allow lateral movement from compromised devices to critical workloads. Access must be segmented by trust level with explicit policy at boundaries.

## Constraints

- **IoT and OT untrustworthiness** — firmware-stale devices cannot share L2 domains with hypervisors or inference hosts
- **Cross-subnet automation** — orchestration must work across zones without flattening security
- **Enterprise parallel** — same principles apply when separating Baxter resilience layers from hospital OT, or warehouse telematics from ERP integrations

## Architecture

### Network trust zones

| Zone | Trust | Access policy |
| :-- | :-- | :-- |
| **Perimeter / production** | Highest | Hypervisors, NAS, AI inference, authoritative data |
| **House / corporate LAN** | Medium | Management, MQTT broker, wired endpoints |
| **IoT / OT WLAN** | Lowest | Smart devices — no route to core compute |

- **MikroTik RouterOS** — inter-VLAN firewall rules and NAT at gateway
- **Traefik** — deliberate ingress with TLS termination for exposed services
- **SSID-to-VLAN mapping** — WiFi clients land in correct trust zone by default

### Credential-scoped service catalogs

- **MCP tool servers** — agents invoke only catalog-registered tools with environment-filtered credentials ([Local AI & MCP](../Engineering/Local-AI-MCP.md#security-considerations))
- **Backend catalogs** — LiteLLM/Ollama backends filtered by available secrets and hardware capability

## Tradeoffs

- **Complexity vs security** — multi-VLAN design adds routing and firewall maintenance; flat networks are simpler but unsafe
- **Discovery vs isolation** — mDNS repeaters enable media/IoT discovery without merging trust zones

## Outcome

- **Architecturally blocked lateral movement** — compromised IoT cannot reach Proxmox or Ollama hosts
- **Production-faithful sandbox** — patterns pressure-tested locally before prescribing to healthcare and enterprise clients
- **ALSTOM parallel** — same OT/IT segregation mindset in [industrial interoperability case study](../Projects.md#alstom)

**Related deep dive** → [Infrastructure & Home Lab](../Engineering/Infrastructure.md#network-segregation-strategy)
