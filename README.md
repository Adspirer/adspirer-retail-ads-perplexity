# Adspirer Retail Ads for Perplexity

Amazon & Walmart retail advertising. Analyze ad performance, track ACoS and ROAS, research keywords, and create and optimize campaigns with your approval.

This package connects Perplexity to the hosted Adspirer Retail Ads MCP server and gives its agent the
skills to use it well. It covers Amazon Ads and Walmart Connect. It can change ad accounts, and only with your approval: campaigns are built paused, every change is shown first and read back afterwards.

## What's included

| File | Purpose |
| --- | --- |
| [connector.json](connector.json) | Connector details: name, URL, sign-in, logo, links |
| [LISTING.md](LISTING.md) | Paste-ready name, descriptions and submission notes |
| [AGENT.md](AGENT.md) | Agent instructions to paste into Perplexity |
| `skills/` | 11 Agent Skills (`SKILL.md` folders) |
| `dist/skills/` | The same skills as one zip each, for upload |
| `examples/` | Agent API request examples |

## Connect in Perplexity

1. In Perplexity, open **Computer** and choose **Connectors** in the left sidebar.
2. Choose **+ Custom connector** in the top-right corner.
3. Enter the name `Adspirer Retail Ads`, a short description, and the MCP server URL `https://mcp.adspirer.com/retail-ads`.
4. Tick **I understand custom connectors can introduce risks** and choose **Add**.
5. Perplexity opens the Adspirer authorization page. Sign in and approve access.
6. Connect your ad accounts at https://adspirer.ai/connections.

Custom connectors need a Perplexity Pro, Max or Enterprise plan. The full guide with screenshots
is at https://www.adspirer.com/docs/ai-clients/perplexity.

## Use with the Perplexity Agent API

A Project administrator adds the server once on the Project connectors page in the API Console
(server name, MCP URL, authentication, transport **Streamable HTTP**), then copies the connector
ID. Requests reference it by ID; see [examples/agent_api.py](examples/agent_api.py) and
[examples/agent_api.sh](examples/agent_api.sh).

Authentication: Perplexity's API Console offers **API Key** or **None** for custom connectors.
Use an Adspirer API key (starts with `sk_live_`), created at https://adspirer.ai/keys; it gives
the same access as browser sign-in. Revoke it there when you no longer need it. This route has not
been tested end to end.

Agent API connector calls run **without approval by default**. This connector can change ad accounts, so the examples set an approval policy and you should keep one on every request.

## Add the skills

Perplexity Computer supports Agent Skills:

1. In Perplexity, open **Computer** and choose **Skills** in the left sidebar.
2. Choose **+ Create skill** in the top-right corner.
3. In the **Upload skill** dialog, upload a skill: the `SKILL.md` file from a folder in `skills/`,
   or that skill's zip from `dist/skills/`, which also carries its `references/` files.
4. The skill appears in your Skills list, and Perplexity applies it when a request matches.

Upload `adspirer-retail-ads-tools` first; the other skills refer to it. If you upload `SKILL.md` on its
own, its `references/` files are not included, so prefer the zip. You can also paste
[AGENT.md](AGENT.md) into a Space's instructions as a short always-on version.

| Skill | Use it for |
| --- | --- |
| `adspirer-retail-ads-ad-creative` | Develop Amazon and Walmart advertising copy and asset plans using product evidence, platform formats and user-approved uploads or changes. |
| `adspirer-retail-ads-amazon` | Manage Amazon Sponsored Products, Sponsored Brands and Sponsored Display using the Retail endpoint, with profile-aware research, reporting and approved changes. |
| `adspirer-retail-ads-campaign-launch` | Plan and build paused Amazon and Walmart advertising campaigns with approved products, targeting, budgets and verified resources. |
| `adspirer-retail-ads-keyword-research` | Research retail keywords, ASINs, shopper demand, competitive products and targeting opportunities for Amazon and Walmart. |
| `adspirer-retail-ads-optimization` | Find wasted retail ad spend and propose Amazon or Walmart bid, targeting and budget improvements with explicit approval and readback. |
| `adspirer-retail-ads-performance` | Review Amazon and Walmart spend, attributed sales, ACoS, ROAS, item performance and budget pacing without changing campaigns. |
| `adspirer-retail-ads-product-help` | Answer Adspirer product, pricing, connection, quota and troubleshooting questions from current documentation, scoped to Amazon and Walmart. |
| `adspirer-retail-ads-setup` | Connect Amazon Ads and Walmart Connect accounts and optionally establish an approved retail brand workspace. |
| `adspirer-retail-ads-strategy` | Coordinate Amazon and Walmart retail-media planning, research, reporting, campaign creation and approved optimization. |
| `adspirer-retail-ads-tools` | Discover and call Amazon Ads and Walmart Connect tools through Adspirer Retail Ads. Use before retail tool calls to select the correct router and live schema. |
| `adspirer-retail-ads-walmart` | Manage Walmart Connect advertising, keyword and item performance, catalog insights, placements and approved campaign or asset changes. |

## Example prompts

- "Show ACoS and ROAS by campaign for my Amazon Sponsored Products last month."
- "Find negative keyword candidates in my Amazon search terms."
- "Which Walmart items are out of budget or underperforming this week?"

## Safety

- It can change ad accounts, and only with your approval: campaigns are built paused, every change is shown first and read back afterwards.
- **No purchases.** The agent never buys, upgrades, renews or starts a trial of a subscription or
  paid feature for you, including when it runs on its own with browser or payment tools. At a
  quota or plan limit it stops, explains and waits.
- **No unattended changes.** Scheduled or background runs are read-only.
- Sign-in is browser OAuth. Never paste tokens into chat.

An Adspirer account and an applicable plan are required; ad-platform permissions and usage limits
apply.

## Status

Built from https://github.com/Adspirer/adspirer-retail-ads-cursor-plugin v1.0.2 on 2026-11-11. Not yet installed or tested in
Perplexity. Run `node scripts/validate.mjs` after editing.

## Support

- Support: support@adspirer.com
- Documentation: https://www.adspirer.com/docs
- Privacy: https://www.adspirer.com/privacy
- Terms: https://www.adspirer.com/terms
- Security: see [SECURITY.md](SECURITY.md)
