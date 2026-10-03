# Your first guest post in five minutes (self-serve, with an agent)

What you need: a Linkio account on self-serve billing, an API key from https://www.linkio.com/account/api-keys,
and Claude Code (or Claude.ai / ChatGPT with the Linkio connector; see the keys page). The agent does the
work; you answer one question at a time and approve anything that spends or sends.

## 0. Money first (30 seconds)
Either add your own OpenAI and DataForSEO keys at https://www.linkio.com/account/ai-keys and get the $10
free start, or add money at https://www.linkio.com/shop, or add a card at https://www.linkio.com/billing.
Every paid step tells you what it will hold before it runs; a step the account cannot fund answers with
those three links instead of running.

## 1. Connect (1 minute)
```
export LINKIO_API_KEY=acc_your_key
claude --plugin-dir ./linkio        # the plugin folder from the Linkio repo (plugins/linkio); a marketplace install follows once published
```
Then: "I run https://yoursite.com and I want links to my pricing page."

## 2. What the agent does, and what it asks you
| Minute | The agent | You |
|---|---|---|
| 1 | Reads your site and the account, proposes the pages to link to and the keywords, says what the account can fund | "go", or correct it |
| 2 | Creates your brand and pages, stores the keywords (free), activates a monthly plan | nothing |
| 3 | Searches the site inventory (0.25c a site after the first 100 a day; the first page is free), shows a short table: site, authority, traffic, price, record with Linkio (delivered 6 of 6, 10 days) | pick, or say "your call under $150" |
| 4 | Opens the order for the picks; writes the article in your own words with your own model, or asks before paying Linkio's writer (price shown first) | approve the article |
| 5 | Shows you the exact message to the publisher | "yes" sends it |

After that it watches: tells you when the publisher replies, when the link is live (it opens the page and
checks the link itself), when an invoice arrives (you pay the publisher directly, at the price you saw;
the agent shows the link and the amount, and records the payment when you say you paid), and what the
month cost (`usage_jobs`).

## The rules it keeps
- One question per message. Proposal first, question last.
- Nothing sent to a publisher and nothing paid without your explicit yes on the exact text or amount.
- Every number comes from a tool result or a page it opened; it says "my judgment" otherwise.
- A site is described by its numbers and its record, never by labels about the seller.

## Without an agent
The same steps are buttons in the app: https://www.linkio.com/orders/new. Each paid button shows the hold
under it; the billing page shows what you paid for.

## API and MCP
Everything above is a tool call: `account_me`, `client_create`, `target_pages_add`, `website_search`,
`ai_find_sites_start`, `order_create`, `article_gen_start`, `workflow_send_to_publisher`,
`workflow_verify_publication`, `usage_estimate`, `usage_receipt`, `usage_jobs`. Prices:
`docs/05-reference/self-serve-billing-api.md`.
