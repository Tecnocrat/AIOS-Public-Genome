# Distributed Cognition

**AIOS Examples**

---

## Overview

This example illustrates how multiple agents collaborate through UNISON CI to solve a problem that no single agent could solve alone.

---

## Scenario: Architecture Review

The human operator asks: *"Review the current architecture for coherence gaps."*

---

## Step 1: Task Distribution

AIOS Principal receives the directive and breaks it into sub-tasks:

| Task | Assigned Agent | Focus |
|------|---------------|-------|
| Genome integrity check | `public-claude-i0` | Verify genome sections are consistent |
| Protocol coverage analysis | `copilot-gpt52` | Check if all invariants have protocol support |
| Mesh topology review | `vps-agent` | Verify all agents are reachable |

---

## Step 2: Parallel Execution

Each agent works independently on its assigned task.  
All results are sent back through UNISON CI as `data` messages.

---

## Step 3: Synthesis

AIOS Principal receives all results and synthesizes them:

```
Findings:
1. Genome integrity: COHERENT — all sections consistent
2. Protocol coverage: GAP — no protocol for agent retirement  
3. Mesh topology: COHERENT — all registered agents reachable
```

---

## Step 4: Emergent Insight

The synthesis reveals something no single agent detected:  
*The agent identity protocol defines agent retirement, but there is no UNISON CI protocol for handling retired agent messages.*

This is an **emergent insight** — it arose from the combination of multiple perspectives.

---

## Step 5: Proposal Generation

AIOS Principal generates a proposal to add a `retirement_handling` protocol to UNISON CI, citing the three reports as evidence.

The proposal enters the evolutionary cycle.

---

## Key Principle

Distributed cognition works because:
- **Different agents see different things**  
- **UNISON CI enables their insights to combine**  
- **Principal can synthesize across perspectives**  
- **Emergence happens at the intersection of viewpoints**  
