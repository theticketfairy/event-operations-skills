---
name: manage-orders-and-refunds
description: "Find and manage Ticket Fairy orders: checkout questions, order approval, refunds, transfers, waiting lists and buyer support. Use when an organiser asks about an order, a refund or the checkout."
---

# Manage orders and refunds

This skill covers checkout questions, order approval, refunds, transfers, waiting lists and buyer support on Ticket Fairy. It lists the 20 published guides for this area and what an agent can do for each one.

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

- [Add custom questions to your event checkout](#add-custom-questions-to-your-event-checkout)
- [Add custom terms to your event checkout](#add-custom-terms-to-your-event-checkout)
- [Choose which AI assistants sell your tickets](#choose-which-ai-assistants-sell-your-tickets)
- [Choose which details checkout asks your ticket buyers for](#choose-which-details-checkout-asks-your-ticket-buyers-for)
- [Clear the ticket orders waiting on an ID check](#clear-the-ticket-orders-waiting-on-an-id-check)
- [Design your own PDF tickets with your brand and sponsors](#design-your-own-pdf-tickets-with-your-brand-and-sponsors)
- [Download your ticket buyers](#download-your-ticket-buyers)
- [Find and manage the orders for your event](#find-and-manage-the-orders-for-your-event)
- [Let buyers pay for tickets in instalments](#let-buyers-pay-for-tickets-in-instalments)
- [Let buyers refund their own tickets](#let-buyers-refund-their-own-tickets)
- [Let buyers resell their tickets at face value](#let-buyers-resell-their-tickets-at-face-value)
- [Move a buyer to a different ticket type or seat](#move-a-buyer-to-a-different-ticket-type-or-seat)
- [Print venue directions and entry details on your tickets](#print-venue-directions-and-entry-details-on-your-tickets)
- [Refund an order on your event](#refund-an-order-on-your-event)
- [Resend a buyer's tickets and fix their details](#resend-a-buyers-tickets-and-fix-their-details)
- [Respond to a disputed ticket order](#respond-to-a-disputed-ticket-order)
- [Run a waiting list for a sold-out event](#run-a-waiting-list-for-a-sold-out-event)
- [Sell a block of tickets to a company and invoice them](#sell-a-block-of-tickets-to-a-company-and-invoice-them)
- [Turn on the ID check for buyers](#turn-on-the-id-check-for-buyers)
- [Win back buyers who left checkout](#win-back-buyers-who-left-checkout)

### Add custom questions to your event checkout

Slug `add-custom-checkout-questions`. Guide: https://www.ticketfairy.com/guides/add-custom-checkout-questions

Collect extra information from buyers or ticket holders for your event checkout, such as a meal choice, accessibility request or company detail, and decide where each answer belongs.

For: Your event team collecting extra buyer, ticket-holder or add-on information at checkout.

What an agent can do: Fai can list an event's checkout fields and create basic order, ticket or add-on fields after showing you the proposed type, label and where the answer belongs. She can also remove every custom field at once, after you confirm you want them all deleted. Edit a single field and set conditional rules in the dashboard. You can't manage these fields with MCP or the CLI.

Prompt for Fai: "Show me the custom checkout fields on <EVENT NAME>, then add a required ticket question called Meal preference with Vegetarian, Vegan and No preference as the choices. Show me the complete field and ask before saving it"

#### Then: Review or remove existing questions

What an agent can do: Fai can list the current fields, or remove every custom field once you confirm you want them all deleted. Edit a single field in the dashboard.

Prompt for Fai: "List the custom checkout fields on <EVENT NAME>, then show me which one I should edit in the dashboard to make it optional"

### Add custom terms to your event checkout

Slug `add-custom-terms-to-your-checkout`. Guide: https://www.ticketfairy.com/guides/add-custom-terms-to-your-checkout

Add labelled terms and conditions to your event checkout agreement, so buyers can open each section and accept the complete agreement before they pay.

For: Getting your own refund policy or code of conduct onto your event checkout.

What an agent can do: Only Ticket Fairy staff can add custom event terms in the dashboard. Fai can take you to the event Settings page, but she can't create or edit the agreement, and neither can MCP or the CLI.

Prompt for Fai: "Open the Settings page for <EVENT NAME> so a Ticket Fairy staff member can add the approved custom checkout terms"

#### Then: Change or remove a section

What an agent can do: Fai can take you to the event Settings page for a staff member to review, change or remove custom terms.

Prompt for Fai: "Open the custom checkout terms for <EVENT NAME> in Event Settings so a Ticket Fairy staff member can review them"

#### Then: Collect answers instead of agreement

What an agent can do: Fai can list or add basic custom order, ticket or add-on fields. Use the custom questions guide for that workflow.

Prompt for Fai: "Show me the custom checkout fields on <EVENT NAME>, then add a required ticket question after I approve the details"

### Choose which AI assistants sell your tickets

Slug `choose-which-ai-assistants-sell-your-tickets`. Guide: https://www.ticketfairy.com/guides/choose-which-ai-assistants-sell-your-tickets

AI shopping assistants can start a ticket order for buyers who ask them about events, at your prices and with your ticket rules, and send the buyer to the Ticket Fairy checkout page to pay. Turn an assistant off for your brand, or pause it for one event, to stop new ticket sales through it.

For: Brand owners and admins deciding which AI assistants sell their event tickets.

What an agent can do: Fai can tell you which AI assistants sell your brand's tickets and turn one on or off for the brand. She shows you the change and asks you to approve it before she makes it.

Prompt for Fai: "Which AI assistants can sell tickets for <BRAND NAME>? Turn off <ASSISTANT NAME> so it stops selling our tickets"

#### Then: Turn an assistant back on

What an agent can do: Fai can turn an assistant back on for your brand. She shows you the change and asks you to approve it first.

Prompt for Fai: "Turn <ASSISTANT NAME> back on for <BRAND NAME> so it can sell our tickets again"

#### Then: Pause an assistant for one event

What an agent can do: Fai can pause an assistant for one event. She shows you the change and asks you to approve it first.

Prompt for Fai: "Pause <ASSISTANT NAME> for <EVENT NAME> so it stops selling tickets for that event"

#### Then: Resume an assistant for one event

What an agent can do: Fai can resume an assistant you paused for one event. She shows you the change and asks you to approve it first.

Prompt for Fai: "Resume <ASSISTANT NAME> for <EVENT NAME> so it can sell tickets for that event again"

### Choose which details checkout asks your ticket buyers for

Slug `choose-which-attendee-details-checkout-collects`. Guide: https://www.ticketfairy.com/guides/choose-which-attendee-details-checkout-collects

Make every ticket buyer at your event's checkout enter a phone number, nationality, Instagram handle or date of birth before they can pay, and turn away buyers under your event's minimum age.

For: Collecting a phone number, nationality, Instagram handle or date of birth from every ticket buyer.

What an agent can do: Fai can turn each of these questions on or off for an event and set its minimum age, and she shows you the change and asks you to approve it first. You change these checkout settings in the dashboard or through Fai.

Prompt for Fai: "On <EVENT NAME>, make checkout ask every buyer for their <PHONE NUMBER, NATIONALITY, INSTAGRAM HANDLE OR DATE OF BIRTH>, set the minimum age to <AGE>, and show me the change before you save it"

### Clear the ticket orders waiting on an ID check

Slug `verify-buyer-identity-at-checkout`. Guide: https://www.ticketfairy.com/guides/verify-buyer-identity-at-checkout

See which buyers have a card on hold in the Needs Verification tab, send the ID check again, take the payment without it, or release the hold and put the tickets back on sale.

For: Clearing the card holds waiting on an ID check so the tickets go back on sale.

What an agent can do: Fai opens the event and takes you to its orders. You decide what happens to a hold on the page itself, because taking the money and releasing it both change what the buyer has and cannot be undone.

CLI MCP tools that read: `select_event`, `get_event`.

Prompt for Fai: "Take me to the orders on <EVENT NAME>"

#### Then: Clear old holds every day

What an agent can do: Fai can take you to the tab. You make the decisions yourself on the page, because taking a buyer's money and releasing it both change what they have and cannot be undone.

CLI MCP tools that read: `select_event`, `get_event`.

Prompt for Fai: "Take me to the orders on <EVENT NAME> that are waiting on an ID check"

#### Then: Turn on the buyer ID check

What an agent can do: Fai can turn the buyer ID check on or off for your event. She asks you to approve the change. For your own assistant over MCP, allow it to make changes and keep human approval on.

Command line:

- Require buyers to complete an ID check: `ticketfairy event update <EVENT_ID> --body '{"idVerificationRequired":true}'`
- Turn off the event-wide requirement: `ticketfairy event update <EVENT_ID> --body '{"idVerificationRequired":false}'`

CLI MCP tools that read: `select_event`, `get_event`.

CLI MCP tools that make changes (not available with `--read-only`): `update_event`.

Prompt for Fai: "Turn on the buyer ID check for <EVENT NAME>. Show me the current setting and ask me to approve the change"

### Design your own PDF tickets with your brand and sponsors

Slug `design-your-own-pdf-tickets`. Guide: https://www.ticketfairy.com/guides/design-your-own-pdf-tickets

Design the PDF tickets your buyers get in your logo, colours and fonts, add your own information, artwork and sponsor logos, and choose which events and ticket types use each design.

For: Promoters, festivals and venues who want tickets in their own brand, with their sponsors on them.

What an agent can do: Fai can start a design from one of the starting designs, change its blocks, artwork, colours, fonts, text and sponsor logos, copy or delete a design, choose the design for all your events, and choose the design for an event or one of its ticket types. She tells you which brand kit fonts your tickets can use and why the others cannot be used. She shows you each change and asks you to approve it before saving. Upload logo, artwork and font files in the dashboard, or give Fai their web addresses, because Fai cannot upload files.

Prompt for Fai: "Create a ticket design called <DESIGN NAME> from the Partner showcase starting design, with these sponsor logos and websites: <SPONSOR NAMES, LOGO ADDRESSES AND WEBSITES>. Show me the design before you save it"

#### Then: Use your brand's own font on your tickets

What an agent can do: Fai can tell you which brand kit fonts your tickets can use and why the others cannot. Once you have uploaded the font file in the dashboard and told her that your brand has the right to use the font, she can add it to your brand kit and choose it in a design, after you approve each change.

Prompt for Fai: "Which of my brand kit fonts can I use on my tickets? Use <FONT NAME> as the heading font in the <DESIGN NAME> ticket design and show me the design before you save it"

#### Then: Give one ticket type its own design

What an agent can do: Fai can choose the design for an event and for each of its ticket types once you approve the change.

Prompt for Fai: "On <EVENT NAME>, use the <DESIGN NAME> ticket design for the <TICKET TYPE NAME> tickets"

#### Then: Use one design for all your events

What an agent can do: Fai can choose the design every event uses, or go back to the standard ticket, once you approve it.

Prompt for Fai: "Use the <DESIGN NAME> ticket design for all my events"

#### Then: Copy or delete a design

What an agent can do: Fai can copy or delete a design once you approve it.

Prompt for Fai: "Copy the <DESIGN NAME> ticket design and call the copy <NEW NAME>"

### Download your ticket buyers

Slug `download-your-ticket-buyers`. Guide: https://www.ticketfairy.com/guides/download-your-ticket-buyers

Get a CSV of every ticket for your event, with buyer details and optional add-ons as rows or columns.

For: Getting your event's ticket buyers into a spreadsheet.

What an agent can do: Ask Fai to prepare tickets only or tickets and add-ons for your event, with add-ons as rows or columns. If you do not choose, she prepares rows without add-ons. She shows you the request and waits for your approval, then gives you a dashboard link to your file. With an owner or admin login, you come back to the file in Orders; with a marketing login, you come back to it in Marketing Assets. Open the link with the account that requested the file and select Download when it is ready. Fai checks progress without reading the buyers' details into the conversation.

Prompt for Fai: "Prepare a file of tickets and add-ons for <EVENT NAME>, then give me the page where I can download it"

### Find and manage the orders for your event

Slug `find-and-manage-your-event-orders`. Guide: https://www.ticketfairy.com/guides/find-and-manage-your-event-orders

Find any ticket order on your event by buyer, email address or order number, see which tab each order sits in, open it to read the tickets, the buyer and where the sale came from, and leave a note your team can see.

For: Looking after the orders on your event.

What an agent can do: Fai finds an order by the buyer's email address or the order number, reads it back to you with its notes, and adds a note once you approve the wording. She also finds disputed orders and explains their status, reason, amount and response deadline when recorded. Over MCP your own assistant can list an event's orders by status and open one, and the command line does the same. Neither MCP nor the command line reads or changes order notes.

Command line:

- Lists the event's paid orders, newest first: `ticketfairy order list <EVENT_ID> --status paid`
- Opens one order with its tickets and buyer, using the number from the Order column: `ticketfairy order get <EVENT_ID> <ORDER_ID>`

CLI MCP tools that read: `select_brand`, `select_event`, `list_orders`, `get_order`.

Prompt for Fai: "Find the order for <BUYER EMAIL ADDRESS> on <EVENT NAME>, tell me its status, tickets and any notes on it, then add this note once I approve it: <NOTE>"

#### Then: Find and read a disputed order

What an agent can do: Fai can find and count orders matching Disputed or Not disputed on your event, and read a dispute's recorded details. She does not submit evidence or accept the dispute.

Prompt for Fai: "Find the disputed orders for <EVENT NAME>, tell me how many there are, and show me the status, reason, amount and response deadline for order <ORDER NUMBER>"

#### Then: Save a filtered view

What an agent can do: Saved views are kept in the dashboard for your login, and Fai cannot save one. She can count an event's orders, one buyer's by email address, or the orders matching Disputed or Not disputed, but she cannot save a dashboard view.

Prompt for Fai: "How many orders does <EVENT NAME> have, and which of them are from <BUYER EMAIL ADDRESS>"

#### Then: Edit or delete a note

What an agent can do: Fai reads an order's notes, then edits or deletes one after you approve the change. She asks before either, and you can't get a deleted note back.

Prompt for Fai: "Show me the notes on order <ORDER NUMBER> on <EVENT NAME>, then change the one about <SUBJECT> to say: <NEW WORDING>"

### Let buyers pay for tickets in instalments

Slug `let-buyers-pay-for-tickets-in-instalments`. Guide: https://www.ticketfairy.com/guides/let-buyers-pay-for-tickets-in-instalments

Turn on a payment plan for your event so buyers pay a first instalment at checkout and the rest in weekly or monthly instalments that finish before the event.

For: Selling higher-priced festival or multi-day tickets.

What an agent can do: Fai can set up or turn off an event's payment plan. She shows you the settings and asks you to approve them before she saves, because they change how buyers pay. The command line and MCP have no payment plan commands.

Prompt for Fai: "Set up a payment plan on <EVENT NAME> with 4 monthly instalments, the last one 2 weeks before the event, unpaid orders cancelled 1 week before the event, and a fixed £50 first instalment per order; show me the settings before you save"

#### Then: Follow the instalments as they come in

What an agent can do: Follow instalments on the Payment Plan tab of the Orders page.

### Let buyers refund their own tickets

Slug `let-buyers-refund-themselves`. Guide: https://www.ticketfairy.com/guides/let-buyers-refund-themselves

Turn on self-refunds, see what a buyer is offered on their order page, and know what happens to the ticket and the stock afterwards.

For: Letting buyers refund their own tickets from their order page.

What an agent can do: Fai can turn self-refunds on or off for an event and asks you to approve the change first. She refuses to turn them on once the event's money has been released, and says why. She can't see the terms a buyer is offered, so ask Ticket Fairy support for those.

Command line:

- Show the event, including whether buyers can refund themselves: `ticketfairy event get <EVENT_ID> --output json`

Prompt for Fai: "Turn on self-refunds for <EVENT NAME> and confirm the setting is on"

#### Then: Where the ticket goes

What an agent can do: Fai can tell you the state each ticket on an order is in. Where a refunded place went afterwards is not recorded against the ticket, so ask Ticket Fairy support to check that one.

Prompt for Fai: "What state is each ticket on <ORDER NUMBER> for <EVENT NAME> in"

#### Then: When a buyer cannot refund

What an agent can do: Fai can see the ticket's own state, so she can tell you it is refunded, transferred, checked in or on resale. She can't see the rules that come from the event rather than the ticket, so ask Ticket Fairy support where none of those fits.

Prompt for Fai: "What state is the ticket on order <ORDER NUMBER> in"

#### Then: Refund on a buyer's behalf

What an agent can do: Fai can refund an order for you in two steps: she asks for a code, which reaches your email address, and you give it to her with your approval before anything is refunded.

Prompt for Fai: "Refund order <ORDER NUMBER> on <EVENT NAME> for <REASON>, and send me the code first"

### Let buyers resell their tickets at face value

Slug `let-buyers-resell-their-tickets-at-face-value`. Guide: https://www.ticketfairy.com/guides/let-buyers-resell-their-tickets-at-face-value

Turn on ticket resale so a buyer who can't come to your event passes their ticket to the next fan on your waiting list, or to someone they name, at the ticket's own price, and follow every resale ticket on the Ticket Resale report.

For: Letting ticket buyers pass their tickets to fans who want them.

What an agent can do: Fai can turn ticket resale, add-on resale and the waiting list on for you, tell you the resale fee on your event and list the tickets buyers have put up for resale. She shows you each change and asks you to approve it before she saves. Over MCP your own assistant can switch resale on and read the setting back.

Command line:

- Turn on ticket resale and add-on resale for an event: `ticketfairy event update <EVENT_ID> --body '{"flagResaleEnabled": true, "flagEnableAddOnResale": true}'`
- Check whether ticket and add-on resale are on, and the resale fee percentage the event carries: `ticketfairy event get <EVENT_ID> --fields flagResaleEnabled,flagEnableAddOnResale,resaleFeePercentage`
- List every ticket buyers have put up for resale, with its status, how it sold and the ticket it went to: `ticketfairy api /api/events/<EVENT_ID>/relationships/performance --query section=resale --output json`

CLI MCP tools that read: `select_brand`, `select_event`, `get_event`.

CLI MCP tools that make changes (not available with `--read-only`): `update_event`.

Prompt for Fai: "Turn on ticket resale, add-on resale and the waiting list for <EVENT NAME>, then tell me the resale fee on the event and list the tickets buyers have put up for resale"

#### Then: Keep one ticket type out of resale

What an agent can do: Fai can withhold a ticket type from resale after showing you which one she will change, and asks you to approve it. Over MCP your own assistant can do the same, and the command line sets it with the ticket type's ID from the ticket list.

Command line:

- List the event's ticket types with their IDs: `ticketfairy ticket list <EVENT_ID>`
- Withhold one ticket type from resale: `ticketfairy ticket update <EVENT_ID> <TICKET_TYPE_ID> --body '{"disableResale": true}'`

CLI MCP tools that read: `select_event`, `list_tickets`.

CLI MCP tools that make changes (not available with `--read-only`): `update_ticket`.

Prompt for Fai: "Stop buyers reselling the <TICKET TYPE NAME> tickets on <EVENT NAME>, and show me the ticket type before you change it"

#### Then: Stop one buyer reselling their order

What an agent can do: Fai can find the order and block or unblock resale on it, and asks you to approve the change first. MCP and the command line do not block resale on an order.

Prompt for Fai: "Find order <ORDER NUMBER> on <EVENT NAME> and block resale on it once I approve"

#### Then: Turn resale off

What an agent can do: Fai can turn ticket resale off after showing you the change, and asks you to approve it. Over MCP your own assistant can switch it off too, and so can the command line.

Command line:

- Turn off ticket resale for an event: `ticketfairy event update <EVENT_ID> --body '{"flagResaleEnabled": false}'`

CLI MCP tools that read: `select_event`.

CLI MCP tools that make changes (not available with `--read-only`): `update_event`.

Prompt for Fai: "Turn off ticket resale for <EVENT NAME>"

### Move a buyer to a different ticket type or seat

Slug `move-a-buyer-to-a-different-ticket-type-or-seat`. Guide: https://www.ticketfairy.com/guides/move-a-buyer-to-a-different-ticket-type-or-seat

Change every ticket on a buyer's order to another ticket type in one go, move one ticket on its own, or give a ticket holder a different seat on your seat map, without the buyer placing a new order.

For: Moving a buyer to the right ticket or seat after they have bought.

What an agent can do: Fai finds the order and reads out each ticket's type, holder and state, before and after you move it. She can't change a ticket type or a seat, so make either change yourself on the page. Neither MCP nor the command line has a command for these changes.

Prompt for Fai: "For order <ORDER NUMBER> on <EVENT NAME>, list each ticket with its ticket type, holder and state, and tell me which of them are checked in or up for resale"

#### Then: Move one ticket rather than the whole order

What an agent can do: Fai can read the ticket afterwards so you can check which one now works at the door. You make the change yourself on the page.

Prompt for Fai: "For order <ORDER NUMBER> on <EVENT NAME>, list its tickets with the type, barcode and state of each"

### Print venue directions and entry details on your tickets

Slug `print-venue-directions-and-entry-details-on-your-tickets`. Guide: https://www.ticketfairy.com/guides/print-venue-directions-and-entry-details-on-your-tickets

Add your own words to every ticket PDF for your event, such as how to get to the venue, which entrance to use and what to bring, and give one ticket type its own text or hide the date on its tickets.

For: Getting the door information onto every ticket your buyers carry.

What an agent can do: Fai can set the words printed on every ticket for your event, or on one ticket type's tickets, and hide the date on a ticket type. She shows you the change and asks you to approve it before saving. MCP has no tool for ticket text.

Command line:

- Sets the text printed on every ticket PDF for the event, replacing the event's current ticket text: `ticketfairy event update <EVENT_ID> --body '{"ticketText":"<TICKET_TEXT>"}'`

Prompt for Fai: "On <EVENT NAME>, print this on every ticket PDF: <DIRECTIONS AND ENTRY DETAILS>. Show me the text before you save it"

#### Then: Give one ticket type its own text

What an agent can do: Fai can set one ticket type's text for you once you approve it. She asks before saving the change.

Prompt for Fai: "On <EVENT NAME>, print this on the <TICKET TYPE NAME> tickets only: <TEXT>"

#### Then: Hide the date on one ticket type's tickets

What an agent can do: Fai can hide the date on one ticket type's tickets once you approve it.

Prompt for Fai: "On <EVENT NAME>, hide the date on the <TICKET TYPE NAME> ticket PDFs"

### Refund an order on your event

Slug `refund-an-order`. Guide: https://www.ticketfairy.com/guides/refund-an-order

Return the face value of a paid order to the buyer's card from the Orders page, confirm it with the authorisation code Ticket Fairy emails you, and see what changes for the buyer, the tickets and your reports.

For: Returning a buyer's money for an order they no longer want.

What an agent can do: Fai can request the authorisation code for an order and, once you give her the code from your email, refund it. She shows you the order and the amount and asks you to approve before any money moves, and she can turn on dashboard refunds for the event when they are off. Your own AI assistant can do the same over the MCP server, where each refund also waits for your approval in your MCP client.

Command line:

- Email yourself the authorisation code for an order without refunding it: `ticketfairy order refund <ORDER_HASH> --request-code-only`
- Refund the order with the code from your email: `ticketfairy order refund <ORDER_HASH> --code <CODE>`

CLI MCP tools that read: `select_event`, `get_order`.

CLI MCP tools that make changes (not available with `--read-only`): `request_refund_code`, `refund_order`.

Prompt for Fai: "Find order <ORDER NUMBER> on <EVENT NAME>, show me the buyer, the tickets and the amount that would be refunded, then request the refund authorisation code and wait for me to give you the code before refunding"

#### Then: Resend or cancel a code you have not used

What an agent can do: Fai can resend or revoke the code for an order. The CLI requests a fresh code with the same command as the first one.

Prompt for Fai: "Revoke the refund authorisation code for order <ORDER NUMBER> on <EVENT NAME>"

#### Then: Let buyers request their own refund

What an agent can do: Fai can turn buyer self-refunds on or off for an event after showing you what changes. The CLI sets the same switch through the event's attributes.

Prompt for Fai: "Turn on customer self-refunds for <EVENT NAME> and tell me what that changes for the payout"

### Resend a buyer's tickets and fix their details

Slug `resend-tickets-and-fix-a-buyers-details`. Guide: https://www.ticketfairy.com/guides/resend-tickets-and-fix-a-buyers-details

Send an order's tickets again to any email address the buyer gives you, and correct the name or email on a ticket so it matches the person arriving at the door.

For: Answering a buyer whose tickets went missing.

What an agent can do: Fai finds the order and reads what was sent and to which address. She can't send the tickets again or correct a name, so make either change yourself on the Orders page.

Prompt for Fai: "Find the order for <BUYER EMAIL ADDRESS> on <EVENT NAME> and tell me which tickets it holds and what state each one is in"

#### Then: Resend from the order itself

What an agent can do: Fai can find the order and read it out to you, and you resend the tickets yourself on the page.

Prompt for Fai: "Show me order <ORDER NUMBER> on <EVENT NAME> with the address it was sent to"

### Respond to a disputed ticket order

Slug `respond-to-a-disputed-ticket-order`. Guide: https://www.ticketfairy.com/guides/respond-to-a-disputed-ticket-order

When a buyer disputes their card payment with their bank, find the order, collect your evidence and send it in time, either by replying to our email or from the payments view of your own payment account.

For: Answering a buyer's chargeback so you can win the money back.

What an agent can do: no agent route is recorded for this guide. Send the organiser the guide link and walk them through the steps in the dashboard.

### Run a waiting list for a sold-out event

Slug `run-a-waiting-list`. Guide: https://www.ticketfairy.com/guides/run-a-waiting-list

Switch on the waiting list, decide how many tickets one person can ask for, see who is waiting, and find out how the next person in line is offered a returned ticket and how long they have to buy it.

For: Offering returned tickets to buyers who missed out.

What an agent can do: Fai can switch the waiting list on or off, set the most tickets one person can ask for when they sign up, tell you who is waiting and email the list. She shows you each change before she makes it. The whole workflow is also in the dashboard.

Command line:

- Turn on the ticket and add-on waiting lists for an event: `ticketfairy event update <EVENT_ID> --body '{"flagEnableWaitingList": true, "flagEnableAddOnWaitingList": true}'`

Prompt for Fai: "Turn on the waiting list for <EVENT NAME> for tickets and add-ons, cap each signup at <NUMBER> tickets, then show me who is waiting and how many tickets they asked for"

#### Then: Close the list without losing the names

What an agent can do: Fai can turn the waiting list off after showing you how many people are on it. The CLI sets the same attribute.

Prompt for Fai: "Tell me how many people are on the waiting list for <EVENT NAME>, then turn the waiting list off"

#### Then: Send returned tickets to the right ticket type

What an agent can do: Fai can create the categories and set each one's resale type after showing you the ticket types in it. The CLI does not manage categories.

Prompt for Fai: "On <EVENT NAME>, put each ticket type into a category by entry time and set the resale type so a returned ticket is offered as the same kind of admission"

### Sell a block of tickets to a company and invoice them

Slug `take-a-group-booking-and-invoice-it`. Guide: https://www.ticketfairy.com/guides/take-a-group-booking-and-invoice-it

Record a company's block of tickets with its purchase order and payment terms, get it signed off, and send the company one invoice with a due date that matches their terms.

For: Selling blocks of tickets to companies and teams.

What an agent can do: Fai can draft the booking, send it for sign-off and raise the invoice. She asks before each of those, because each one commits money or can go out to the company.

Prompt for Fai: "Create a group booking for <EVENT NAME>: forty passes for <COMPANY NAME> against <PURCHASER NAME OR EMAIL>, on the general admission ticket at its current price, purchase order 8841, thirty day terms, and show it to me before saving"

#### Then: Handle a booking that changes

What an agent can do: Fai can change a draft or cancel a booking once you approve it, and read back the ones waiting on sign-off or payment.

Prompt for Fai: "For <EVENT NAME>, which group bookings are still waiting to be paid"

### Turn on the ID check for buyers

Slug `turn-on-the-id-check-for-buyers`. Guide: https://www.ticketfairy.com/guides/turn-on-the-id-check-for-buyers

Ask Fai to turn on the ID check for an event, so each buyer proves who they are with a photo ID before we take their payment and issue their tickets.

For: Making sure every buyer has proved who they are before their tickets are issued.

What an agent can do: Fai turns the ID check on or off for one event. She shows you the change and asks you to approve it before she saves it. The command line and MCP have no setting for the ID check.

Prompt for Fai: "Turn on the ID check for buyers on <EVENT NAME> and show me the change before you save it"

#### Then: Turn off the ID check

What an agent can do: Fai turns the ID check off for one event after you approve the change.

Prompt for Fai: "Turn off the ID check for buyers on <EVENT NAME>"

### Win back buyers who left checkout

Slug `recover-abandoned-carts`. Guide: https://www.ticketfairy.com/guides/recover-abandoned-carts

Find the buyers who entered their details at checkout and never paid for their tickets, see why each one is on the list, and email them back to your event.

For: Turning lost checkouts into sales.

What an agent can do: Fai can check the list and tell you how big it is and how recent. You send the email in the dashboard, so she sends you to the composer, and MCP can't read this list.

Prompt for Fai: "For <EVENT NAME>, how many people left checkout without paying in the last <NUMBER> days, and how many of them never got as far as an order"

#### Then: The reminder Ticket Fairy sends for you

What an agent can do: Fai can check the abandoned-cart list and tell you how big it is and how recent. She can't see whether the automatic reminder runs for an event, so ask Ticket Fairy support about that one.

Prompt for Fai: "How many people left checkout on <EVENT NAME> yesterday without paying"

#### Then: What takes a row off the list

What an agent can do: Fai sees the same list, so she sees what's on it now. A buyer who has bought is already off it, and there's no record that they were ever on it.

Prompt for Fai: "For <EVENT NAME>, show me who is on the abandoned cart list now and how many times each of them reached checkout"

#### Then: When a buyer opts out

What an agent can do: Fai sees the tab, which includes opt-outs, so ask her for the total rather than for who will receive a send.

Prompt for Fai: "How many people are on the abandoned-cart list for <EVENT NAME>"

## More

- All guides: https://www.ticketfairy.com/guides
- Guides MCP server: https://www.ticketfairy.com/docs/mcp (tools `search_guides` and `get_guide`)
- CLI reference: https://www.npmjs.com/package/ticketfairy
- Developer documentation: https://www.ticketfairy.com/developers
- Support: support@ticketfairy.com
