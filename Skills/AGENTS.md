# Skills

> **TL;DR:** Library of reusable playbooks, one subfolder per skill (`SKILL.md`) — read only when executing a known repeatable procedure.

## What belongs here

- One subdirectory per skill, e.g. `Skills/<skill-name>/SKILL.md` plus any supporting scripts/templates.
- Skills should be self-contained: a description of when to use it, step-by-step instructions, and any helper files it depends on.
- Generic, project-agnostic procedures (e.g. "how to cut a release", "how to triage a flaky test", "how to deploy to staging") belong here.

## What does NOT belong here

- Facts about specific projects/systems — put those in [../Knowledge/AGENTS.md](../Knowledge/AGENTS.md).
- Working scratch files — keep them outside the deliverable; do not store secrets here.

## Creating a Skill

1. Create a folder: `Skills/{skill-name}/`
2. Add a `SKILL.md` with:
   - **When to use** — triggers that should invoke this skill
   - **Steps** — the procedure, written for an AI agent to follow
   - **Supporting files** — any scripts, templates, or configs the skill needs
3. Reference it from this file in the "Available Skills" list below.

## Available Skills

No hay procedimientos adicionales instalados en esta entrega. Esta carpeta conserva únicamente la guía de la plantilla; no se instaló ningún harness.

## Conventions

- Skill names use kebab-case: `daily-report`, `cut-release`, `triage-flaky-test`.
- Each skill is self-contained — an agent should be able to execute it by reading only that skill's folder.
- Keep skills updated when processes change.
