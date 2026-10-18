# Merge field to trigger map

Runtime lookup for the merge field check. Distilled from `research/distilled-research-article.md` (section 1). Last verified 2026-10-18.

The contact always exists. Everything else only exists if the trigger brought it in.

| If the message uses | The workflow needs | If not | Status |
|---|---|---|---|
| `{{appointment.*}}`, `{{appointment.user.*}}`, `{{calendar.name}}`, add-to-calendar links | Appointment Status or Customer Booked Appointment trigger | Blank. Pipeline stage changed and every other trigger cannot tell which appointment | Verified |
| `{{order.line_items}}` (pluck) | Order Submitted (V2 funnels) or a trigger carrying a list (Inbound Webhook) | Blank. On V1 funnels use Payment Received | Verified via owner page |
| `{{payment.*}}`, `{{payment.line_items}}` | Payment Received | Blank. Insert sub-fields from the picker | Sub-fields unverified |
| Company fields | Contact associated with a Company record | Blank | Verified |
| Task ID | Task-related trigger | Not in the picker | Verified |
| Note created by (Name) | Note-related trigger | Not in the picker | Verified |
| Contact Engagement Score | Engagement Scoring enabled in the sub-account | Blank | Verified |
| Inbound webhook payload fields | Inbound Webhook trigger, sample request sent first | Fields not mappable | Syntax unverified |
| `{{invoice.*}}`, `{{servicebooking.*}}`, `{{this.*}}`, `{{message.*}}`, `{{campaign.event_*}}` | Matching context (KB names no trigger) | Unknown | Unverified: test first |
| `{{contact.*}}`, `{{user.*}}`, `{{location.*}}`, `{{right_now.*}}`, custom values | Nothing | Always fill (blank only if the record field is empty) | Verified |

## Traps to mention with the check

- Test sends never fill appointment fields. Test with a real booking.
- Payment Received only fires on a test payment once the workflow is published.
- Empty data renders blank ("Hi ,"). Fix with Conditional Send. Fallback values: the KB contradicts itself (newest article says unsupported), so test in the account before promising a client.
- Merge fields are case-sensitive.
- Calling-number and click ID fields: insert from the picker, never type them.
- AI agents use `{{company.*}}`; workflows and emails use `{{location.*}}`.

## Fix options to offer (pick what fits, never invent actions)

1. Move the message into a workflow whose trigger carries the data.
2. Change or add the trigger so it carries the data.
3. Use data that was already saved to a contact or opportunity field.
4. Drop the merge field and write the line without it.

Full field list for the owner: the vault page **Workflow Merge Fields and Gotchas** (cheat sheet section) and the KB list: https://help.gohighlevel.com/support/solutions/articles/48001078171-list-of-merge-fields
