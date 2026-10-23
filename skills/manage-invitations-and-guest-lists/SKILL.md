---
name: manage-invitations-and-guest-lists
description: "Send Ticket Fairy invitations and guest tickets, and manage partner allocations and group bookings. Use when an organiser wants to give people tickets without a normal purchase."
---

# Manage invitations and guest lists

This skill covers invitations, guest tickets, partner allocations and group bookings on Ticket Fairy. It lists the 9 published guides for this area and what an agent can do for each one.

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

- [Build an application or sign-up form for your event](#build-an-application-or-sign-up-form-for-your-event)
- [Let a partner hand out their own tickets for your event](#let-a-partner-hand-out-their-own-tickets-for-your-event)
- [Make your event invitation-only](#make-your-event-invitation-only)
- [Password-protect your event](#password-protect-your-event)
- [Sell tickets by personal invitation](#sell-tickets-by-personal-invitation)
- [Sell tickets only to your NFT holders](#sell-tickets-only-to-your-nft-holders)
- [Send free tickets to your guest list](#send-free-tickets-to-your-guest-list)
- [Share one invitation link to your event](#share-one-invitation-link-to-your-event)
- [Unlock hidden tickets with an access code](#unlock-hidden-tickets-with-an-access-code)

### Build an application or sign-up form for your event

Slug `take-applications-with-a-form`. Guide: https://www.ticketfairy.com/guides/take-applications-with-a-form

Build a form for your event from a ready-made form, a description Fai turns into questions, or an empty one, ask only what each applicant needs to answer, read every application in one list, accept or decline each one, and send the people you accept a ticket.

For: Choosing acts, traders or guests from the people who apply.

What an agent can do: Fai can draft a form from your description or from a ready-made form, save it once you say yes, read every application, open the files applicants sent, and accept, decline or add an applicant to your event lists, asking you first each time.

Prompt for Fai: "Draft a trader application form for <EVENT NAME> with a pitch fee of 150 and an insurance certificate upload, and add each applicant to our trader applications"

#### Then: Send an accepted applicant a free ticket

What an agent can do: Fai can send guest tickets to the applicants you accepted. She reads their names and email addresses from the form, and shows you the recipients, the ticket type and the count for you to approve before she sends anything.

Prompt for Fai: "Send one Artist ticket each to the applicants I accepted on the artist applications form for <EVENT NAME>, and show me who gets what before you send"

#### Then: Invite an accepted applicant to buy tickets

What an agent can do: Send this invitation from the application in the dashboard, which fills in the applicant's email address and name for you.

#### Then: Work through a long list of applications

What an agent can do: Fai can read the applications on your form and list the ones that match what you describe, such as every act who picked Saturday. Tag and export the applications in the dashboard.

Prompt for Fai: "Go through the artist applications form for <EVENT NAME> and list the acts who picked Saturday, with their email addresses"

#### Then: Get the form in front of applicants

What an agent can do: Fai can draft social captions that ask acts or traders to apply, in your brand's voice, and shows you every version to choose from. She doesn't post anything, so add the form's address to the caption you pick, and download the QR code from the form in the dashboard.

Prompt for Fai: "Draft three social captions for <EVENT NAME> asking acts to apply for a slot, and leave space for the application link"

### Let a partner hand out their own tickets for your event

Slug `let-a-partner-hand-out-their-own-tickets`. Guide: https://www.ticketfairy.com/guides/let-a-partner-hand-out-their-own-tickets

Give an act's management, a radio station or a sponsor a fixed allocation they can hand out themselves, without a login to your event and without asking you each time.

For: Handing a counted allocation to a partner who issues their own tickets.

What an agent can do: Fai can create the delegation with the ticket types and limits you name, add the people who hold it and read you its access link. She shows you the delegation and the people before saving and asks you to approve each change, and once your event is published, each person she adds gets their invitation by email. Choose the email template for an Invitation row in the dashboard.

CLI MCP tools that read: `select_event`, `get_event`.

Prompt for Fai: "Create a delegation called <PARTNER NAME> on <EVENT NAME> that can hand out <NUMBER> guest tickets on <TICKET TYPE NAME>, give <NAME> <EMAIL> access to it, and show me the delegation before you save it"

#### Then: Change an allocation later

What an agent can do: Fai can read how many tickets a partner has issued against each limit, change a limit, and add or remove the people who hold the delegation. She shows you the change and asks you to approve it before saving.

CLI MCP tools that read: `select_event`, `get_event`.

Prompt for Fai: "On <EVENT NAME>, show me how many tickets the <PARTNER NAME> delegation has issued, raise its limit on <TICKET TYPE NAME> to <NUMBER> and add <NAME> <EMAIL> to it, and show me the changes before saving"

### Make your event invitation-only

Slug `make-an-event-invitation-only`. Guide: https://www.ticketfairy.com/guides/make-an-event-invitation-only

Compare a shared password, personal invitations and a ticket access code, or approve each order after checkout before the buyer gets their tickets.

For: Controlling who can buy tickets before or after checkout.

What an agent can do: Fai can compare the four approaches, check how your event is currently configured and set up the option you choose. She explains who gets access and when, then asks you to approve each change separately. You can also make every change in the dashboard.

Prompt for Fai: "Find my event by name. Ask me whether access should use shared passwords, personal invitations, a shared access code, or a decision after checkout. Recommend the best fit from my answer, explain who can get through and when access is decided, then show me every setting, ticket, promotion or invitation message you would change and ask me to approve each change separately"

### Password-protect your event

Slug `password-protect-your-event`. Guide: https://www.ticketfairy.com/guides/password-protect-your-event

Put your event page behind one or more shared passwords, test them and change a password without locking out the groups that still need access.

For: Sharing a private event through one or more trusted groups.

What an agent can do: Fai can add or remove event passwords and turn password protection on or off. She shows you the event and asks you to approve each change before she makes it. You can also complete the whole workflow in the dashboard.

Prompt for Fai: "Find my event by name, add these event passwords: <PASSWORDS>, and turn on Password required to view event only after at least one password is saved. Show me the event and every password that will remain, then ask me to approve each change"

#### Then: Replace a shared password

What an agent can do: Fai can create the replacement and remove the old password after you have tested the new one. MCP and the CLI do not manage event passwords.

Prompt for Fai: "For <EVENT NAME>, create a replacement for the password <OLD PASSWORD>. Show me the new password before saving it, and do not remove the old one until I confirm that I have tested the replacement"

#### Then: Review sales made with each password

What an agent can do: Fai can show Sales by Password and explain the rows. MCP and the CLI do not provide this password report.

Prompt for Fai: "Show me Sales by Password for <EVENT NAME>. Compare sales and revenue for each password and explain what the report can and cannot identify"

#### Then: Turn password protection off

What an agent can do: Fai can turn password protection off after showing you the event and the effect of the change. MCP and the CLI do not expose this setting.

Prompt for Fai: "Turn password protection off for <EVENT NAME>. Show me the event and confirm that its page will open without a password before changing it"

### Sell tickets by personal invitation

Slug `sell-tickets-by-personal-invitation`. Guide: https://www.ticketfairy.com/guides/sell-tickets-by-personal-invitation

Send each approved guest a personal ticket link, set how many tickets they can buy and how many orders they can place, and track or cancel an invitation after you send it.

For: Selling tickets through an approved invitation list.

What an agent can do: Fai can turn on the invitation requirement and prepare and send the approved list. She asks you to approve each change before she makes it. To check, resend or cancel an invitation you have sent, use the Invitations page, or your own AI assistant over the MCP server.

CLI MCP tools that read: `select_event`, `list_invitations`.

CLI MCP tools that make changes (not available with `--read-only`): `resend_invitation`, `cancel_invitation`.

Prompt for Fai: "Find my event by name, turn on Invitation required to attend, and prepare an invitation email for these approved guests: <names, email addresses, maximum tickets and maximum orders>. Unlock these ticket types with the same invitation: <ticket type names>. Show me the event setting, subject, message, ticket access and each recipient limit, then ask me to approve the event change and the send"

#### Then: Cancel a scheduled invitation

What an agent can do: Cancel a scheduled invitation in the dashboard. Fai, MCP and the CLI cannot cancel it before it is sent.

#### Then: Check what happened after you sent an invitation

What an agent can do: Your own AI assistant over the MCP server can list the invitations and their current statuses. Fai cannot list them, and the CLI does not have an invitation status command.

CLI MCP tools that read: `select_event`, `list_invitations`.

#### Then: Resend one invitation

What an agent can do: Your own AI assistant over the MCP server can resend one active invitation after you confirm the recipient. Fai cannot find the invitation, and the CLI does not expose invitation resends.

CLI MCP tools that read: `select_event`, `list_invitations`.

CLI MCP tools that make changes (not available with `--read-only`): `resend_invitation`.

#### Then: Cancel one invitation

What an agent can do: Your own AI assistant over the MCP server can cancel one active invitation after showing you the recipient and ticket choice. Fai cannot find the invitation, and the CLI does not expose invitation cancellation.

CLI MCP tools that read: `select_event`, `list_invitations`.

CLI MCP tools that make changes (not available with `--read-only`): `cancel_invitation`.

#### Then: Send an invitation reminder

What an agent can do: Send an invitation reminder in the dashboard. Fai, MCP and the CLI cannot send this reminder.

### Sell tickets only to your NFT holders

Slug `sell-tickets-only-to-your-nft-holders`. Guide: https://www.ticketfairy.com/guides/sell-tickets-only-to-your-nft-holders

Require ticket buyers to connect a wallet that holds one of your NFTs before they can buy tickets to your event, for every ticket or for one ticket type, and have the door check the NFT again at entry.

For: Selling event tickets to the holders of an NFT collection.

What an agent can do: Fai can take you to the event's Settings page, where you turn on the NFT requirement. The command line can set the requirement for the whole event through an event update.

Command line:

- Requires buyers of any ticket to the event to hold an NFT from one Ethereum collection: `ticketfairy event update <EVENT_ID> --body '{"flagNftOwnershipRequired":true,"nftContracts":{"ethereum":["<CONTRACT_ADDRESS>"],"polygon":[]},"nftLists":{"solana-mainnet":[]}}'`

Prompt for Fai: "Open the settings page for <EVENT NAME> so I can require NFT ownership to buy tickets"

#### Then: Require an NFT for one ticket type only

What an agent can do: Fai can take you to the event's Tickets page, and you set the requirement on the ticket type on that page. The command line sets it through a ticket type update.

Command line:

- Find every ticket type and its ID: `ticketfairy ticket list <EVENT_ID> --all`
- Requires buyers of one ticket type to hold an NFT from one Polygon collection: `ticketfairy ticket update <EVENT_ID> <TICKET_ID> --body '{"flagNftOwnershipRequired":true,"nftContracts":{"ethereum":[],"polygon":["<CONTRACT_ADDRESS>"]},"nftLists":{"solana-mainnet":[]}}'`

Prompt for Fai: "Open the tickets page for <EVENT NAME> so I can make <TICKET TYPE> available to NFT holders only"

#### Then: Stop requiring an NFT

What an agent can do: Fai can take you to the Settings page to turn the requirement off. The command line turns off the event's requirement through an event update.

Command line:

- Stops requiring an NFT for the whole event: `ticketfairy event update <EVENT_ID> --body '{"flagNftOwnershipRequired":false}'`

Prompt for Fai: "Open the settings page for <EVENT NAME> so I can stop requiring NFT ownership"

### Send free tickets to your guest list

Slug `issue-guest-tickets`. Guide: https://www.ticketfairy.com/guides/issue-guest-tickets

Send a guest, a reviewer or a crew member a ticket at no charge from the Guest Tickets page, one person at a time or from a spreadsheet, and see who you have sent tickets to.

For: Giving press, guests and crew a ticket at no charge.

What an agent can do: Fai can send guest tickets for you from a list you give her. She shows you the recipients, the ticket type and the count and asks you to approve before she emails anyone, because you can't unsend a ticket. You can also do all of this in the dashboard.

Prompt for Fai: "Send a Guest list ticket for <EVENT NAME> to <NAME> at <EMAIL ADDRESS>, show me the ticket type and the count before you send it"

#### Then: Send a whole list at once

What an agent can do: Fai takes the same list in the conversation and shows it to you before she sends anything.

Prompt for Fai: "Here is my press list for <EVENT NAME>. Send each of them one Guest list ticket, and show me the whole list and the total before you send"

#### Then: Issue more tickets than the type has left

What an agent can do: Fai reads what the type has left, names the shortfall and waits for you to say yes before she goes past it.

Prompt for Fai: "Send 12 Guest list tickets for <EVENT NAME> to <EMAIL ADDRESS> and tell me first whether that type has 12 left"

#### Then: Take a guest ticket back

What an agent can do: Fai finds the order and shows you the guest and the tickets on it. She can't cancel it unless you ask Ticket Fairy support to turn that on for her, so cancel it yourself on the page.

Prompt for Fai: "Find the guest ticket order for <EMAIL ADDRESS> on <EVENT NAME> and show me what it holds"

### Share one invitation link to your event

Slug `share-one-invitation-link-to-your-event`. Guide: https://www.ticketfairy.com/guides/share-one-invitation-link-to-your-event

Create one invitation link for a group, such as a sponsor's staff or a members' chat, choose the hidden tickets it unlocks and cap the tickets and orders the whole group can buy through it, then copy it and share it yourself.

For: Sharing ticket access with a group through one link.

What an agent can do: Fai can create an invitation link with the hidden ticket types it unlocks and its ticket and transaction limits. She asks you to approve it before she creates it. Then copy the new link with **Copy Link** on the Links tab. To give the link a held allocation, create it in the dashboard.

Prompt for Fai: "Create an invitation link for <EVENT NAME> for <GROUP NAME>. It should unlock the <HIDDEN TICKET TYPE> ticket type and allow up to <TICKETS> tickets across <ORDERS> orders in total. Show me the details before you create it"

### Unlock hidden tickets with an access code

Slug `unlock-hidden-tickets-with-an-access-code`. Guide: https://www.ticketfairy.com/guides/unlock-hidden-tickets-with-an-access-code

Keep your event page public with the ticket types hidden, and let buyers see them by entering an access code that carries no discount.

For: Sharing a private ticket sale through one reusable access code.

What an agent can do: Fai can hide the tickets, create a no-discount access code and close the promotion later. She shows you each change and asks you to approve it before she makes it. You can also complete the whole workflow in the dashboard.

Prompt for Fai: "Find my event by name. Keep <TICKET NAMES> active, hide them from the public with Always hidden, then create a promotion called <NAME> with access code <CODE>, No Discount, no automatic application, and only those tickets attached. Use <START AND END TIMES OR NO SCHEDULE> and <SHARED LIMIT OR NO LIMIT>. Show me the exact tickets, normal prices, schedule and limit, then ask me to approve the ticket changes and promotion separately"

#### Then: Replace an access code

What an agent can do: Fai can add the replacement code and remove the old one after you confirm the new code works. MCP and the CLI do not manage the hidden-ticket access-code workflow.

Prompt for Fai: "For the access-code promotion <PROMOTION NAME> on <EVENT NAME>, add <NEW CODE>. Keep <OLD CODE> active until I confirm the replacement works, then ask before removing the old code"

#### Then: Close every access code on the promotion

What an agent can do: Fai can delete the promotion after showing you its codes and hidden tickets. MCP and the CLI do not close this access-code workflow.

Prompt for Fai: "Show me the access-code promotion <PROMOTION NAME> on <EVENT NAME>, including its codes and hidden tickets, then ask before deleting the promotion"

## More

- All guides: https://www.ticketfairy.com/guides
- Guides MCP server: https://www.ticketfairy.com/docs/mcp (tools `search_guides` and `get_guide`)
- CLI reference: https://www.npmjs.com/package/ticketfairy
- Developer documentation: https://www.ticketfairy.com/developers
- Support: support@ticketfairy.com
