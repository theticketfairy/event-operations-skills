# Ticket Fairy: rules for AI coding agents

These rules apply when you write code or run an agent that uses Ticket Fairy, the
ticketing platform at https://www.ticketfairy.com. Follow them from the first prompt.

## Choose the right interface

| Task | Use |
| --- | --- |
| Read live public events (no account, no key) | `GET https://www.ticketfairy.com/api/v1/events/listing` |
| Read the full API description | https://www.ticketfairy.com/api/v1/openapi.json |
| Public event search from an MCP client | `https://www.ticketfairy.com/agentic/mcp` (Streamable HTTP, tool `search_events`) |
| How to do something on Ticket Fairy, from the official guides | `https://www.ticketfairy.com/docs/mcp` (Streamable HTTP, tools `search_guides` and `get_guide`) |
| Public event search over A2A 1.0 | Agent Card at https://www.ticketfairy.com/.well-known/agent-card.json |
| Manage an organiser's own events, tickets and orders | The official CLI: `npm install -g ticketfairy`, then `ticketfairy --help`. `ticketfairy mcp` starts its local MCP server. |
| Step-by-step agent workflows | The skills in [`skills/`](skills/) |

Full developer documentation: https://www.ticketfairy.com/developers

## Rules

1. **Public reads need no credential.** Do not send cookies, bearer tokens or payment
   details to the public listing API, the public MCP endpoint or the A2A endpoint.
2. **Never use `q` as a query parameter.** Use `search` for a name search.
3. **Page with the cursor.** Start with `size=20`. Send `data.pagination.nextCursor` back as
   `cursor` with the same filters, and stop when it is `null` or when you have enough
   results. Never download the whole catalogue. The maximum `size` is 200.
4. **Respect rate limits.** Read the `RateLimit` headers. On HTTP 429 or 503, wait for
   `Retry-After` and do not retry in parallel.
5. **Dates need a timezone.** With `section_type=none`, send `from`, `to` and an explicit
   IANA `timezone`. Do not infer a buyer's timezone from your server's location.
6. **Public search creates no reservation, order or payment.** Buyer purchases use the
   supported checkout described in `find-event-tickets`, with its published handler and the
   buyer's explicit approval of the final tickets, total and currency. Otherwise continue in
   the browser at the event's `url`. Organiser credentials do not grant purchase authority.
7. **Use the consumer domain for links you give people.** Public event pages, embeds and
   checkout links use `www.ticketfairy.com`. The organiser dashboard is
   `manage.ticketfairy.com`, and the organiser API is `www.theticketfairy.com/api`.
8. **Organiser actions run as the signed-in organiser.** Use the CLI or an organiser
   credential, and only for events that organiser can manage. Confirm with the user before
   you create, change, refund or cancel anything.
9. **Keep secrets out of code and logs.** Read credentials from the environment. Never
   commit, print or paste an API key or token.

## Example

```sh
curl 'https://www.ticketfairy.com/api/v1/events/listing?search=festival&section_type=upcoming&sort=start_date&order=asc&size=20'
```

## Support

Email support@ticketfairy.com.
