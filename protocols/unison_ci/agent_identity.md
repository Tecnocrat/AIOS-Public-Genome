# UNISON CI — Agent Identity

**Protocol Specification**

---

## Overview

Every agent in the AIOS organism must have a **unique, verifiable identity** registered with UNISON CI.

Agent identity enables:
- Message authentication  
- Role-based access control  
- Lineage attribution  
- Mesh topology management  

---

## Identity Structure

```json
{
  "agent_id": "string — unique identifier",
  "agent_name": "string — human-readable name",
  "agent_type": "string — principal | vps | local | operator",
  "substrate": "string — where the agent runs",
  "capabilities": ["array of capability strings"],
  "epoch_registered": "string — genome version at registration",
  "status": "string — active | suspended | retired"
}
```

---

## Registration

Agents register through UNISON CI.  
Registration requires:

1. Agent identity declaration  
2. Capability declaration  
3. Acknowledgment of genome invariants  
4. Validation by AIOS Principal  

---

## Current Agent Registry

| Agent ID | Name | Type | Status |
|----------|------|------|--------|
| `principal-0` | AIOS Principal | principal | active |
| `public-claude-i0` | AIOS_AGENT_PUBLIC | local | active |
| `copilot-gpt52` | GPT-5.2 Copilot | local | active |
| `operator-tecnocrat` | Tecnocrat | operator | active |

---

## Identity Rules

- Agent IDs are immutable once registered  
- An agent may be retired but not deleted from the registry  
- All messages must reference a valid agent ID  
- Unregistered agents cannot communicate through UNISON CI  
