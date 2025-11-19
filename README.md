![Status: WIP](https://img.shields.io/badge/status-WIP-orange)
![License: Apache-2.0](https://img.shields.io/badge/license-Apache%202.0-blue)
![Platform: Windows 10/11](https://img.shields.io/badge/platform-Windows%2010%2F11-lightgrey)

# Deving Gene (WIP — OSS 2026)
Focus &amp; automation toolkit designed to increase productivity for twice-exceptional developers. Combines an **Alexa skill**, **PC Client (Python)**, **VS Code extension**, and a **profile engine** (FRI/VCI/WMI) with adapters for **Roblox MCP Server** and LLMs to help with executive functioning and coding. Effectively turns Alexa into a learning **and** developer assistant, with proper tooling to serve as a neurocognitive scaffolding system for different neurotypes.

> 📌 This is a planning/documentation repo. **Source code will be open-sourced sometime in 2026.** Until then, this page hosts images, roadmap, and architecture notes.

**What’s here today**
- Planning docs, screenshots, roadmap ✔️
- License ✔️
- Public API & CLI sketch (coming soon) ⏳
- Trello REST API Integration (reading card progress throughout the day outloud via Alexa Skill)
- Schedule block chunking, idle alerts, site blocking (via NextDNS API), schedule syncing (currently from Alexa->PC)

**What’s not here yet**
- Public Source code, release packages (scheduled OSS: 2026) ⏳
- PC Assistant UI (currently in development since November 2025) ⏲
- AI functionality (currently in development since November 2025) ⏲

## TL;DR value
- **Intuitive Setup (coming soon)**: Easy setup and adjustment allow developers to adjust wanted routines intuitively (also automatic setup for "deving-gene" Alexa skill communication)
- **Roadmap Functionality**: Contains monthly/weekly/specific day roadmap tuning (via file or dashboard), allowing you to map your day however you need. Contains schedule realignment (start from the beginning, go to the previous block/next block, etc.)
- **Trello Functionality/Alexa Reading** Trello REST API integration allows for multiple boards to be specified/projects. Alexa can read how much progress has been made between checklist items, the percent of completion, and more. Currently read throughout the day (via periodic routines)
- **PC-Client** Computer client to serve as a broadcasting point for idle (frequent ALT+TAB alerts, no input detected after X minutes) frequent distraction detection, app blocking. Pomodoro session alerts delivered via Alexa.
- **Workflow Glue**: Trello audits/exports, session logging, focus timers, gentle/aggressive “idle detection” (program switching, etc)
- **Adaptive Profiles (coming soon)**: High-FRI / High-VCI / Low-WMI presets tune prompts, notes, and UI density. (Able to tailor proper workflow strategies based on cognitive battery).
- **Mindfulness Breaks**: Allows proper breaks to preserve proper energy for coding sessions/prevent burnout
- **Webhook Routines**: Allows Webhook Routine Triggers to be configured for Alexa Setup in a similar manner as Virtual Smart Home [URLRoutineTrigger](https://www.amazon.com/Virtual-Smart-Home-Routine-Trigger/dp/B08SHHS8JZ/) for cross-platform Alexa communication (currently uses Virtual Smart Home triggers for dev build; considered for early OSS 2026 release)

**Security & operation (short version).**
Deving Gene is **local-first** and **least-privilege**. The PC client enforces focus rules (e.g., app/process blocking and DNS toggles) and can expose an **optional** localhost webhook for automations.
It **does not** read keystrokes, files, or page contents, etc. Data (schedules, prefs, logs) stays on your machine by default.

## PC Client Explanation
**Current Configuration (late Q1 2025)**

Currently, the PC Client receives the schedule from the Alexa Skill **after** setting up local-host tunneling point (because I have not yet designed more user-friendly data reading)
The PC Client localhost tunneled URL endpoints are responsible for allowing the Alexa Skill to communicate data (like `sessionAttributes`, `roadmap`, etc) back to the PC Client and VSCode Extensions
to properly read from

**Planned Configuration (sometime in Q1-Q2 2026)**

The Alexa skill is planned to talk to your computer **mainly** through the PC client. If the client isn’t running, Alexa can still run generic routines, but she won’t see or update your local roadmap/progress—or the upcoming cognitive profile metrics (FRI/VCI/PSI/WMI) you choose to sync. When the client is active, it exposes a single localhost endpoint (tunnel optional/disable-able) to exchange just the data needed for those features. 

*Road to OSS 2026:* secrets/config will use **environment variables** (with OS keychain support) and a `.env.example` in the repo; potential install scripts will wire everything without committing credentials.

## Screenshots
![Alexa Skill Simulator](https://www.notion.so/image/attachment%3A2a49635b-ed69-4324-9e98-07f4a5efeb34%3Aimage.png?table=block&id=2a34773f-9ff0-8034-b8ae-f336eea49c3b&spaceId=efeada7c-1a0f-4675-b93f-0a166276a715&width=810&userId=&cache=v2 "Alexa Skill Schedule Greeting")

![PC Client](https://www.notion.so/image/attachment%3A0bed283d-41af-4349-827c-5a3856f83a7f%3Aimage.png?table=block&id=2a34773f-9ff0-80cc-b881-e93f7c471ebd&spaceId=efeada7c-1a0f-4675-b93f-0a166276a715&width=1420&userId=&cache=v2 "PC Client (WIP) — dev log")

![Alexa Trello Audit](https://www.notion.so/image/attachment%3A517703c3-5388-472c-b5a8-49ab639ec027%3Aimage.png?table=block&id=2a34773f-9ff0-809e-8be2-e77aa28482cd&spaceId=efeada7c-1a0f-4675-b93f-0a166276a715&width=730&userId=&cache=v2 "Alexa Skill Trello audit summary (WIP)")

![RTFocuser Extension Preview](https://www.notion.so/image/attachment%3A84839b78-e2b5-4f40-84b7-b6ef24e45426%3Afc7c1c5b-967d-41a6-a44d-c0fc87b95460.png?table=block&id=2a34773f-9ff0-80a0-8b9c-cde77de501fa&spaceId=efeada7c-1a0f-4675-b93f-0a166276a715&width=1420&userId=&cache=v2 "VS Code panel RTFocuser Extension Preview, fires mindfulness alert if script progress isnt made")

![Alexa Routine Image](https://www.notion.so/image/attachment%3Abed27bbd-465b-401e-b744-be1ca8ca3ba3%3Aimage.png?table=block&id=2a34773f-9ff0-80b3-a326-daa4b9623110&spaceId=efeada7c-1a0f-4675-b93f-0a166276a715&width=1420&userId=&cache=v2 "Alexa Routine App Preview")

![Studio focus/idle indicator (RTFocuser add-on)](https://www.notion.so/image/attachment%3A7dfc1f7f-751c-4ea4-aa98-ef167748ab72%3Aimage.png?table=block&id=2a34773f-9ff0-8085-a131-f18dd6c9555e&spaceId=efeada7c-1a0f-4675-b93f-0a166276a715&width=1420&userId=&cache=v2 "Studio focus/idle indicator (RTFocuser add-on)")

## Architecture (high-level mock-up for git repository 2026, subject to change)
- **apps/**
  - `alexa-skill` — intents, routines, speech models, etc (already exists)
  - `vscode-extension` — notes pane, timers, status bar
- **packages/**
  - `core-profiles` — FRI/VCI/WMI engine & presets
  - `adapters` — Roblox MCP, Alexa, Gemini 2.5 Pro (PC Client running required with IDEs)
- **docs/** — Neccessary documentation for proper setup/capabilities

## Roadmap
- **2024 Q4** — Alexa Skill, PC Client, Extension developed ✅
- **2025 Q1** — Local host tunneling (to expose data from PC Client->Alexa Skill), webhook routine, cross-platform communication established ✅
- **2025 Q2** — Roadmap, timeboxing, pomodoro session, site blocking (via NextDNS API) ✅
- **2025 Q4** — Private beta/alpha testing, image-first docs ✅
- **2026 Q1** — time bug fixes, need for automatic routine automation/easier routine setup/swapping (separate application for Echo Dot Routine Creation?)
- **2026 Q1-Q2** — **Open-source initial release (timeline may vary)**
- **2026 H2** — automation packs, richer analytics (for audits/exports -- monitoring progress)
## TO DO:
- Need more customizability/reliable local host tunneling, as well as dynamic routine creation/deletion
- More intuitive onboarding process, documentation, and features to become a "true workflow"
- Confirm proper safety protocols are implemented when exposing localhost/ensure skill interacts only with the right tools
## License
Planned: Apache-2.0. (Until code release, docs/images are © Robert Clark.)
