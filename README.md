# Deving Gene (WIP — OSS 2026)
Focus &amp; automation toolkit designed to increase productivity for twice-exceptional developers. Combines an **Alexa skill**, **PC Client (Python)**, **VS Code extension**, and a **profile engine** (FRI/VCI/WMI) with adapters for **Roblox MCP Server** and LLMs to help with executive function. Effectively turns Alexa into a developer assistant, with proper tooling to serve as a neurocognitive scaffolding system.

> 📌 This is a planning/documentation repo. **Source code will be open-sourced sometime in 2026.** Until then, this page hosts images, roadmap, and architecture notes.

## TL;DR value
- **Intuitive Setup**: Easy setup and adjustment allow developers to adjust wanted routines intuitively (also automatic setup for "deving-gene" Alexa skill communication)
- **Roadmap Functionality**: Contains monthly/weekly/specific day roadmap tuning (via file or dashboard), allowing you to map your day however you need. Contains schedule realignment (start from the beginning, go to the previous block/next block, etc.)
- **Trello Functionality/Alexa Reading** Trello REST API integration allows for multiple boards to be specified/projects. Alexa can read how much progress has been made between checklist items, the percent of completion, and more. Currently read throughout the day (via periodic routines)
- **PC-Client** Computer client to serve as a broadcasting point for idle/frequent distraction detection, app blocking. Pomodoro session alerts delivered via Alexa
- **Workflow Glue**: Trello audits/exports, session logging, focus timers, gentle/aggressive “idle detection” (program switching, etc)
- **Adaptive Profiles (coming soon)**: High-FRI / High-VCI / Low-WMI presets tune prompts, notes, and UI density. (Able to tailor proper workflow strategies based on cognitive battery).
- **Mindfulness Breaks**: Allows proper breaks to preserve proper energy for coding sessions/prevent burnout

