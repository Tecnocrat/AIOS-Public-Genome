# UNISON CI — Validation Rules

**Protocol Specification**

---

## Overview

Validation is the mechanism by which UNISON CI ensures that proposals, messages, and mutations conform to the organism's invariants before they are accepted.

---

## Validation Layers

### Layer 1: Schema Validation
- Message conforms to the defined message schema  
- All required fields are present  
- Data types are correct  

### Layer 2: Identity Validation
- Source agent is registered and recognized  
- Agent has authority to send the given message type  
- Signature hash is valid  

### Layer 3: Invariant Validation
- Message does not violate any of the five genome invariants  
- Proposals are checked against the current genome state  
- Mutations respect the evolutionary cycle  

### Layer 4: Coherence Validation
- Message is logically consistent with the organism's current state  
- No conflicting proposals are active  
- Lineage references are valid  

---

## Validation Results

| Result | Meaning |
|--------|---------|
| `accepted` | Message passes all layers |
| `rejected` | Message fails one or more layers |
| `deferred` | Message requires human operator review |
| `conflict` | Message conflicts with an existing proposal |

---

## Rejection Handling

Rejected messages are:
1. Logged with the reason for rejection  
2. Returned to the source agent with feedback  
3. Not propagated through the mesh  

Agents may revise and resubmit after addressing the rejection reason.
