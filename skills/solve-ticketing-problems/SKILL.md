---
name: solve-ticketing-problems
description: "Solve common event ticketing problems with Ticket Fairy: queues, no-shows, reports, marketing and access. Use when an organiser describes a problem rather than a feature."
---

# Solve ticketing problems

This skill covers queues, no-shows, reports, marketing and access on Ticket Fairy. It lists the 16 published guides for this area and what an agent can do for each one.

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

- [Can ticket buyers join your email list automatically?](#can-ticket-buyers-join-your-email-list-automatically)
- [Can you hold and spend your ticket money without a separate bank?](#can-you-hold-and-spend-your-ticket-money-without-a-separate-bank)
- [Can you run a festival's marketing and production from one dashboard?](#can-you-run-a-festivals-marketing-and-production-from-one-dashboard)
- [How can fan club members get presale access?](#how-can-fan-club-members-get-presale-access)
- [How do you answer a ticket sales question no report covers?](#how-do-you-answer-a-ticket-sales-question-no-report-covers)
- [How do you keep a high-demand on-sale running smoothly?](#how-do-you-keep-a-high-demand-on-sale-running-smoothly)
- [How do you keep touts and bots off your tickets?](#how-do-you-keep-touts-and-bots-off-your-tickets)
- [How do you manage accreditation and backstage passes for your event?](#how-do-you-manage-accreditation-and-backstage-passes-for-your-event)
- [How do you manage many events without repeating the same work?](#how-do-you-manage-many-events-without-repeating-the-same-work)
- [How do you manage tickets for a multi-day event?](#how-do-you-manage-tickets-for-a-multi-day-event)
- [How do you run a guest list for your event without a spreadsheet?](#how-do-you-run-a-guest-list-for-your-event-without-a-spreadsheet)
- [How do you sell more tickets without spending more on ads?](#how-do-you-sell-more-tickets-without-spending-more-on-ads)
- [What can you find out about the people who buy your tickets?](#what-can-you-find-out-about-the-people-who-buy-your-tickets)
- [What is social ticketing, and how do referral rewards work?](#what-is-social-ticketing-and-how-do-referral-rewards-work)
- [What marketing tools should a ticketing platform give you?](#what-marketing-tools-should-a-ticketing-platform-give-you)
- [What should you compare when choosing a ticketing platform?](#what-should-you-compare-when-choosing-a-ticketing-platform)

### Can ticket buyers join your email list automatically?

Slug `add-ticket-buyers-to-your-email-list`. Guide: https://www.ticketfairy.com/guides/add-ticket-buyers-to-your-email-list

Yes. Connect your email platform once, and every buyer who opts in joins the audience you choose after checkout, while a buyer who later opts out comes off it.

For: Sending campaigns to the people who buy your tickets.

What an agent can do: Fai can show which email platforms your brand can connect, choose the audience once a connection exists, change the sync settings and disconnect it later. Connect the platform in the dashboard under brand settings, using its sign-in button or API key form. Keep an API key in that form rather than in a message to Fai. She asks before she changes a sync, because the change can start sending buyer details to the platform.

Prompt for Fai: "Show me which email platforms this brand can connect and which are connected already. For the connected one, show me the audiences I can pick and what the sync settings are now."

### Can you hold and spend your ticket money without a separate bank?

Slug `hold-and-spend-your-ticket-money-in-one-place`. Guide: https://www.ticketfairy.com/guides/hold-and-spend-your-ticket-money-in-one-place

Yes. When your events take payment through TF Pay, the money stays in your Vault balance, in each currency you sell in, ready to spend on a card, pay suppliers or invoice a client.

For: Paying for an event out of the ticket money you have already taken.

What an agent can do: Fai opens Vault and tells you a balance. You move money yourself on the page, so a chat message alone never moves money out of an account.

CLI MCP tools that read: `select_brand`.

Prompt for Fai: "What is in our Vault balance right now, and how much of it is still settling?"

### Can you run a festival's marketing and production from one dashboard?

Slug `run-a-festival-from-one-dashboard`. Guide: https://www.ticketfairy.com/guides/run-a-festival-from-one-dashboard

Tickets, the schedule, the artists, their travel, the crew, the budget and every message to buyers all sit on the same event, so you don't need a second tool for any of it.

For: Running a festival's tickets and production on the same event.

What an agent can do: Fai can check all of it in one question: what is unsold, what is unbooked, what is late. She drafts the messages and asks you before anything changes your event.

CLI MCP tools that read: `select_event`, `get_event`.

Prompt for Fai: "For <EVENT NAME>, tell me what is behind: unsold ticket types, artists with no travel booked and tasks past their date"

### How can fan club members get presale access?

Slug `give-fan-club-members-presale-access`. Guide: https://www.ticketfairy.com/guides/give-fan-club-members-presale-access

Take registrations before the on-sale, then give registered fans a presale window before tickets open to everybody.

For: Rewarding a fan club, members list or mailing list.

What an agent can do: Fai can check and set the pre-registration and presale date windows for the event, including the switches and both ends of each window. She asks before saving. She doesn't change ticket releases, so hide the public release and test the presale as a registered buyer yourself.

Prompt for Fai: "Set pre-registration to open at 9am on 1 September and close at 5pm on 7 September, then set presales to open at 10am on 8 September and close at 10pm on 9 September. Show me the dates before you save."

### How do you answer a ticket sales question no report covers?

Slug `answer-custom-ticket-sales-questions`. Guide: https://www.ticketfairy.com/guides/answer-custom-ticket-sales-questions

Start with the event report that matches your question, filter the Orders table when you need a narrower view, then export those rows for further analysis.

For: Answering a ticket sales question with the orders and tickets behind it.

What an agent can do: Ask Fai or your own assistant for event statistics, or use the command line to return them as JSON for a scheduled report.

Command line:

- What has sold, as the summary at the top of Performance: `ticketfairy event stats <EVENT_ID> --metric sales`
- The same numbers per ticket type: `ticketfairy event stats <EVENT_ID> --metric performance --output json`

CLI MCP tools that read: `select_event`, `get_event_performance`.

Prompt for Fai: "Compare this event with the last one I ran and tell me what sold, where the buyers came from, and which age band bought the most"

### How do you keep a high-demand on-sale running smoothly?

Slug `keep-a-high-demand-on-sale-running-smoothly`. Guide: https://www.ticketfairy.com/guides/keep-a-high-demand-on-sale-running-smoothly

Use the waiting room to control entry to checkout, stagger ticket releases to spread demand and collect a waiting list for later releases.

For: Putting a high-demand event on sale.

What an agent can do: no agent route is recorded for this guide. Send the organiser the guide link and walk them through the steps in the dashboard.

### How do you keep touts and bots off your tickets?

Slug `keep-touts-off-your-tickets`. Guide: https://www.ticketfairy.com/guides/keep-touts-off-your-tickets

Cap how many tickets one buyer can take, ask buyers to prove who they are before the ticket is issued, put returned tickets back on sale at the price you set, and offer a waiting list to the fans who missed out.

For: Keeping your tickets with the fans who wanted them.

What an agent can do: Fai reads how the controls are set, and can change the per-order and per-account limits, the anti-scalping settings, the buyer ID check and the waiting list for you. She asks you before she saves anything that changes what buyers can do.

CLI MCP tools that read: `select_event`, `get_event`.

Prompt for Fai: "For <EVENT NAME>, what are the limits per order and per account, and is ticket resale allowed?"

### How do you manage accreditation and backstage passes for your event?

Slug `manage-event-accreditation`. Guide: https://www.ticketfairy.com/guides/manage-event-accreditation

Give staff, crew, press, artists and guests a named pass that lets each of them in as many times as you allow, then scan it with the same door app as your tickets.

For: Handing out staff, crew, press, artist and guest access for an event.

What an agent can do: no agent route is recorded for this guide. Send the organiser the guide link and walk them through the steps in the dashboard.

### How do you manage many events without repeating the same work?

Slug `run-many-events-on-one-platform`. Guide: https://www.ticketfairy.com/guides/run-many-events-on-one-platform

Manage your customers, team and branding at brand level, reuse a published event template and group related dates into an event series.

For: Running a regular programme of events.

What an agent can do: no agent route is recorded for this guide. Send the organiser the guide link and walk them through the steps in the dashboard.

### How do you manage tickets for a multi-day event?

Slug `manage-tickets-for-a-multi-day-event`. Guide: https://www.ticketfairy.com/guides/manage-tickets-for-a-multi-day-event

Run the days as one event with a ticket category for each day, so a buyer compares the full run, the single days and the upgrades on one page and pays once.

For: Running a festival, conference or other event across several days.

What an agent can do: no agent route is recorded for this guide. Send the organiser the guide link and walk them through the steps in the dashboard.

### How do you run a guest list for your event without a spreadsheet?

Slug `run-a-guest-list-without-a-spreadsheet`. Guide: https://www.ticketfairy.com/guides/run-a-guest-list-without-a-spreadsheet

Issue each name on the guest list a ticket with a barcode, give each promoter their own allocation to hand out from, and see who came in and who has been before.

For: Running the door and the guest list for a club night.

What an agent can do: Fai issues the guest tickets when you name the people and the ticket type. She shows you the list before she sends anything.

CLI MCP tools that read: `select_event`, `get_event`.

Prompt for Fai: "Issue guest-list tickets for <EVENT NAME> to these six names on the comp tier, and show me the list before you send"

### How do you sell more tickets without spending more on ads?

Slug `sell-more-tickets-without-more-ad-spend`. Guide: https://www.ticketfairy.com/guides/sell-more-tickets-without-more-ad-spend

Reward the buyers who bring friends, give each promoter their own link so you can see what they sold, and go back to the people who reached checkout and stopped. You pay a reward on a sale rather than on a click.

For: Bringing your cost per ticket down.

What an agent can do: Fai can tell you which promotion sold what and draft the message you send to bring people back. You set up the rewards yourself on the page.

CLI MCP tools that read: `select_event`, `get_event_performance`.

Prompt for Fai: "For <EVENT NAME>, which promoters and referral links sold the most, and how much in rewards did each referral earn?"

### What can you find out about the people who buy your tickets?

Slug `what-you-can-learn-about-your-ticket-buyers`. Guide: https://www.ticketfairy.com/guides/what-you-can-learn-about-your-ticket-buyers

See who bought, where they live, the device they checked out on, the promoter or post that brought them and whether they have bought from you before, and which report answers each question.

For: Deciding your next event from who bought tickets to the last one.

What an agent can do: Ask Fai for any of these figures in plain language. She reads the same reports and can draw the answer as a chart or turn it into a document you can send on.

CLI MCP tools that read: `select_event`, `get_event_performance`.

Prompt for Fai: "For <EVENT NAME>, tell me which age band bought the most, which cities they came from and what they bought on, and draw the age bands as a chart"

### What is social ticketing, and how do referral rewards work?

Slug `social-ticketing-and-referral-rewards`. Guide: https://www.ticketfairy.com/guides/social-ticketing-and-referral-rewards

Give eligible buyers a personal referral link, reward them when friends buy tickets and see how many sales and how much revenue each buyer brings in.

For: Comparing ticketing platforms for word-of-mouth sales.

What an agent can do: Fai can turn referral rewards on and set the targets for an event before its first sale, after showing you the change and asking you to approve it. Once the event has sales, turn rewards on in the dashboard instead. She also reads back each buyer's referral sales.

Prompt for Fai: "Turn on referral rewards for <EVENT NAME> with buyers earning back 25% at 3 sales, 50% at 6 and the full price at 10, and show me the change before you save it"

### What marketing tools should a ticketing platform give you?

Slug `ticketing-platform-marketing-tools`. Guide: https://www.ticketfairy.com/guides/ticketing-platform-marketing-tools

Look for buyer segments and messaging, campaign tracking, ad-network connections and a way to contact people who abandoned checkout.

For: Marketing an event as well as selling tickets.

What an agent can do: no agent route is recorded for this guide. Send the organiser the guide link and walk them through the steps in the dashboard.

### What should you compare when choosing a ticketing platform?

Slug `compare-ticketing-platforms`. Guide: https://www.ticketfairy.com/guides/compare-ticketing-platforms

Compare what buyers pay, when you receive your ticket money and whether you can see and export your buyers while tickets are on sale.

For: Choosing where to sell tickets for your next event.

What an agent can do: no agent route is recorded for this guide. Send the organiser the guide link and walk them through the steps in the dashboard.

## More

- All guides: https://www.ticketfairy.com/guides
- Guides MCP server: https://www.ticketfairy.com/docs/mcp (tools `search_guides` and `get_guide`)
- CLI reference: https://www.npmjs.com/package/ticketfairy
- Developer documentation: https://www.ticketfairy.com/developers
- Support: support@ticketfairy.com
