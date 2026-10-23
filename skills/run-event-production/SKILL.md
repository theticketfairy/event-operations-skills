---
name: run-event-production
description: "Run an event day to day in Ticket Fairy Event Management: the Today page, tasks, the event inbox, call notes, messages to the team and attendee feedback. Use when an organiser runs the event itself."
---

# Run your event day to day

This skill covers the Today page, tasks, the event inbox, call notes, team messages and feedback on Ticket Fairy. It lists the 14 published guides for this area and what an agent can do for each one.

## How to work

1. **Find the guide.** Pick the guide below that matches the task. If none fits, search all guides:
   connect an MCP client to `https://www.ticketfairy.com/docs/mcp` (Streamable HTTP, no account or
   key) and call `search_guides` with the task in plain words.
2. **Read it before you act.** Call `get_guide` with the guide's slug. It returns who the guide is
   for, what to have ready, every step and the common questions. Follow those steps; do not guess
   the dashboard from memory.
3. **Do the work, or hand it over.** Each guide below says what an agent can do:
   - **Command line.** With the organiser's permission, install the official CLI
     (`npm install -g ticketfairy`) and sign in with `ticketfairy login`, or use a Personal Access
     Token that the organiser stores in `TICKET_FAIRY_API_KEY`. Then check the account and pick the
     brand: `ticketfairy auth status`, `ticketfairy brand list` and
     `ticketfairy brand use <BRAND_ID>`. Add `--output json --non-interactive` to every command
     you run that does not already choose its own mode, such as `--output csv` or `--interactive`;
     the commands below leave them out to stay short.
   - **MCP.** `ticketfairy mcp --read-only` starts the CLI's MCP server with read tools. Drop
     `--read-only` only when the organiser wants you to make changes.
   - **Fai.** Fai is the assistant inside the organiser's dashboard. When a task is not on the
     command line, give the organiser the suggested prompt to paste into Fai.
   - **Dashboard.** Otherwise, send the organiser the guide link and walk them through it.
4. **Keep secrets out of the chat.** Codes, passwords and tokens that the organiser receives go
   into the Ticket Fairy dashboard: the page that asks for them, or Fai there when the guide says
   so. They never go into your conversation with the organiser.
5. **Keep actions within the organiser's approval.** Use their explicit approval for this exact
   action, or show what you will create, change, send, refund or cancel and wait for their yes.
   Installing a skill or asking for a draft does not authorise sending messages. Use only the
   approved brand, event and recipients, and only what the person's team role allows.
6. **Organiser access does not authorise ticket payments.** A buyer uses a separate supported
   checkout with their explicit approval, or pays in the browser. Bank, tax and payout details
   stay in the organiser's own browser.
7. **Recover the original result after an uncertain change.** Read the original order or operation
   before retrying. Reuse its idempotency key when the documented operation supports one. Never
   repeat an uncertain refund, transfer, message send or ticket grant as a fresh operation.

## Guides

