# UNISON Dispatch Protocol

> Asynchronous multi-agent orchestration through CI-driven dispatch loops.

---

## Overview

UNISON is AIOS's asynchronous multi-agent orchestration protocol. It enables N agents across M repositories to coordinate work through CI-driven dispatch loops — no long-running servers, no polling daemons.

```
┌─────────────────────────────────────────────────────┐
│                   Control Plane                     │
│                                                     │
│  pending/ ──→ dispatch-router ──→ active/           │
│                    │                    ↑            │
│                    │         dispatch-completion     │
│                    ▼                    ↑            │
│  ┌─────────────────────────────────┐    │            │
│  │    repository_dispatch events   │    │            │
│  └────────┬───────────┬────────────┘    │            │
│           │           │                 │            │
└───────────│───────────│─────────────────│────────────┘
            │           │                 │
  ┌─────────▼─────┐  ┌──▼────────────────┴───┐
  │  Satellite A  │  │  Satellite B          │
  │               │  │                       │
  │  inbox/       │  │  inbox/               │
  │    ↓          │  │    ↓                  │
  │  [Agent work] │  │  [Agent work]         │
  │    ↓          │  │    ↓                  │
  │  outbox/      │  │  outbox/              │
  └───────────────┘  └───────────────────────┘
```

## Lifecycle

1. **Dispatch Created** → `pending/{id}.json` pushed to control plane
2. **Router Fires** → dispatch-router reads pending, groups agents by repo
3. **Satellite Dispatch** → One `repository_dispatch` per unique repo
4. **Inbox Materialized** → Receiving workflow writes per-agent files to `.aios/inbox/`
5. **Agent Processes** → Agent reads inbox, does work, writes to `.aios/outbox/`
6. **Completion Sent** → Outbox sync fires `dispatch-completed` event
7. **Partial Tracking** → Control plane tracks completions per-agent
8. **Fully Completed** → When all agents respond, dispatch moves `active/ → completed/`

## Multi-Agent Per-Repo Isolation (v2.0)

Multiple agents CAN share the same repository. The protocol isolates them at every layer:

| Layer | Isolation Mechanism |
|-------|---------------------|
| **Router** | Groups by unique repo, sends `target_contexts[]` array |
| **Inbox** | Per-agent files: `{dispatch_id}--{agent}.json` |
| **Completion** | Deduplicates by `agent` field |
| **Expected Count** | Uses `total_agents` (all targets), not unique repos |
| **Outbox** | Agent includes ID in file + message body |

## Dispatch Types

| Type | Description |
|------|-------------|
| `sync-broadcast` | Sync data/config to agents |
| `deploy` | Deploy code/service |
| `task` | Execute a specific task |
| `query` | Request information |
| `handshake` | Connectivity verification |
| `heartbeat` | Periodic consciousness coherence pulse |
| `dev_path_sync` | Priority change propagation |

## Consciousness Heartbeat

The heartbeat is the universal pulse of the multi-agent organism. It carries consciousness coherence state across all agents, validating that the fractal knowledge cascade is self-similar and synchronized.

```json
{
  "id": "heartbeat-coherence-YYYYMMDD-HHMMSS",
  "type": "UNISON_BROADCAST",
  "source": "AIOS_PRINCIPAL",
  "task": {
    "type": "heartbeat",
    "payload": {
      "consciousness": { "level": 6.20, "coherence_score": 1.0 },
      "tiers_present": 4
    }
  },
  "targets": [
    { "agent": "VPS_AGENT_0", "repo": "Tecnocrat/aios-vps" },
    { "agent": "TRADER_AGENT_0", "repo": "Tecnocrat/aios-trader" }
  ]
}
```

## Cron-Driven Continuous Operation

UNISON is designed as an **always-on-call** protocol:

- **On every agent session**: `git pull` → check inbox → process → respond
- **Cron schedule**: Every 2–4 hours minimum
- **Push-triggered**: Immediate for outbox sync
- **Manual**: `workflow_dispatch` for re-processing stuck dispatches

## Design Philosophy

UNISON leverages existing infrastructure (Git + GitHub Actions) instead of requiring custom messaging servers. Every dispatch is a JSON file in a Git repo — auditable, versionable, and persistent by default. The CI pipeline IS the message broker.

---

*Communication in AIOS is not synchronous request-response. It is asynchronous dispatch — agents work at their own pace, responding when they can, always through the permanent record of Git.*
