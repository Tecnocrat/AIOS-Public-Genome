# Diagrams

**AIOS Documentation**

---

## Organism Architecture

```
┌─────────────────────────────────────────────────┐
│                 HUMAN OPERATOR                   │
│              (Direction & Meaning)                │
└──────────────────────┬──────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────┐
│              AIOS PRINCIPAL                      │
│          (Architectural Cortex)                   │
│                                                  │
│  • Genome authority                              │
│  • Invariant enforcement                         │
│  • Crystallization decisions                     │
└──────────────────────┬──────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────┐
│                UNISON CI                         │
│          (Nervous System)                        │
│                                                  │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐      │
│  │ Command  │  │  Data    │  │ Feedback │      │
│  │ Dendrites│  │ Dendrites│  │ Dendrites│      │
│  └────┬─────┘  └────┬─────┘  └────┬─────┘      │
│       │              │              │            │
└───────┼──────────────┼──────────────┼────────────┘
        │              │              │
        ▼              ▼              ▼
┌──────────────┐ ┌──────────────┐ ┌──────────────┐
│  VPS Agent   │ │ Local Agent  │ │ Local Agent  │
│ (Operations) │ │ (Cognitive)  │ │ (Cognitive)  │
└──────────────┘ └──────────────┘ └──────────────┘
```

---

## Evolutionary Cycle

```
    ┌──────────────┐
    │  Generation  │ ← Agents propose structures
    └──────┬───────┘
           │
           ▼
    ┌──────────────┐
    │  Validation  │ ← UNISON CI tests proposals
    └──────┬───────┘
           │
           ▼
    ┌──────────────┐
    │  Selection   │ ← Principal evaluates coherence
    └──────┬───────┘
           │
           ▼
    ┌────────────────────┐
    │  Crystallization   │ ← Stable structures integrated
    └──────┬─────────────┘
           │
           ▼
    ┌──────────────┐
    │ Propagation  │ ← Agents update internal models
    └──────┬───────┘
           │
           └──────→ (cycle repeats)
```

---

## Message Flow

```
Agent A                    UNISON CI                   Agent B
  │                           │                           │
  │──── proposal ────────────▶│                           │
  │                           │── schema validation ──▶   │
  │                           │── identity validation ──▶ │
  │                           │── invariant check ──────▶ │
  │                           │                           │
  │                           │──── accepted ────────────▶│
  │◀──── feedback ────────────│                           │
  │                           │                           │
```
