---
name: run-door-check-in
description: "Run Ticket Fairy check-in at the door: scanning, entry rules, live check-in reports and wristbands. Use when an organiser prepares or runs entry to an event."
---

# Run door check-in

This skill covers scanning, entry rules, live check-in reports and wristbands on Ticket Fairy. It lists the 10 published guides for this area and what an agent can do for each one.

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

- [Assign wristbands to each ticket type](#assign-wristbands-to-each-ticket-type)
- [Check in attendees and print name badges at your event registration desk](#check-in-attendees-and-print-name-badges-at-your-event-registration-desk)
- [Issue reusable event passes to crew and artists](#issue-reusable-event-passes-to-crew-and-artists)
- [Let ticket holders pick the conference sessions they attend](#let-ticket-holders-pick-the-conference-sessions-they-attend)
- [Scan delegates into event sessions at the door and see who came](#scan-delegates-into-event-sessions-at-the-door-and-see-who-came)
- [Scan tickets at the door](#scan-tickets-at-the-door)
- [See why tickets and passes were refused at the door](#see-why-tickets-and-passes-were-refused-at-the-door)
- [Set ticket entry and repeat-scan rules](#set-ticket-entry-and-repeat-scan-rules)
- [Set up a self-service check-in kiosk for your event](#set-up-a-self-service-check-in-kiosk-for-your-event)
- [Track your event check-ins by hour](#track-your-event-check-ins-by-hour)

### Assign wristbands to each ticket type

Slug `issue-wristbands-by-ticket-type`. Guide: https://www.ticketfairy.com/guides/issue-wristbands-by-ticket-type

Match each ticket type and add-on to the wristband or badge its holder gets, so the scanning app shows your door team the right band as each ticket is scanned.

For: Handing out the right wristband or badge for every ticket at the gate.

What an agent can do: no agent route is recorded for this guide. Send the organiser the guide link and walk them through the steps in the dashboard.

#### Then: Change which tickets get a band

What an agent can do: Fai, the MCP server and the command line can't manage credentials, so change a credential on the Credentials page.

#### Then: Stop handing out a band for now

What an agent can do: Fai, the MCP server and the command line can't manage credentials, so deactivate or activate a credential on the Credentials page.

#### Then: Remove a band

What an agent can do: Fai, the MCP server and the command line can't manage credentials, so delete a credential on the Credentials page.

### Check in attendees and print name badges at your event registration desk

Slug `check-in-attendees-and-print-badges-at-registration`. Guide: https://www.ticketfairy.com/guides/check-in-attendees-and-print-badges-at-registration

Run the registration desk at your conference, trade show or festival from any browser: scan a ticket or find the attendee by name, email or order number, check them in and print their name badge on an A6 or card printer. To print a second badge, you give a reason. Walk-ups buy a ticket from a QR code, and you can share a desk link so volunteers work the desk from their own laptop.

For: Checking attendees in and printing their name badges at registration.

What an agent can do: Fai finds a ticket holder, reads the desk's counts and a badge's print history, checks a ticket in and changes the badge setup, after you confirm. You print badges in the browser at the desk, so Fai tells you where to print it.

Prompt for Fai: "How many people have checked in at registration for <EVENT NAME> so far, and how many badges were printed again?"

#### Then: Print a second badge

What an agent can do: Print a second badge at the registration desk, where you enter the reason. Fai can read you a person's badge history first.

#### Then: Let volunteers work the desk from a link

What an agent can do: Fai makes a registration desk link after you confirm. Open Desks and links and select **Get a new link** to see its address.

Prompt for Fai: "Make a registration desk link called Registration desk 2 for <EVENT NAME>"

#### Then: Help walk-ups without a ticket

What an agent can do: Show walk-ups the QR code in the Registration view of Desks, then check them in with their new ticket.

### Issue reusable event passes to crew and artists

Slug `issue-entry-passes-to-your-crew`. Guide: https://www.ticketfairy.com/guides/issue-entry-passes-to-your-crew

Give crew and artists named multi-entry passes. Your door team can scan them in the same app they use for tickets.

For: Letting your team in and out of an event all day.

What an agent can do: Fai can create the pass types, issue the passes and send them out. She asks you to approve each action first. You can also manage the passes in the dashboard. Review every recipient before sending, because you can't recall an email once it's sent.

Prompt for Fai: "Create a Crew Member pass type for this brand with twelve entries per event, issue one to every person in the list I paste next, and show me the names before sending anything"

#### Then: Update a pass

What an agent can do: Fai can find the pass and update its holder, type, uses or notes after showing you the current details. MCP and the CLI do not manage entry passes.

Prompt for Fai: "Find the entry pass for <PERSON> on <EVENT OR BRAND>, show me its type, email address, uses and notes, then ask what I want to change"

#### Then: Remove a pass

What an agent can do: Fai can show the pass holder, type and remaining uses, then remove it after you approve the change. MCP and the CLI do not manage entry passes.

Prompt for Fai: "Find the entry pass for <PERSON> on <EVENT OR BRAND>, show me its type and remaining uses, then ask before removing the pass"

### Let ticket holders pick the conference sessions they attend

Slug `let-ticket-holders-pick-the-sessions-they-attend`. Guide: https://www.ticketfairy.com/guides/let-ticket-holders-pick-the-sessions-they-attend

Turn the talks and workshops on your agenda into sessions ticket holders pick on their order page, with a place for each person, a waiting list when a room is full and a warning before two picks clash. Your team can add anyone to a session or give a place back.

For: Letting delegates choose their talks and workshops.

What an agent can do: Fai lists the sessions and the agenda items people cannot pick yet, makes a session from an agenda item or from scratch, and opens it for picking. She shows you each change and waits for your yes first.

Prompt for Fai: "Let ticket holders at <EVENT NAME> pick the sponsor deck workshop, with 40 places and a waiting list"

#### Then: Add a session that is not on your agenda

What an agent can do: Fai adds a session with the details you give and can open it for picking, after you confirm.

Prompt for Fai: "Add a 45 minute pricing clinic at 2pm on day two of <EVENT NAME> in Room B for 25 people"

#### Then: Add a ticket holder to a session or give their place back

What an agent can do: Fai looks up a ticket holder's picks by ticket code or email, adds them to a session and gives a place back, after you confirm each change.

Prompt for Fai: "Add the delegate with ticket code TF8841QX to the sponsor deck workshop at <EVENT NAME>"

#### Then: Change a session

What an agent can do: Fai changes a session's title, track, room, description or waiting list, and its time and places while nobody has picked it, after you confirm.

Prompt for Fai: "Move the design panel at <EVENT NAME> to the Design track"

#### Then: Finish or cancel a session

What an agent can do: Fai marks a session as finished or cancels it, after you confirm.

Prompt for Fai: "Cancel the Friday morning yoga session at <EVENT NAME>"

### Scan delegates into event sessions at the door and see who came

Slug `scan-ticket-holders-into-sessions-and-see-who-came`. Guide: https://www.ticketfairy.com/guides/scan-ticket-holders-into-sessions-and-see-who-came

Scan tickets at the door of each conference session so only the people who picked it go in, from the dashboard or a door link on a volunteer's phone. The attendance report then shows who came, who did not, who was turned away and your most popular sessions.

For: Running the doors of your conference sessions.

What an agent can do: Fai scans a ticket into a session for you, after you confirm, and tells you whether to let the person in and why not. She also makes a door link for volunteers, without showing its address.

Prompt for Fai: "Scan ticket TF8841QX into the Hiring your first designer talk at <EVENT NAME>"

#### Then: Give door staff a door link

What an agent can do: Fai makes a session door link with the name you give, after you confirm. She never shows the link's address, so copy it from the dashboard.

Prompt for Fai: "Make a door link for Room 2 phone for the sponsor deck workshop at <EVENT NAME>"

### Scan tickets at the door

Slug `scan-tickets-at-the-door`. Guide: https://www.ticketfairy.com/guides/scan-tickets-at-the-door

Get your door team on the scanning app with the right login, set the re-entry rules before the day, and watch arrivals and individual tickets while the doors are open.

For: Getting a crowd through the door on event night.

What an agent can do: Fai reads how the doors are going and can find one person's ticket while you are standing at the entrance. Your door team admits people with the app.

Prompt for Fai: "For <EVENT NAME>, how many have checked in so far, and has <ATTENDEE NAME> arrived"

#### Then: Undo a scan

What an agent can do: Fai reads the ticket so you can see whether it went in and when. You undo the scan yourself on the page.

Prompt for Fai: "For <EVENT NAME>, has <ATTENDEE NAME> checked in, and at what time"

#### Then: Admit an attendee when a phone stops working

What an agent can do: Fai finds the order and the ticket, so you can see whether the attendee has gone in. You check them in with the app or at the registration desk.

Prompt for Fai: "Find the order for <BUYER EMAIL ADDRESS> on <EVENT NAME> and show me its tickets and their states"

### See why tickets and passes were refused at the door

Slug `see-why-tickets-and-passes-were-refused-at-the-door`. Guide: https://www.ticketfairy.com/guides/see-why-tickets-and-passes-were-refused-at-the-door

See how many scans your door scanners and staff gates refused, by reason, entrance, hour and ticket or pass type, on the Check-in page. Spot shared screenshots of tickets and doors turning people away, then open each refused scan to see who it was.

For: Understanding the scans your door and staff gates turned away.

What an agent can do: Fai reads the refused scans by reason, entrance, hour and type for the whole event or one day, and lists the refused scans for one reason.

Prompt for Fai: "Why were people refused at the doors of <EVENT NAME> on Saturday, and at which entrance?"

### Set ticket entry and repeat-scan rules

Slug `set-ticket-entry-and-repeat-scan-rules`. Guide: https://www.ticketfairy.com/guides/set-ticket-entry-and-repeat-scan-rules

Control how often each ticket can admit its holder, from one visit per event to a set number of scans each hour or day.

For: Setting re-entry limits for multi-day events, passes and tickets with repeat access.

What an agent can do: Fai can set or clear a ticket type's repeat-scan rules, explain the hourly or daily limit and show the proposed change before asking you to approve it.

Prompt for Fai: "For <EVENT NAME>, set the repeat-scan rules for <TICKET TYPE NAME>. Allow one scan per day and two scans per hour, show me the change, and wait for my approval"

### Set up a self-service check-in kiosk for your event

Slug `set-up-a-self-service-check-in-kiosk-for-your-event`. Guide: https://www.ticketfairy.com/guides/set-up-a-self-service-check-in-kiosk-for-your-event

Put a tablet and a badge printer by your event entrance so attendees check themselves in and print their own name badge. They scan the ticket from their email, or confirm their email address with a six-digit code, and each ticket gets one badge from the kiosk.

For: Letting attendees check in and print their own badges at your event.

What an agent can do: Fai makes, changes or stops a kiosk link after you confirm, and turns finding a ticket by email on or off in the badge setup. Open Desks and links and select **Get a new link** to see a kiosk link's address.

Prompt for Fai: "Make a self-service kiosk link called Kiosk by the main entrance for <EVENT NAME>"

#### Then: Accept scanned tickets only

What an agent can do: Fai turns finding a ticket by email on or off after you confirm.

Prompt for Fai: "At <EVENT NAME>, stop the kiosks finding tickets by email"

#### Then: Close the kiosk

What an agent can do: Fai stops a kiosk link after you confirm.

Prompt for Fai: "Close the Kiosk by the main entrance at <EVENT NAME>"

### Track your event check-ins by hour

Slug `watch-check-ins-live`. Guide: https://www.ticketfairy.com/guides/watch-check-ins-live

Use the **Arrivals** card on your event's **Check-In** page to see how many ticket holders are in right now, how fast they are arriving and which zone is busiest, then use the **Hourly** tab for **Check-Ins by Hour**, the running **Checked In** total, **Total Sold** and how many are **remaining**.

For: Watching arrivals during your event.

What an agent can do: Fai can read the live arrival figures, the hourly check-in figures and the ticket counts by ticket type from the sales report for the event, and explain how **Checked In**, **Total Sold** and **remaining** relate. Those ticket counts add up to **Total Sold**: they count tickets rather than orders, complimentary and not-yet-paid tickets included and payment-plan tickets left out, so they are not a paid-sales figure. The command line and the MCP server read the same figures.

Command line:

- The event check-in aggregate, including hourly buckets, as JSON: `ticketfairy checkin status <EVENT_ID> --output json`
- The release breakdown used for Total Sold, as JSON: `ticketfairy api /api/events/<EVENT_ID>/relationships/performance --query section=release_breakdown --output json`

CLI MCP tools that read: `select_event`, `get_checkin_stats`, `api`.

Prompt for Fai: "Find my event, tell me how many ticket holders are in right now and which zone is busiest, then show me its Check-Ins by Hour for each date and the running Checked In total, then show me the ticket counts by ticket type from the sales report and add them up the way the Total Sold card does"

## More

- All guides: https://www.ticketfairy.com/guides
- Guides MCP server: https://www.ticketfairy.com/docs/mcp (tools `search_guides` and `get_guide`)
- CLI reference: https://www.npmjs.com/package/ticketfairy
- Developer documentation: https://www.ticketfairy.com/developers
- Support: support@ticketfairy.com
