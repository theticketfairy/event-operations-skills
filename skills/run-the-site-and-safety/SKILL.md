---
name: run-the-site-and-safety
description: "Draw site maps, book deliveries, order hire, raise purchase orders, log incidents and keep a risk register in Ticket Fairy. Use when an organiser runs the event site, suppliers and safety."
---

# Run the site and safety

This skill covers site maps, deliveries, hire, contracts, purchase orders, incidents and risks on Ticket Fairy. It lists the 17 published guides for this area and what an agent can do for each one.

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

- [Book delivery times for your event and check vehicles in at the gate](#book-delivery-times-for-your-event-and-check-vehicles-in-at-the-gate)
- [Build a budget for your event](#build-a-budget-for-your-event)
- [Collect insurance and certificates from your event's outside teams](#collect-insurance-and-certificates-from-your-events-outside-teams)
- [Draw your event site map and share it](#draw-your-event-site-map-and-share-it)
- [Get hire suppliers to confirm orders and count deliveries for your event](#get-hire-suppliers-to-confirm-orders-and-count-deliveries-for-your-event)
- [Handle lost property at your event](#handle-lost-property-at-your-event)
- [Keep a risk register for your event](#keep-a-risk-register-for-your-event)
- [Let outside teams order kit and equipment for your event](#let-outside-teams-order-kit-and-equipment-for-your-event)
- [Raise purchase orders and track what your event owes](#raise-purchase-orders-and-track-what-your-event-owes)
- [Report and handle incidents at your event](#report-and-handle-incidents-at-your-event)
- [See what your brand spends across its events](#see-what-your-brand-spends-across-its-events)
- [Send contracts to many performers, traders or suppliers for your event at once](#send-contracts-to-many-performers-traders-or-suppliers-for-your-event-at-once)
- [Send your event contracts and get them signed online](#send-your-event-contracts-and-get-them-signed-online)
- [Send your event hire lists to suppliers](#send-your-event-hire-lists-to-suppliers)
- [Share a power sheet with your event electrician](#share-a-power-sheet-with-your-event-electrician)
- [Share a private event site map with emergency services and suppliers](#share-a-private-event-site-map-with-emergency-services-and-suppliers)
- [Work out the backline and production to hire for your event](#work-out-the-backline-and-production-to-hire-for-your-event)

### Book delivery times for your event and check vehicles in at the gate

Slug `book-delivery-times-and-check-vehicles-in-at-the-gate`. Guide: https://www.ticketfairy.com/guides/book-delivery-times-and-check-vehicles-in-at-the-gate

Set the times vehicles can arrive at each gate of your event and how many can come each time. Suppliers, contractors and other outside teams book a delivery on their own page and get a code for the gate, and on the day your gate team finds each vehicle by its code or number plate and checks it in and out.

For: Planning deliveries and running the gate for your event.

What an agent can do: Fai reads your arrival times, the deliveries booked and the day at the gate, adds or changes an arrival time, books, moves or cancels a delivery for a team, and checks a vehicle in or out or marks it as not arrived. She shows you each change first and waits for your yes, and she only emails the team when you say so.

Prompt for Fai: "Add an arrival time at Gate B on Friday 2 October from 8 to 11 for 6 vehicles from outside teams at <EVENT NAME>, then tell me who has booked so far"

#### Then: Book a delivery for a team

What an agent can do: Fai books a delivery for a team with the time and vehicle you give, after you confirm, and emails the team only if you ask.

Prompt for Fai: "Book Northern Staging a delivery at Gate B on Friday morning for their 7.5 tonne truck, plate AB12 CDE, and email them"

#### Then: Move or cancel a delivery

What an agent can do: Fai moves or cancels a delivery that has not arrived, after you confirm.

Prompt for Fai: "Move Northern Staging's delivery K7QX at <EVENT NAME> to the afternoon time at Gate B"

#### Then: Mark a vehicle as not arrived

What an agent can do: Fai marks a vehicle as not arrived once its arrival time has ended, after you confirm.

Prompt for Fai: "Mark delivery K7QX at <EVENT NAME> as not arrived"

### Build a budget for your event

Slug `build-a-budget-for-your-event`. Guide: https://www.ticketfairy.com/guides/build-a-budget-for-your-event

Set out what your event will cost and earn on its Budget page: sections such as Talent and Production, a line for each cost or income with its amount and type, a person responsible for each line, and totals that show whether costs or income come out ahead.

For: Planning what your event will cost and earn.

What an agent can do: Fai can read your event budget and its totals, create, rename or delete a section, and add, change or remove a planned cost with its amount. She shows you each change and asks before she makes it. Choose a line's type and the person assigned to it on the Budget page.

Prompt for Fai: "Set up a budget for <EVENT NAME> with sections for talent, production and venue hire. Add <COST> at <AMOUNT> under production, show me the plan and ask before you save anything"

#### Then: Change a line or a section

What an agent can do: Fai can rename a section you added and change a planned cost's amount or name after you approve. Change a line's type, Expense or Revenue, or assignee on the Budget page.

Prompt for Fai: "In the budget for <EVENT NAME>, change <LINE> to <AMOUNT> and show me the new total before you save it"

#### Then: Remove a line or a section

What an agent can do: Fai can remove a planned cost or a section you added, after showing you what goes with it and asking first.

Prompt for Fai: "Remove <LINE> from the budget for <EVENT NAME>. Show me what it is and the new total, then ask before you remove it"

#### Then: Copy the budget into a spreadsheet

What an agent can do: Fai can read you the whole budget, section by section, with the totals.

Prompt for Fai: "Read me the budget for <EVENT NAME> section by section with each total and tell me whether it comes out in profit"

### Collect insurance and certificates from your event's outside teams

Slug `collect-insurance-and-certificates-from-your-outside-teams`. Guide: https://www.ticketfairy.com/guides/collect-insurance-and-certificates-from-your-outside-teams

Ask your event's suppliers, contractors, caterers and other outside teams for public liability insurance, risk assessments, method statements and safety certificates. Each team adds the file on its own page with no sign-in, and Fai reads the expiry date and cover. You accept the file or ask for changes, and reminders go out before it's due and before it expires.

For: Getting every outside team's paperwork in before your event.

What an agent can do: Fai lists what you asked outside teams for and where each team stands, asks teams for a new document, changes, closes or removes a request, accepts a file with its expiry date, asks a team for changes, gives a team more time and sends reminders. She shows you each change or email first and waits for your yes. She cannot add a file for a team; select Add their file in the dashboard for that.

Prompt for Fai: "Ask every supplier at <EVENT NAME> for public liability insurance by 1 October, and tell me which teams still owe their risk assessment"

#### Then: Send a reminder now

What an agent can do: Fai emails a reminder to the teams that still owe a document, after you confirm.

Prompt for Fai: "Remind the suppliers who have not sent their insurance for <EVENT NAME>"

#### Then: Give a team more time

What an agent can do: Fai gives one team a later due date, after you confirm.

Prompt for Fai: "Give Northern Staging until Friday to send their insurance for <EVENT NAME>"

#### Then: Add a file a team emailed you

What an agent can do: Fai cannot upload a file. Add it with Add their file, then ask Fai what she read in it.

Prompt for Fai: "What did you read in the insurance Northern Staging sent for <EVENT NAME>"

#### Then: Close or remove a request

What an agent can do: Fai closes, opens again or removes a request, after you confirm.

Prompt for Fai: "Close the gas safety certificate request for <EVENT NAME>, we have everything we need"

### Draw your event site map and share it

Slug `draw-your-event-site-map-and-share-it`. Guide: https://www.ticketfairy.com/guides/draw-your-event-site-map-and-share-it

Upload your event's site plan as an image, mark the arena, campsites, stages, bars, toilets, first aid, entrances and routes on it, and let Fai check it for the safety essentials your crowd needs. Your whole team can open the map on any device, and you can publish a map with only the places attendees need on your event page.

For: Planning and sharing where everything is on your event site.

What an agent can do: Fai reads your site map, adds, changes, moves, removes or puts back a place, links it to a stage or a team, places a trader on a pitch, sets the scale and expected attendance, puts a street or satellite map under the plan from the venue address, checks the map for first aid, ways out, water, toilets and accessible viewing, and publishes or takes down the attendee map. She shows you each change and waits for your yes first. Upload the plan itself in the dashboard.

Prompt for Fai: "Check the site map for <EVENT NAME> and tell me what safety essentials are missing for 12,000 people"

#### Then: Remove a place

What an agent can do: Fai removes a place or puts one back when you ask, after you confirm.

Prompt for Fai: "Remove the old car park from the site map for <EVENT NAME>"

#### Then: Take the attendee map down

What an agent can do: Fai takes the attendee map down when you ask, after you confirm.

Prompt for Fai: "Take the attendee site map for <EVENT NAME> off the event page"

### Get hire suppliers to confirm orders and count deliveries for your event

Slug `get-hire-suppliers-to-confirm-orders-and-count-deliveries`. Guide: https://www.ticketfairy.com/guides/get-hire-suppliers-to-confirm-orders-and-count-deliveries

Give each hire supplier for your event its own page, with no sign-in, where it confirms what you ordered, asks for a change and sends its quote. Fai reads the quote against your list, your crew counts what arrives and goes back, and the purchase order shows any shortfall or damage before you pay the invoice.

For: Working with the suppliers who hire kit to your event.

What an agent can do: Fai reads goods in and out, what your suppliers asked on their page and where each quote stands. She counts goods in or out, undoes a count, accepts or declines a supplier's request, sets which outside team's page shows a supplier, and reads or puts aside a quote, showing you each change first and waiting for your yes. She cannot upload a quote for you; select Add their quote in the dashboard for that.

Prompt for Fai: "What have my hire suppliers asked for on their page at <EVENT NAME>, and what came up short when the staging arrived"

#### Then: Add a quote the supplier emailed you

What an agent can do: Fai cannot upload a file. Upload the quote with Add their quote, then ask Fai what she read in it.

Prompt for Fai: "What did you read in Northern Sound Hire's quote for <EVENT NAME>, and which lines are short"

#### Then: Undo a count

What an agent can do: Fai undoes a count when you ask, after you confirm.

Prompt for Fai: "Undo the last count of stage decks at <EVENT NAME>, it should have been 24"

#### Then: Put a quote aside

What an agent can do: Fai puts a quote aside when you ask, after you confirm.

Prompt for Fai: "Ignore the old Northern Sound Hire quote for <EVENT NAME>, they sent a new one"

### Handle lost property at your event

Slug `handle-lost-property-at-your-event`. Guide: https://www.ticketfairy.com/guides/handle-lost-property-at-your-event

Log every phone, wallet and bag handed in at your event with a photo and a reference, take lost reports from your team or from attendees on a public page, and let Fai spot the found items that may match. Hand each item back and keep track of who collected it and how you checked it was theirs.

For: Reuniting attendees with what they lost at your event.

What an agent can do: Fai reads what has been handed in, the lost reports and her possible matches, logs a found item or a lost report, hands an item back with a note of how you checked it was theirs, records an item as gone or undoes it, confirms or dismisses a match, and changes the settings. She shows you each change and waits for your yes first. Any member of your event's team can ask Fai to log an item, take a report or hand an item back.

Prompt for Fai: "Log a found item at <EVENT NAME>: black backpack with a red keyring, found by the main stage bar, kept in box 3 at the info tent"

#### Then: Record items as gone

What an agent can do: Fai records items as gone, or keeps one again, when you ask, after you confirm.

Prompt for Fai: "Record the unclaimed items at <EVENT NAME> as donated to charity"

### Keep a risk register for your event

Slug `keep-a-risk-register-for-your-event`. Guide: https://www.ticketfairy.com/guides/keep-a-risk-register-for-your-event

List what could go wrong at your event, how likely and how bad each risk is and what you are doing about it, start from a draft Fai builds from your event and past incidents, and keep every risk's owner, review date and status current.

For: Keeping your event's risk assessment current.

What an agent can do: Fai reads the register, builds a draft from your event without saving it, adds risks one at a time or many at once, edits them and marks them controlled, accepted, closed or open again. She shows you each change and waits for your yes first. Risks are never deleted. Your own AI assistant can read the register, add a risk and change its status over the MCP server, after your approval in your MCP client.

Command line:

- List the risks: `ticketfairy event-os risks list <EVENT_ID>`
- Add a risk, with how likely it is and how bad it would be, each from 1 to 5: `ticketfairy event-os risks add <EVENT_ID> --title "<THE RISK>" --likelihood <LIKELIHOOD> --impact <IMPACT> --owner "<WHO LOOKS AFTER IT>"`
- Mark a risk as controlled: `ticketfairy event-os risks set-status <EVENT_ID> <RISK_ID> --status mitigated --note "<WHY>"`

CLI MCP tools that read: `select_event`, `get_event_risks`.

CLI MCP tools that make changes (not available with `--read-only`): `manage_event_risks`.

Prompt for Fai: "Draft a risk register for <EVENT NAME>, an outdoor festival for 8,000 people, and show me before you add anything"

### Let outside teams order kit and equipment for your event

Slug `let-outside-teams-order-kit-and-equipment-for-your-event`. Guide: https://www.ticketfairy.com/guides/let-outside-teams-order-kit-and-equipment-for-your-event

Offer radios, hi-vis vests, buggies and other kit from your event's kit list to contractors, suppliers, press and other outside teams at a price you set. Each team orders from its own page. When you approve an order, we hold the kit for the team and make its invoice, and you hand the kit out and take it back at your event.

For: Renting your event's kit to the outside teams working on it.

What an agent can do: Fai reads your price list, the teams' orders and the pick list, offers a piece of kit or changes its price, limit or last day to order, approves or declines an order, orders for a team, hands an order out, takes it back and makes or emails its invoice. She shows you each change and waits for your yes first. Only owners, admins and producers can change the price list or decide an order.

Prompt for Fai: "Which kit orders from outside teams are waiting for a yes at <EVENT NAME>, and approve Harbour Radio's order and email them the invoice"

#### Then: Decline an order

What an agent can do: Fai declines an order with the reason you give, after you confirm.

Prompt for Fai: "Decline Coastline Catering's buggy order at <EVENT NAME>, all the buggies are with the stage crew that weekend"

#### Then: Cancel an order

What an agent can do: Fai cancels an order that is not handed out yet, after you confirm.

Prompt for Fai: "Cancel order 3 for Harbour Radio at <EVENT NAME>, they are bringing their own radios"

#### Then: Order kit for a team yourself

What an agent can do: Fai places an order for a team with the kit, amounts and dates you give, after you confirm. It then waits for a yes like any other order.

Prompt for Fai: "Order 6 radios and 6 hi-vis vests for Northern Sound Hire at <EVENT NAME> from Friday to Sunday, for the production office"

#### Then: Email an invoice you held back

What an agent can do: Fai makes or emails an approved order's invoice, after you confirm. She also suggests on Today emailing an invoice still waiting to go, and a reminder when one is due in 3 days or overdue.

Prompt for Fai: "Email Harbour Radio the invoice for their kit order at <EVENT NAME>"

### Raise purchase orders and track what your event owes

Slug `raise-purchase-orders-and-track-what-your-event-owes`. Guide: https://www.ticketfairy.com/guides/raise-purchase-orders-and-track-what-your-event-owes

Send suppliers a purchase order for your event, check their invoice against it, and see every deposit, balance, per diem and supplier payment that is overdue, due this week or coming up. Approved orders count as committed costs in your event budget, and you record each payment as you make it.

For: Ordering from suppliers and paying performers and suppliers on time.

What an agent can do: Fai reads your purchase orders, committed costs and payments due, drafts an order by hand or from a confirmed supplier quote, changes, approves, sends or cancels it, enters an invoice total to check it against the order, marks a payment as paid, reverses a payment and adds or removes a per diem or cost. She shows you each change and waits for your yes first. Fai records payments and never moves money; to pay from Vault she uses a Vault transfer you approve, then records it.

Prompt for Fai: "What does <EVENT NAME> still owe, and what is overdue?"

#### Then: Add a per diem or cost

What an agent can do: Fai adds or removes a per diem, backline or other cost on a booking when you ask, after you confirm.

Prompt for Fai: "Add a 40 pound per diem for Nova Twins on Saturday at <EVENT NAME>"

#### Then: Reverse a payment recorded by mistake

What an agent can do: Fai reverses a payment with your reason when you ask, after you confirm.

Prompt for Fai: "Reverse the cash payment I recorded for Nova Twins' per diem at <EVENT NAME>, it was a mistake"

#### Then: Cancel a purchase order

What an agent can do: Fai cancels a purchase order with your reason when you ask, after you confirm.

Prompt for Fai: "Cancel PO-0013 at <EVENT NAME>, we are using a different barrier supplier"

### Report and handle incidents at your event

Slug `report-and-handle-incidents-at-your-event`. Guide: https://www.ticketfairy.com/guides/report-and-handle-incidents-at-your-event

Log anything that goes wrong on site at your event in seconds, alert your safety lead about serious incidents at once, keep medical and safeguarding details to your safety team, and follow each incident through to closed with its full history.

For: Logging and following up what happens on site.

What an agent can do: Fai reads the incident log, logs an incident or adds an update to one, suggests its type and seriousness, changes its details, moves it on, reopens it or removes its personal details. She shows you each change and waits for your yes first. Any member of your event's team can report an incident through Fai, and add an update to one that is not sensitive or that they reported. Your own AI assistant can read the log, report an incident, add an update and move it on or reopen it over the MCP server, after your approval in your MCP client.

Command line:

- List the incidents: `ticketfairy event-os incidents list <EVENT_ID>`
- Report an incident: `ticketfairy event-os incidents report <EVENT_ID> --summary "<WHAT HAPPENED>"`
- Add an update to an incident. Anyone on the event's team can update one that is not sensitive. On a sensitive incident, only your safety team and the person who reported it can: `ticketfairy event-os incidents update <EVENT_ID> <INCIDENT_ID> --note "<WHAT HAPPENED NEXT>"`
- Move an incident on, for example to resolved, with an update. Owners, admins and producers only: `ticketfairy event-os incidents update <EVENT_ID> <INCIDENT_ID> --status resolved --note "<WHAT HAPPENED NEXT>"`

CLI MCP tools that read: `select_event`, `get_event_incidents`.

CLI MCP tools that make changes (not available with `--read-only`): `report_event_incident`, `update_event_incident`.

Prompt for Fai: "Log an incident at <EVENT NAME>: someone fainted near the main bar, medium, first aid is with them"

#### Then: Remove personal details from an incident

What an agent can do: Fai removes an incident's personal details when you ask, after you confirm. You can't undo it.

Prompt for Fai: "Remove the personal details from incident 31 at <EVENT NAME>"

### See what your brand spends across its events

Slug `see-what-your-brand-spends-across-its-events`. Guide: https://www.ticketfairy.com/guides/see-what-your-brand-spends-across-its-events

See the planned and recorded costs of every event your brand ran or has coming up in a period, the cost per person scanned in at the doors, your budget sections, your biggest suppliers and each event's figures, with every amount in its own currency.

For: Reviewing costs across all of your brand's events.

What an agent can do: Fai reads the same figures for a period: planned and recorded costs, income recorded, people scanned in, cost per checked-in attendee, budget sections, biggest suppliers and each event. She only reads here and changes nothing.

Prompt for Fai: "What did our events cost over the last 12 months, and what was the cost per person scanned in?"

### Send contracts to many performers, traders or suppliers for your event at once

Slug `send-contracts-to-many-performers-traders-or-suppliers-at-once`. Guide: https://www.ticketfairy.com/guides/send-contracts-to-many-performers-traders-or-suppliers-at-once

Make a contract for every booked performer or speaker, approved trader or supplier on your event from one template, each filled in from their own booking or details. You check every contract before anything is made, then send them all for signature in one approval or keep them as drafts, and see each person's result.

For: Sending the same agreement to all your performers, traders or suppliers.

What an agent can do: Fai shows who a batch can go to and a preview of every contract, then makes and sends the contracts from one template or keeps them as drafts, reads each batch's results and starts a batch that did not start. She shows you every contract first and waits for your yes.

Prompt for Fai: "Send the performance agreement to every booked performer at <EVENT NAME> who has no contract yet, and show me each contract first"

#### Then: Open a batch you made earlier

What an agent can do: Fai reads your latest batches and each contract's result and current status.

Prompt for Fai: "Which contracts from the batch I sent at <EVENT NAME> are still waiting for a signature"

#### Then: Try again for the people a batch missed

What an agent can do: Fai starts a batch that did not start after you confirm.

Prompt for Fai: "The contracts batch at <EVENT NAME> did not start, start it again"

### Send your event contracts and get them signed online

Slug `send-contracts-and-get-them-signed-online`. Guide: https://www.ticketfairy.com/guides/send-contracts-and-get-them-signed-online

Turn an accepted offer, a booked performer or speaker, an approved trader or a supplier's quote into a contract for your event, send it for signature by email, and sign it yourself once they have. The other party reads the agreement and signs by entering their name, with no account, and you both get the signed copy.

For: Getting performer, speaker, trader and supplier agreements signed.

What an agent can do: Fai reads your contracts, drafts one from an offer, a booking, a trader, a supplier quote or a template, changes a draft, sends it for signature or sends a reminder, signs it for you once the other party has, starts a new version or an amendment, cancels an unsigned one and manages your contract templates. She shows you each change and waits for your yes first, and nothing is emailed until you agree. When a contract has waited 5 days for a signature, Fai suggests a reminder on Today. Your own AI assistant can list and read the contracts and send one for signature over the MCP server, after your approval in your MCP client.

Command line:

- List the event's contracts: `ticketfairy event-os contracts list <EVENT_ID>`
- Send a contract for signature: `ticketfairy event-os contracts send <EVENT_ID> <CONTRACT_ID>`

CLI MCP tools that read: `select_event`, `get_event_contracts`.

CLI MCP tools that make changes (not available with `--read-only`): `send_contract_for_signature`.

Prompt for Fai: "Draft the contract for Nova Twins at <EVENT NAME> from their accepted offer and tell me what is missing before I send it"

#### Then: Send a reminder

What an agent can do: Fai sends a reminder with a new link when you ask, after you confirm.

Prompt for Fai: "Remind Nova Twins to sign their contract for <EVENT NAME>"

#### Then: Change a contract that is already sent

What an agent can do: Fai starts a new version of a sent or declined contract when you ask, after you confirm.

Prompt for Fai: "Nova Twins asked for a later set time at <EVENT NAME>, start a new version of their contract"

#### Then: Amend a signed contract

What an agent can do: Fai starts an amendment or a termination agreement to a signed contract when you ask, after you confirm.

Prompt for Fai: "Start an amendment to the signed Nova Twins contract at <EVENT NAME> for an extra 15 minutes"

#### Then: Cancel a contract

What an agent can do: Fai cancels an unsigned contract with your reason when you ask, after you confirm.

Prompt for Fai: "Cancel the draft speaker contract for Dr Amara Lee at <EVENT NAME>, the session was dropped"

### Send your event hire lists to suppliers

Slug `send-your-hire-lists-to-suppliers`. Guide: https://www.ticketfairy.com/guides/send-your-hire-lists-to-suppliers

Send each supplier the items they are providing for your event, with the quantities, hire dates, delivery and collection, in an email Fai drafts for you to check. We keep a copy of the list each time you send it, so you can see what changed and send only the changes. You can also turn a supplier's priced items into a draft purchase order in one step.

For: Sending equipment and shopping lists to the suppliers of your event.

What an agent can do: Fai drafts the email to a supplier from their items and what changed since the last send, and sends it after you have read it and said yes. When a supplier's items change after a send, she also suggests sending the changes on Today.

Prompt for Fai: "Send Northern Backline the changes to our backline hire for <EVENT NAME>"

#### Then: Make a purchase order from a supplier's items

What an agent can do: Fai makes a draft purchase order from a supplier's priced items when you ask, after you confirm. You approve and send it in Contracts.

Prompt for Fai: "Make a purchase order for Northern Backline's items at <EVENT NAME>"

#### Then: Print a supplier's list

What an agent can do: You print from the dashboard. Fai reads you a supplier's items, dates and delivery times instead.

Prompt for Fai: "What is on Northern Backline's list for <EVENT NAME>, and when do they deliver and collect?"

### Share a power sheet with your event electrician

Slug `share-a-power-sheet-with-your-electrician`. Guide: https://www.ticketfairy.com/guides/share-a-power-sheet-with-your-electrician

Send your electrician a link to a sheet of every trader's pitch, the power they need in amps and whether they need water, for one zone of your event site map or the whole site. Your electrician doesn't need to sign in, the sheet always shows the latest pitches, and you can stop the link at any time.

For: Giving your electrician and site crew the traders' power and water needs.

What an agent can do: Fai makes a power sheet link for one zone or the whole site, lists the links you have made and stops one. She waits for your yes before she makes or stops a link. You see a new link's address once, in the dashboard.

Prompt for Fai: "Make a power sheet link for the food court at <EVENT NAME> that works for 14 days"

#### Then: Stop a power sheet link

What an agent can do: Fai stops a power sheet link after you confirm.

Prompt for Fai: "Stop the power sheet link for the food court at <EVENT NAME>"

### Share a private event site map with emergency services and suppliers

Slug `share-a-private-site-map-with-emergency-services-and-suppliers`. Guide: https://www.ticketfairy.com/guides/share-a-private-site-map-with-emergency-services-and-suppliers

Send the fire service, an accessibility team or a supplier a private link to your event's live site map, showing the exits, routes, power or other places they need on top of the public map. Each link stops working on a date, we record every time it's opened, and you can stop it at any time.

For: Sharing your site plan with emergency services, accessibility teams and suppliers.

What an agent can do: Fai lists your map links and how often each was opened, makes a link for the audience you name, gives a link a new address or stops it, after you confirm. She never shows a link's address, so copy it from Share links.

Prompt for Fai: "Make a map link for the fire service at <EVENT NAME> that works for 30 days"

#### Then: Give a link a new address or stop it

What an agent can do: Fai gives a map link a new address or stops it, after you confirm.

Prompt for Fai: "Stop the Northern Power map link at <EVENT NAME>"

### Work out the backline and production to hire for your event

Slug `work-out-the-backline-and-production-to-hire-for-your-event`. Guide: https://www.ticketfairy.com/guides/work-out-the-backline-and-production-to-hire-for-your-event

Turn every act's technical rider into one backline hire list for your event, add the PA, lighting, staging and power you hire yourself, and see how many of each item to hire across every stage and day. Gear you can reuse on other days counts once, for the busiest day, and anything a stage already has or you already own comes off the number.

For: Working out how much equipment to hire for a festival or multi-stage event.

What an agent can do: Fai reads the hire lists with how each number was worked out, adds an item or a need, changes an item's details, reuse or status, answers a rider change and puts one item under another. She shows you each change and waits for your yes first. She also reads riders as they change and suggests adding items she finds in production documents you upload.

Prompt for Fai: "How many CDJs do we need to hire for <EVENT NAME>, and which acts need them on which days?"

#### Then: Change the hire period

What an agent can do: Fai changes the hire period when you ask, after you confirm.

Prompt for Fai: "Give every hire at <EVENT NAME> two load-in days before the first day"

#### Then: Put one item under another

What an agent can do: Fai puts one item under another when you ask, after you confirm.

Prompt for Fai: "CDJ3000 and Pioneer CDJ-3000 are the same thing at <EVENT NAME>, put them together"

## More

- All guides: https://www.ticketfairy.com/guides
- Guides MCP server: https://www.ticketfairy.com/docs/mcp (tools `search_guides` and `get_guide`)
- CLI reference: https://www.npmjs.com/package/ticketfairy
- Developer documentation: https://www.ticketfairy.com/developers
- Support: support@ticketfairy.com
