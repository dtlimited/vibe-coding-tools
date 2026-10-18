# Build sheet template

The output of a design request. The platform API cannot create workflows yet, so the owner builds from this sheet. Keep it skimmable.

```markdown
## {Workflow name, per Naming Conventions > Decided}

**What it does:** one sentence.
**Audience:** internal or client-facing.

### Trigger
- Trigger: {name}
- Filters: {filters, or "none"}

### Steps
1. {Action}: {setting that matters}
2. {Action}: {setting that matters}

### Merge fields
| Field | Needs | This trigger carries it? |
|---|---|---|
| `{{...}}` | {trigger or context} | Yes / NO: {fix} / Unverified: test |

### Watch out
- {Gotchas from the map or her vault that apply. Omit the section if none.}

### Your logic applied
- {Log entry title}: {how it shaped this build}

### Open questions
- {Only real blockers. Omit the section if none.}
```

For client-facing copy inside the sheet (email or SMS text): Tekmatix clients see "Tekmatix" only, never the underlying platform name.
