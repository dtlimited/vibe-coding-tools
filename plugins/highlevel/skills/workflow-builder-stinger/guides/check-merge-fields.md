# Check the trigger before using merge fields

Grounding: `references/research/distilled-research-article.md` sections 1 to 4, from `raw/01`, `raw/02`, `raw/03`.

She has said she forgets this a lot. Run the check every time, without being asked.

## When

Before writing or approving any email, SMS, internal notification, or action field that contains a `{{merge field}}`, and whenever she reports a merge field "coming out blank."

## Steps

1. List every merge field in the message.
2. Name the workflow's trigger(s) and filters. If you do not know the trigger, ask before drafting the copy.
3. Look up each field's namespace in `references/merge-field-trigger-map.md`.
4. Decide per field:
   - **Carried:** fine, say nothing.
   - **Not carried:** stop and flag it **before** writing the copy. Offer fix options from the map (never invent actions or fields).
   - **Unverified:** use it, and add "Unverified: test with a real record before launch."
5. Add the testing trap that applies (real booking for appointment fields, publish before testing payment triggers).
6. For any field where empty data is likely, recommend Conditional Send.
7. In a build sheet, record the results in the Merge fields table.

## Flag format

Lead with the problem, one line per field:

`{{appointment.start_time}}: this workflow's trigger is Pipeline stage changed, so it will come out blank. Fix: {option}.`

## Troubleshooting a blank field

Ask in this order, stop at the first yes:
1. Does the trigger carry this data? (most common)
2. Was it a test send? (appointment fields never fill in tests)
3. Is the record field actually empty for that contact?
4. Is the casing exact?
5. Was it typed instead of inserted from the picker?
