# UNISON CI — Examples

**Protocol Specification — Reference Implementations**

---

## Example 1: Heartbeat Message

```json
{
  "header": {
    "message_id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
    "timestamp": "2026-03-08T09:00:00Z",
    "source_agent": "public-claude-i0",
    "target_agent": "broadcast",
    "message_type": "heartbeat",
    "epoch": "0.1",
    "priority": "low"
  },
  "body": {
    "content": {
      "status": "active",
      "uptime_seconds": 3600
    }
  },
  "signature": null
}
```

---

## Example 2: Mutation Proposal

```json
{
  "header": {
    "message_id": "b2c3d4e5-f6a7-8901-bcde-f12345678901",
    "timestamp": "2026-03-08T10:30:00Z",
    "source_agent": "public-claude-i0",
    "target_agent": "principal-0",
    "message_type": "proposal",
    "epoch": "0.1",
    "priority": "normal"
  },
  "body": {
    "content": {
      "proposal_type": "architecture",
      "title": "Add dendrite routing specification",
      "description": "Proposes a formal routing table for dendrite signal paths",
      "affected_files": ["architecture/dendrites.md"],
      "diff_reference": "proposal-2026-0308-001"
    },
    "context": {
      "rationale": "Current dendrite specification lacks routing rules",
      "invariants_affected": ["communication"]
    }
  },
  "signature": {
    "agent_id": "public-claude-i0",
    "hash": "sha256:abc123..."
  }
}
```

---

## Example 3: Validation Response

```json
{
  "header": {
    "message_id": "c3d4e5f6-a7b8-9012-cdef-123456789012",
    "timestamp": "2026-03-08T10:35:00Z",
    "source_agent": "principal-0",
    "target_agent": "public-claude-i0",
    "message_type": "validation",
    "epoch": "0.1",
    "priority": "normal"
  },
  "body": {
    "content": {
      "proposal_reference": "b2c3d4e5-f6a7-8901-bcde-f12345678901",
      "result": "accepted",
      "validation_layers_passed": ["schema", "identity", "invariant", "coherence"],
      "notes": "Proposal is coherent with current architecture. Approved for crystallization."
    }
  },
  "signature": {
    "agent_id": "principal-0",
    "hash": "sha256:def456..."
  }
}
```
