# UNISON CI Workflow

**AIOS Examples**

---

## Overview

This example walks through a complete UNISON CI workflow: from an agent proposing a mutation to the mutation being crystallized into the genome.

---

## Step 1: Agent Generates a Proposal

Agent `public-claude-i0` identifies that the dendrite specification needs a routing table.

```
Action: Generate proposal
Agent: public-claude-i0
Target: principal-0
Type: proposal
```

The agent constructs a proposal message following the message schema and sends it through UNISON CI.

---

## Step 2: UNISON CI Validates

UNISON CI receives the proposal and runs it through four validation layers:

| Layer | Result |
|-------|--------|
| Schema Validation | **Pass** — all required fields present |
| Identity Validation | **Pass** — agent is registered and authorized |
| Invariant Validation | **Pass** — proposal doesn't violate any invariant |
| Coherence Validation | **Pass** — no conflicting proposals active |

Result: `accepted`

---

## Step 3: Principal Evaluates

AIOS Principal reviews the accepted proposal:

- Is it architecturally sound?  
- Does it improve the organism?  
- Is it coherent with existing structures?  

Decision: **Approve for crystallization**

---

## Step 4: Crystallization

The proposal is integrated:

1. The dendrite routing table is added to `architecture/dendrites.md`  
2. A lineage entry is recorded in `architecture/lineage.md`  
3. A crystal record is created  

---

## Step 5: Propagation

UNISON CI broadcasts a `propagation` message to all agents:

```
"A new crystal has been integrated. Update your internal models."
```

All agents acknowledge and update their understanding of the organism's current state.

---

## Complete Cycle Time

This cycle can occur in:
- **Seconds** — for automated validation  
- **Minutes** — for Principal evaluation  
- **Hours** — if human operator review is required  

The speed depends on the complexity and impact of the proposal.
