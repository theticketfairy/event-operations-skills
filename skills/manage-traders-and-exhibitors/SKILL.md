---
name: manage-traders-and-exhibitors
description: "Take trader applications, place pitches, publish a directory, check takings and give exhibitors lead scanners in Ticket Fairy. Use when an organiser runs traders or an exhibition."
---

# Manage traders and exhibitors

This skill covers trader applications, pitches, directories, takings and lead scanning on Ticket Fairy. It lists the 9 published guides for this area and what an agent can do for each one.

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

- [Check your traders' takings after your event and invoice their share of sales](#check-your-traders-takings-after-your-event-and-invoice-their-share-of-sales)
- [Get your traders ready for show day](#get-your-traders-ready-for-show-day)
- [Give exhibitors a lead scanner for their booth at your event](#give-exhibitors-a-lead-scanner-for-their-booth-at-your-event)
- [Handle trader requests to move pitch at your event](#handle-trader-requests-to-move-pitch-at-your-event)
- [Let exhibitors follow up their event leads and see their results](#let-exhibitors-follow-up-their-event-leads-and-see-their-results)
- [Place your traders on pitches on your event site map](#place-your-traders-on-pitches-on-your-event-site-map)
- [Set pitch rules and let Fai plan your trader pitches at your event](#set-pitch-rules-and-let-fai-plan-your-trader-pitches-at-your-event)
- [Show your traders in a directory on your website](#show-your-traders-in-a-directory-on-your-website)
- [Take food, drink and market trader applications for your event](#take-food-drink-and-market-trader-applications-for-your-event)

### Check your traders' takings after your event and invoice their share of sales

Slug `check-trader-takings-and-invoice-a-share-of-sales`. Guide: https://www.ticketfairy.com/guides/check-trader-takings-and-invoice-a-share-of-sales

Collect each trader's takings with their till and card reports after your event, and let Fai read the reports and say whether they match. Accept the figure or ask the trader about it, then raise the share-of-sales invoice with your minimum and maximum applied.

For: Taking a share of your traders' sales as their pitch fee.

What an agent can do: Fai lists your traders' takings with her reading of their reports and every trader invoice, enters takings for a trader, accepts takings, asks a trader for a corrected figure, reads the reports again and raises the share-of-sales invoice. She shows you each change and waits for your yes first.

Prompt for Fai: "Which traders at <EVENT NAME> sent takings whose reports do not match, and what did Fai read in each"

#### Then: Enter takings a trader gave you on paper

What an agent can do: Fai enters a trader's takings for you after you confirm.

Prompt for Fai: "Enter takings of 4,520 pounds for <BUSINESS NAME> at <EVENT NAME>, from their paper sheet"

#### Then: Ask Fai to read the reports again

What an agent can do: Fai reads a trader's reports again when you ask.

Prompt for Fai: "Read the takings reports from <BUSINESS NAME> at <EVENT NAME> again"

### Get your traders ready for show day

Slug `get-your-traders-ready-for-show-day`. Guide: https://www.ticketfairy.com/guides/get-your-traders-ready-for-show-day

Give each approved trader their own page to accept your trading terms, pay their invoice, book a load-in time and upload certificates. Chase what's missing, and check every pitch, power and water need before your event.

For: Getting approved traders' paperwork, payments and load-in sorted.

What an agent can do: Fai sets up your trading terms and load-in times, sends a trader their page or a reminder of what is missing, sets a pitch and reads the certificates traders upload. She asks you before anything is sent or changed. Your own AI assistant can list the traders and what each still owes over the MCP server.

Command line:

- List the traders: `ticketfairy event-os traders list <EVENT_ID>`
- Show one trader: `ticketfairy event-os traders show <EVENT_ID> <VENDOR_ID>`

CLI MCP tools that read: `select_event`, `get_traders`.

Prompt for Fai: "Which traders at <EVENT NAME> are still missing certificates or have not paid, and send each of them a reminder"

#### Then: Stop a trader page link

What an agent can do: Fai stops a trader's page link after you confirm.

Prompt for Fai: "Stop the trader page link for <BUSINESS NAME> on <EVENT NAME>"

### Give exhibitors a lead scanner for their booth at your event

Slug `give-exhibitors-a-lead-scanner-for-their-booth`. Guide: https://www.ticketfairy.com/guides/give-exhibitors-a-lead-scanner-for-their-booth

Give each exhibitor's booth staff at your event a scanner link for their own phone or tablet, with no sign-in. Each scan becomes a named lead with a rating and notes, and you see every booth's leads and results.

For: Capturing leads at the exhibitor booths at your conference or expo.

What an agent can do: Fai reads every exhibitor's leads and results, adds or removes booth staff, sets an exhibitor's rating words and tracking link, records that a visitor no longer wants contact and removes a lead. She makes a scanner link for you, and its address shows in the dashboard. She waits for your yes before every change.

Prompt for Fai: "How many leads has each exhibitor at <EVENT NAME> captured so far, and which booths have no scanner link yet"

#### Then: Record that a visitor no longer wants contact

What an agent can do: Fai records that a visitor no longer wants contact after you confirm.

Prompt for Fai: "<VISITOR NAME> asked Northwind Audio at <EVENT NAME> not to contact them, record it"

#### Then: Download an exhibitor's leads

What an agent can do: Download the leads from the exhibitor's panel in the dashboard, where the download is recorded with your name.

#### Then: Stop a scanner link

What an agent can do: Fai stops a scanner link after you confirm.

Prompt for Fai: "Stop Lena Brandt's lead scanner link for Northwind Audio at <EVENT NAME>"

### Handle trader requests to move pitch at your event

Slug `handle-trader-requests-to-move-pitch`. Guide: https://www.ticketfairy.com/guides/handle-trader-requests-to-move-pitch

Let traders at your event ask to move pitch from their own trader page, with their reason and where they would like to be. You move them to a free pitch that keeps your pitch rules, or decline with a note, and they see your answer on their page and by email.

For: Answering traders who ask for a different pitch.

What an agent can do: Fai lists the move requests waiting, checks a pitch against your rules, and moves a trader or declines their request with your note, after you confirm.

Prompt for Fai: "Rocket Coffee Van at <EVENT NAME> wants to move, what free pitch would keep our rules?"

#### Then: Decline a request

What an agent can do: Fai declines a move request with the note you give, after you confirm.

Prompt for Fai: "Decline Rocket Coffee Van's move request at <EVENT NAME>, every hard-standing pitch is taken"

### Let exhibitors follow up their event leads and see their results

Slug `let-exhibitors-follow-up-their-leads-and-see-results`. Guide: https://www.ticketfairy.com/guides/let-exhibitors-follow-up-their-leads-and-see-results

Give each exhibitor a page of its own, with no sign-in, where its team sees the leads from its booth at your event, approves follow-up emails that Fai drafts, gives booth staff scanner links, downloads its leads and sees its results. You make the page from the exhibitor's leads and send the link from Outside teams.

For: Handing exhibitors their leads, follow-up emails and booth results.

What an agent can do: Fai gives an exhibitor its own page, reads its leads, follow-ups and results, and sets a sponsor's page and tracking link. She waits for your yes before every change. Only the exhibitor approves its follow-up emails, on its own page.

Prompt for Fai: "Give Northwind Audio its own page at <EVENT NAME> and tell me how many of its leads can be contacted"

#### Then: Show a sponsor its results

What an agent can do: Fai links a sponsor to its outside team and chooses its tracking link after you confirm.

Prompt for Fai: "Give the sponsor <SPONSOR NAME> at <EVENT NAME> its own page with the <TRACKING LINK NAME> tracking link"

### Place your traders on pitches on your event site map

Slug `place-your-traders-on-pitches-on-your-site-map`. Guide: https://www.ticketfairy.com/guides/place-your-traders-on-pitches-on-your-site-map

Drag each approved trader onto a pitch you drew on your event site map, move a trader when a pitch changes hands, and check every pitch with its power and water. Each trader then sees their own pitch on a map on their trader page.

For: Giving each approved trader a pitch on your site plan.

What an agent can do: Fai places a trader on a pitch of your site map, moves them to another pitch or takes them off the map. She shows you the change and waits for your yes first.

Prompt for Fai: "Put Smoke & Salt BBQ on pitch F2 on the site map for <EVENT NAME>"

#### Then: Take a trader off the map

What an agent can do: Fai takes a trader off the site map after you confirm.

Prompt for Fai: "Take <BUSINESS NAME> off the site map for <EVENT NAME>"

### Set pitch rules and let Fai plan your trader pitches at your event

Slug `set-pitch-rules-and-let-fai-plan-your-trader-pitches`. Guide: https://www.ticketfairy.com/guides/set-pitch-rules-and-let-fai-plan-your-trader-pitches

Enter your event's pitch rules the way you would say them, such as keeping the two coffee vans apart or the fire lane clear. The pitch check shows every pitch that breaks a rule, and Fai places the traders still without a pitch on free pitches that keep every rule, for you to approve.

For: Placing traders on your site plan by your own rules.

What an agent can do: Fai adds a pitch rule from your words, reads you the pitch check, and makes a pitch plan for the traders still without a pitch. She shows you each rule and plan, and nothing is placed until you approve it.

Prompt for Fai: "At <EVENT NAME>, keep the two coffee vans at least 30 metres apart, then plan pitches for the traders who still need one"

#### Then: Turn a rule off or remove it

What an agent can do: Fai turns a pitch rule off or on, or removes it, after you confirm.

Prompt for Fai: "Turn off the power rule for the food court at <EVENT NAME>"

### Show your traders in a directory on your website

Slug `show-your-traders-in-a-directory-on-your-website`. Guide: https://www.ticketfairy.com/guides/show-your-traders-in-a-directory-on-your-website

Publish a public list of the food, drink and market traders at your event, and check each trader's listing before it goes up. Ask a trader to change it, choose how the list looks, and put it on your own website with the embed code.

For: Showing the traders at your event on your own website.

What an agent can do: Fai reads your trader directory and its embed code, changes a trader's listing, publishes it, asks the trader for changes or takes it out of the directory. She shows you each change and waits for your yes first.

Prompt for Fai: "Which trader listings for <EVENT NAME> are waiting for review, and publish the ones that say what they sell"

#### Then: Take a trader out of the directory

What an agent can do: Fai takes a trader's listing out of the directory after you confirm.

Prompt for Fai: "Take <BUSINESS NAME> out of the trader directory for <EVENT NAME>"

### Take food, drink and market trader applications for your event

Slug `take-trader-applications-for-your-event`. Guide: https://www.ticketfairy.com/guides/take-trader-applications-for-your-event

Open an application page for food, drink, merchandise and market traders, set your pitch fees and how they are taxed, let Fai rank the applications against the mix you want, then approve, waitlist or decline each trader for your event and invoice the ones you approve.

For: Choosing and invoicing the traders who sell at your event.

What an agent can do: Fai lists your traders and applications with her reading of each, sets up the application page, fees and tax, adds a trader you already know, and approves, waitlists or declines an application. She shows you the email and invoice first and waits for your yes.

Command line:

- List the traders and applications on the event: `ticketfairy event-os traders list <EVENT_ID> --view to_review --sort fai`
- Show one trader's application, fees, paperwork and history: `ticketfairy event-os traders show <EVENT_ID> <VENDOR_ID>`
- Approve a trader, email them and raise and send their pitch invoice. This asks you first unless you add --force: `ticketfairy event-os traders decide <EVENT_ID> <VENDOR_ID> --decision approve --raise-invoice --send-invoice`

CLI MCP tools that read: `get_traders`.

CLI MCP tools that make changes (not available with `--read-only`): `decide_trader_application`.

Prompt for Fai: "Show me the trader applications for <EVENT NAME> that best fit our food mix, and approve Smoke & Salt BBQ on the 6m pitch with the invoice"

#### Then: Add a trader you already know

What an agent can do: Fai adds a trader to the event from the details you give her, after you confirm.

Prompt for Fai: "Add <BUSINESS NAME> to the traders on <EVENT NAME> as already agreed, contact <NAME> at <EMAIL>"

#### Then: Raise or send an invoice later

What an agent can do: Fai raises a trader's invoice and sends it after you confirm.

Prompt for Fai: "Raise and send the pitch invoice for <BUSINESS NAME> on <EVENT NAME>"

#### Then: Cancel an approved trader

What an agent can do: Fai cancels an approved trader after you confirm.

CLI MCP tools that read: `get_traders`.

CLI MCP tools that make changes (not available with `--read-only`): `decide_trader_application`.

Prompt for Fai: "Cancel <BUSINESS NAME> as a trader at <EVENT NAME>"

## More

- All guides: https://www.ticketfairy.com/guides
- Guides MCP server: https://www.ticketfairy.com/docs/mcp (tools `search_guides` and `get_guide`)
- CLI reference: https://www.npmjs.com/package/ticketfairy
- Developer documentation: https://www.ticketfairy.com/developers
- Support: support@ticketfairy.com