## Screenshots
![Alexa Skill Simulator](https://private-user-images.githubusercontent.com/177498987/510546642-9f8d4e5b-5976-4794-95d2-9de01dd990ab.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NjI0MDM2MjIsIm5iZiI6MTc2MjQwMzMyMiwicGF0aCI6Ii8xNzc0OTg5ODcvNTEwNTQ2NjQyLTlmOGQ0ZTViLTU5NzYtNDc5NC05NWQyLTlkZTAxZGQ5OTBhYi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUxMTA2JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MTEwNlQwNDI4NDJaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1mYjI3MWMzYmJlY2Q1OTkxZDNkNWMyMWM5OGIyYzE5NDAzZGJjYWQ3NjJiYWNlZGE1OGEwNTFiYTMzZjlhNzMzJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.B_IcXLsZrmHVjBiOYL8aODtRKOnJOiudiTL2Ti_rr4g "Schedule")

![PC Client](https://private-user-images.githubusercontent.com/177498987/510443845-96ed1c15-042b-47bc-8225-ddb84d3141de.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NjI0MDQxNjksIm5iZiI6MTc2MjQwMzg2OSwicGF0aCI6Ii8xNzc0OTg5ODcvNTEwNDQzODQ1LTk2ZWQxYzE1LTA0MmItNDdiYy04MjI1LWRkYjg0ZDMxNDFkZS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUxMTA2JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MTEwNlQwNDM3NDlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1kZGU0N2Y4YzdiMzcwZDIyNmRhNjg1ZWQ5MGY5NmM2OGJkZDJlZGEyM2M5ZTE2OTA3YzI0ODY5NTFmOWExMmI0JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.4VAU4OZqsff9egkMfJVpaiNG8Sqq_lY6dSRkfkgaGG8 "PC Client (WIP) — dev log")

![Trello Audit](https://private-user-images.githubusercontent.com/177498987/510549507-d87635f7-e298-484d-934d-303ff3ea04d9.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NjI0MDQxMzEsIm5iZiI6MTc2MjQwMzgzMSwicGF0aCI6Ii8xNzc0OTg5ODcvNTEwNTQ5NTA3LWQ4NzYzNWY3LWUyOTgtNDg0ZC05MzRkLTMwM2ZmM2VhMDRkOS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUxMTA2JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MTEwNlQwNDM3MTFaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0zY2FhZTM5M2Q2N2UxZDIzZmY1YWRlYzcwZmM3ZmI4ZmIxOTFlZjVjZDVjMmJkZDRiMWIzMjZjN2NhMjU0MDUwJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.O6z3EijkA6Z_u6yIFnBnMg1LspUsgiKmEFtI42x8n1s "Trello audit summary (WIP)")

![RTFocuser Extension Preview](https://private-user-images.githubusercontent.com/177498987/510549092-2eb63ddf-3223-49e9-ab52-fb925a35f32d.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NjI0MDQwODEsIm5iZiI6MTc2MjQwMzc4MSwicGF0aCI6Ii8xNzc0OTg5ODcvNTEwNTQ5MDkyLTJlYjYzZGRmLTMyMjMtNDllOS1hYjUyLWZiOTI1YTM1ZjMyZC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUxMTA2JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MTEwNlQwNDM2MjFaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT01ZGNlMTAzNjgxZDU0YTcxYmM0ZjNhMmEzYmVjZjljMDgzOWJjYmZlNWQwN2RiNTE3M2ZhMjkwMjc0ZDg2MGExJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.gtRO7g1n4VU88NzK7-we8jzI3gGFd7kVTpRHXT7izUg "VS Code panel RTFocuser Extension Preview, fires mindfulness alert if script progress isnt made")

![Alexa Webhook Routine](https://private-user-images.githubusercontent.com/177498987/510496923-ad9bfb3c-4418-4f88-af69-85f2e6b7ad41.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NjI0MDM4NDIsIm5iZiI6MTc2MjQwMzU0MiwicGF0aCI6Ii8xNzc0OTg5ODcvNTEwNDk2OTIzLWFkOWJmYjNjLTQ0MTgtNGY4OC1hZjY5LTg1ZjJlNmI3YWQ0MS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUxMTA2JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MTEwNlQwNDMyMjJaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1lNGMxZWNiMmQ5OTA4NWMxMjYwMjI4ZDQ4MWFjNmMzN2U0NGNkZmRiMmYyYWQ0Y2VhZjcyOTY4Mzg0Y2MxNGZhJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.5mUx7NRbsr_bBAclwMw_jbYdbXKHR8vo6Q93OffKgdY)

![Alexa Routine Image](https://private-user-images.githubusercontent.com/177498987/510505796-e10d58db-9389-43e6-a4fd-241e6b99b44d.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NjI0MDM1MTAsIm5iZiI6MTc2MjQwMzIxMCwicGF0aCI6Ii8xNzc0OTg5ODcvNTEwNTA1Nzk2LWUxMGQ1OGRiLTkzODktNDNlNi1hNGZkLTI0MWU2Yjk5YjQ0ZC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUxMTA2JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MTEwNlQwNDI2NTBaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1iYjg2NzQzNDQwNTdiMzY5MmZkZjc5YjU0NThmNWMzMDY4YzM5NjQ0OTE5ZWFiYTQ0OTQ2ZTdlM2ExMDIwMWI4JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.jnXovIMbkOKq5SD38rkBKf-o_QIIOKwLpU26AtnYIrc)

![Studio focus/idle indicator (RTFocuser add-on)](https://private-user-images.githubusercontent.com/177498987/510505796-e10d58db-9389-43e6-a4fd-241e6b99b44d.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NjI0MDM4NDIsIm5iZiI6MTc2MjQwMzU0MiwicGF0aCI6Ii8xNzc0OTg5ODcvNTEwNTA1Nzk2LWUxMGQ1OGRiLTkzODktNDNlNi1hNGZkLTI0MWU2Yjk5YjQ0ZC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUxMTA2JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MTEwNlQwNDMyMjJaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1lZmZjYjM0N2FkY2NlYzUwN2YzODY3NWQzZTg4ZWQ2NDRkNjMzNTI3NGVhODAxY2I3ZGQ1N2Y4OWE4NjBlNTIyJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.NJDB9saTKeeehPNwEFN5PjMwRteSm2OeVi5JBfP83zM)

## Architecture (high-level mock-up for git repository 2026, subject to change)
- **apps/**
  - `alexa-skill` — intents, routines, speech models, etc
  - `vscode-extension` — notes pane, timers, status bar
- **packages/**
  - `core-profiles` — FRI/VCI/WMI engine & presets
  - `adapters` — Roblox MCP, Alexa, Gemini 2.5 Pro
- **docs/** — Neccessary documentation for proper expansion

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
