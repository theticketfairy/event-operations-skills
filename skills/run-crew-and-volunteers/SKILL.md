---
name: run-crew-and-volunteers
description: "Build rotas, recruit volunteers, collect certificates, run inductions, plan meals and approve hours in Ticket Fairy. Use when an organiser staffs an event."
---

# Run crew and volunteers

This skill covers rotas, shifts, volunteers, certificates, inductions, meals and hours on Ticket Fairy. It lists the 15 published guides for this area and what an agent can do for each one.

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

- [Add everyone who sends your event form to your volunteers, traders or crew](#add-everyone-who-sends-your-event-form-to-your-volunteers-traders-or-crew)
- [Add shifts to your event rota from a spreadsheet](#add-shifts-to-your-event-rota-from-a-spreadsheet)
- [Approve the hours your event crew and volunteers worked](#approve-the-hours-your-event-crew-and-volunteers-worked)
- [Build your event rota and check staff in](#build-your-event-rota-and-check-staff-in)
- [Charge outside teams for the crew meals they eat at your event](#charge-outside-teams-for-the-crew-meals-they-eat-at-your-event)
- [Collect crew certificates and licences before they work an event shift](#collect-crew-certificates-and-licences-before-they-work-an-event-shift)
- [Find the crew and volunteers who work your events](#find-the-crew-and-volunteers-who-work-your-events)
- [Give crew meals at your event meal desk](#give-crew-meals-at-your-event-meal-desk)
- [Give your event crew one page for all their shifts](#give-your-event-crew-one-page-for-all-their-shifts)
- [Give your event volunteers their own page and track their hours](#give-your-event-volunteers-their-own-page-and-track-their-hours)
- [Let department leads approve their team's hours at your event](#let-department-leads-approve-their-teams-hours-at-your-event)
- [Offer open shifts on your event rota to crew and volunteers](#offer-open-shifts-on-your-event-rota-to-crew-and-volunteers)
- [Plan crew meal times and food needs for your event](#plan-crew-meal-times-and-food-needs-for-your-event)
- [Recruit volunteers for your event](#recruit-volunteers-for-your-event)
- [Run a safety induction for everyone who works your event](#run-a-safety-induction-for-everyone-who-works-your-event)

### Add everyone who sends your event form to your volunteers, traders or crew

Slug `add-form-applicants-to-your-event-teams`. Guide: https://www.ticketfairy.com/guides/add-form-applicants-to-your-event-teams

Connect a form on your event to your volunteers, traders, press, crew or an act's contacts, match each detail to a question, and every person who sends the form is added to that list in the Event Operating System, with their answers kept on the form.

For: Getting form applicants into the lists your event team works from.

What an agent can do: Fai sets where a form's answers go when she creates or updates the form, and adds one applicant to your Event Operating System list when you ask. She shows you the change and waits for your yes.

Prompt for Fai: "Make the trader form on <EVENT NAME> add every applicant to our traders, and add the applicants who already sent it"

#### Then: Add people who applied before you connected the form

What an agent can do: Fai adds the applicants who sent the form before you connected it, after you confirm.

Prompt for Fai: "Add everyone who already sent the trader form on <EVENT NAME> to our traders"

### Add shifts to your event rota from a spreadsheet

Slug `add-shifts-to-your-event-rota-from-a-spreadsheet`. Guide: https://www.ticketfairy.com/guides/add-shifts-to-your-event-rota-from-a-spreadsheet

Drop the event rota spreadsheet your team already keeps, in CSV or Excel, and Fai works out which column has the day, the times, the department and the role. You check every row and fix any column before up to 500 shifts are added to your rota in one go.

For: Bringing a rota you planned in a spreadsheet into your event.

What an agent can do: Fai reads rows you paste into the chat as a spreadsheet, shows you each shift and its problems, and adds the ready rows after you confirm. For an Excel file, use the dialog in Shifts.

Prompt for Fai: "Add these shifts to the rota at <EVENT NAME>: <PASTED ROWS WITH A HEADING ROW>"

### Approve the hours your event crew and volunteers worked

Slug `approve-the-hours-your-crew-and-volunteers-worked`. Guide: https://www.ticketfairy.com/guides/approve-the-hours-your-crew-and-volunteers-worked

Approve each person's hours at your event from the times they were checked in and out of their shifts. Fai checks every line first, so you approve the lines with nothing odd in one go, fix the rest with a reason, and check an agency's invoice against the hours its people worked.

For: Approving worked hours for your crew, agency staff and volunteers.

What an agent can do: Fai reads the hours lines of a day with what she noticed on each, and approves the lines you choose or every line with nothing odd. She tells you how many lines she will approve and waits for your yes first.

Prompt for Fai: "Approve the hours at <EVENT NAME> on Saturday that have nothing odd in them"

#### Then: Check an agency's invoice

What an agent can do: Fai reads the hours by outside team, and sets a shift's outside team and cost per hour after you confirm.

Prompt for Fai: "How many hours did SecureCo's stewards work at <EVENT NAME>, and how many are approved?"

#### Then: Download the hours

What an agent can do: Fai starts the same file of the hours lines you choose after you confirm. You download it from the Hours view, where it waits for 7 days and each download is recorded.

Prompt for Fai: "Give me the approved hours at <EVENT NAME> for SecureCo as a file"

#### Then: Change hours that are already approved

What an agent can do: Fai changes a line's hours with the reason you give, after you confirm, and the line goes back for approval.

Prompt for Fai: "Take 30 minutes off Ana Lima's bar shift on Saturday at <EVENT NAME> for an unpaid break"

### Build your event rota and check staff in

Slug `build-your-event-rota-and-check-staff-in`. Guide: https://www.ticketfairy.com/guides/build-your-event-rota-and-check-staff-in

Plan the shifts each team needs across your event, let Fai suggest shifts and the people to fill them, send everyone their own shift times, and check your crew and volunteers in and out at the door on the day.

For: Staffing every team and hour of your event.

What an agent can do: Fai reads the rota, its coverage and clashes, suggests shifts from your expected crowd and people for open places, adds and changes shifts, adds people, sets the rota rules, emails people their own shifts and checks people in or out. She shows you each change and waits for your yes first; only sending shifts emails anyone. Your own AI assistant can read the shifts, add a shift, put someone on one and check people in or out over the MCP server, where each change waits for your approval in your MCP client.

Command line:

- List the shifts: `ticketfairy event-os rota shifts <EVENT_ID>`
- Add a shift, with its start and end as YYYY-MM-DD HH:MM in the event's local time and the number of people it needs: `ticketfairy event-os rota add-shift <EVENT_ID> --start "<START TIME>" --end "<END TIME>" --headcount <PEOPLE> --department "<TEAM>"`
- Put a crew member on a shift: `ticketfairy event-os rota assign <EVENT_ID> <SHIFT_ID> --crew <CREW_ID>`
- Check a person in for their shift: `ticketfairy event-os rota check-in <EVENT_ID> <ASSIGNMENT_ID>`

CLI MCP tools that read: `select_event`, `get_event_rota`.

CLI MCP tools that make changes (not available with `--read-only`): `manage_event_rota`, `check_in_shift_person`.

Prompt for Fai: "Which shifts on Saturday at <EVENT NAME> still need people? Suggest volunteers to fill them"

#### Then: Cancel a shift

What an agent can do: Fai cancels a shift or brings one back when you ask, after you confirm.

Prompt for Fai: "Cancel the Sunday pit barrier shift at <EVENT NAME>"

#### Then: Take someone off a shift

What an agent can do: Fai takes someone off a shift when you ask, after you confirm.

Prompt for Fai: "Take Cai Jones off the Saturday bar shift at <EVENT NAME>"

### Charge outside teams for the crew meals they eat at your event

Slug `charge-outside-teams-for-their-crew-meals`. Guide: https://www.ticketfairy.com/guides/charge-outside-teams-for-their-crew-meals

Charge suppliers, contractors and other outside teams for the meals their people ate at your event's crew catering. We count the meals from the meal desk, you choose the days, the price per meal and the currency, and the team gets an invoice with a payment page.

For: Recovering the cost of meals your event gives to outside teams.

What an agent can do: Fai lists the meals each outside team ate and what is charged, charges a team for chosen days at your price, tries a failed invoice again and emails an invoice to the team. She waits for your yes before each charge or email, and only an owner or admin can approve them.

Prompt for Fai: "Charge Northern PA Hire for the crew meals they ate at <EVENT NAME> on Friday and Saturday, at 8.50 GBP a meal"

### Collect crew certificates and licences before they work an event shift

Slug `collect-crew-certificates-before-they-work-a-shift`. Guide: https://www.ticketfairy.com/guides/collect-crew-certificates-before-they-work-a-shift

Ask the crew and volunteers on your event's shifts for the certificates and licences the work needs, such as a first aid certificate for medics or a food hygiene certificate for the bar. Each person adds a document once from their My shifts page, it counts at every event of your brand until it expires, and nobody goes on a shift without it unless you give a reason.

For: Making sure everyone on your event's shifts holds the certificates the work needs.

What an agent can do: Fai asks for a document, tells you who on the shifts lacks one or has one to check, marks a document as checked, sends one back with your reason and records a document someone showed you. She waits for your yes before each change. You open files in the dashboard.

Prompt for Fai: "Ask everyone on the medic shifts at <EVENT NAME> for a first aid certificate, and tell me who still needs one"

#### Then: Add a document a person gave you

What an agent can do: Fai records a document you saw, with its expiry date, after you confirm. Add a file in the dashboard.

Prompt for Fai: "I have seen Priya Shah's first aid certificate for <EVENT NAME>, it expires in March 2028, record it"

#### Then: Put someone on a shift without the document

What an agent can do: Fai tells you who lacks a document when she adds people to a shift, and adds them anyway only with the reason you give, after you confirm.

Prompt for Fai: "Put Priya Shah on the Saturday medic shift at <EVENT NAME> anyway, her new certificate is on its way"

#### Then: Stop asking for a document

What an agent can do: Fai stops asking for a document when you ask, after you confirm.

Prompt for Fai: "Stop asking for the food hygiene certificate at <EVENT NAME>"

### Find the crew and volunteers who work your events

Slug `find-the-crew-and-volunteers-who-work-your-events`. Guide: https://www.ticketfairy.com/guides/find-the-crew-and-volunteers-who-work-your-events

Search everyone who has worked or volunteered at any of your events in one People list, and see how many shifts each person worked and whether they turned up. Add their skills and confirm their age for shifts that need one. Fai suggests skills from the shifts they worked, and nobody is rated.

For: Rebooking the people who have worked your events before.

What an agent can do: Fai searches your brand's People, reads you a person's events, shift history, skills and age, and adds skills or confirms an age after you confirm.

Prompt for Fai: "Who has worked the bar at our events and always turned up?"

### Give crew meals at your event meal desk

Slug `give-crew-meals-at-your-meal-desk`. Guide: https://www.ticketfairy.com/guides/give-crew-meals-at-your-meal-desk

Run the crew catering counter at your event from each person's pass: scan it, see the meals left today and their dietary needs, and give a meal against their allowance. To give an extra meal, you enter a reason and we keep your name with it. The kitchen sees how many meals to expect each day, with the dietary needs counted.

For: Serving crew and volunteer meals against each person's allowance.

What an agent can do: Fai finds a pass at the meal desk, records a meal or an extra meal with its reason, undoes the last meal, and reads you the kitchen forecast and who ate. She shows you the pass and waits for your yes before she records a meal.

Prompt for Fai: "How many meals should the kitchen expect at <EVENT NAME> tomorrow, and how many are vegetarian or gluten-free?"

#### Then: Give a whole team's meals to one collector

What an agent can do: Fai gives a team's meals to a named collector when you ask, after you confirm, and tells you who was skipped.

Prompt for Fai: "Jo from Northern PA Hire is collecting lunch for their crew at <EVENT NAME>"

#### Then: Give an act's drinks

What an agent can do: Fai gives or undoes a drink for a pass from an act's travel party, after you confirm, and gives one beyond the allowance only with your reason.

Prompt for Fai: "Give one of Nova Lights' crew a drink at <EVENT NAME>, pass code TF-7702-1188"

#### Then: Undo a meal

What an agent can do: Fai undoes a person's last meal today when you ask, after you confirm.

Prompt for Fai: "Undo the meal we gave Ana Ruiz a minute ago at <EVENT NAME>, it was scanned twice"

#### Then: See who ate

What an agent can do: Fai reads you the meals given on a day, the extra meals and who gave them.

Prompt for Fai: "Who was given an extra meal at <EVENT NAME> today, and by whom?"

### Give your event crew one page for all their shifts

Slug `give-your-crew-one-page-for-all-their-shifts`. Guide: https://www.ticketfairy.com/guides/give-your-crew-one-page-for-all-their-shifts

Email each crew member or volunteer a private My shifts link. On it they see their shifts at every one of your events, accept the shifts you offer them, say they're still coming, tell you the days they can work and add their shifts to their calendar. Their documents, safety induction and food needs are on the same page, and nobody needs an account.

For: Keeping crew and volunteers up to date on their shifts.

What an agent can do: Fai emails a person their My shifts link or turns their links off when you ask, after you confirm.

Prompt for Fai: "Email Ama Owusu her My shifts link"

#### Then: Turn off their links

What an agent can do: Fai turns off a person's My shifts links when you ask, after you confirm.

Prompt for Fai: "Turn off Leah Grant's My shifts links, she has left the team"

### Give your event volunteers their own page and track their hours

Slug `give-volunteers-their-own-page-and-track-hours`. Guide: https://www.ticketfairy.com/guides/give-volunteers-their-own-page-and-track-hours

Send each volunteer you accepted for your event a private page where they pick shifts, ask to swap or drop one, read their day sheet and the induction and add documents. Then see hours given against hours worked, give the rewards people earned and download the list, with every download recorded.

For: Looking after accepted volunteers from their first shift to their reward.

What an agent can do: Fai sends volunteers their page links, answers shift requests, reads hours given and worked and gives the rewards people earned. She asks you before anything is sent, and only an owner or admin can approve rewards.

Command line:

- List each volunteer's hours given and worked: `ticketfairy event-os volunteers list <EVENT_ID> --hours`

Prompt for Fai: "Send every accepted volunteer on <EVENT NAME> their page link, and tell me who has earned the free weekend ticket"

#### Then: Download the volunteer list

What an agent can do: Download the list from the Volunteers section in the dashboard, where the download is recorded with your name.

#### Then: Turn off a volunteer's link

What an agent can do: Turn a volunteer's link off or make a new one from their application in the dashboard.

### Let department leads approve their team's hours at your event

Slug `let-department-leads-approve-their-teams-hours`. Guide: https://www.ticketfairy.com/guides/let-department-leads-approve-their-teams-hours

Give the lead of each on-site department at your event the job of approving their own team's hours. Leads approve and correct the hours of their department's shifts from their My shifts page, with Fai's checks and no sign-in, and never see costs or their own hours.

For: Sharing hours approval with the leads of your on-site teams.

What an agent can do: Fai adds a person to a department and makes them its lead, after you confirm. The lead approves their team's hours on their own My shifts page.

Prompt for Fai: "Make Dan Price the lead of the Security department at <EVENT NAME>, his email is dan@secureco.example"

### Offer open shifts on your event rota to crew and volunteers

Slug `offer-open-shifts-to-your-crew-and-volunteers`. Guide: https://www.ticketfairy.com/guides/offer-open-shifts-to-your-crew-and-volunteers

Fill the gaps in your event rota by offering a shift to the crew and volunteers who fit it. Fai picks people who are free, rested, old enough and have the skill across all your events, each person gets an email with their own link, and the first to accept gets the place.

For: Filling the open places on your event rota.

What an agent can do: Fai lists the shifts that need people, finds who fits each one across your events, offers a shift to the people you choose and takes an offer back. She shows you who she will email and waits for your yes before anything is sent.

Prompt for Fai: "The Saturday bar shift at <EVENT NAME> still needs 2 people, offer it to whoever fits"

#### Then: Take back an offer

What an agent can do: Fai takes back an offer that is still waiting when you ask, after you confirm.

Prompt for Fai: "Take back the gate shift offer to Tomás Reyes at <EVENT NAME>"

#### Then: Ask who is still coming

What an agent can do: Fai asks everyone on the next day's shifts whether they are still coming, after you confirm, and reads you the answers.

Prompt for Fai: "Ask everyone on tomorrow's shifts at <EVENT NAME> if they are still coming"

#### Then: Find cover for someone who has not arrived

What an agent can do: Fai marks someone as not arrived and offers their place to people who fit, after you confirm each change.

Prompt for Fai: "Cai Jones hasn't turned up for his steward shift at <EVENT NAME>, mark him as not arrived and find cover"

#### Then: Let Fai send offers and ask by herself

What an agent can do: Fai turns either switch on or off in the rota rules when you ask, after you confirm.

Prompt for Fai: "At <EVENT NAME>, send the first shift offers yourself and ask people the day before if they are still coming"

### Plan crew meal times and food needs for your event

Slug `plan-crew-meal-times-and-food-needs-for-your-event`. Guide: https://www.ticketfairy.com/guides/plan-crew-meal-times-and-food-needs-for-your-event

Set when your event's crew catering serves each day, with meal times suggested from the shifts, and see how many people are on shift at each meal and what food needs they have. Crew give their food needs once, and the kitchen follows the day's counts on its own link, with no names on it.

For: Telling your crew kitchen what to cook and when.

What an agent can do: Fai reads the meal times and the kitchen count, suggests meal times from the shifts, adds, changes or removes a meal time, and records a person's food needs. She waits for your yes before each change.

Prompt for Fai: "Add the meal times the shifts suggest for every day of <EVENT NAME>, and tell me how many vegan meals the kitchen needs for Saturday lunch"

#### Then: Change or remove a meal time

What an agent can do: Fai changes or removes a meal time when you ask, after you confirm.

Prompt for Fai: "Move Sunday lunch at <EVENT NAME> to 12:30 to 14:30"

#### Then: Record someone's food needs at the desk

What an agent can do: Fai records a person's food needs when you tell her them, after you confirm.

Prompt for Fai: "Ben Ode at <EVENT NAME> is vegan with a nut allergy, record his food needs"

### Recruit volunteers for your event

Slug `recruit-volunteers-for-your-event`. Guide: https://www.ticketfairy.com/guides/recruit-volunteers-for-your-event

Open a volunteer application form for your event that people fill in on their phone, and let Fai read each application against the roles you need. Accept, waitlist or decline people in batches with one email each, and invite back last year's volunteers with their answers already filled in.

For: Recruiting and choosing the volunteers who work your event.

What an agent can do: Fai sets up the volunteer form, lists applications with her reading of each, accepts, waitlists, declines or shortlists people, and invites back last year's volunteers. She shows you who gets which email and waits for your yes.

Command line:

- List the applications still to decide that Fai rates a strong fit, with each person's id and version: `ticketfairy event-os volunteers list <EVENT_ID> --status undecided --strong-fit`
- Accept people and email them the decision. Use id:version pairs from the list. This asks you first unless you add --force: `ticketfairy event-os volunteers decide <EVENT_ID> --decision accept --volunteers <VOLUNTEER_ID>:<VERSION>`

CLI MCP tools that read: `get_volunteer_applications`.

CLI MCP tools that make changes (not available with `--read-only`): `decide_volunteer_applications`.

Prompt for Fai: "Show me the volunteer applications for <EVENT NAME> that are a strong fit for the bar, and accept them with the usual email"

#### Then: Invite last year's volunteers back

What an agent can do: Fai suggests who to invite back from an earlier event, from the shifts they worked, and sends the invitations after you confirm.

Prompt for Fai: "Invite back the volunteers from last year's <EVENT NAME> who worked every shift"

### Run a safety induction for everyone who works your event

Slug `run-a-safety-induction-for-everyone-who-works-your-event`. Guide: https://www.ticketfairy.com/guides/run-a-safety-induction-for-everyone-who-works-your-event

Put the safety briefing your crew, volunteers and suppliers must read before they work your event in one place, let Fai draft a short test from it, and have the hand-out desk check that each person has done it before they collect their pass. You see who has done it and mark it done for anyone you briefed in person.

For: Briefing everyone who works on your event site on safety.

What an agent can do: Fai sets up or changes the induction, drafts the short test from your briefing, makes it live or takes it down, tells you who has not done it and marks it done for someone you briefed. She waits for your yes before each change.

Prompt for Fai: "Draft a short safety test from the induction at <EVENT NAME> and show me the questions"

#### Then: Take the test down

What an agent can do: Fai takes the test down or removes it when you ask, after you confirm.

Prompt for Fai: "Take the safety test down at <EVENT NAME>, I need to change a question"

## More

- All guides: https://www.ticketfairy.com/guides
- Guides MCP server: https://www.ticketfairy.com/docs/mcp (tools `search_guides` and `get_guide`)
- CLI reference: https://www.npmjs.com/package/ticketfairy
- Developer documentation: https://www.ticketfairy.com/developers
- Support: support@ticketfairy.com
