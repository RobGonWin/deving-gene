![Status: WIP](https://img.shields.io/badge/status-WIP-orange)
![License: Apache-2.0](https://img.shields.io/badge/license-Apache%202.0-blue)
![Platform: Windows 10/11](https://img.shields.io/badge/platform-Windows%2010%2F11-lightgrey)

# Deving Gene (WIP — OSS 2026)

Deving Gene is a focus, automation, and AI-assisted workflow system designed with neurodivergent awareness and giftedness protocols (to support twice-exceptionality, spiky cognitive profiles, and executive-function) along with other planned features for real-time scaffolding. Combining an **Alexa Skill** (communicates through a LAN-based protocol with proper URL tunneling and security measures in place), **PC Client (Python/FastAPI)**, **PC dashboards**, **PC assistant UI**, **VS Code extension**, and evolving adaptive workflow layers (more secrets to be explored soon!) to help users preserve flow state, reduce context loss, and build with more consistency.

At its core, Deving Gene is about creating a system that can work **with** your brain instead of against it using automation, roadmap systems, voice integration, local-first AI, and workflow feedback loops - essentially
optimizing your flow state and providing a more **frictionless** experience using AI, without sacrificing your critical thinking skills. This effectively encourages a "synchronization" with artificial intelligence, powered by personalized context, learning language models, and more--all while being **local-first, consent-first, auditable, with multiple trust profiles.** out of the box. This allows for a secure **Individualized Education Plan** (with different security profiles on what you allow to be shared with Amazon+Alexa to reduce security concerns) all while turning your Alexa smart device into something that can be used consistently to monitor, regulate, learn, and do development with for everyday work.

It is especially aimed at developers and learners who may be:

- highly capable but inconsistent in output
- strong in reasoning but weaker in working-memory continuity
- prone to context loss during task switching
- bored or under-stimulated by generic productivity systems
- looking for a more adaptive, privacy-aware "external frontal lobe" like workflow


> 📌 This is a planning/documentation repo, which mirrors my experimental private repo (which contains actual code). **Source code will be open-sourced sometime in 2026.** Until then, this page hosts images, roadmap, and architecture notes.

## What Deving Gene is trying to solve

Traditional productivity systems assume everyone works well with the same structure.

Deving Gene does not.

This project is built around the idea that some people need:

- external memory scaffolding
- flow-state protection
- adaptive prompts and pacing
- gentle or aggressive interruption management
- context-aware roadmap realignment
- voice-assisted check-ins
- privacy-respecting local-first AI support
- workflow systems that account for cognitive peaks, dips, and uneven profiles

Rather than replacing thinking, Deving Gene is intended to help users hold onto their thinking long enough to execute on it.

---
## Repository status

### What’s here today

**General Stuff**

- License ✔️
- Planning docs, architecture notes, and implementation plans ✔️
- Trello REST API Integration (reading card progress throughout the day outloud via Alexa Skill) ✔️
- Schedule block chunking, idle alerts, site blocking (via NextDNS API), schedule syncing (PC->Alexa, Alexa Intents for schedule realignment to allow Alexa to jump blocks) ✔️
- Conversation hygiene storage under `convos/` ✔️
- Local-first config and integration scaffolding ✔️

**Apps In Development / Partially Working**

Deving Gene currently spans multiple subprojects in a monorepo-style setup:

- **`apps/pc-client`** - local orchestration layer, FastAPI micro-APIs, schedule sync, conversation hygiene, Alexa bridge, LLM routing, focus/fallback tooling, and EVC voice features
- **`apps/pc-assistant`** - Tauri + Next.js desktop assistant for chat, hygiene metrics, pending ops, project switching, and Alexa hand-off
- **`apps/pc-dashboards`** - Tauri + Next.js dashboards for convos, insights, projects, learning, sessions, alerts, and offline filesystem fallback
- **`apps/alexa-skill`** - Alexa intents, routines, session handling, SSML-safe readouts, and PC communication glue
- **`apps/vscode-extension`** - VS Code sidebar/webview for Deving Gene insights and editor-connected workflows

Supporting repo areas include:

- **`configs/`** - shared JSON config map and docs
- **`convos/`** - canonical conversation/session store
- **`docs/`** - API reference, configuration guide, PRD, and integration plans
- **`packages/shared/`** - shared workspace code

**What’s not here yet**
- Public Source code, release packages (scheduled OSS: 2026, around Q3-Q4 2026) ⏳

### What is still in progress

- config cleanup and onboarding polish
- broader desktop/UI packaging
- adaptive profile expansion (more telemetry layers)
- richer AI workflow and telemetry layers
- tighter cross-app integration ergonomics

---
## TL;DR value
### Adaptive workflow support

Deving Gene is being designed to help users shape their workflow around how they actually think, instead of forcing them into rigid generic systems.

### Roadmap-driven focus

Supports roadmap chunking across monthly, weekly, and day-level planning, with schedule realignment tools that help users recover from drift without losing the whole day.

### Local PC orchestration

The PC Client serves as the local control point for scheduling, sync, automation behaviors, focus enforcement, LLM routing, and conversation hygiene.

### Executive-function scaffolding

The system is designed to reduce the "what am I supposed to be doing right now?" tax through structured external memory, roadmap systems, check-ins, and workflow glue.

### Local-first and least-privilege design

Deving Gene is built around the belief that helpful systems should not need unlimited access to be useful.


---
## Current Features Implemented behavior

### Alexa specific behavior

Admittedly, part of the charm of using this workflow is the Alexa specific behavior (which is deterministic and least-privilege based on project & user settings, preventing certain data from being shared)
- **Mindfulness Breaks**: 
    Allows proper breaks to preserve proper energy for coding sessions/prevent burnout
- **Webhook Routines**: 
    Allows Webhook Routine Triggers to be configured in a similar manner as Virtual Smart Home [WebhookRoutineTrigger](https://www.amazon.com/Virtual-Smart-Home-Routine-Trigger/dp/B08SHHS8JZ/)) for proper Alexa communication

- **Schedule Sync / Alignment State**

    The PC Client and Alexa Skill already exchange schedule and session data. The current backend supports routes such as:

    - `/alexa/schedule`
    - `/alexa/roadmap`
    - `/alexa/status`
    - `/receive-session-data`

    This means Alexa can stay aware of roadmap state while the PC layer can fall back to local schedule data when Alexa session data is unavailable.

    > Side Note: Triggering Alexa BlockIntents (i.e, JumpForwardBlockIntent with trigger "Alexa, jump to the next block") -> also realigns the schedule on PC. This allows for more hands free realignment, mitigating rumination and feeling of shame loops when missing deadlines.

### PC Client Integration
**Current Configuration (as of March 31st, 2026)**

The current PC Client is the main local coordination layer. It already exposes FastAPI endpoints for:

- Alexa schedule and status sync
- conversation turns and summaries
- pending ops and apply/reject flows
- MCP tool listing/execution
- learning summaries
- EVC microphone and streaming support (for metacognitive strategies + data)
- periodic snapshotting (takes snapshots of whats going on, gets summaries compiled by )

It also maintains local fallback behavior when Alexa session state is unavailable, which keeps roadmap/schedule-related workflows usable from the PC side.

### LLM routing and local-first safeguards

The current backend already contains:

- local and cloud adapter plumbing
- Ollama-first local routing support
- per-turn model/provider/origin metadata handling
- Corporate Mode alignment in project docs and config direction (specific project files handling MCP, code sharing, etc behavior- with proper PII redaction models integrated for good measure)
- SSML-safe local readout flow for Alexa (depending on user settings. SSML readout can be used for regulation and personalized "training" scripts, as well as other updates)

### Expanded Verbal Comprehension & additional voice features

The `pc-client` includes implemented `Expanded Verbal Comprehension` groundwork (real-time analysis of what you are saying outloud) including:

- realtime STT routes and runtime management
- microphone enumeration/config support
- transcript post-processing (with contextual awareness)
- todo card extraction/validation (able to generate based on thoughts reasoned outloud)
- prosody capture, enrichment, snapshots, and session baselines (for memory, and helping "Deving Gene" learn how you react to cues, your behavior while developing, etc)
- voice log append/readback support


### Focus and interruption tooling

The current PC-side (`pc-client`, `pc-assistant`) codebase includes focus-oriented infrastructure for:

- idle monitoring (pc-client) - doesn't constantly nag you; has situational awareness to distinguish micro-breaks / dopamine "bursts" of media/thought engagement
- app switching awareness (for locally logging how certain apps help reset dopamine)
- session logging (pc-client)
- schedule/block behavior handling (task chunking and "mode" switching-allowing for different blocks to help with daily executive function tasks)
- media/site blocking integrations (via NextDNS, currently experimental-planned MCP control later)
- tray/runtime helpers and local client control

### Desktop assistant and dashboards

The desktop surfaces are no longer just planned. Current apps include:

- **PC Assistant** with chat UI, project switching, pending ops, hygiene cards, error toasts, and "Read via Alexa"
- **PC Dashboards** with longitudinal convos, insights, learning, sessions, alerts, projects, and offline filesystem fallback (allows for macro-pattern analysis of how you develop & work throughout your day)
- **VS Code extension** with a sidebar webview and prebuilt webview UI pipeline


## Screenshots
![Alexa Skill Simulator](https://www.notion.so/image/attachment%3A2a49635b-ed69-4324-9e98-07f4a5efeb34%3Aimage.png?table=block&id=2a34773f-9ff0-8034-b8ae-f336eea49c3b&spaceId=efeada7c-1a0f-4675-b93f-0a166276a715&width=810&userId=&cache=v2 "Alexa Skill Schedule Greeting")

![PC Client](https://www.notion.so/image/attachment%3A0bed283d-41af-4349-827c-5a3856f83a7f%3Aimage.png?table=block&id=2a34773f-9ff0-80cc-b881-e93f7c471ebd&spaceId=efeada7c-1a0f-4675-b93f-0a166276a715&width=1420&userId=&cache=v2 "PC Client (WIP) — dev log")

![Alexa Trello Audit](https://www.notion.so/image/attachment%3A517703c3-5388-472c-b5a8-49ab639ec027%3Aimage.png?table=block&id=2a34773f-9ff0-809e-8be2-e77aa28482cd&spaceId=efeada7c-1a0f-4675-b93f-0a166276a715&width=730&userId=&cache=v2 "Alexa Skill Trello audit summary (WIP)")

![RTFocuser Extension Preview](https://www.notion.so/image/attachment%3A84839b78-e2b5-4f40-84b7-b6ef24e45426%3Afc7c1c5b-967d-41a6-a44d-c0fc87b95460.png?table=block&id=2a34773f-9ff0-80a0-8b9c-cde77de501fa&spaceId=efeada7c-1a0f-4675-b93f-0a166276a715&width=1420&userId=&cache=v2 "VS Code panel RTFocuser Extension Preview, fires mindfulness alert if script progress isnt made")

![Alexa Routine Image](https://www.notion.so/image/attachment%3Abed27bbd-465b-401e-b744-be1ca8ca3ba3%3Aimage.png?table=block&id=2a34773f-9ff0-80b3-a326-daa4b9623110&spaceId=efeada7c-1a0f-4675-b93f-0a166276a715&width=1420&userId=&cache=v2 "Alexa Routine App Preview")

![Studio focus/idle indicator (RTFocuser add-on)](https://www.notion.so/image/attachment%3A7dfc1f7f-751c-4ea4-aa98-ef167748ab72%3Aimage.png?table=block&id=2a34773f-9ff0-8085-a131-f18dd6c9555e&spaceId=efeada7c-1a0f-4675-b93f-0a166276a715&width=1420&userId=&cache=v2 "Studio focus/idle indicator (RTFocuser add-on)")

![PC Assistant App (Preview)](https://file.notion.so/f/f/efeada7c-1a0f-4675-b93f-0a166276a715/935d7ab8-5cc6-4862-ba51-6ed57979511e/image.png?table=block&id=3364773f-9ff0-80c4-b492-ec349fd13604&spaceId=efeada7c-1a0f-4675-b93f-0a166276a715&expirationTimestamp=1775311200000&signature=xG-HJgKsPqGQRSgJybFuBjYRfuORlUUE5U3fIzHAn7o&downloadName=image.png "PC Assistant App (Preview)")

![PC Dashboards (Preview)](https://file.notion.so/f/f/efeada7c-1a0f-4675-b93f-0a166276a715/46d81f63-ead3-4a8e-b9ad-18fc7286db7f/image.png?table=block&id=3364773f-9ff0-80a9-aa6e-d0acea15390a&spaceId=efeada7c-1a0f-4675-b93f-0a166276a715&expirationTimestamp=1775311200000&signature=9RTnMLpH0jPMfJkEGpuFiK6LuLSXxr5kLTK_ADmD-Is&downloadName=image.png "PC Dashboards App (Preview)")

---
## Repository layout

Current high-level layout contains different folders for the monorepo subtree

```text
.
|- apps/
|  |- alexa-skill/        # Alexa skill subtree package, lambda handlers, interaction models
|  |- pc-assistant/       # Tauri + Next.js desktop assistant
|  |- pc-client/          # Python/FastAPI orchestrator, storage, voice, adapters, tests
|  |- pc-dashboards/      # Tauri + Next.js dashboards with offline fallback
|  `- vscode-extension/   # VS Code extension + webview UI
|- configs/               # Shared config files and schema docs
|- convos/                # Canonical conversation/session store
|- docs/                  # PRD, API reference, configuration, implementation plans
|- packages/
|  `- shared/             # Shared workspace package(s)
|- resources/             # Project assets/resources
`- tools/                 # Supporting scripts and tooling
```

---
## Roadmap
- **2024 Q4** — Alexa Skill, PC Client, Extension developed ✅
- **2025 Q1** — Local host tunneling (to expose data from PC Client->Alexa Skill), webhook routine, cross-platform communication established ✅
- **2025 Q2** — Roadmap, timeboxing, pomodoro session, site blocking (via NextDNS API) ✅
- **2025 Q4** — Private beta/alpha testing, image-first docs ✅

- **2026 Q1-Q2** — Monorepo architecture honed (pc-assistant, pc-dashboards integration) + LLM support (tested with Ollama + embeddings)
- **2026 Q3-Q4** — **Open-source initial release (timeline may vary)**
- **2026 H2** — automation packs, richer analytics, deeper-app integration & experiments (for audits/exports -- monitoring progress)
---
## TO DO:
- Need more customizability/reliable local host tunneling, as well as dynamic routine creation/deletion
- More intuitive onboarding process, documentation, and features to become a "true workflow"
- Confirm proper safety protocols are implemented when exposing localhost/ensure skill interacts only with the right tools
---
## License

This repository is licensed under Apache 2.0. See [`LICENSE`](./LICENSE).

## Project summary

**Deving Gene** is a local-first focus, automation, and workflow scaffolding system for developers who need more adaptive support than standard productivity tools usually provide.

It combines voice workflows, local orchestration, roadmap systems, dashboards, desktop clients, editor integrations, and evolving AI-assisted workflow layers to help users maintain context, protect flow state, and build with more consistency.

**Status:** WIP, with broader OSS release work targeted for 2026. 
