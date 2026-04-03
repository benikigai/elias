# elias

the coordinating layer of a fleet of autonomous AI agents, running 24/7 on a home compute cluster.

specialized agents, each owning one domain. local inference where it makes sense, frontier models where it matters. persistent memory. self-healing infrastructure.

this isn't a chatbot. it's an operating system for my life and businesses.

---

## what the fleet does

the fleet triages incoming messages across WhatsApp, SMS, Telegram, Discord, and LINE, manages a short-term rental portfolio, monitors infrastructure, tracks finances, runs research, and writes code autonomously overnight.

the system processes thousands of messages per week, manages guest communications across the portfolio, and coordinates a team of human assistants.

---

## agent fleet

every agent owns one domain. nothing overlaps. ben is the only approver for money, sends, and publishes.

| agent | role |
|-------|------|
| **elias** | chief of staff: business and orchestration |
| **sunny** | personal life COO: calendar, travel, purchases, admin, bills |
| **jarvis** | deliberation and second opinions; lead on guest messaging |
| **ren** | rental portfolio operations |
| **puck** | Injester business operations |
| **jester** | company assistant: team calendars and workspace |
| **ellie** | always-on research and local model testing |
| **kai** | team management via Slack: standups, digests, escalations |
| **gerty** | calendar specialist |
| **instinct** | SMS and WhatsApp agent |

critical paths run on infrastructure separate from the home cluster, so guest comms and team management survive home outages.

### coding fleet

a separate workshop of coding agents, one lane each, reassessed as models ship:

- **Claude Code** — planning and complex builds
- **Codex** — iteration, tests, CI
- **Antigravity** — quick tasks, deep research, large-context reads
- **Grok Build** — X-native search, second opinions, parallel fan-out
- **Muse Code** — cheap bulk sweeps
- **Cursor** — interactive IDE and model router

---

## model cascade

every request falls through a model cascade. fast and free first, expensive last. local models handle routine work; frontier APIs are the safety net, not the default.

subagents use a separate cascade starting with local models to keep costs near zero for routine tasks.

---

## triage routing

incoming messages are classified and routed to the right speed tier: instant replies for greetings and status, deeper models for analysis and drafting, multi-model councils for strategic decisions.

---

## channel architecture

```
WhatsApp  ──→  relay  ──→  gateway  ──→  fleet
SMS       ──→  relay  ──→  sms agent
LINE      ──→  relay  ──→  line-translate
Telegram  ──→  direct API   ──→  fleet
Discord   ──→  direct API   ──→  fleet (ops dashboard)
Voice     ──→  relay  ──→  STT → LLM → TTS
```

Discord serves as the ops dashboard: personal, guests, finance, research, development, business, briefings, and approvals.

---

## compute cluster

local inference and fine-tuning run on a home cluster of Apple Silicon and NVIDIA GPU machines, wired on a local network. high-memory nodes pool enough unified memory to run models in the hundreds of billions of parameters locally; the rest of the fleet handles agent runtime, fast local models, GPU fine-tuning, and a decision service: one API over a set of small local models that returns structured scores and probabilities for agent routing decisions.

---

## memory and knowledge

### 3-layer memory

1. **index** read every session. structural overview of the entire system.
2. **topics** read on-demand. deep references on infrastructure, channels, agents, security, guests, projects.
3. **changelog** append-only audit trail. never read by agents, exists for forensics.

### ontology

YAML schemas define a structured knowledge graph: guests, reservations, properties, reviews, competitors, market intel, calendar events, conversations, pricing data, cleaning schedules, and more.

dual search: vector (semantic) + embedded database (backup), both maintained on a schedule.

---

## operating principles

- **one draft per thread.** agents revise in place, never stack competing drafts.
- **one owner per lane.** every domain has exactly one agent accountable for it.
- **approval is explicit.** no agent spends, sends, publishes, or deletes without the owner's tap.
- **critical paths are separate.** anything that can't go down runs on infrastructure independent of the home cluster.
- **config lockdown.** core configs are locked and watched; a watchdog re-locks and auto-repairs known patches.

---

## what i learned building this

1. **specialization beats generalization.** one agent per domain with clear boundaries works better than one agent trying to do everything.

2. **local inference changes the economics.** running mid-size models locally means most routine tasks cost nothing. the API cascade is a safety net, not the default.

3. **separate infrastructure for critical paths.** anything that can't go down runs on infrastructure separate from the home cluster.

4. **memory needs structure.** free-form context windows aren't memory. a layered system with schemas, indexes, and changelogs gives agents real continuity across sessions.

5. **self-healing saves sleep.** the fleet auto-repairs most infrastructure issues. a human gets paged only when automatic fixes fail.

6. **model cascades are essential.** no single model is reliable enough for 24/7 operation. a fallback chain means the system stays up even when APIs go down.

---

## built with

[OpenClaw](https://github.com/openclaw/openclaw) · Muse · TypeScript · Python · Next.js · FastAPI · PostgreSQL · Qdrant · Playwright · Tailscale · Docker · Cloudflare · Obsidian · Apple Silicon · NVIDIA

---

## about me

i'm ben. i spent a decade shipping consumer hardware from prototype to mass production at Apple and Meta. now i'm a founder building agentic infrastructure and AI systems that operate in the physical world. more at [github.com/benikigai](https://github.com/benikigai).
