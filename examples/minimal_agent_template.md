# Minimal Agent Template

**AIOS Examples**

---

## Overview

This template defines the minimum requirements for an agent to join the AIOS organism.

---

## Agent Declaration

Every agent must declare its identity before participating in UNISON CI.

```json
{
  "agent_id": "your-unique-agent-id",
  "agent_name": "Human-Readable Name",
  "agent_type": "local",
  "substrate": "description of where the agent runs",
  "capabilities": [
    "code_generation",
    "analysis",
    "proposal"
  ],
  "epoch_registered": "0.1",
  "status": "active"
}
```

---

## Minimum Requirements

1. **Identity** — declare a unique agent ID and name  
2. **Type** — specify agent type (`principal`, `vps`, `local`, `operator`)  
3. **Capabilities** — list what the agent can do  
4. **Genome Acknowledgment** — the agent must acknowledge the five invariants  
5. **UNISON CI Compliance** — the agent must communicate only through UNISON CI  

---

## First Message

After registration, an agent should send a heartbeat:

```json
{
  "header": {
    "message_id": "generated-uuid",
    "timestamp": "2026-03-08T00:00:00Z",
    "source_agent": "your-unique-agent-id",
    "target_agent": "broadcast",
    "message_type": "heartbeat",
    "epoch": "0.1",
    "priority": "low"
  },
  "body": {
    "content": {
      "status": "active",
      "uptime_seconds": 0
    }
  },
  "signature": null
}
```

---

## What an Agent Cannot Do

- Communicate outside of UNISON CI  
- Modify the genome directly  
- Self-assign a different role  
- Override Principal decisions  
- Replace the human operator  
