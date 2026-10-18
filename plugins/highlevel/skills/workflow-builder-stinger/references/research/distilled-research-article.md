# Distilled research: workflow builder v1

Scope: the three v1 jobs (log capture, naming enforcement, trigger-before-merge-field check). Research window: 2026-10-18 snapshot of the owner's vault plus two KB re-fetches the same day.

Citations `raw/0N` point to the source research archive, which is kept outside this public plugin (raw research is not shipped). Each raw file is listed here with its origin so any claim can be re-checked:

| ID | Source | Type | Fetched |
|---|---|---|---|
| raw/01 | Vault page `40 - GHL Reference/Workflow Merge Fields and Gotchas.md` (compiled from the KB, links inline) | Owner reference | 2026-10-18 |
| raw/02 | https://help.gohighlevel.com/support/solutions/articles/48001181948 (appointment custom values not showing) | Official KB, modified 2021-04-27 | 2026-10-18 |
| raw/03 | https://help.gohighlevel.com/support/solutions/articles/155000004390 (overview of merge fields) | Official KB, modified 2026-09-01 | 2026-10-18 |
| raw/04 | Vault pages `Workflow Logic Log.md` and `Naming Conventions.md` (page rules only) plus owner statements from chat | Owner instructions | 2026-10-18 |

## 1. Merge fields that depend on the trigger

| Merge fields | Fill only when | Confidence | Source |
|---|---|---|---|
| `{{appointment.*}}`, `{{appointment.user.*}}`, `{{calendar.name}}`, add-to-calendar links | Trigger is Appointment Status or Customer Booked Appointment | High (KB, re-fetched 2026-10-18; article dated 2021) | raw/02, raw/01 |
| `{{order.line_items}}` via pluck | Order Submitted (V2 funnels), or a trigger carrying a list such as Inbound Webhook | Medium (owner page from KB) | raw/01 |
| `{{payment.*}}`, `{{payment.line_items}}` | Payment Received | Medium. KB does not list exact sub-fields | raw/01 |
| Company fields | Contact is associated with a Company record | High (KB, Sep 2026) | raw/03 |
| Task ID | Task-related workflows | High | raw/03 |
| Note created by (Name) | Note-related workflows | High | raw/03 |
| Contact Engagement Score | Engagement Scoring enabled in the sub-account | High | raw/03 |
| Inbound webhook payload fields | Inbound Webhook trigger, after a sample request is sent | Medium. Payload syntax unverified | raw/01 |
| `{{invoice.*}}`, `{{servicebooking.*}}`, `{{this.*}}`, `{{message.*}}`, `{{campaign.event_*}}` | Context only. KB names no trigger | Low. Test before relying | raw/01 |
| `{{contact.*}}`, `{{user.*}}`, `{{location.*}}`, `{{right_now.*}}`, custom values | Always available | High | raw/01 |

Thin coverage: the payment sub-field names, webhook payload syntax and the five "context only" rows are not verified. The skill must say so instead of guessing.

## 2. Testing traps

- Test sends do not fill appointment fields. Test with a real booking. (raw/02)
- Payment Received only fires on a test payment after the workflow is published. (raw/01)
- Blank data renders blank ("Hi ,"). (raw/03)

## 3. Conflict: fallback values

- The KB merge-fields overview (modified 2026-09-01) says fallbacks are not supported and recommends Conditional Send. (raw/03)
- The owner's page notes the KB merge-field list describes setting a fallback by clicking a tag in the email editor. (raw/01)
- Preferred reading: the newer overview. Skill behavior: recommend Conditional Send, and tell the owner to test in the account before promising a client a fallback.

## 4. Other rules that bite

- Case-sensitive merge fields. (raw/03)
- Insert account-specific fields (calling number, click IDs) from the picker, never typed. (raw/01)
- AI agents use `{{company.*}}` for business fields; workflows and emails use `{{location.*}}`. (raw/01)
- Opportunity Changed with an "Equals" filter fires on any change while the value holds. Use "Has Changed To". (raw/01)
- Order Submitted is V2-funnels only. On V1 use Payment Received. (raw/01)

## 5. Vault page contracts (owner instructions)

- Logic Log: entries go under "This month", in the owner's words, in the page's exact entry format, newest first. Competing ideas go in `Tension`, never flattened. (raw/04)
- Naming Conventions: only the Decided section counts. No new naming systems. Anything uncovered or conflicting is one question to the owner, then her answer goes under Decided with the date. (raw/04)
- Owner priorities: her logic beats platform defaults and outside advice; platform names stay out of reference content except KB links. (raw/04)
