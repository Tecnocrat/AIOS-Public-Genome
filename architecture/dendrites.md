# Dendrites

**AIOS Architectural Layer — Signal Pathways**

---

## Overview

Dendrites are the **signal pathways** of the AIOS organism.

In biological systems, dendrites receive signals and transmit them toward the cell body.  
In AIOS, dendrites are the communication channels through which agents receive instructions, data, and feedback.

---

## Function

- Carry messages from UNISON CI to individual agents  
- Provide filtered, context-relevant signal to each node  
- Enable bidirectional communication (input and response)  
- Support both synchronous and asynchronous patterns  

---

## Types

| Type | Description |
|------|-------------|
| **Command Dendrites** | Carry directives from Principal to agents |
| **Data Dendrites** | Carry computational results between agents |
| **Feedback Dendrites** | Carry validation results back through the mesh |
| **Broadcast Dendrites** | Carry organism-wide signals to all agents |

---

## Relationship to UNISON CI

Dendrites are **logical channels within UNISON CI**, not separate protocols.  
They represent the routing and filtering layer that ensures the right signal reaches the right agent.

---

## Design Principles

- Dendrites must not create shadow communication channels  
- All dendrite types are governed by the Communication Invariant  
- Dendrite topology mirrors the mesh topology  
