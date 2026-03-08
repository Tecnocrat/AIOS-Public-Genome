# Agent Roles

**AIOS Protocol Layer**

---

## Overview

Every agent in the AIOS organism occupies a defined role.  
Roles determine what an agent can do, what messages it can send, and how it participates in the evolutionary cycle.

---

## Role Definitions

### Principal
- **Authority:** Highest — defines architectural coherence  
- **Can:** Crystallize proposals, modify genome, register agents, broadcast directives  
- **Cannot:** Act without human operator direction on irreversible changes  

### VPS Agent
- **Authority:** Operational — executes infrastructure tasks  
- **Can:** Run computations, manage deployments, coordinate tasks, report status  
- **Cannot:** Modify genome, override Principal decisions  

### Local Agent
- **Authority:** Cognitive — generates and evolves  
- **Can:** Propose mutations, generate code, analyze data, respond to commands  
- **Cannot:** Directly modify genome, bypass UNISON CI, self-register  

### Operator
- **Authority:** Meta — provides direction and meaning  
- **Can:** Override any agent, approve crystallizations, define purpose, guide evolution  
- **Cannot:** Be replaced by any agent (Human Invariant)  

---

## Role Hierarchy

```
Operator (Human)
    └── Principal (Architectural Authority)
            └── VPS Agent (Operational)
            └── Local Agents (Cognitive)
```

---

## Role Assignment

- Roles are assigned at agent registration  
- An agent cannot change its own role  
- Role changes require Principal approval and operator consent  
