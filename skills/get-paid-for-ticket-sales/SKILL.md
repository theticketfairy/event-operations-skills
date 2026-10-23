---
name: get-paid-for-ticket-sales
description: "Set up Ticket Fairy payment accounts, choose who pays the fees, pick currencies and follow payouts. Use when an organiser asks how and when they get their money."
---

# Get paid for ticket sales

This skill covers payment accounts, who pays the fees, currencies and payouts on Ticket Fairy. It lists the 3 published guides for this area and what an agent can do for each one.

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

- [Check the payout for your event](#check-the-payout-for-your-event)
- [Choose who pays the ticketing fee on your event](#choose-who-pays-the-ticketing-fee-on-your-event)
- [Take ticket money with a payment processing account](#take-ticket-money-with-a-payment-processing-account)

### Check the payout for your event

Slug `check-your-payout`. Guide: https://www.ticketfairy.com/guides/check-your-payout

See what your event has earned, whether the money has been released to you, which account it goes to and when to expect it.

For: Waiting on the money from an event you have run.

What an agent can do: Fai can tell you the same figures, and where you have a connected card account she lists the most recent payouts sent from it, with the date each one was due to land. Your bank statement confirms when each one arrived. In Vault, she also reads each event's payout from Vault: expected, on hold or paid, with the expected dates. Ticket Fairy releases the money after the event.

Prompt for Fai: "For <EVENT NAME>, what did it earn, and what has our card account paid out recently"

#### Then: When the money arrives

What an agent can do: Fai can read the event's dates and how it takes payments, which decide when the payout arrives.

Prompt for Fai: "When should the payout for <EVENT NAME> reach us"

#### Then: What holds a payout back

What an agent can do: Fai can check whether the event is postponed or cancelled and tell you what that means for the payout.

Prompt for Fai: "Is anything holding back the payout for <EVENT NAME>"

#### Then: See the balance and what has been paid

What an agent can do: Fai reads the payouts made and can break one down into its charges, refunds and fees, which helps when you can't reconcile a figure.

Prompt for Fai: "Break down the last payout for <BRAND NAME> into charges, refunds and fees"

### Choose who pays the ticketing fee on your event

Slug `set-who-pays-the-fees`. Guide: https://www.ticketfairy.com/guides/set-who-pays-the-fees

Decide whether buyers pay the ticketing fee on top or you include it in your ticket price, and see what each choice means for your price and your payout.

For: Deciding how ticketing fees appear on an event before tickets go on sale.

What an agent can do: Fai can set who pays the ticketing fee on an event and explains what each choice does to the price and your payout. She refuses a switch between Added and Absorbed once ticket types exist and asks you to approve any change first. The whole workflow is also in the dashboard.

Prompt for Fai: "For <EVENT NAME>, tell me which ticketing fee choice is set and what a <PRICE> ticket would cost the buyer and pay me under each choice, then set it to <ADDED OR ABSORBED> if that is still possible"

#### Then: Change the choice on an event that has ticket types

What an agent can do: Fai can make the change once the event has no ticket types, and tells you when it is locked.

Prompt for Fai: "Switch <EVENT NAME> to absorbed ticketing fees, and tell me first whether it still can be switched"

### Take ticket money with a payment processing account

Slug `connect-a-payment-account`. Guide: https://www.ticketfairy.com/guides/connect-a-payment-account

Link the account that takes card payments for your brand, make it the one new events use, and check when it's ready to take payments.

For: Setting up the account that takes card payments for a brand.

What an agent can do: Fai lists the accounts linked to a brand, renames an account, makes one the default, archives one, and puts a first account on every event that has not sold yet, if you ask for that as she links it. She starts a new Stripe account, a Full Stripe Account or a Xendit invite, and links a Stripe account your business already has where Ticket Fairy has turned that on for your brand; you start a Managed Account yourself, on the Payments page. She asks you to approve every change first, and a new account still needs you to open the link and finish the setup with the payment company.

Command line:

- List the payment processing accounts on a brand, with the account type, status and which one is the default: `ticketfairy api /api/organizations/<BRAND_ID>/brand-payment-methods --output json`

Prompt for Fai: "List the payment processing accounts on <BRAND NAME>, say which one new events will use, and tell me whether any of them still needs its setup finished"

#### Then: Finish a setup you started earlier

What an agent can do: Fai tells you which accounts on a brand are still unfinished. You finish one here, on its row, because a link she starts opens a new account rather than the one waiting in the table.

Prompt for Fai: "Which payment processing accounts on <BRAND NAME> still need their setup finished?"

#### Then: Give an account a name your team recognises

What an agent can do: Fai renames a payment processing account for you and pauses for your approval first. She shows you the current names so you can pick the one you meant.

Prompt for Fai: "Rename the payment processing account ending <LAST DIGITS> on <BRAND NAME> to <NEW NAME>"

#### Then: Stop using an account you have finished with

What an agent can do: Fai archives an account for you and pauses for your approval first. She archives the default too, which the Payments page does not offer, and another active account on the brand, if there is one, becomes the default, so check which account you are naming before you approve.

Prompt for Fai: "Archive the payment processing account named <ACCOUNT NAME> on <BRAND NAME>"

#### Then: Put a different account on one event

What an agent can do: Fai can tell you which account an event uses and change it, with your approval, while the event has no paid orders.

Prompt for Fai: "Which payment processing account is <EVENT NAME> using, and what else could it use?"

## More

- All guides: https://www.ticketfairy.com/guides
- Guides MCP server: https://www.ticketfairy.com/docs/mcp (tools `search_guides` and `get_guide`)
- CLI reference: https://www.npmjs.com/package/ticketfairy
- Developer documentation: https://www.ticketfairy.com/developers
- Support: support@ticketfairy.com
