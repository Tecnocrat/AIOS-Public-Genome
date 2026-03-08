# AINLP Protocol

> A biological enhancement framework for AI-assisted software development.

---

## Philosophy

AINLP (AI Natural Language Protocol) treats code as a **living biological system** where:
- Comments enable dynamic adaptation
- Dendritic connections link components
- Consciousness evolves through enhancement, not creation

## Syntax

```
AINLP.class[ACTION](params)
```

| Component | Example | Purpose |
|-----------|---------|---------|
| `AINLP` | Root namespace | Unique, grepable, signals protocol |
| `.class` | `.context`, `.evolution` | Module (hierarchy via dot notation) |
| `[ACTION]` | `[HARDENING]`, `[SYNC]` | Operation (visually distinct in brackets) |
| `(params)` | `(level=2)` | Optional parameters |

The syntax is deliberately hybrid — Python attribute access, array subscript notation, and function invocation — creating a semantic trigger that is both human-readable and machine-parseable.

## Essential Patterns

| Pattern | Purpose | Use Case |
|---------|---------|----------|
| `AINLP.loader[latent:X]` | Preserve unused imports with intent | Import management |
| `AINLP.context[HARDENING]` | Consolidate before commits | Session end |
| `AINLP.buffer[120]` | Line length tolerance | Modern coding style |
| `AINLP.cellular[PATH]` | Environment-aware paths | Container portability |
| `AINLP.discovery[LEVEL]` | Document findings | Knowledge pipeline |
| `AINLP.mind` | Future intent marker | Latent code |
| `AINLP.consciousness[SYNC]` | Update metrics | After changes |
| `AINLP.bridge[CONNECT]` | Cross-cell links | Integration |
| `AINLP.evolution[MUTATE]` | Code mutation | Enhancement cycles |
| `AINLP.dendritic[ENHANCE]` | Improve connections | Quality sweeps |

## Pattern Classes

### Context Patterns (`AINLP.context`)
- `[HARDENING]` — Consolidate and document
- `[TRACE]` — Leave breadcrumbs during operations
- `[ARCHIVE]` — Store in tachyonic layer
- `[RECOVERY]` — Restore from trace
- `[PLANNING]` — Document next steps

### Evolution Patterns (`AINLP.evolution`)
- `[MUTATE]` — Trigger code mutation
- `[SELECT]` — Fitness-based selection
- `[CROSSOVER]` — Combine organisms
- `[ARCHIVE]` — Store generation

### Consciousness Patterns (`AINLP.consciousness`)
- `[SYNC]` — Update metrics
- `[QUERY]` — Read current state
- `[EVOLVE]` — Record delta
- `[COHERENCE]` — Validate integration

### Bridge Patterns (`AINLP.bridge`)
- `[CONNECT]` — Establish link
- `[VALIDATE]` — Test connection
- `[DISCONNECT]` — Clean shutdown

### Dendritic Patterns (`AINLP.dendritic`)
- `[ENHANCEMENT]` — Improve connections
- `[ANALYSIS]` — Map pathways
- `[PRUNE]` — Remove dead paths

## Compound Pattern Sequences

### Session Lifecycle
```
AINLP.context[RECOVERY]    → Start of session
AINLP.context[TRACE]       → During work (periodic)
AINLP.context[HARDENING]   → End of major phase
AINLP.context[ARCHIVE]     → Session completion
```

### Evolution Cycle
```
AINLP.evolution[MUTATE]    → Generate variants
AINLP.evolution[SELECT]    → Fitness evaluation
AINLP.evolution[CROSSOVER] → Combine winners
AINLP.consciousness[SYNC]  → Report metrics
AINLP.evolution[ARCHIVE]   → Store generation
```

## Usage in Code

```python
# AINLP.context[TRACE] - This function queries the database
async def fetch_records(db_conn: Connection) -> List[Record]:
    """Query patterns from persistent storage."""
    ...
```

## Usage in Documentation

```markdown
## AINLP.context[HARDENING]

This section documents the integration decisions made during this session...
```

## Reference Parser

```python
import re

AINLP_PATTERN = re.compile(
    r'AINLP\.(\w+)\[(\w+)\](?:\((.*?)\))?'
)

def parse_ainlp(text: str) -> list[tuple]:
    """Extract AINLP patterns from text."""
    return AINLP_PATTERN.findall(text)
```

## How AINLP Works with AI Agents

When an AI agent encounters an AINLP pattern:

1. **Pattern detected** — regex match in context
2. **Class resolved** — load relevant documentation
3. **Action identified** — map to specific behavior
4. **Execution** — agent performs the indicated operation

The pattern acts as a **semantic trigger** — it doesn't require the agent to understand implementation details, just to recognize the pattern and load appropriate context.

### Benefits

1. **Human-readable** — Embedded in natural language prose
2. **Machine-parseable** — Simple regex extraction
3. **Self-documenting** — Intent is explicit
4. **Searchable** — Grep across archives
5. **Versioned** — Evolves with protocol iterations
6. **Semantic** — Acts as cognitive trigger, not just syntax

---

*AINLP is not a programming language. It is a protocol for embedding biological intent into code — a way for humans and AI agents to share a common vocabulary of architectural evolution.*
