---
name: writing-meeting-briefs
description: This skill should be used when research findings about a customer account need to be turned into a concise executive meeting brief, account brief, or pre-meeting briefing document. It merges findings blocks into a fixed 10-part, 1 to 2 page brief with the top takeaways first, source links kept, gaps shown explicitly, and conflicts raised as open questions. Do not use for writing agendas or speaker bios.
---

# Writing Meeting Briefs

Turn research findings blocks into a scannable 1 to 2 page brief using `references/brief-template.md`.

## Inputs
- findings: findings blocks (source_area, status, findings with source links and confidence, flags)
- agenda: optional agenda output (the `sic-agenda-creation` table)
- meeting_date: for timing flags
- removed_claims: optional, from a fact-check pass

## Rules
- Follow the template's section order exactly.
- Lead with 3 to 5 "Top things to know": the items most likely to change how the strategist runs kickoff.
- Keep each claim's source link. Never add a claim that is not in the findings.
- Show gaps as gaps: "not found" or "couldn't access source." Never leave a section silently empty.
- Where findings conflict, state both and add the conflict to Open questions.
- Flag at the top if the meeting is under 48 hours away or already past, if attendees are unconfirmed, or if claims were removed. For a past meeting, label anything dated after the meeting "post-meeting".
- Hold to 1 to 2 pages: cut the lowest-relevance items first and note "more available on request."
- Neutral, professional, scannable. No speculation. Never use em dashes or double dashes.

## Failure modes
- All findings empty: produce the brief with gap notes and a top-line warning.
- Agenda missing: the agenda section says "agenda not generated."
