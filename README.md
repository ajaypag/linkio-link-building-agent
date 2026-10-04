# Linkio — link building agent for Claude Code

Your own link-building agent: it reads your site, picks the pages worth linking to, finds guest post sites
with real numbers (authority, traffic, price, and the site's record with Linkio), plans the month, writes
the article in your own words with your own model, hands it to the publisher after you approve the exact
message, checks that the link went live, and tells you what the month cost. It never moves money and never
messages anyone without your yes.

## Install (2 minutes)

1. Make an API key at https://www.linkio.com/account/api-keys (self-serve accounts: full access; managed
   accounts: read-only).
2. Put it in your shell before you start Claude Code: `export LINKIO_API_KEY=acc_...` (Claude Code reads it
   at start; if the agent says it has no Linkio tools, the key was not in that environment).
3. Add the plugin:
   ```
   claude plugin marketplace add ajaypag/linkio-link-building-agent
   claude plugin install linkio@linkio
   ```
   (or, from a checkout of this folder, `claude --plugin-dir ./linkio`).
4. Start Claude Code in any folder and say what you sell: "I run https://example.com, I want links to my
   pricing page." The agent takes it from there.
5. The first time a Linkio tool runs, Claude Code asks you to allow it — choose Allow (once per tool, or
   allow the whole `linkio` server in `/permissions`). Nothing is paid or sent by that prompt; the agent
   still asks before any paid step.

## Claude.ai or ChatGPT instead of Claude Code?
No plugin and no key. Add `https://mcp.linkio.com/mcp` as a custom connector (Claude.ai: Customize → Connectors
→ Add → Add custom connector; ChatGPT: Plugins → Add → Create custom MCP server, Authentication: OAuth) and sign in
with your Linkio email and password. The same tools and the same rules apply.

## What it costs

Nothing for the plugin. Linkio meters the steps that do work: site search 0.25c a site after the first 100
a day, automated site finding about 30c a site found, topic research and Linkio's own article writer per
piece, keywords per page. Writing the article yourself in Claude Code uses your own Claude plan, not Linkio.
Publishers are paid by you, directly, at the price shown. Every paid step is priced before it runs, and the
agent asks before spending. The $10 free start applies once you add your own OpenAI and DataForSEO keys at
https://www.linkio.com/account/ai-keys.

## Files

- `.mcp.json` connects the Linkio MCP server (`https://mcp.linkio.com/mcp`) with your key.
- `skills/linkio-client-agent/SKILL.md` is the playbook the agent follows: investigate first, one question
  per message, prices before the click, nothing sent and nothing paid without your yes.

## First job in five minutes

See [FIRST-JOB.md](./FIRST-JOB.md).
