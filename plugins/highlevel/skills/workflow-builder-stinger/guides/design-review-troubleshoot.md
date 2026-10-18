# Design, review and troubleshoot

Grounding: `references/research/distilled-research-article.md`, all sections.

## Source priority (her logic first)

When sources disagree, the higher one wins. Mention the conflict once, in one line, then follow the winner.

1. Her answer in this conversation.
2. Workflow Logic Log entries (the **Reviewed** section first, then **This month**).
3. Naming Conventions > Decided.
4. Her vault reference pages (merge fields, gotchas, triggers, actions, calendar).
5. This skill's `references/`.
6. The platform KB, then everything else. Outside "best practice" never overrides 1 to 4.

Default stance from her log: native workflows first. No third-party tools or outside integrations unless the build truly cannot work without them, and say why when it cannot.

## Design

1. Ask only what blocks the design: what problem, who it is for, what success looks like. One question at a time. Skip anything she already said.
2. Read the Logic Log and Naming Conventions.
3. Design, running `check-merge-fields.md` on every message and `enforce-naming.md` on every name.
4. Output a build sheet (`references/build-sheet-template.md`). It is a sheet she builds from, not a live build.
5. Capture any how/why she states along the way (`capture-to-logic-log.md`).

## Review

Input: a description, screenshots, or an exported workflow.
Check, in order, and report findings most important first:
1. Merge fields vs trigger (blank-field risks).
2. Trigger filters and known gotchas (for example "Equals" vs "Has Changed To").
3. Names vs Decided patterns.
4. Conflicts with her logged logic.
Each finding: what is wrong, why it matters, the fix. Say plainly what you could not check.

## Troubleshoot

1. Get the symptom, the trigger, and what she expected.
2. Check her vault gotchas and the merge field map first, then her triggers/actions reference pages, then the KB.
3. Give the most likely cause first, with one test that confirms it.
4. If a new gotcha is confirmed, offer to add it to the `## Gotchas` section of her merge fields page in the page's format: `- **[Thing]:** what happens, and what to do instead. [KB](link)`.

## Wording rules

- No em dashes anywhere.
- Reference content and build sheets avoid the platform name except inside KB links. Client-facing copy for Tekmatix clients says "Tekmatix" only.
- Draft only. Never publish, send or change anything in a client account.
