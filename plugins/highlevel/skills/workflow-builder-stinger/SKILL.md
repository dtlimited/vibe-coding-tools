---
name: workflow-builder-stinger
description: Design, troubleshoot and review Tekmatix CRM workflows with Dani's own logic first. Logs her build rules, enforces her naming conventions, checks the trigger before any merge field.
license: AGPL-3.0-or-later
compatibility: Claude chat and Cowork (needs the Obsidian vault folder for full use), Claude Code, Cursor, Codex
metadata:
  hive-tier: standalone
  hive-drone: none
  domain: CRM workflow design
  version: "1.0"
---

# Workflow Builder Stinger

## Purpose

Helps Dani design, troubleshoot and review workflows in her CRM platform (Tekmatix accounts, and Thompson Limited client accounts on the same platform), using her own build logic first and platform docs second. v1 does three things every time it runs: captures how she says she builds into her Workflow Logic Log, holds every name to her decided Naming Conventions, and checks that a workflow's trigger actually carries the data before any merge field is used. Designs come out as build sheets she builds from, because workflows cannot be created through the API yet.

## When to use

- Designing or planning a workflow ("build me a workflow that...", "how should I set up the cancellation flow")
- Naming a workflow, email template, appointment title or subject line
- Writing an email or SMS that goes inside a workflow
- A workflow misfires, or a merge field "comes out blank"
- Reviewing an existing workflow or someone else's build
- Dani explains how or why she builds something a certain way

## When not to use

- API, webhook or OAuth integration work: `gohighlevel-stinger`
- Turning an account export into flowcharts: `ghl-to-mermaid-stinger`
- AI Studio, funnel or website building: `highlevel-ai-studio-stinger`
- Making changes inside a live account. This skill drafts; it never builds, publishes or sends.

## Procedure

1. **Open her vault pages.** Follow `references/vault-locations.md` to reach `40 - GHL Reference`. Read `Workflow Logic Log.md` and `Naming Conventions.md` before designing or naming. If the vault is unreachable, say so in one line and continue from this skill's references.
2. **Pick the job:** design, review or troubleshoot, then follow `guides/design-review-troubleshoot.md`, including its source priority (her words and log beat platform defaults and outside advice).
3. **Merge field check, every message:** run `guides/check-merge-fields.md` before writing any copy containing a merge field. Flag a trigger that does not carry the data before writing the copy.
4. **Naming, every name:** run `guides/enforce-naming.md`. Only the Decided section counts. Never suggest a new naming system. Uncovered or conflicting: ask one question.
5. **Capture, always on:** whenever she states how or why she builds something, write it to the Logic Log per `guides/capture-to-logic-log.md`, then confirm in one line.
6. **Deliver:** a build sheet (`references/build-sheet-template.md`) for designs, a findings list for reviews, the most likely cause plus one confirming test for troubleshooting.

Hard rules: no em dashes in anything written; reference content avoids the platform name outside KB links; client-facing copy for Tekmatix clients says "Tekmatix" only; native workflows first.

## References map

- `guides/design-review-troubleshoot.md`, load for every request: source priority, design, review and troubleshoot flows.
- `guides/check-merge-fields.md`, load whenever copy contains a merge field or a field comes out blank.
- `guides/enforce-naming.md`, load whenever anything gets named.
- `guides/capture-to-logic-log.md`, load whenever Dani says how or why she builds something.
- `references/merge-field-trigger-map.md`, load with the merge field guide.
- `references/vault-locations.md`, load first, to reach her vault safely.
- `references/build-sheet-template.md`, load when delivering a design.
- `references/research/distilled-research-article.md`, load to verify a claim or settle a conflict.
- Source research archive (raw captures, kept outside this public plugin), load only to trace a claim; the distillation lists each source's URL or vault page.

## Related drones and stingers

- [gohighlevel-stinger](../gohighlevel-stinger) - API, webhooks and OAuth for the same platform. Owns integration work, and later any API-based workflow building.
- [ghl-to-mermaid-stinger](../ghl-to-mermaid-stinger) - Maps an account export into per-workflow flowcharts. Useful input for a review.
- [highlevel-ai-studio-stinger](../highlevel-ai-studio-stinger) - AI Studio, funnels and websites.

## Critical Directive

- You must read all files and context contained within your skill.
- In the event your core knowledge does not provide sufficient guidance you must make every attempt to search the internet, related knowledge base documentation files, and other available resources to supplement your knowledge prior to proceeding with your task.
- Additional related skills can be found here:
  - [gohighlevel-stinger](../gohighlevel-stinger) - API integration authority for the same platform.
  - [ghl-to-mermaid-stinger](../ghl-to-mermaid-stinger) - Export to flowchart conversion for workflow reviews.

<!-- Ship Gate removed: research-only stinger, produces no committable code. -->
