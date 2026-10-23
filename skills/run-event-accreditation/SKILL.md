---
name: run-event-accreditation
description: "Issue accreditation passes with zones, approvals, a pass desk and staff gates in Ticket Fairy. Use when an organiser accredits crew, artists, press or guests."
---

# Run event accreditation

This skill covers passes, zones, approvals, the pass desk, staff gates and kit on Ticket Fairy. It lists the 9 published guides for this area and what an agent can do for each one.

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

- [Approve or decline accreditation requests for your event](#approve-or-decline-accreditation-requests-for-your-event)
- [Check accreditation passes in and out at your event staff gates](#check-accreditation-passes-in-and-out-at-your-event-staff-gates)
- [Choose who approves accreditation requests for your event](#choose-who-approves-accreditation-requests-for-your-event)
- [Hand out accreditation passes at your event desk](#hand-out-accreditation-passes-at-your-event-desk)
- [Hand out radios and kit to your event crew](#hand-out-radios-and-kit-to-your-event-crew)
- [Issue accreditation passes for your event](#issue-accreditation-passes-for-your-event)
- [Let event staff work a desk from their phone with a desk link](#let-event-staff-work-a-desk-from-their-phone-with-a-desk-link)
- [Let outside teams name their own people for event passes](#let-outside-teams-name-their-own-people-for-event-passes)
- [See which event pass holders have arrived and send a pass again](#see-which-event-pass-holders-have-arrived-and-send-a-pass-again)

### Approve or decline accreditation requests for your event

Slug `approve-or-decline-accreditation-requests-for-your-event`. Guide: https://www.ticketfairy.com/guides/approve-or-decline-accreditation-requests-for-your-event

Decide the pass requests your event's approval rules send you, with facts beside each one such as how many passes the group has left, from Approvals in the dashboard or from the link in your email with no sign-in. When you decline, the person who asked sees your reason. When you approve, the request goes to the next person or is ready to issue.

For: Deciding the pass requests that wait for you.

What an agent can do: Fai lists what is waiting for you with the facts beside each request, approves or declines one or up to 100 at once, and emails an approver a fresh decision link. She reads you each request and waits for your yes before she decides. Declining needs a reason, which the person who asked sees.

Prompt for Fai: "What is waiting for my approval at <EVENT NAME>? Approve Jane Smith's press pass and decline Tom Price, the Harbour FM allowance is used up"

#### Then: Decide many requests at once

What an agent can do: Fai approves or declines up to 100 requests at once when you ask, after you confirm.

Prompt for Fai: "Approve every press pass waiting for me at <EVENT NAME>"

#### Then: Decide in someone's place

What an agent can do: Fai decides a step in the named approver's place when an owner or admin asks, with the reason you give, after you confirm.

Prompt for Fai: "Sam is away, approve Jane Smith's press pass at <EVENT NAME> for him"

#### Then: Send an approver a new decision link

What an agent can do: Fai emails an approver a fresh decision link when you ask, after you confirm. She never shows the link itself.

Prompt for Fai: "Send Sam Carter a new link to decide the passes waiting for him at <EVENT NAME>"

### Check accreditation passes in and out at your event staff gates

Slug `check-passes-in-and-out-at-your-staff-gates`. Guide: https://www.ticketfairy.com/guides/check-passes-in-and-out-at-your-staff-gates

Scan crew, performer and supplier passes at the staff gates of your event so only people whose pass opens that zone, on that day and at that hour, get in. A supervisor can let a refused person through with a reason, and every scan in and out keeps a live count of who is on site and inside each zone.

For: Controlling who goes backstage and into each zone of your event.

What an agent can do: Fai tells you how many people are on site and in each zone, who is inside one zone, a pass's movements and a gate's latest scans. Fai also records a scan in or out for you after you confirm, and lets a refused person through only with your reason.

Prompt for Fai: "How many people are backstage at <EVENT NAME> right now, and who are they?"

### Choose who approves accreditation requests for your event

Slug `choose-who-approves-accreditation-requests`. Guide: https://www.ticketfairy.com/guides/choose-who-approves-accreditation-requests

Send the passes your event's rules pick out, such as press passes or a contractor's crew, to named people who approve them in order before the pass can go out. Each rule reads as a sentence, the first rule that matches decides who is asked, and a pass that matches no rule goes ahead as it always did.

For: Getting the right people to approve passes before they go out.

What an agent can do: Fai reads your approval rules and adds, changes, turns off, reorders or deletes a rule when you say it as a sentence. She shows you the rule and waits for your yes first. The people she names must be on the event's team.

Prompt for Fai: "At <EVENT NAME>, when passes from press organisations come in, ask Sam Carter, then Jo Patel from security"

#### Then: Change or delete a rule

What an agent can do: Fai changes, turns off or deletes a rule when you ask, after you confirm.

Prompt for Fai: "Turn off the lighting crew approval rule at <EVENT NAME>"

### Hand out accreditation passes at your event desk

Slug `hand-out-accreditation-passes-at-your-desk`. Guide: https://www.ticketfairy.com/guides/hand-out-accreditation-passes-at-your-desk

Run your accreditation desk from the pass list: scan a ticket or badge, or enter a name, check the card with the photo, zones and days, and hand the pass to the holder or to a team lead collecting for their crew. The desk tells you what to sort out first, such as a missing badge photo, and keeps track of who took each pass and which teammate gave it out.

For: Handing out passes to crew, performers and guests at your accreditation desk.

What an agent can do: Fai finds a pass by its code or by a name, organisation or role, says whether it is ready to collect and what to sort out first, and records a collection, a whole group's collection or an undo. She shows you the pass and waits for your yes before she records anything.

Prompt for Fai: "Is Ana Ruiz's pass ready to collect at <EVENT NAME>? She is here now to collect it"

#### Then: Give out a whole group's passes

What an agent can do: Fai records a group's issued passes as taken by a named collector when you ask, after you confirm, and tells you which passes it left out and why.

Prompt for Fai: "Jo Lead is collecting all the bar crew's passes at <EVENT NAME>"

#### Then: Undo a collection

What an agent can do: Fai undoes a collection when you ask and give a reason, after you confirm.

Prompt for Fai: "Dev Patel's pass at <EVENT NAME> went to the wrong collector, undo it"

### Hand out radios and kit to your event crew

Slug `hand-out-radios-and-kit-to-your-event-crew`. Guide: https://www.ticketfairy.com/guides/hand-out-radios-and-kit-to-your-event-crew

Keep a list of the radios, hi-vis vests, tablets, torches, keys and buggies for your event, hand them out at the kit desk with a scan or a search, and take them back with their condition. See who has what at any moment, keep a radio plan of channels and call signs, and let Fai chase anyone who has not returned their kit after the event.

For: Handing out and getting back your event's radios and kit.

What an agent can do: Fai reads your kit list, who has what, the kit history, the not-returned list and the radio plan, hands kit out or takes it back, adds or changes kit, marks kit as lost and changes channels and call signs. She shows you each change and waits for your yes first. Any member of your event's team can ask Fai to hand out or take back kit; only owners, admins and producers can change the kit list or the radio plan.

Prompt for Fai: "Hand radio R-12 to Ana Silva from security at <EVENT NAME>, due back at midnight"

#### Then: Take lost kit off the list

What an agent can do: Fai takes lost units of a batch off the kit list when you ask, after you confirm.

Prompt for Fai: "Take the 4 hi-vis vests Sam from the bar lost off the kit list at <EVENT NAME>"

### Issue accreditation passes for your event

Slug `issue-accreditation-passes-for-your-event`. Guide: https://www.ticketfairy.com/guides/issue-accreditation-passes-for-your-event

Give your crew, performers and their guests, traders' staff, volunteers and press a named pass for your event, with the zones it opens, the days and hours it works, meals and parking. Your door team scans each pass in the same app as your tickets and sees what it allows, and you print photo badges from the same list.

For: Accrediting everyone who works on or visits your event.

What an agent can do: Fai reads your passes, groups, zones and pass types, brings in everyone confirmed elsewhere in the event, sets up zones, pass types and group allowances, adds or changes a pass, issues passes, cancels a pass or issues it again, and makes a photo link for a pass holder. She shows you each change and waits for your yes first. Issuing emails each person their pass, so Fai always asks before she issues anything. You print badges in the dashboard. Your own AI assistant can list the passes and issue them over the MCP server, after your approval in your MCP client.

Command line:

- List the passes: `ticketfairy event-os passes list <EVENT_ID>`
- Issue the passes that are ready: `ticketfairy event-os passes issue <EVENT_ID> --all-ready`

CLI MCP tools that read: `select_event`, `get_event_passes`.

CLI MCP tools that make changes (not available with `--read-only`): `issue_event_passes`.

Prompt for Fai: "Bring in everyone for passes at <EVENT NAME>"

#### Then: Cancel a pass

What an agent can do: Fai cancels a pass and its ticket, or issues a cancelled pass again, when you ask, after you confirm.

Prompt for Fai: "Cancel the pass for Sam Lee at <EVENT NAME>, he is not coming"

#### Then: Decline a request

What an agent can do: Fai declines a pass request or brings one back when you ask, after you confirm.

Prompt for Fai: "Decline the late guest list name for Bicep at <EVENT NAME>"

### Let event staff work a desk from their phone with a desk link

Slug `let-event-staff-work-a-desk-from-their-phone`. Guide: https://www.ticketfairy.com/guides/let-event-staff-work-a-desk-from-their-phone

Share a desk link so volunteers, caterers and gate staff without a dashboard login can hand out passes, give crew meals, check passes at a staff gate or run registration at your event from their own phone or tablet. Each link opens one desk of one event, everything done through it is recorded under its name, and you can stop it at any time.

For: Giving the staff at your event desks their own desk on their phone.

What an agent can do: Fai lists your event's desk links, and makes, changes or stops one after you confirm. Fai never gives out a link's address: to see it, open Desks and links and select **Get a new link**.

Prompt for Fai: "Make a staff gate desk link called Backstage gate phone for the backstage zone at <EVENT NAME>"

#### Then: Change a link

What an agent can do: Fai changes a link's name, zone, supervisor switch or end date after you confirm.

Prompt for Fai: "Let the Main desk tablet link at <EVENT NAME> work until Monday night"

#### Then: Get a new address for a link

What an agent can do: Fai replaces a link's address after you confirm, so the old address stops working, for example when it was shared by mistake. Fai never gives out the new address: select **Get a new link** in Desks and links when you need to see one.

Prompt for Fai: "The Main desk tablet link at <EVENT NAME> was shared by mistake, replace it so the old one stops working"

#### Then: Stop a link

What an agent can do: Fai stops a desk link after you confirm, for example when a phone goes missing.

Prompt for Fai: "Stop the Crew catering tent desk link at <EVENT NAME>, the phone went missing"

### Let outside teams name their own people for event passes

Slug `let-outside-teams-name-their-own-people-for-passes`. Guide: https://www.ticketfairy.com/guides/let-outside-teams-name-their-own-people-for-passes

Give each company working on your event an allowance of passes and its own page, with no sign-in, where its contact names its people. The names arrive in Accreditation for you to check and issue.

For: Collecting names for passes from the companies working on your event.

What an agent can do: Fai lists your outside teams and who still owes names, adds or changes a team, gives, changes or takes away its passes, and emails its contact the page link. She shows you each change or email and waits for your yes first, and she never shows the link itself in the conversation. A week before names close, Fai also drafts a reminder to each team that still has places left, for you to approve on Today.

Prompt for Fai: "Add Brightline Security as a contractor at <EVENT NAME>, contact Tom Okafor at tom@brightline.example, give them 40 crew passes with names by Friday 6pm, then email Tom the link"

#### Then: Stop a team's page link

What an agent can do: Fai stops a team's page link when you ask, after you confirm.

Prompt for Fai: "Stop the page link for Brightline Security at <EVENT NAME>"

#### Then: Take away a team's passes

What an agent can do: Fai takes an allowance away from a team when you ask, after you confirm. The pass group and its people stay.

Prompt for Fai: "Take the guest passes away from Harbour Catering at <EVENT NAME>"

#### Then: Archive an organisation

What an agent can do: Fai archives an organisation or restores one when you ask, after you confirm.

Prompt for Fai: "Archive the Daily Echo at <EVENT NAME>, they are not covering it this year"

### See which event pass holders have arrived and send a pass again

Slug `see-which-pass-holders-have-arrived-and-send-a-pass-again`. Guide: https://www.ticketfairy.com/guides/see-which-pass-holders-have-arrived-and-send-a-pass-again

See when and how each accreditation pass holder arrived, from the desk hand-over, a staff gate or the door scanner, and how many of each group have arrived. Send a pass email again to anyone who cannot find theirs.

For: Tracking who has arrived with an accreditation pass.

What an agent can do: Fai lists who has arrived and who has not, tells you how many of each group have arrived, and sends a pass email again after you confirm.

Prompt for Fai: "How many of the Northern Bars crew have arrived at <EVENT NAME>?"

#### Then: Send a pass again

What an agent can do: Fai sends a pass email again to the address it was issued to, after you confirm.

Prompt for Fai: "Send Jane Doe's crew pass for <EVENT NAME> again, she cannot find the email"

## More

- All guides: https://www.ticketfairy.com/guides
- Guides MCP server: https://www.ticketfairy.com/docs/mcp (tools `search_guides` and `get_guide`)
- CLI reference: https://www.npmjs.com/package/ticketfairy
- Developer documentation: https://www.ticketfairy.com/developers
- Support: support@ticketfairy.com
