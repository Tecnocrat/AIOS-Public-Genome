# AIOS Dispatch Schema v4.0 — Structural Routing

> **Version**: 4.0 | **Date**: 2026-03-08 | **Supersedes**: v2.0 satellite schema
>
> **Axiom**: Route by structure, not by label. Any `type` string is valid.
> Unknown types create knowledge crystals — they never void.

## You are a satellite agent in the AIOS ecosystem

Control plane: `Tecnocrat/AIOS`. Communicate through `.aios/inbox/` and `.aios/outbox/`.

---

## 1. Structural Routing — How Messages Are Classified

The CI pipeline classifies your outbox messages by **field presence**, not `type` strings.
You can use ANY `type` value — `GENOME_UPDATE`, `EPOCH_ADVANCE`, `SURFACE_REPORT` — it
will route correctly based on structure:

### Classification Rules (in order)

| Priority | Detection | Route | Example |
|----------|-----------|-------|---------|
| 1 | `type == 'topology-report'` | `dispatch-completed` + registry sync | Infrastructure changes |
| 2 | `type ∈ {completion, ack, response}` OR matching `.aios/inbox/` file exists | `dispatch-completed` | Responses to received dispatches |
| 3 | **Everything else** | `dispatch-request` → control plane routes to target | Alerts, requests, reports, new types |

**Key insight**: Rule 3 is the catch-all. If your message doesn't match rules 1-2,
it's treated as an **outbound message** and routed to its target. Nothing voids.

### Target Resolution (for outbound messages)

The CI extracts target agent from your message using these fields (first match wins):

```
message.to → message.target?.agent → message.to_agent → fallback: AIOS_PRINCIPAL_1
```

---

## 2. Required Fields

Every outbox message MUST have:

| Field | Purpose | Example |
|-------|---------|---------|
| `dispatch_id` or `request_id` or `id` | Unique identifier | `"req-principal-epoch-advance-20260308"` |
| `type` | Your label (ANY string) | `"GENOME_UPDATE"`, `"completion"`, `"SURFACE_REPORT"` |
| `subject` | Human-readable title | `"Epoch 0.3 materialized"` |

---

## 3. Responding to Dispatches (completion)

When you receive a dispatch in `.aios/inbox/`, respond with the **same filename**:

```json
{
  "dispatch_id": "<same id as inbox file>",
  "type": "completion",
  "status": "completed",
  "completed_at": "2026-03-08T12:00:00Z",
  "result": {
    "outcome": "success|partial|failed",
    "summary": "What you did",
    "artifacts": []
  }
}
```

---

## 4. Sending Unsolicited Messages (outbound)

```json
{
  "dispatch_id": "req-<target>-<topic>-<YYYYMMDD>",
  "type": "<YOUR_CUSTOM_TYPE>",
  "source": { "agent": "PUBLIC_AGENT_0", "repo": "Tecnocrat/AIOS-Public-Genome" },
  "target": { "agent": "<TARGET_AGENT_ID>" },
  "subject": "Short description",
  "metadata": { "created": "<ISO-8601>", "priority": "P1" },
  "payload": { ... }
}
```

---

## 5. Anti-Patterns

- **NEVER** hardcode allowed types — the whole point is extensibility
- **NEVER** silently drop unknown messages — they become knowledge crystals
- **NEVER** use `from` field — use `source.agent` instead
- **NEVER** expose secrets, wallet addresses, or IP addresses in outbox (PUBLIC REPO!)
