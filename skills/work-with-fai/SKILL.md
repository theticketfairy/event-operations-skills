---
name: work-with-fai
description: "Use Fai, Ticket Fairy's AI teammate in the dashboard, for questions, the inbox and the buyer concierge. Use when an organiser wants Fai to do work for them."
---

# Work with Fai

This skill covers Fai in the dashboard, inbox handling and the buyer concierge on Ticket Fairy. It lists the 4 published guides for this area and what an agent can do for each one.

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

- [Add your ticket concierge to your website](#add-your-ticket-concierge-to-your-website)
- [Ask Fai about your event](#ask-fai-about-your-event)
- [Give ticket buyers an AI concierge](#give-ticket-buyers-an-ai-concierge)
- [Teach your concierge from your event FAQ pages and Google Docs](#teach-your-concierge-from-your-event-faq-pages-and-google-docs)

### Add your ticket concierge to your website

Slug `add-your-ticket-concierge-to-your-website`. Guide: https://www.ticketfairy.com/guides/add-your-ticket-concierge-to-your-website

Add your concierge to the website where buyers find your event, so it answers ticket questions and sells tickets in a chat on your own pages, and choose who takes the questions it passes on.

For: Getting your concierge onto the website your ticket buyers use.

What an agent can do: Fai can open your concierge widgets so you can copy the snippet. On the Install tab in the dashboard, choose the sites the chat loads on and who gets the questions it passes on, then add the snippet to your own site.

Prompt for Fai: "Open the concierge widgets for <BRAND NAME> so I can copy the snippet for our website"

#### Then: Change the snippet after a key leak

What an agent can do: Fai can open your concierge widgets for you. You rotate the key in the dashboard and replace the snippet on your own site.

Prompt for Fai: "Open the concierge widgets for <BRAND NAME>"

### Ask Fai about your event

Slug `ask-fai-about-your-event`. Guide: https://www.ticketfairy.com/guides/ask-fai-about-your-event

Ask Fai about your event by typing or out loud, have her chart the answer or make the change for you, and check her work before you rely on it.

For: Getting answers about your own events, orders and buyers.

What an agent can do: Fai is the agent path. She works on the brand and event you have open, sees what your role can see, and asks before she changes anything.

Command line:

- Show an event and its current sales: `ticketfairy event stats <EVENT_ID>`

CLI MCP tools that read: `select_event`, `get_event`.

Prompt for Fai: "How many tickets has <EVENT NAME> sold so far, and how does that compare with the same point before my last event"

#### Then: Ask her to do the work, not only describe it

What an agent can do: Fai proposes the changes and waits for your approval on each one.

Command line:

- Create a ticket release: `ticketfairy ticket create <EVENT_ID> --name "Early Bird" --price 18`

CLI MCP tools that read: `select_event`, `get_event`.

Prompt for Fai: "Set up an early bird tier for <EVENT NAME> at twenty per cent below the standard price, ask me for the allocation and the dates, and show me the change before you save it"

#### Then: Things worth asking her for

What an agent can do: Fai reads, draws charts and drafts freely. She asks you before she issues a ticket or changes your event, and you take back a guest ticket sent to the wrong person by cancelling its order.

CLI MCP tools that read: `select_event`, `get_event`.

Prompt for Fai: "Issue two guest tickets on the comp tier for <EVENT NAME> to ada@example.com and noor@example.com, then show me the list before you send"

#### Then: Talk to her instead of typing

What an agent can do: When you talk, you reach the same Fai, with the same permissions, the same tools and the same approvals as typing. Only the exact words Fai reads out approve a change by voice.

CLI MCP tools that read: `select_event`, `get_event`.

Prompt for Fai: "How did <EVENT NAME> sell last weekend, and how does that compare with the weekend before"

### Give ticket buyers an AI concierge

Slug `give-buyers-an-ai-concierge`. Guide: https://www.ticketfairy.com/guides/give-buyers-an-ai-concierge

Put a concierge on your own website that answers buyers' questions before they buy, using the answers you give it.

For: Answering buyer questions on your own website.

What an agent can do: Fai can open the concierge builder for you. You enter what the concierge knows, and you keep it up to date.

Command line:

- Show the brands you can act for: `ticketfairy brand list`

CLI MCP tools that read: `select_brand`.

Prompt for Fai: "Open the concierge widgets for <BRAND NAME>"

#### Then: Keep it current as the event changes

What an agent can do: Fai can open the widget so you can update what it knows.

Command line:

- Show the brands you can act for: `ticketfairy brand list`

CLI MCP tools that read: `select_brand`.

Prompt for Fai: "Open the concierge widget for <BRAND NAME> so I can update its answers"

### Teach your concierge from your event FAQ pages and Google Docs

Slug `teach-your-concierge-from-your-event-faq-pages`. Guide: https://www.ticketfairy.com/guides/teach-your-concierge-from-your-event-faq-pages

Point your ticket concierge at the event FAQ, policy and venue pages you already keep, a Google Doc or your whole website, and it answers buyers from them and picks up your changes on a schedule you choose.

For: Giving your concierge the answers you already keep on your website and in documents.

What an agent can do: Fai can open your concierge's reference pages for you. Add a page, a Google Doc or a website, and choose which widgets answer from it, in the dashboard.

Prompt for Fai: "Open the concierge reference pages for <BRAND NAME>"

#### Then: Read a whole website instead of one page

What an agent can do: Fai can open the reference pages for you. You add the website and review the pages she kept in the dashboard.

Prompt for Fai: "Open the concierge reference pages for <BRAND NAME> so I can add our website"

#### Then: Give one widget a page of its own

What an agent can do: Fai can open your concierge widgets for you. You add a widget's own reference pages in the dashboard.

Prompt for Fai: "Open the concierge widgets for <BRAND NAME>"

#### Then: Let the concierge mention events you sell elsewhere

What an agent can do: Fai can suggest listing pages near your venues and open the concierge's events on other platforms for you. You add a page to watch in the dashboard.

Prompt for Fai: "Suggest listing pages my concierge could watch for <BRAND NAME>"

## More

- All guides: https://www.ticketfairy.com/guides
- Guides MCP server: https://www.ticketfairy.com/docs/mcp (tools `search_guides` and `get_guide`)
- CLI reference: https://www.npmjs.com/package/ticketfairy
- Developer documentation: https://www.ticketfairy.com/developers
- Support: support@ticketfairy.com
