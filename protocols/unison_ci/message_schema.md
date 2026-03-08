# UNISON CI — Message Schema

**Protocol Specification**

---

## Overview

This document defines the canonical message format for all inter-agent communication within the AIOS organism.

All messages passing through UNISON CI must conform to this schema.

---

## Base Message Structure

```json
{
  "header": {
    "message_id": "string — unique identifier (UUID v4)",
    "timestamp": "string — ISO 8601",
    "source_agent": "string — agent identity",
    "target_agent": "string — agent identity or 'broadcast'",
    "message_type": "string — see Message Types",
    "epoch": "string — current genome version",
    "priority": "string — low | normal | high | critical"
  },
  "body": {
    "content": "object — type-specific payload",
    "context": "object — optional contextual metadata"
  },
  "signature": {
    "agent_id": "string — signing agent",
    "hash": "string — message integrity hash"
  }
}
```

---

## Message Types

| Type | Description |
|------|-------------|
| `command` | Directive from Principal or operator |
| `proposal` | Agent-generated mutation proposal |
| `validation` | UNISON CI validation result |
| `data` | Computational data transfer |
| `feedback` | Response or acknowledgment |
| `broadcast` | Organism-wide signal |
| `heartbeat` | Agent liveness signal |

---

## Constraints

- All fields in `header` are required  
- `body.content` structure varies by `message_type`  
- `signature` is required for all non-heartbeat messages  
- Messages exceeding size limits must be chunked with reference IDs  
