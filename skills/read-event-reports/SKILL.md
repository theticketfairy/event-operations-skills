---
name: read-event-reports
description: "Read Ticket Fairy event reports: sales, page views, buyers and what each figure counts. Use when an organiser asks how an event is selling or what a report means."
---

# Read event reports

This skill covers the dashboard reports, what each one counts and how to use the figures on Ticket Fairy. It lists the 19 published guides for this area and what an agent can do for each one.

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

- [Check the weather for your event](#check-the-weather-for-your-event)
- [Compare ticket sales across all your events](#compare-ticket-sales-across-all-your-events)
- [Create a recap of your event and share it](#create-a-recap-of-your-event-and-share-it)
- [Email your ticket sales report to your team](#email-your-ticket-sales-report-to-your-team)
- [Export every ticket sale across your brand](#export-every-ticket-sale-across-your-brand)
- [See how many ticket buyers come back to your events](#see-how-many-ticket-buyers-come-back-to-your-events)
- [See how visitors find your event page](#see-how-visitors-find-your-event-page)
- [See how your ticket sales are going](#see-how-your-ticket-sales-are-going)
- [See where your event audiences are strongest](#see-where-your-event-audiences-are-strongest)
- [See which devices your ticket buyers order on](#see-which-devices-your-ticket-buyers-order-on)
- [See which sources and campaigns sell your tickets](#see-which-sources-and-campaigns-sell-your-tickets)
- [See which team members sell your tickets](#see-which-team-members-sell-your-tickets)
- [See who visits your event website](#see-who-visits-your-event-website)
- [See your ticket sales pace and sell-out forecast](#see-your-ticket-sales-pace-and-sell-out-forecast)
- [Share a live ticket sales report with a partner](#share-a-live-ticket-sales-report-with-a-partner)
- [Track which promotion sells your tickets](#track-which-promotion-sells-your-tickets)
- [Understand who buys tickets across your events](#understand-who-buys-tickets-across-your-events)
- [Understand who buys tickets to your event](#understand-who-buys-tickets-to-your-event)
- [Understand your event's referral results](#understand-your-events-referral-results)

### Check the weather for your event

Slug `check-your-event-weather`. Guide: https://www.ticketfairy.com/guides/check-your-event-weather

See the weather forecast for your event's venue on the Performance page, with your event days marked and any severe-weather warning for the area, and see what the date is usually like while the event is still weeks away.

For: Planning an outdoor event around the weather at your venue.

What an agent can do: Fai reads the same forecast for your event's venue, including any severe-weather warning, and what the date is usually like when the event is further out. You read the weather on your event's Performance page or through Fai.

Prompt for Fai: "What's the weather looking like for <EVENT NAME> on the day, is there any warning out for the venue, and what is that date usually like there"

### Compare ticket sales across all your events

Slug `compare-ticket-sales-across-your-events`. Guide: https://www.ticketfairy.com/guides/compare-ticket-sales-across-your-events

Use the brand Performance report to check tickets sold, revenue and how full each event is across every event under your brand, then narrow it to a series, a venue or a place and compare how two to five events sold.

For: Following sales across a season, a series or every event under your brand.

What an agent can do: Fai reads the same report for the whole brand or for any series, venue, city, country or set of events, and lines up two to five events to compare how they sold. She only reads the figures and doesn't change anything.

Prompt for Fai: "Look at the Performance report for my brand for the last 90 days. Tell me which upcoming events are selling slowest against their capacity, then compare this year's summer opening night with last year's by days before the event"

### Create a recap of your event and share it

Slug `create-a-recap-of-your-event-and-share-it`. Guide: https://www.ticketfairy.com/guides/create-a-recap-of-your-event-and-share-it

See your event's ticket sales, check-ins, buyer cities and campaign sources on its Recap page, then send the recap to a venue, artist or sponsor in a link they open without signing in, with or without your revenue.

For: Reporting how an event went to your venue, artists and sponsors.

What an agent can do: Fai reads the same recap, and can make a recap link with the name and revenue choice you give her or stop one. She asks you to approve each link she makes or stops.

Prompt for Fai: "Give me a recap of <EVENT NAME>, then make a recap link called <NAME> <WITH OR WITHOUT> revenue for me to send, and show it to me before you create it"

#### Then: Send a link again

What an agent can do: Fai lists your recap links with their names and dates but never shows a link itself. Copy it from the Recap page, or ask Fai to make a new one.

Prompt for Fai: "List the recap links of <EVENT NAME> and the date each stops working"

#### Then: Stop a link

What an agent can do: Ask Fai to stop a recap link by its name. She finds it, shows you which link she will stop and asks you to approve it.

Prompt for Fai: "Stop the recap link called <NAME> on <EVENT NAME>"

### Email your ticket sales report to your team

Slug `email-your-sales-report-to-your-team`. Guide: https://www.ticketfairy.com/guides/email-your-sales-report-to-your-team

Send your event's ticket sales to the people who need them by email, every day or once a week, each in their own language and with or without revenue.

For: Keeping your co-promoters, venue and team up to date on ticket sales.

What an agent can do: Fai can show you who gets the sales report and change it: turn it on or off, set every day or once a week, and add or remove people with their language and revenue choice. She shows you the change and asks you to approve it before she saves.

Prompt for Fai: "On <EVENT NAME>, email the sales report every Monday to <NAME> at <EMAIL> with revenue and to <NAME> at <EMAIL> in <LANGUAGE> without revenue, and show me the change before you save it"

#### Then: Stop the emails for everyone

What an agent can do: Ask Fai to turn the sales report email off for the event. She shows the change and asks you to approve it.

Prompt for Fai: "Turn off the sales report email for <EVENT NAME> and keep the people on the list"

#### Then: Take one person off the list

What an agent can do: Ask Fai to remove a person from the sales report email. She shows the list without them and asks you to approve it.

Prompt for Fai: "Take <EMAIL> off the sales report email for <EVENT NAME>"

### Export every ticket sale across your brand

Slug `export-every-ticket-sale-across-your-brand`. Guide: https://www.ticketfairy.com/guides/export-every-ticket-sale-across-your-brand

Download one ZIP of spreadsheets with every ticket bought across your brand's events in up to 12 months: each transaction, each event's totals and each ticket tier's sales.

For: Handing a season's ticket sales to an accountant, a partner or a client.

What an agent can do: Fai can start the same export for the dates and events you name, after she shows you what it covers and you approve it, and she can tell you when it is ready and list your recent exports. You download the file from the brand's Performance page; Fai never sends it.

Prompt for Fai: "Export every ticket sale of my brand from <FIRST DAY> to <LAST DAY> for <ALL EVENTS OR A SERIES, VENUE OR CITY>, email me a link when it is ready, and show me what it covers before you start it"

#### Then: Download an earlier export again

What an agent can do: Ask Fai for your recent exports of the brand. She lists them with their days and whether each is ready, and gives you the Performance page link to download a ready one.

Prompt for Fai: "List my recent sales exports for <BRAND NAME> and tell me which ones I can still download"

### See how many ticket buyers come back to your events

Slug `see-how-many-ticket-buyers-come-back-to-your-events`. Guide: https://www.ticketfairy.com/guides/see-how-many-ticket-buyers-come-back-to-your-events

Use Buyer loyalty on your brand's Performance page to see how many of your ticket buyers came back for two or more of your events, how many events each buyer has bought for, and which events bring buyers back, for every event or one series, venue, place or set of events.

For: Growing the audience that comes back to every event you run.

What an agent can do: Fai reads the same Buyer loyalty figures for any period and for the whole brand or one series, venue, city, country or set of events, and can suggest how to bring first-time buyers back. She only reads the figures and doesn't change anything.

Prompt for Fai: "Look at the buyer loyalty of my brand <BRAND NAME> for the last 12 months. Tell me how many buyers came back for two or more events, which events bring buyers back, and what I could do to turn more first-time buyers into returning ones"

### See how visitors find your event page

Slug `see-how-visitors-find-your-event-page`. Guide: https://www.ticketfairy.com/guides/see-how-visitors-find-your-event-page

See how many visits your event page receives, where they came from and how many of them reached order confirmation.

For: Choosing where to promote your event next.

What an agent can do: Ask Fai for a date range. She applies it to every traffic result except the referrer list, which always covers the event's full run.

Command line:

- Visits, unique visits and conversions: `ticketfairy event stats <EVENT_ID> --metric traffic`
- The sites that sent you visits, a day at a time: `ticketfairy event stats <EVENT_ID> --metric referrer-by-day`

CLI MCP tools that read: `select_event`, `get_event_performance`.

Prompt for Fai: "Where did the traffic for this event come from, and how many times was the order confirmation page reached"

### See how your ticket sales are going

Slug `check-your-sales`. Guide: https://www.ticketfairy.com/guides/check-your-sales

See how many tickets you have sold and what your event has earned, from the figures across the top of the Performance page to the day-by-day table and the breakdown for every ticket type.

For: Following an on-sale and reporting on it afterwards.

What an agent can do: Fai can use the same figures and explain what each one counts. She only reads them; you change anything on the page itself.

Command line:

- The figures across the top of the page: `ticketfairy event stats <EVENT_ID> --metric summary`
- Sales day by day, the same run the Ticket Sales chart plots: `ticketfairy api /api/events/<EVENT_ID>/relationships/performance --query section=sales --output json`
- The same totals per ticket type: `ticketfairy event stats <EVENT_ID> --metric performance --output json`

CLI MCP tools that read: `select_event`, `get_event_performance`.

Prompt for Fai: "For <EVENT NAME>, tell me how many tickets have sold and what the event has earned after referral rebates, then which ticket type is selling fastest"

#### Then: Tell gross from net

What an agent can do: Fai can tell you both figures and which is which.

Prompt for Fai: "For <EVENT NAME>, give me revenue with and without the ticketing fee and tell me whether refunds are already taken off"

#### Then: Find the report behind a figure

What an agent can do: Fai can pull any of those sections and compare them for you.

Prompt for Fai: "For <EVENT NAME>, break the sales down by promo code and tell me which code brought in the most"

#### Then: What each role sees here

What an agent can do: Fai is held to the same limits as the person she acts for, so she reports only what that login can see.

Prompt for Fai: "Which of my team can see revenue on <EVENT NAME>, and who only sees ticket counts"

### See where your event audiences are strongest

Slug `see-where-your-event-audiences-are-strongest`. Guide: https://www.ticketfairy.com/guides/see-where-your-event-audiences-are-strongest

Compare where ticket buyers are based across all your events, or focus on a series, venue, city, country or any events you choose.

For: Planning where to advertise, tour or grow next.

What an agent can do: Ask Fai to compare where buyers are based across the brand or for any group of events you can choose on the Geographics page. She can find the matching series, venue, host city or host country before reading the report.

Prompt for Fai: "Where are the buyers for our Manchester events based, compare orders and tickets in the leading cities, and tell me which places are strong enough for a local campaign"

### See which devices your ticket buyers order on

Slug `see-which-devices-your-ticket-buyers-order-on`. Guide: https://www.ticketfairy.com/guides/see-which-devices-your-ticket-buyers-order-on

Use the Devices report for your event to see the browsers, device types, platforms, device brands and models your ticket buyers ordered on, with the number of orders and the share for each.

For: Checking where your buyers finish checkout.

What an agent can do: Fai and your own AI assistant through our MCP server can both read the Devices report and tell you what your buyers ordered on, with refunded and cancelled orders left in or taken out.

Command line:

- The browser, device type, platform, device brand and device name counts: `ticketfairy event stats <EVENT_ID> --metric devices`
- The same counts, ready for a script: `ticketfairy event stats <EVENT_ID> --metric devices --output json`

CLI MCP tools that read: `select_event`, `get_event_performance`.

Prompt for Fai: "Look at the devices report for this event and tell me how many orders came from phones, which browser and app buyers used most, and whether that changes if you leave out refunded and cancelled orders"

### See which sources and campaigns sell your tickets

Slug `see-which-sources-and-campaigns-sell-your-tickets`. Guide: https://www.ticketfairy.com/guides/see-which-sources-and-campaigns-sell-your-tickets

Use the Campaigns tab of your event's Traffic report to see the link clicks, visits, orders, tickets and revenue each tagged link brought in, by source, medium or campaign, then follow visitors from your event page to a purchase on the Funnel tab.

For: Deciding which adverts, posts and partners to keep paying for.

What an agent can do: Fai reads the same Campaigns and Funnel figures for any days you name, grouped by source, medium or campaign, and can say which tags sold the most and where visitors dropped off. She only reads the figures and doesn't change anything.

Prompt for Fai: "For <EVENT NAME>, show me the sales by campaign for the last 30 days, tell me which campaign sold the most tickets for each visit, and then show me where visitors dropped off between the event page and a purchase"

### See which team members sell your tickets

Slug `see-which-team-members-sell-your-tickets`. Guide: https://www.ticketfairy.com/guides/see-which-team-members-sell-your-tickets

Use the brand Promoters report to compare every team member's referred visits and credited sales across all your events, and see who is selling the most, who has slowed down and who never shared a link.

For: Deciding who to back and who to bring onto your brand team.

What an agent can do: Ask Fai to read the brand Promoters report for you. She can name the people behind each insight, compare two team members, narrow the report to a period or a group of events, and, with your confirmation, invite the person she recommends to the brand team.

Prompt for Fai: "Look at our brand's Promoters report for the last 90 days, tell me which event-level promoters should join the brand team and why, and who has stopped selling"

### See who visits your event website

Slug `see-who-visits-your-event-website`. Guide: https://www.ticketfairy.com/guides/see-who-visits-your-event-website

See how many page views your event website gets, how many visitors select a ticket button and how many open the ticket checkout, day by day, with the pages and events that draw the most interest.

For: Checking how your website sells tickets.

What an agent can do: Ask Fai for the days you want. She reads the same page views, ticket clicks, checkouts opened and top pages and events for your website.

Prompt for Fai: "How many people visited my <WEBSITE NAME> website in the last 30 days, and which pages and events did they click on most"

### See your ticket sales pace and sell-out forecast

Slug `see-your-ticket-sales-pace-and-sell-out-forecast`. Guide: https://www.ticketfairy.com/guides/see-your-ticket-sales-pace-and-sell-out-forecast

Use Sales pace and forecast on your event's Insights page to see whether you are selling faster or slower than a past event, how many tickets and how much revenue to expect, and the day you can expect to sell out, then see how many of your buyers are new and how many came back.

For: Knowing early whether an event will sell out, and when.

What an agent can do: Fai reads the same forecast against the event she picks, or against any past event of your brand you name, says how sure the estimate is and why, and reads the split of new and returning buyers. She only reads the figures and doesn't change anything.

Prompt for Fai: "For <EVENT NAME>, compare my sales so far with <PAST EVENT NAME> at the same number of days before the event, tell me how many tickets I can expect to sell, whether and when it sells out and how sure that is, and how many of my buyers came back from my other events"

### Share a live ticket sales report with a partner

Slug `share-a-live-sales-report`. Guide: https://www.ticketfairy.com/guides/share-a-live-sales-report

Give a venue, co-promoter or sponsor a sales report link that shows the live ticket sales and revenue of the ticket types and add-ons you choose, without giving them a role on your event.

For: Showing a partner the live ticket sales of the part of your event they share in.

What an agent can do: Fai can make a sales report link for the ticket types and add-ons you name, after she shows it to you and you approve it. Copy the finished link from the External/3rd-Party Sales Reporting section on the event's Settings page. You can make sales report links in the dashboard or through Fai.

Prompt for Fai: "On <EVENT NAME>, make a sales report link called <NAME> for the <TICKET TYPES> ticket types and the <ADD-ONS> add-ons, <WITH OR WITHOUT> the day-by-day breakdown, and show it to me before you create it"

#### Then: Replace a link that has been passed on

What an agent can do: Fai cannot list the sales report links you already have, so replace a link in the dashboard.

#### Then: Stop sharing a report

What an agent can do: Fai cannot list the sales report links you already have, so delete a link in the dashboard.

### Track which promotion sells your tickets

Slug `track-which-promotion-sold-your-tickets`. Guide: https://www.ticketfairy.com/guides/track-which-promotion-sold-your-tickets

Give each advert, post, email or partner a separate tracking link so your event report shows the clicks, orders and ticket revenue each link brings in.

For: Promoting an event in more than one place at once.

What an agent can do: Fai can go through this table and tell you which link brought in the most: she gives you the same clicks, orders and revenue, with the same caution that an order counts from the moment it is placed while a refund lowers the revenue. She can't create or delete a link, so you do that on this page.

Prompt for Fai: "Show me the tracking links on this event and tell me which one brought in the most orders"

#### Then: Delete a tracking link you no longer use

What an agent can do: Delete a tracking link in the dashboard. Fai can show you the links and their results, but she cannot create or delete one, and neither MCP nor the CLI manages them.

### Understand who buys tickets across your events

Slug `understand-who-buys-tickets-across-your-events`. Guide: https://www.ticketfairy.com/guides/understand-who-buys-tickets-across-your-events

Use **Customers** to see everybody who has bought from your brand, which events and tickets they ordered, what they spent and which sales their referrals brought in.

For: Finding repeat customers for your next event.

What an agent can do: In the dashboard, Fai can rank repeat customers and the customers whose referral links drove the most ticket purchases.

Command line:

- Your customers, fifty at a time: `ticketfairy customer list`

Prompt for Fai: "Show me the customers who have ordered tickets for more than one of my events, then separately show the customers whose referral links drove the most ticket purchases"

### Understand who buys tickets to your event

Slug `read-your-audience-demographics`. Guide: https://www.ticketfairy.com/guides/read-your-audience-demographics

Use the Demographics and Devices reports for your event to compare age bands, gender, jobs and employers, see which devices buyers ordered on, and understand what each figure counts.

For: Deciding who to market your next event to.

What an agent can do: Ask Fai for the age figures and for what buyers bought on. Your own AI assistant reads the age figures through our MCP server. Review the Gender and Professions sections in the dashboard.

Command line:

- The age bands shown in the dashboard: `ticketfairy event stats <EVENT_ID> --metric demographics`
- The same figures, ready for a script: `ticketfairy event stats <EVENT_ID> --metric demographics --output json`
- What buyers bought on, from the Devices report: `ticketfairy event stats <EVENT_ID> --metric devices`

CLI MCP tools that read: `select_event`, `get_event_performance`.

Prompt for Fai: "Look at the ages of the people who bought for this event and tell me which band bought the most, then tell me what they bought on, counting refunded and cancelled orders too"

### Understand your event's referral results

Slug `read-your-referral-results`. Guide: https://www.ticketfairy.com/guides/read-your-referral-results

Use the Influencers report to see how much buyers shared your event, how many clicks those shares brought, which referral links led to sales and what you owe in rewards.

For: Running a referral push for an event.

What an agent can do: Fai and your own AI assistant through our MCP server can both get your referral figures and explain what they show.

Command line:

- Your referrers and what each of them brought in: `ticketfairy event stats <EVENT_ID> --metric referrals`
- The same figures, ready for a spreadsheet: `ticketfairy event stats <EVENT_ID> --metric referrals --output csv`

CLI MCP tools that read: `select_event`, `get_event_performance`.

Prompt for Fai: "Look at the referral results for this event and tell me who brought in the most sales and whether the reward is paying for itself"

## More

- All guides: https://www.ticketfairy.com/guides
- Guides MCP server: https://www.ticketfairy.com/docs/mcp (tools `search_guides` and `get_guide`)
- CLI reference: https://www.npmjs.com/package/ticketfairy
- Developer documentation: https://www.ticketfairy.com/developers
- Support: support@ticketfairy.com
