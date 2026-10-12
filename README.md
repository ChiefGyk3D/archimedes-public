# Archimedes

An autonomous cyber threat intelligence analyst. Collects, grades, analyzes, and delivers OSINT-based threat intel with a focus on the aerospace & defense sector, Iranian cyber operations, and global APT tracking.

> *"Intelligence is only useful if it's actionable."*

> **Public snapshot.** This repository is a read-only snapshot of a personal project as of September 14, 2026, published for reference and teaching. Host, network and workplace details have been removed, and the git history starts fresh here. Scheduled briefs ran from May 1 to August 2, 2026; the corpus is not being updated in this repo. It is not affiliated with or endorsed by any employer.

---

## What this is

Archimedes is a CTI analyst built on [Claude Code](https://docs.claude.com/en/docs/claude-code). It runs on a single PC, produces scheduled briefs twice daily plus async FLASH alerts, maintains a living corpus of threat actor profiles, and logs everything to Splunk for full audit trail.

This project is a rebuild of an earlier agent (C3PO, on OpenClaw) with a clean architecture, stricter doctrine, and Claude Code as the runtime.

## What it produces

**Scheduled output**
- Morning Brief — 08:00 EDT, posted to Discord
- Afternoon Brief — 16:00 EDT, posted to Discord
- Weekly Synthesis — Sundays 10:00 EDT
- Threat Detection Weekly — Wednesdays 10:30 EDT
- Threat Actor Summary — Fridays 12:00 EDT

**Async output**
- FLASH alerts (9am–9pm EDT, queued outside those hours)
- Alert sweeps every 6 hours

**On-demand**
- `/investigate` any actor, domain, hash, campaign, or CVE
- `/ioc-hunt` any indicator across the repo + first-party telemetry + external sources
- `/new-actor` to add a new actor profile from scratch
- `/update-tracking` to refresh actor profiles on a weekly rotation

## How it works

Archimedes is an orchestrator that delegates to eight specialized subagents, each with its own isolated context:

- **collector** — gathers raw signal from sources
- **grader** — promotes raw signal to graded findings (NATO Admiralty Scale)
- **analyst** — runs structured analytic techniques
- **red-team-analyst** — challenges high-confidence assessments
- **actor-profiler** — maintains actor dossiers
- **vuln-tracker** — maintains vulnerability profiles
- **briefer** — composes Smart Brevity briefs per standards
- **librarian** — updates indices, commits to git, logs to Splunk

See `CLAUDE.md` for the orchestrator's full charter and `.claude/agents/` for subagent definitions.

## How it's graded

Every finding carries an Admiralty Scale digraph (e.g., `A2`, `B2`) — source reliability (A–F) × information credibility (1–6). Forward assessments use Words of Estimative Probability with explicit probability bands. Full doctrine in `doctrine/INTEL-GRADING.md`.

## Tracked adversaries

A roster of 29 tracked actors (13 with full dossiers), covering Russian GRU/SVR, Iranian IRGC/MOIS, Chinese MSS/PLA, DPRK, and major cybercriminal syndicates. Full roster in `threats/threat-actors/_roster.yaml`.

## What this project is NOT

- Not a SOC. No alerting on internal incidents (use your actual SIEM for that).
- Not an attack tool. Read `doctrine/LEGAL-POLICY.md` — defensive research only.
- Not a replacement for commercial CTI. It's a personal analytic workbench.
- Not a news aggregator. Every item is graded, corroborated, and attributed.

## Getting started

See `doctrine/INTEL-OPERATIONS.md` for operational details and `CLAUDE.md` for the orchestrator charter.

## License

Copyright © 2026 Ryan. All rights reserved.

You're welcome to read, study and reference this repository, and to reuse its ideas in your own work. Copying or redistributing the code, doctrine or intelligence corpus requires permission. Threat reporting summarized in `threats/` remains the property of the original publishers, who are cited in each file.

Nothing here is an official assessment, and none of it should be treated as current: intelligence findings reflect open-source reporting at the time they were written.

## Author

Maintained by Ryan. Built iteratively, session by session, with care.
