---
name: use-vault-and-capital
description: "Use the Ticket Fairy Vault account, cards, transfers and invoices, and Capital working capital. Use when an organiser asks about their Vault balance, cards, transfers or funding."
---

# Use Vault and Capital

This skill covers the Vault account, cards, transfers, invoices and working capital on Ticket Fairy. It lists the 23 published guides for this area and what an agent can do for each one.

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

- [Add receipts, notes and events to your team's Vault card payments](#add-receipts-notes-and-events-to-your-teams-vault-card-payments)
- [Apply for a line of credit to pay your event costs](#apply-for-a-line-of-credit-to-pay-your-event-costs)
- [Collect table deposits, venue hire and sponsorship for your events with Vault payment links](#collect-table-deposits-venue-hire-and-sponsorship-for-your-events-with-vault-payment-links)
- [Convert currencies and follow every movement of your event money in Vault](#convert-currencies-and-follow-every-movement-of-your-event-money-in-vault)
- [Freeze, cancel or change the limits on an event team's Vault card](#freeze-cancel-or-change-the-limits-on-an-event-teams-vault-card)
- [Get a Vault statement of your event money for your accountant](#get-a-vault-statement-of-your-event-money-for-your-accountant)
- [Get paid for your events in local currencies with Vault](#get-paid-for-your-events-in-local-currencies-with-vault)
- [Invoice sponsors and partners for your event from Vault](#invoice-sponsors-and-partners-for-your-event-from-vault)
- [Issue Vault cards to your whole event crew at once](#issue-vault-cards-to-your-whole-event-crew-at-once)
- [Let Fai prepare the finance work after your events](#let-fai-prepare-the-finance-work-after-your-events)
- [Let your event team spend with Vault cards](#let-your-event-team-spend-with-vault-cards)
- [Make a second person send every payment from your event money](#make-a-second-person-send-every-payment-from-your-event-money)
- [Mark a supplier you pay every event as trusted](#mark-a-supplier-you-pay-every-event-as-trusted)
- [Open a Vault account for event money with the older setup form](#open-a-vault-account-for-event-money-with-the-older-setup-form)
- [Open a Vault account to hold your ticket money](#open-a-vault-account-to-hold-your-ticket-money)
- [Pay everyone you owe for an event](#pay-everyone-you-owe-for-an-event)
- [Pay your event suppliers from Vault](#pay-your-event-suppliers-from-vault)
- [Pay your event's artists, suppliers and crew at once from Vault](#pay-your-events-artists-suppliers-and-crew-at-once-from-vault)
- [Pay your venue rent, artist residencies and regular event suppliers automatically from Vault](#pay-your-venue-rent-artist-residencies-and-regular-event-suppliers-automatically-from-vault)
- [Report a problem with an event supplier's Vault card payment and follow the dispute](#report-a-problem-with-an-event-suppliers-vault-card-payment-and-follow-the-dispute)
- [See how much of your ticket money you can spend from Vault](#see-how-much-of-your-ticket-money-you-can-spend-from-vault)
- [See what each event earned in Vault](#see-what-each-event-earned-in-vault)
- [Track what your event team spends on Vault cards](#track-what-your-event-team-spends-on-vault-cards)

### Add receipts, notes and events to your team's Vault card payments

Slug `add-receipts-to-vault-card-payments`. Guide: https://www.ticketfairy.com/guides/add-receipts-to-vault-card-payments

Add a photo or PDF of the receipt to each Vault card payment, see whether its total matches the payment, note what it was for and link it to the event, and let Fai remind cardholders about receipts that are missing.

For: Keeping a receipt and a reason behind every card payment.

What an agent can do: Fai lists your card payments with their receipts, notes and events. After you agree, she sets the note and the event on a payment, and adds a receipt that is already in your brand's documents. She can't save a photo you share in the chat, so add that receipt in Card activity or to your brand's documents first. MCP and the command line change nothing here.

Prompt for Fai: "Note the Vault card payment of <AMOUNT> at <MERCHANT> as <WHAT IT WAS FOR> and link it to <EVENT NAME>"

#### Then: Replace or remove a receipt

What an agent can do: After you agree, Fai replaces a receipt with one that is already in your brand's documents, or removes a receipt from a payment. Vault notes the change in the same way.

Prompt for Fai: "Remove the receipt from the Vault card payment of <AMOUNT> at <MERCHANT>"

#### Then: Let Fai remind cardholders about receipts

What an agent can do: Fai finds card payments without a receipt and, after you accept, emails the cardholder a reminder. She tells you the amount to remind from, and changes it after you agree if you're the brand owner.

Prompt for Fai: "Only remind our cardholders about missing receipts on Vault card payments of <AMOUNT> or more"

### Apply for a line of credit to pay your event costs

Slug `apply-for-a-line-of-credit-for-your-event-costs`. Guide: https://www.ticketfairy.com/guides/apply-for-a-line-of-credit-for-your-event-costs

Open Line of Credit in your brand's menu and complete the credit application inside your dashboard. The application uses your Ticket Fairy login, so you can come back to it from the same page.

For: Brands in the United States looking for working capital.

What an agent can do: no agent route is recorded for this guide. Send the organiser the guide link and walk them through the steps in the dashboard.

### Collect table deposits, venue hire and sponsorship for your events with Vault payment links

Slug `get-paid-with-vault-payment-links`. Guide: https://www.ticketfairy.com/guides/get-paid-with-vault-payment-links

Create a payment link from Vault for a VIP table deposit, venue hire, a sponsorship instalment, merchandise pre-orders or a group deposit for your event, share it or email it, and see how many times it was paid and what it collected, with the money going straight into your Vault balance.

For: Collecting deposits and other payments around your events.

What an agent can do: Fai can create a payment link with a set amount or one the payer chooses, list your links with what each one collected, email a link, and turn a link off or back on. She shows you the link's details and asks before each change. MCP and the command line have no payment link commands.

Prompt for Fai: "Create a Vault payment link for <BRAND NAME> for a <AMOUNT> <CURRENCY> VIP table deposit at <EVENT NAME> that can be paid once, then email it to <EMAIL>"

#### Then: Send a payment link by email

What an agent can do: Fai can email a payment link that is taking payments, after she shows you the link and the address and you agree.

Prompt for Fai: "Email the Vault payment link <LINK NAME> to <EMAIL>"

#### Then: Turn a payment link off or back on

What an agent can do: Fai can turn a payment link off or back on after she shows you which link and you agree.

Prompt for Fai: "Turn off the Vault payment link <LINK NAME>, we've had enough deposits"

### Convert currencies and follow every movement of your event money in Vault

Slug `convert-currencies-and-read-your-vault-activity`. Guide: https://www.ticketfairy.com/guides/convert-currencies-and-read-your-vault-activity

See every movement in and out of your Vault balances for your events, from ticket money in to artist payments and card spending, with the balance after each one, and convert money between currencies at a rate you see and agree to first.

For: Holding and converting the currencies your events earn and spend.

What an agent can do: Fai can list the movements in your balances for any dates, currency and type, get a rate, and convert money between your balances after she shows you the rate, the mid-market rate and the difference between them and you agree. You may still need to confirm it's you in Vault. MCP and the command line have no commands for this.

Prompt for Fai: "Show me every Vault movement in <CURRENCY> for <BRAND NAME> last month, then get me a rate to convert <AMOUNT> <CURRENCY> into <CURRENCY> for <EVENT NAME>"

#### Then: Cancel a conversion

What an agent can do: Fai can tell you what cancelling a conversion costs and cancel it after you agree.

Prompt for Fai: "What would it cost to cancel the Vault conversion of <AMOUNT> <CURRENCY> into <CURRENCY>? Cancel it if it's under <AMOUNT>"

### Freeze, cancel or change the limits on an event team's Vault card

Slug `freeze-cancel-or-change-a-vault-card`. Guide: https://www.ticketfairy.com/guides/freeze-cancel-or-change-a-vault-card

Freeze a Vault card your event team spends with, unfreeze it, cancel it for good, change its spending limits or where and when it works, rename it or link it to the event it pays for, all from the card in Vault.

For: Keeping control of the cards your event team spends with.

What an agent can do: Fai can freeze, unfreeze or cancel a card, change its limits and controls, rename it and link it to an event. She names the card and the change and asks before each one, and you may still need to confirm it's you in Vault. MCP and the command line read cards but change nothing.

Prompt for Fai: "Freeze the Vault card <CARD NAME> for <BRAND NAME>, it has been lost"

#### Then: Unfreeze a card

What an agent can do: Fai can unfreeze a frozen card after she names it and you agree.

Prompt for Fai: "Unfreeze the Vault card <CARD NAME>, we found it"

#### Then: Cancel a card for good

What an agent can do: Fai can cancel a card after she names it, says it can't be undone and you agree.

Prompt for Fai: "Cancel the Vault card <CARD NAME> for good, the person has left"

#### Then: Change a card's spending limits

What an agent can do: Fai can set a card's per-payment, daily and monthly limits after she shows you the new limits and you agree.

Prompt for Fai: "Raise the monthly limit on the Vault card <CARD NAME> to <AMOUNT>"

#### Then: Change where and when a card works

What an agent can do: Fai can change the ways to pay, cash withdrawals, kinds of business and dates on a card after she shows you the new controls and you agree.

Prompt for Fai: "Make the Vault card <CARD NAME> work only from <START DATE> to <END DATE>"

#### Then: Link a card to an event

What an agent can do: Fai can link a card to one of your events, or remove the link, after you agree.

Prompt for Fai: "Link the Vault card <CARD NAME> to <EVENT NAME>"

#### Then: Rename a card

What an agent can do: Fai can rename a card after you agree.

Prompt for Fai: "Rename the Vault card <CARD NAME> to <NEW NAME>"

### Get a Vault statement of your event money for your accountant

Slug `get-a-vault-statement`. Guide: https://www.ticketfairy.com/guides/get-a-vault-statement

Download an official PDF statement of one Vault currency, or a file of every payment in and out of your event money, for any dates up to a year, see who asked for each one, and download a letter that proves you paid an artist or supplier.

For: Handing your accountant a record of your event money.

What an agent can do: Fai can ask Vault for a statement or an activity export after you agree, and tell you when it is ready. You download the file yourself on the Statements page. MCP and the command line have no statement commands.

Prompt for Fai: "Get me a PDF statement of our GBP Vault balance for last month for <BRAND NAME>"

#### Then: Download proof that you paid someone

What an agent can do: You download a payment confirmation yourself in Transfer details. Fai can find the payment and tell you whether it was sent.

Prompt for Fai: "Did our Vault payment to <RECIPIENT> for <AMOUNT> go through, and when was it sent?"

### Get paid for your events in local currencies with Vault

Slug `receive-money-in-global-accounts`. Guide: https://www.ticketfairy.com/guides/receive-money-in-global-accounts

Open a Vault receiving account for a currency, such as pounds, euros or dollars, and give its bank details to sponsors, partners and anyone else who pays your events by bank transfer. Each payment arrives in Vault in that currency.

For: Taking bank transfers for your events in the currencies you are paid in.

What an agent can do: Fai can list your receiving accounts, give you the bank details a payer needs and show the money each account has received. She can also open a new receiving account for you. She shows you the country, currency, transfer method and name, and asks before she opens it. MCP and the command line have no commands for receiving accounts.

Prompt for Fai: "Open a <CURRENCY> receiving account in Vault for <BRAND NAME> and give me the bank details to send to <PAYER NAME>"

#### Then: Rename a receiving account

What an agent can do: Fai can rename a receiving account for you. She shows you the account and the new name, and asks before she saves it. The bank details stay the same.

Prompt for Fai: "Rename the <CURRENCY> Vault receiving account for <BRAND NAME> to <NEW NAME>"

#### Then: Close a receiving account

What an agent can do: Fai can close a receiving account for you. She shows you the account, tells you that closing it can't be undone, and asks before she closes it.

Prompt for Fai: "Close the <CURRENCY> Vault receiving account for <BRAND NAME>"

### Invoice sponsors and partners for your event from Vault

Slug `manage-vault-invoices`. Guide: https://www.ticketfairy.com/guides/manage-vault-invoices

Raise an invoice from your brand's Vault for a sponsor, a trader or a partner venue at your event, finalise it and send them its link, then mark it paid or void it if plans change.

For: Invoicing the sponsors, traders and venues behind your events.

What an agent can do: Fai can list your invoices and billing customers, add a customer and create a draft invoice. She can also finalise a draft, mark an invoice as paid and void one. She shows you the invoice and asks before each change. You add line items in the dashboard, because Fai creates the draft without them.

Command line:

- Show the brands you can act for, with their ids: `ticketfairy brand list`
- List the brand's Vault invoices, with each invoice's number, status, payment status and total: `ticketfairy api /api/brand/<BRAND_ID>/banking/invoices --output json`

Prompt for Fai: "Create a draft <CURRENCY> invoice in Vault for <CUSTOMER NAME> on <BRAND NAME>, due in 30 days"

#### Then: Mark an invoice as paid

What an agent can do: Fai can mark a finalised invoice as paid for you. She shows you the invoice, tells you that no money moves and that it can't be undone, and asks before she records it.

Prompt for Fai: "Mark Vault invoice <INVOICE NUMBER> for <BRAND NAME> as paid"

#### Then: Void an invoice you no longer want paid

What an agent can do: Fai can void a finalised, unpaid invoice for you. She shows you the invoice, tells you that it can't be undone, and asks before she voids it.

Prompt for Fai: "Void Vault invoice <INVOICE NUMBER> for <BRAND NAME>"

#### Then: Change a draft before you finalise it

What an agent can do: You change a draft invoice in the dashboard. Fai can open the Invoices page in Vault for you.

Prompt for Fai: "Open the Vault invoices for <BRAND NAME> so I can change a draft"

#### Then: Add a product or price you haven't invoiced before

What an agent can do: You add products and prices in the dashboard, from the invoice you're working on. Fai can open the Invoices page in Vault for you.

Prompt for Fai: "Open the Vault invoices for <BRAND NAME> so I can add a line item"

### Issue Vault cards to your whole event crew at once

Slug `issue-vault-cards-to-your-event-crew`. Guide: https://www.ticketfairy.com/guides/issue-vault-cards-to-your-event-crew

Give up to 50 people on your event crew a virtual Vault card each in one go, with one set of controls, the event linked and a name on every card, then see which cards were issued.

For: Giving your event crew their own spending cards.

What an agent can do: Fai can issue up to 50 virtual cards to cardholders you have already added, with one preset, limits and the event. She shows you every card and its controls and asks before she issues them. MCP and the command line have no command for this.

Prompt for Fai: "Issue virtual crew cards for <EVENT NAME> to <CARDHOLDER NAME>, <CARDHOLDER NAME> and <CARDHOLDER NAME>, with a daily limit of <AMOUNT>"

### Let Fai prepare the finance work after your events

Slug `let-fai-prepare-your-finance-work`. Guide: https://www.ticketfairy.com/guides/let-fai-prepare-your-finance-work

Let Fai prepare the routine finance work around your events in Vault: who to pay after a show, percentage deal fees with her working shown, payment batches, invoice reminders and card spend on event budgets. You accept, change or dismiss each one, and Fai never sends money on her own.

For: Getting help with the finance work that follows every event.

What an agent can do: You can ask Fai in chat what she prepared and how she worked any of it out, from the same facts, working and sources the card shows. She accepts, dismisses or undoes a suggestion only after she shows you what will happen and you agree, and a money suggestion only prepares a payment that a person on your team sends. MCP and the command line have no commands for this.

Prompt for Fai: "What have you prepared in Vault for <BRAND NAME>, and how did you work out <ARTIST NAME>'s fee?"

#### Then: Choose what Fai does for you

What an agent can do: Fai can change what she does for each kind of work for a brand owner, after she shows you the change and you agree. She can't set a kind that moves money to Do it for me.

Prompt for Fai: "Stop suggesting invoice reminders for <BRAND NAME>, and add card spend to event budgets for me automatically"

#### Then: Undo something Fai did for you

What an agent can do: Fai can undo a card payment she added to an event budget on her own, after you agree.

Prompt for Fai: "Undo the card payment you added to the <EVENT NAME> budget"

### Let your event team spend with Vault cards

Slug `issue-vault-cards`. Guide: https://www.ticketfairy.com/guides/issue-vault-cards

Issue a virtual or physical Vault card in a team member's name for an event, a supplier or online subscriptions, with the limits, dates and places it works set for you, so the people running your events pay straight from the ticket money in Vault.

For: Giving the people who spend for your events a card of their own.

What an agent can do: Fai can issue virtual cards to cardholders you have already added, with a crew, supplier or subscriptions preset and the limits and event you give her. She shows you each card and its controls and asks before she issues anything. You add a cardholder and issue a physical card on the Cards page. The command line lists the cards you have issued, and MCP has no card tools.

Command line:

- List the cards issued on the brand's Vault account, with the id of each: `ticketfairy vault cards list --brand <BRAND_ID>`
- Show one card's spending limits, using an id from the list: `ticketfairy vault cards get <CARD_ID> --brand <BRAND_ID> --limits`

Prompt for Fai: "Issue <CARDHOLDER NAME> a virtual crew card for <EVENT NAME> with a daily limit of <AMOUNT> from our Vault for <BRAND NAME>"

#### Then: Show a card's full number

What an agent can do: Only you can show a card's full details, on the page. Fai, MCP and the command line never show a card number.

#### Then: Change a cardholder's details

What an agent can do: Fai opens the Cardholders page for you. You change the person's details there yourself.

Prompt for Fai: "Open the Vault cardholders page for <BRAND NAME>"

#### Then: Stop a team member's cards

What an agent can do: Fai opens the Cardholders page for you. You delete the cardholder there yourself, after a confirmation.

Prompt for Fai: "Open the Vault cardholders page for <BRAND NAME>"

### Make a second person send every payment from your event money

Slug `turn-on-payment-approvals`. Guide: https://www.ticketfairy.com/guides/turn-on-payment-approvals

Turn on payment approvals in Vault so every payment from your event money needs two people: one prepares it and a different owner sends it. It covers payment batches, single payments and recurring payments.

For: Owners who want two people on every payment from their event money.

What an agent can do: Fai can tell you whether the rule is on and, for a brand owner, turn it on or off after you agree. MCP and the command line have no command for it.

Prompt for Fai: "Turn on payment approvals for <BRAND NAME> so a second person has to send every payment"

#### Then: Turn payment approvals off

What an agent can do: Fai can turn the rule off for a brand owner, after she shows you the change and you agree.

Prompt for Fai: "Turn off payment approvals for <BRAND NAME>"

### Mark a supplier you pay every event as trusted

Slug `trust-a-payout-recipient`. Guide: https://www.ticketfairy.com/guides/trust-a-payout-recipient

Give a venue or supplier you pay for every event trusted status in Vault, so payments to them ask for fewer security checks. One owner asks for it, a 24-hour cooling period runs, and a second owner approves it.

For: Letting the suppliers you pay every event through with fewer security checks.

What an agent can do: Owners ask for, approve and remove trusted status themselves in the dashboard, because each one changes how payments to a supplier are checked. Fai can open Recipients in Vault for you.

Prompt for Fai: "Open the Vault recipients for <BRAND NAME>"

#### Then: Reject a trust request

What an agent can do: An owner rejects a request in the dashboard. Fai can open Recipients in Vault for you.

Prompt for Fai: "Open the Vault recipients for <BRAND NAME>"

#### Then: Remove trusted status

What an agent can do: An owner removes trusted status in the dashboard, with a security check. Fai can open Recipients in Vault for you.

Prompt for Fai: "Open the Vault recipients for <BRAND NAME>"

### Open a Vault account for event money with the older setup form

Slug `open-a-vault-account-with-the-older-setup-form`. Guide: https://www.ticketfairy.com/guides/open-a-vault-account-with-the-older-setup-form

Open an account for your event money when Vault offers Create new account instead of Financial setup. Enter the business and its people, then complete secure verification from the account card.

For: Opening the account your brand holds its event money in.

What an agent can do: Fai opens Vault for you. You create the account and answer the verification questions yourself on the page, because they're about you and your business. MCP and the command line read the account and its status while you wait for the check, and create nothing.

Command line:

- List the brands you can act for, with the id each one uses: `ticketfairy brand list`
- Print the brand's Vault account as JSON. Its metadata.status reads ACTIVE once the check has passed: `ticketfairy vault account --brand <BRAND_ID> --output json`

CLI MCP tools that read: `select_brand`, `get_vault_account`.

Prompt for Fai: "Open Vault for <BRAND NAME> so I can open an account"

### Open a Vault account to hold your ticket money

Slug `open-a-vault-account`. Guide: https://www.ticketfairy.com/guides/open-a-vault-account

Open your brand's Vault account for event money by completing Financial setup. Save your business details, add its people and documents, then review the agreements and send the details for verification.

For: Brand owners opening an account for their event money.

What an agent can do: Fai can open Financial setup and tell a brand owner the saved profile's status and any requests for more information. You enter private identity details, upload documents and accept agreements yourself. Fai does not accept legal terms or submit account opening for you. MCP and the command line can read the Vault account and its status without creating an account.

Command line:

- List the brands you can act for, with the id each one uses: `ticketfairy brand list`
- Print the brand's Vault account as JSON. Its metadata.status reads ACTIVE once the check has passed: `ticketfairy vault account --brand <BRAND_ID> --output json`

CLI MCP tools that read: `select_brand`, `get_vault_account`.

Prompt for Fai: "Open Financial setup for <BRAND NAME> so I can open its Vault account"

### Pay everyone you owe for an event

Slug `pay-everyone-you-owe-for-an-event`. Guide: https://www.ticketfairy.com/guides/pay-everyone-you-owe-for-an-event

Keep one list of the artists, suppliers, venues and crew an event has to pay, started for you from your artist and supplier bookings, then pay the people on it together from Vault and see each one move from to pay to paid.

For: Settling up with the artists, suppliers and crew behind an event.

What an agent can do: Fai can tell you who an event owes, add people to the list, change them, mark them as paid another way and prepare one batch to pay them. She shows you each change and asks before she makes it, and she never sends money: a person on your team sends the batch in Vault. MCP and the command line have no commands for this list.

Prompt for Fai: "For <EVENT NAME>, add the suggestions from our bookings to who we owe, then prepare a batch to pay everyone who has bank details"

#### Then: Mark someone as paid another way

What an agent can do: Fai can mark a person as paid another way, or put them back as still to pay, after she shows you the change and you agree.

Prompt for Fai: "Mark <NAME> as paid another way for <EVENT NAME>, we paid them in cash"

#### Then: Change or remove someone

What an agent can do: Fai can change the amount, recipient or note on a person still to pay, or remove them, after she shows you the change and you agree.

Prompt for Fai: "Change the amount we owe <NAME> for <EVENT NAME> to <AMOUNT>"

### Pay your event suppliers from Vault

Slug `pay-suppliers-from-your-vault`. Guide: https://www.ticketfairy.com/guides/pay-suppliers-from-your-vault

Send a bank transfer from your Vault balance to the venue, crew or supplier behind your event, with the reference they'll see on their statement, and follow it until it's paid.

For: Paying the venues, suppliers and crew behind your events.

What an agent can do: Fai can find a saved recipient and send them a transfer, now or on a date and from any balance you hold. She shows you the whole payment and asks before she sends it, and you may still need to finish the security check in Vault. When your team needs a second person, she offers to prepare the payment for approval instead. You add a supplier you haven't paid before in the dashboard.

Prompt for Fai: "Pay <SUPPLIER NAME> <AMOUNT> from our Vault for <BRAND NAME>, reference <INVOICE NUMBER>, it's for <WHAT THE PAYMENT IS FOR>"

#### Then: Add a supplier you haven't paid before

What an agent can do: To add a recipient, you enter the supplier's bank details yourself in the dashboard. Fai can open Recipients in Vault for you.

Prompt for Fai: "Open the Vault recipients for <BRAND NAME>"

#### Then: Resolve a transfer awaiting confirmation

What an agent can do: Fai can check whether a transfer is awaiting confirmation and retry the same payment for you. She shows you the amount, the recipient and the reference and asks before she retries, and you may need to finish the security check in Vault.

Prompt for Fai: "Is a Vault transfer waiting for confirmation on <BRAND NAME>? Check it, and retry the same payment if it's still stuck"

#### Then: Cancel a transfer

What an agent can do: Fai can cancel a transfer that hasn't been sent yet. She shows you the payment, tells you that cancelling may cost a fee that isn't refunded and can't be undone, and asks before she cancels it.

Prompt for Fai: "Cancel the Vault transfer to <SUPPLIER NAME> for <AMOUNT> on <BRAND NAME>"

### Pay your event's artists, suppliers and crew at once from Vault

Slug `pay-several-people-at-once`. Guide: https://www.ticketfairy.com/guides/pay-several-people-at-once

Prepare one batch of up to 100 payments to the performers, suppliers, venues and staff behind an event, typed in or uploaded from a spreadsheet, check what each payment costs, then send it from Vault now or on a date, paying from any balance you hold and with an optional rule that a second person sends it.

For: Paying the performers, suppliers and crew behind your events in one go.

What an agent can do: Fai can prepare a batch for saved recipients, with a payment date and a payment taken from another balance, check what each payment costs and, after you agree, send a prepared one. She shows you every payment, the totals and the date and asks before each step, you may still need to confirm it's you in Vault, and she follows your team's second-person rule. You upload a spreadsheet in Vault. MCP and the command line have no batch commands.

Prompt for Fai: "Prepare a Vault batch for <BRAND NAME> paying <RECIPIENT> <AMOUNT> and <RECIPIENT> <AMOUNT> for <EVENT NAME> on <DATE>, check what it costs, then show me it before anything is sent"

#### Then: Check a batch that says Checking

What an agent can do: Fai can tell you where a batch stands and each payment's status. You check again or send again on the batch in Vault, or ask Fai to send it after you agree.

Prompt for Fai: "Where does the Vault batch <BATCH NAME> stand, and did every payment go through?"

#### Then: Cancel a batch before it is sent

What an agent can do: Fai can cancel a batch that hasn't been sent, after she shows you which batch and you agree.

Prompt for Fai: "Cancel the Vault batch <BATCH NAME>, it hasn't been sent"

### Pay your venue rent, artist residencies and regular event suppliers automatically from Vault

Slug `set-up-recurring-payments-from-vault`. Guide: https://www.ticketfairy.com/guides/set-up-recurring-payments-from-vault

Set up a recurring payment from Vault that pays a venue, a resident artist or a regular event supplier the same amount every week, every month or once on a date, then pause, resume or stop it, with a second person approving it when your team needs one.

For: Paying the same venue, artist or supplier on a regular schedule for your events.

What an agent can do: Fai can set up a recurring payment to a saved recipient, list your recurring payments, and pause, resume, stop, approve or decline one. She shows you the recipient, the amount and the schedule and asks before each change, and you may still need to confirm it's you in Vault. When your team needs a second person, she can't approve a payment you set up yourself. MCP and the command line have no commands for recurring payments.

Prompt for Fai: "Set up a Vault recurring payment for <BRAND NAME> paying <RECIPIENT> <AMOUNT> every month on day <DAY>, starting <DATE>, reference <REFERENCE>"

#### Then: Approve a recurring payment a teammate set up

What an agent can do: Fai can approve or decline a recurring payment a teammate set up, after she shows you the recipient, the amount and the schedule and you agree.

Prompt for Fai: "Show me the Vault recurring payments waiting for approval for <BRAND NAME>, then approve the one to <RECIPIENT>"

#### Then: Pause, resume or stop a recurring payment

What an agent can do: Fai can pause, resume or stop a recurring payment after she shows you which one and you agree. She asks you to confirm again before she stops one for good.

Prompt for Fai: "Pause the Vault recurring payment to <RECIPIENT> for <BRAND NAME> until I say so"

### Report a problem with an event supplier's Vault card payment and follow the dispute

Slug `report-a-problem-with-a-vault-card-payment`. Guide: https://www.ticketfairy.com/guides/report-a-problem-with-a-vault-card-payment

Report a Vault card payment for your event that was charged twice, never arrived or that you don't recognise, in your own words and with evidence, then follow the dispute under Disputes in Card activity until the card network decides.

For: Getting money back for a card payment that went wrong.

What an agent can do: Fai can report a problem with a card payment in your own words, for the whole payment or part of it, with documents you have already added as evidence. She shows you the report and asks before she sends it, and you may need to confirm it's you in Vault. She also lists your disputes and where each one stands. MCP and the command line change nothing here.

Prompt for Fai: "Dispute the Vault card payment of <AMOUNT> at <MERCHANT>, we were charged twice"

### See how much of your ticket money you can spend from Vault

Slug `read-your-vault-balances`. Guide: https://www.ticketfairy.com/guides/read-your-vault-balances

See on the Vault Overview how much of your ticket money you can spend today in each currency, what is on its way and what is held, what needs your attention, and your latest events, with quick actions for the common jobs.

For: Checking what money your brand holds in Vault.

What an agent can do: Fai can tell you your balances, and can open Vault when you want the page. You move money on the page itself, behind the extra sign-in it needs.

Command line:

- Show the brands you can act for: `ticketfairy brand list`
- Show the brand's Vault balances: `ticketfairy vault balance --brand <BRAND_ID>`

CLI MCP tools that read: `select_brand`, `get_vault_balance`.

Prompt for Fai: "What is in Vault for <BRAND NAME> right now, and how much of it is still settling?"

#### Then: Check the account itself is healthy

What an agent can do: Fai can open Vault so you can read the account status. The MCP server and the CLI print it for you.

Command line:

- Show the brand's Vault account and its status: `ticketfairy vault account --brand <BRAND_ID>`

CLI MCP tools that read: `select_brand`, `get_vault_account`.

Prompt for Fai: "Open Vault for <BRAND NAME> so I can check the account status"

### See what each event earned in Vault

Slug `see-what-your-event-earned`. Guide: https://www.ticketfairy.com/guides/see-what-your-event-earned

See what each event took in ticket sales, add-ons and extras such as accommodation, what came off, such as refunds, partner shares, Capital and lost disputes, and the estimate of what reaches you.

For: Settling up the money from each event you run.

What an agent can do: Fai can tell you the same figures: every event with where its money goes and when it pays out, and one event's full statement with the estimate marked as an estimate. She can also explain your travel markup earned, not yet earned and paid out, separately from your ticket payout. She doesn't change anything to answer. MCP and the command line have no event money commands.

Prompt for Fai: "What did <EVENT NAME> make, what came off it, and when does the payout reach us?"

### Track what your event team spends on Vault cards

Slug `track-vault-spending`. Guide: https://www.ticketfairy.com/guides/track-vault-spending

See every payment your event team's Vault cards make, with holds, refunds and declined payments and the reason each was declined, and the Vault work in the Action centre that needs someone to act, with its priority and deadline.

For: Keeping track of card spend and Vault reviews for your events.

What an agent can do: Fai can tell you what's in the Action centre, with each task's priority, team and deadline, and opens a task for its details. She also lists your card activity with the merchant, amount, status and any reason a payment was declined. With MCP or the command line, you can list the card activity, but not the Action centre.

Command line:

- List the card events on the brand's Vault cards, newest first, with the id of each: `ticketfairy vault transactions list --brand <BRAND_ID>`
- Open one card event with its merchant, amount and status, using an id from the list: `ticketfairy vault transactions get <TRANSACTION_ID> --brand <BRAND_ID>`

CLI MCP tools that read: `select_brand`, `list_vault_transactions`.

Prompt for Fai: "What is waiting for us in the Vault action centre for <BRAND NAME>, and what is due first?"

## More

- All guides: https://www.ticketfairy.com/guides
- Guides MCP server: https://www.ticketfairy.com/docs/mcp (tools `search_guides` and `get_guide`)
- CLI reference: https://www.npmjs.com/package/ticketfairy
- Developer documentation: https://www.ticketfairy.com/developers
- Support: support@ticketfairy.com