- [Ask attendees for feedback after your event](#ask-attendees-for-feedback-after-your-event)
- [Balance your event team's workload](#balance-your-event-teams-workload)
- [Choose how your event emails look](#choose-how-your-event-emails-look)
- [Choose what Fai does on your event](#choose-what-fai-does-on-your-event)
- [Compare your ticket sales with your last event](#compare-your-ticket-sales-with-your-last-event)
- [Copy the setup of your last event into your next one](#copy-the-setup-of-your-last-event-into-your-next-one)
- [Find any performer, stage or day on your event](#find-any-performer-stage-or-day-on-your-event)
- [Keep the jobs behind your event moving](#keep-the-jobs-behind-your-event-moving)
- [Message the crew, volunteers and traders working on your event](#message-the-crew-volunteers-and-traders-working-on-your-event)
- [Plan next year's event from your attendee feedback](#plan-next-years-event-from-your-attendee-feedback)
- [Read your event's email in one inbox](#read-your-events-email-in-one-inbox)
- [Run your event from its Today page](#run-your-event-from-its-today-page)
- [Send your event lists to your team on a schedule](#send-your-event-lists-to-your-team-on-a-schedule)
- [Take notes on your event calls with Fai](#take-notes-on-your-event-calls-with-fai)

### Ask attendees for feedback after your event

Slug `ask-attendees-for-feedback-after-your-event`. Guide: https://www.ticketfairy.com/guides/ask-attendees-for-feedback-after-your-event

Email everyone who checked in at your event a short survey the morning after it ends, in their own language and with their own link, and optionally ask ticket holders who did not come what stopped them. The standard survey already rates your stages, acts, sessions and traders, and you can change the questions and the send time before anything goes out.

For: Asking the people who came to your event what they thought.

What an agent can do: Fai sets up the standard survey, changes its questions and wording, schedules it, stops it before it sends, and closes or reopens it. She shows you each change and waits for your yes first, and she always asks before scheduling, because the survey emails your attendees.

Prompt for Fai: "Set up the feedback survey for <EVENT NAME> and schedule it for the morning after, and also ask the people who did not come"

#### Then: Close or reopen the survey

What an agent can do: Fai closes or reopens a survey when you ask, after you confirm.

Prompt for Fai: "Close the feedback survey for <EVENT NAME>"

### Balance your event team's workload

Slug `balance-your-event-teams-workload`. Guide: https://www.ticketfairy.com/guides/balance-your-event-teams-workload

See how many hours each person on your event team has day by day, from their tasks and their rota shifts. Spot anyone over the limit before the week of the event, and when Fai suggests it, move a task to the teammate with the most room in one step.

For: Spreading the work across your event team.

What an agent can do: Fai reads each person's task time and rota hours for the next 7 or 14 days, says who is over the daily limit and suggests which tasks to move. When you agree, ask her to move the task: she adds the new person, takes the first one off and waits for your yes first.

Prompt for Fai: "Who on the <EVENT NAME> team is over 8 hours a day in the next two weeks, and which tasks should move?"

### Choose how your event emails look

Slug `choose-how-your-event-emails-look`. Guide: https://www.ticketfairy.com/guides/choose-how-your-event-emails-look

Preview the emails your event sends to agents, suppliers and crew in your brand's logo and colour, and give one event its own logo or colour when it needs a different look.

For: Making the emails your event sends look like your brand.

What an agent can do: Fai tells you how your event's emails look and where each part comes from, and gives an event its own logo or main colour, or sets it back to your brand kit. She shows you the change and waits for your yes first.

Prompt for Fai: "Use our festival logo and the colour #1a73e8 for the emails <EVENT NAME> sends"

#### Then: Go back to the brand kit

What an agent can do: Fai sets an event's emails back to your brand kit when you ask, after you confirm.

Prompt for Fai: "Put the emails for <EVENT NAME> back on our brand kit"

### Choose what Fai does on your event

Slug `choose-what-fai-does-on-your-event`. Guide: https://www.ticketfairy.com/guides/choose-what-fai-does-on-your-event

See the work Fai does on her own for one event and the actions she can take when you ask, and turn off any of her work you do not want on that event.

For: Deciding how much of an event's work Fai does on her own.

What an agent can do: Fai lists what she does on the event and turns any of it off or back on for that event when you ask. She waits for your yes first. Only brand owners and admins can change it.

Prompt for Fai: "Stop reading catering riders on <EVENT NAME>"

### Compare your ticket sales with your last event

Slug `compare-your-ticket-sales-with-your-last-event`. Guide: https://www.ticketfairy.com/guides/compare-your-ticket-sales-with-your-last-event

See how your event is selling against your last edition at the same number of days before the start: tickets sold, share of capacity, last time's total and, after the event, no-shows and how fast people arrived. Ticket Fairy suggests which earlier event to compare with, and you can choose another or turn the comparison off.

For: Checking an on-sale against your last edition.

What an agent can do: Fai reads the comparison with your last edition: tickets sold against last time at the same point, share of capacity, last time's total, and no-shows and arrivals after the event. She also lists the earlier events you can compare with and changes the choice, or turns the comparison off, after you confirm.

Prompt for Fai: "How is <EVENT NAME> selling compared with last year at this point?"

#### Then: Compare with a different event

What an agent can do: Fai lists the earlier events you can compare with and changes the choice after you confirm.

Prompt for Fai: "Compare <EVENT NAME> with <EARLIER EVENT NAME> instead"

#### Then: Turn the comparison off

What an agent can do: Fai turns the comparison off for an event after you confirm.

Prompt for Fai: "Stop comparing <EVENT NAME> with an earlier event"

### Copy the setup of your last event into your next one

Slug `copy-the-setup-of-your-last-event-into-your-next-one`. Guide: https://www.ticketfairy.com/guides/copy-the-setup-of-your-last-event-into-your-next-one

Bring the stages, teams, shifts, passes, site map, kit list, hotel blocks, budget plan, forms and the rest of an earlier event's setup into a new event of the same brand. You see what each part adds before anything is copied, the dates move to the new event, and nothing the new event already has changes.

For: Starting a new edition from the setup of your last one.

What an agent can do: Fai lists the brand's events you can copy from, shows what each part would add, what the new event already has and what is left out, starts the copy of the parts you choose and tells you how it went. She shows you the parts first and waits for your yes before she copies anything.

Prompt for Fai: "Copy the stages, shifts, passes and budget plan from <LAST EVENT NAME> into <EVENT NAME>, and show me what each part adds first"

### Find any performer, stage or day on your event

Slug `find-any-performer-stage-or-day-on-your-event`. Guide: https://www.ticketfairy.com/guides/find-any-performer-stage-or-day-on-your-event

Search your whole event from any section of its Operations page, and open one page for a performer, a stage or a show day with their set times, advance, travel, hotel, crew and tasks together.

For: Finding everything about one act, one stage or one show day.

What an agent can do: Fai finds anything on the event by name and reads you the same performer, stage and day pages, so you can ask about an act, a stage or a show day without opening them. She only reads here and changes nothing.

Prompt for Fai: "What is happening on the Main Stage at <EVENT NAME> on Saturday, and what is still missing?"

### Keep the jobs behind your event moving

Slug `keep-your-event-tasks-on-track`. Guide: https://www.ticketfairy.com/guides/keep-your-event-tasks-on-track

Put every job your team has to finish before the event on one board, give each one an owner and a date, and see what is blocked before it becomes a problem.

For: Running the jobs your team has to finish before the doors open.

What an agent can do: Fai can list your event's tasks, add new ones, give them an owner and a date, and move them on. She shows each change and waits for your yes.

Command line:

- Show the event and its dates: `ticketfairy event get <EVENT_ID>`

CLI MCP tools that read: `select_event`, `get_event`.

Prompt for Fai: "Add a task to <EVENT NAME> to apply for the late licence, give it to <TEAMMATE NAME> and make it due on <DATE>"

#### Then: See the same work as a list, a calendar or a timeline

What an agent can do: Fai lists what is due, by date or by owner, and can move a task on when you ask.

Command line:

- Show the event and its dates: `ticketfairy event get <EVENT_ID>`

CLI MCP tools that read: `select_event`, `get_event`.

Prompt for Fai: "What is due on <EVENT NAME> this week, and who has it?"

### Message the crew, volunteers and traders working on your event

Slug `message-the-people-working-on-your-event`. Guide: https://www.ticketfairy.com/guides/message-the-people-working-on-your-event

Email or text the people working on your event in one go: a department, one day's rota, your volunteers, performers' teams, traders, press or sponsors. Start from a show-day template or let Fai draft it, check exactly who gets it before it goes, and see who it reached.

For: Telling the people working on your event what they need to know.

What an agent can do: Fai drafts a message in your brand's voice, counts who it will reach and sends it after you confirm the count and the channels. She never sends without your yes.

Command line:

- List the groups, statuses and channels this event can message: `ticketfairy event-os messages options <EVENT_ID>`
- Count who a message to every volunteer would reach by email: `ticketfairy event-os messages audience <EVENT_ID> --audience '{"groups":[{"source":"volunteers"}]}'`
- Have Fai draft the message from your words. Nothing is sent: `ticketfairy event-os messages draft <EVENT_ID> --request "Gates open 30 minutes early on Saturday"`
- Email every volunteer. This sends and asks you first. The count must match the one you checked: `ticketfairy event-os messages send <EVENT_ID> --audience '{"groups":[{"source":"volunteers"}]}' --subject "<SUBJECT>" --message "<MESSAGE>" --expected-count <COUNT>`
- List the messages sent and scheduled on the event: `ticketfairy event-os messages list <EVENT_ID>`

CLI MCP tools that read: `get_event_messages`, `count_event_message_audience`.

CLI MCP tools that make changes (not available with `--read-only`): `draft_event_message`, `send_event_message`.

Prompt for Fai: "Email Saturday's stewards and bar volunteers on <EVENT NAME> that the gates open 30 minutes early, and show me who gets it before you send"

#### Then: Send a message again to the people it missed

What an agent can do: Send a message again from its panel in the dashboard.

#### Then: Cancel a scheduled message

What an agent can do: Cancel a scheduled message from its panel in the dashboard.

#### Then: See every message one person was sent

What an agent can do: Fai lists the messages sent on the event and who each one reached.

Prompt for Fai: "Which messages did we send about <EVENT NAME> today, and who did they not reach?"

### Plan next year's event from your attendee feedback

Slug `plan-next-year-from-your-attendee-feedback`. Guide: https://www.ticketfairy.com/guides/plan-next-year-from-your-attendee-feedback

Read your event's feedback as the answers come in: how many people answered, your Net Promoter Score beside the last edition's, each stage, act and trader's rating, and the themes Fai finds in their comments, with real quotes. Add the top things to improve as tasks on next year's event in one step.

For: Turning what your attendees said into next year's plan.

What an agent can do: Fai reads you the response rate, Net Promoter Score, each question's results and the themes in the comments, and reads the comments again when you ask. You add the tasks for next time yourself, from the dashboard or by approving the suggestion on Today.

Prompt for Fai: "What did people think of <EVENT NAME>, and what should we fix next year?"

#### Then: Download the answers

What an agent can do: You download the answers in the dashboard. Fai reads you the results and themes instead.

Prompt for Fai: "Summarise the feedback answers for <EVENT NAME> from people who would not recommend us"

### Read your event's email in one inbox

Slug `read-your-event-email-in-one-inbox`. Guide: https://www.ticketfairy.com/guides/read-your-event-email-in-one-inbox

See every email conversation about one event together, with Fai's summary of each, turn the follow-ups she finds into tasks, reply from your own email app and keep spam out.

For: Keeping up with the email about one event.

What an agent can do: Fai searches the conversations in your connected mailboxes, reads one in full and lists the follow-ups she found, so you can ask about the event's email without opening it.

Prompt for Fai: "What has come in by email about <EVENT NAME> this week, and what do we still need to do about it?"

#### Then: Connect your first mailbox

What an agent can do: Fai tells you which mailboxes your brand has connected and whether each one is working.

Prompt for Fai: "Which mailboxes does Fai read for <EVENT NAME>?"

### Run your event from its Today page

Slug `run-your-event-from-its-today-page`. Guide: https://www.ticketfairy.com/guides/run-your-event-from-its-today-page

Set your event up with Fai on your first visit, then see what needs you each day, approve, change or turn down what Fai suggests, and open any part of your event from one page.

For: Running an event day to day with Fai drafting the routine work.

What an agent can do: Fai reads the same Today page for you, lists what she suggests, and approves, changes, reminds you later or turns down a suggestion when you ask. She can also change what she helps with on the event, add or remove a section for your team and pin one for you. She shows you what she is about to send, add or change and waits for your yes first.

Prompt for Fai: "What does <EVENT NAME> need from me today? Show me your suggestions before you approve any of them"

#### Then: Add a section for your team or pin one for yourself

What an agent can do: Fai adds or removes a section for your team, pins one for you and changes what she helps with on the event, after you confirm.

Prompt for Fai: "Add the rota and incidents to the section list for <EVENT NAME> and pin Show day for me"

#### Then: Change the event type

What an agent can do: Fai reads the event type and changes it when you ask, after you confirm.

Prompt for Fai: "Make <EVENT NAME> a festival and a conference"

### Send your event lists to your team on a schedule

Slug `send-your-event-lists-to-your-team-on-a-schedule`. Guide: https://www.ticketfairy.com/guides/send-your-event-lists-to-your-team-on-a-schedule

Email your rota, run of show, advancing status, rooming list or pickups to the right people on your event team every day or every week, as a file they download after signing in. Every file and every download is recorded, and you can make a file now whenever you need one.

For: Keeping your team up to date with the latest lists.

What an agent can do: Fai reads your scheduled exports, their latest files and who can receive each list, schedules a list every day or week, changes, pauses, turns back on or stops a schedule, and makes a file now. She shows you each change and waits for your yes first.

Prompt for Fai: "Email the rota for <EVENT NAME> to me and Sam every Monday at 9am"

#### Then: Pause or stop a schedule

What an agent can do: Fai pauses, turns back on or stops a scheduled export when you ask, after you confirm.

Prompt for Fai: "Stop sending the rota for <EVENT NAME> every week"

#### Then: Make a file now

What an agent can do: Fai makes a file of the list now when you ask, after you confirm, and you download it in the dashboard.

Prompt for Fai: "Make a file of the run of show for <EVENT NAME> now"

### Take notes on your event calls with Fai

Slug `take-notes-on-your-event-calls-with-fai`. Guide: https://www.ticketfairy.com/guides/take-notes-on-your-event-calls-with-fai

Send Fai's notetaker to a Zoom, Google Meet or Microsoft Teams call about your event and get a summary, the follow-ups agreed and notes you can share, filed under the event.

For: Keeping notes on the calls about one event.

What an agent can do: Fai sends the notetaker to a call link you give her, tells you where it is up to, and finds and reads the notes from earlier calls. She asks before the notetaker joins a call.

Prompt for Fai: "Send the notetaker to this call for <EVENT NAME>: <CALL LINK>"

#### Then: Call off the notetaker

What an agent can do: Fai tells you where the notetaker is up to, and calls it off when you ask. She waits for your yes first.

Prompt for Fai: "Call off the notetaker for the security briefing on <EVENT NAME>"

## More

- All guides: https://www.ticketfairy.com/guides
- Guides MCP server: https://www.ticketfairy.com/docs/mcp (tools `search_guides` and `get_guide`)
- CLI reference: https://www.npmjs.com/package/ticketfairy
- Developer documentation: https://www.ticketfairy.com/developers
- Support: support@ticketfairy.com
