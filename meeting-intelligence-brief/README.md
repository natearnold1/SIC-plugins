# Meeting Intelligence Brief (SIC)

Pre-kickoff brief for a Salesforce Innovation Center (SIC) meeting. Seven research agents run in parallel, a funnel-ordered agenda is suggested from similar past meetings, a fact-checker reviews the draft, and the approved brief is delivered as a Slack canvas.

## Requirements
- Salesforce (org62) connector with read access to `EBC_Meeting__c`, `Agenda_Item__c`, Account, Opportunity, Case and CampaignMember. Read-only operations only.
- Slack connector (read channels, search, users, create canvas).
- Web search and fetch.
- Run it from a Cowork or Claude Code session with those connectors connected. Agents inherit your own connector tools, so no tool names need editing.

## Use
Invoke the `meeting-intelligence-brief` skill and give it an org62 SIC meeting record link (for example `.../EBC_Meeting__c/<Id>/view`) or the Slack message it was piped into.

## Where you are in the loop
| Gate | What you do |
|---|---|
| G1, before research | Confirm or correct attendees (or keep as "expected"), the main account Slack channel, and the total meeting length in hours per day |
| G2, before anything is created | Review the full fact-checked draft and the removed-claims list; approve or request edits |
| After approval | The only write: one Slack canvas. No channel messages, no customer or attendee contact |

## What runs
| Step | Action | Source |
|---|---|---|
| 1 Intake | Read the meeting request | org62 `EBC_Meeting__c` |
| 2 Validate (G1) | Pre-fill attendees and channels | org62, Slack |
| 3 Research (7 agents, parallel) | org62 history; past SIC meetings; Slack context; company and attendees; competitive; customer stories; marketing events | org62, Slack, web, #gfm-all, #global-customer-advisory-boards |
| 4 Agenda | `sic-agenda-creation`: welcome, Voice of the Customer, then strategy, process, specific sessions sized to meeting length, with suggested conversation and Slack-checked speakers | org62 `Agenda_Item__c` (last 18 months, same topic then industry), Slack users |
| 5 Synthesize | `writing-meeting-briefs`: fixed 10-part brief | Findings blocks |
| 6 Fact-check | `fact-checking-briefs`: verify public claims and links, remove untraceable claims | Web |
| 7 Review (G2) | You approve or edit | You |
| 8 Deliver | Create Slack canvas | Slack |

## Known limits
- Fact-checker has web tools only; org62 and Slack claims are checked for tracing, not opened.
- Agenda item length, start time and order fields are usually empty in org62, so durations are suggestions derived from your total meeting length. Similar-meeting data is often thin (median one logged item per meeting).
- The org62 attendee list object is not yet identified; attendees stay "expected".
- Slack "profile found" does not confirm a speaker's availability.
- Canvases have no sharing controls in the tool; check sharing after creation.
- Intake source (how requests arrive) is still TBD.
- Briefs contain internal deal data and customer names. Treat canvases accordingly.

## Contents
- `skills/meeting-intelligence-brief` (orchestrator)
- `skills/sic-agenda-creation`
- `skills/writing-meeting-briefs`
- `agents/` researching-account-history, researching-past-sic-meetings, researching-slack-context, researching-company-and-attendees, researching-competitive-landscape, finding-customer-stories, finding-marketing-events, fact-checking-briefs
