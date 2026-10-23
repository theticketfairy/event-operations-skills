# Ticket Fairy event operations skills

Run an event's orders, entry, crew, accreditation, traders, site, reports and financial administration.

Official [Ticket Fairy](https://www.ticketfairy.com) agent skills, selected from the
[canonical collection](https://github.com/theticketfairy/agent-skills). Install this collection or the individual skills you
need; their names and instructions are the same in both repositories.

## Install

```sh
npx skills add theticketfairy/event-operations-skills
```

List the available skills without installing:

```sh
npx skills add theticketfairy/event-operations-skills --list
```

Or select one skill:

```sh
npx skills add theticketfairy/event-operations-skills --skill manage-orders-and-refunds
```

The current Skills CLI requires Node.js 22.20 or later. Skills install to your
current project by default. Choose the supported agent in the CLI. See the [Skills CLI documentation](https://skills.sh/docs/cli).

## Skills

| Skill | When to use it |
| --- | --- |
| [`manage-orders-and-refunds`](skills/manage-orders-and-refunds/SKILL.md) | Find and manage Ticket Fairy orders: checkout questions, order approval, refunds, transfers, waiting lists and buyer support. Use when an organiser asks about an order, a refund or the checkout. |
| [`manage-invitations-and-guest-lists`](skills/manage-invitations-and-guest-lists/SKILL.md) | Send Ticket Fairy invitations and guest tickets, and manage partner allocations and group bookings. Use when an organiser wants to give people tickets without a normal purchase. |
| [`read-event-reports`](skills/read-event-reports/SKILL.md) | Read Ticket Fairy event reports: sales, page views, buyers and what each figure counts. Use when an organiser asks how an event is selling or what a report means. |
| [`run-door-check-in`](skills/run-door-check-in/SKILL.md) | Run Ticket Fairy check-in at the door: scanning, entry rules, live check-in reports and wristbands. Use when an organiser prepares or runs entry to an event. |
| [`get-paid-for-ticket-sales`](skills/get-paid-for-ticket-sales/SKILL.md) | Set up Ticket Fairy payment accounts, choose who pays the fees, pick currencies and follow payouts. Use when an organiser asks how and when they get their money. |
| [`use-vault-and-capital`](skills/use-vault-and-capital/SKILL.md) | Use the Ticket Fairy Vault account, cards, transfers and invoices, and Capital working capital. Use when an organiser asks about their Vault balance, cards, transfers or funding. |
| [`run-event-production`](skills/run-event-production/SKILL.md) | Run an event day to day in Ticket Fairy Event Management: the Today page, tasks, the event inbox, call notes, messages to the team and attendee feedback. Use when an organiser runs the event itself. |
| [`run-crew-and-volunteers`](skills/run-crew-and-volunteers/SKILL.md) | Build rotas, recruit volunteers, collect certificates, run inductions, plan meals and approve hours in Ticket Fairy. Use when an organiser staffs an event. |
| [`run-event-accreditation`](skills/run-event-accreditation/SKILL.md) | Issue accreditation passes with zones, approvals, a pass desk and staff gates in Ticket Fairy. Use when an organiser accredits crew, artists, press or guests. |
| [`manage-traders-and-exhibitors`](skills/manage-traders-and-exhibitors/SKILL.md) | Take trader applications, place pitches, publish a directory, check takings and give exhibitors lead scanners in Ticket Fairy. Use when an organiser runs traders or an exhibition. |
| [`run-the-site-and-safety`](skills/run-the-site-and-safety/SKILL.md) | Draw site maps, book deliveries, order hire, raise purchase orders, log incidents and keep a risk register in Ticket Fairy. Use when an organiser runs the event site, suppliers and safety. |
| [`solve-ticketing-problems`](skills/solve-ticketing-problems/SKILL.md) | Solve common event ticketing problems with Ticket Fairy: queues, no-shows, reports, marketing and access. Use when an organiser describes a problem rather than a feature. |
| [`work-with-fai`](skills/work-with-fai/SKILL.md) | Use Fai, Ticket Fairy's AI teammate in the dashboard, for questions, the inbox and the buyer concierge. Use when an organiser wants Fai to do work for them. |

## Authority and recovery

A skill grants no account permission and does not authorise sending messages,
creating tickets, refunding orders or taking payment. Keep each action within the
person's approved scope and current role. Buyer discovery is public and read-only;
buyer purchases use a separately supported handler and explicit approval of the
final tickets, total and currency, or continue in the official browser checkout.
Organiser credentials do not grant purchase authority. Keep credentials out of chat
and logs. After an uncertain change, recover its original result before
retrying; never issue a new refund, send or ticket grant to resolve uncertainty.

## Documentation and maintenance

- [Official guides](https://www.ticketfairy.com/guides), read live with the public
  [guides MCP server](https://www.ticketfairy.com/docs/mcp).
- [Developer documentation](https://www.ticketfairy.com/developers).
- [Published skill index](https://www.ticketfairy.com/.well-known/agent-skills/index.json).
- [Agent rules](AGENTS.md) and [canonical source](https://github.com/theticketfairy/agent-skills).

`SOURCE.json` records the canonical revision and skill hashes. Make instruction
changes in the canonical repository, then use its
`scripts/build_skill_repositories.py` to copy the reviewed release into this
repository. Do not maintain an independent fork of a skill here.

GitHub publication does not prove skills.sh indexing. Its
[FAQ](https://skills.sh/docs/faq) describes automatic listing through anonymous
Skills CLI installation telemetry. No installation count or indexing status is
claimed by this repository.

## Licence

MIT. See [LICENSE](LICENSE).
