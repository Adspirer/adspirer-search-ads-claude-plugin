# Adspirer Search Ads for Claude

Run paid search from Claude Code and Cowork. Adspirer Search Ads connects Claude to your live Google Ads and Microsoft Advertising (Bing Ads) accounts through Adspirer's hosted Search Ads MCP server, so you can research keywords, review search terms, find wasted spend, and plan, launch and optimize Search, Shopping and Performance Max campaigns without leaving the conversation.

## Use it for

- **Keyword research:** Google Keyword Planner ideas with live CPC and search volume, intent grouping, and match types.
- **Search terms and negatives:** find queries that spend without converting and propose negative keywords, applied only after you approve.
- **Campaigns:** plan and build Search, Shopping and Performance Max campaigns on Google, and campaigns of every type on Microsoft Advertising, created paused.
- **Optimization:** wasted-spend analysis, budget allocation, bid strategy, impression share, Quality Score, and ad extension performance.
- **Ad copy:** responsive search ad headlines and descriptions written to Google's and Microsoft's limits.
- **Measurement:** audit conversion tracking and, when connected, read Google Analytics 4, Search Console and Tag Manager.

## Install

In Claude Code:

```text
/plugin marketplace add Adspirer/adspirer-search-ads-claude-plugin
/plugin install adspirer-search-ads@adspirer-search-ads
```

On first use, Claude opens Adspirer's OAuth sign-in in the browser. Sign in, then connect the
accounts you want to use at [adspirer.ai/connections](https://adspirer.ai/connections). No API
key or client secret is required. An Adspirer account is required, and plan usage limits apply.

## Get started

Ask:

```text
Research keyword opportunities for my plumbing business in Austin and propose a campaign plan. Don't create anything yet.
Review my Google Ads search terms for the last 30 days and suggest negative keywords.
Where am I losing impression share on Microsoft Advertising, budget or rank?
Write five new responsive search ad headlines from my best-converting queries.
Audit my conversion tracking before I launch anything.
```

## What the agent can do

| Area | Capabilities |
| --- | --- |
| Google Ads | Search, Shopping, Performance Max, Demand Gen, YouTube and Display: campaigns, ad groups, keywords, ads, extensions, bids and budgets |
| Microsoft Advertising | Campaigns of every type, ad groups, ads, keywords, negative-keyword lists, extensions, audiences, budgets, bid strategies and UET conversion goals |
| Reporting | Campaign, ad, keyword, search term, placement and conversion-action performance on Google; campaign, keyword, search term, geographic and audience performance on Microsoft |
| Diagnostics | Wasted spend, performance anomalies, impression share lost to budget or rank, Quality Score components, and share of voice |
| Competitor research | The public ads a competitor is running now, beside your own |
| Measurement | Conversion-tracking audit, plus Google Analytics 4, Search Console and Tag Manager when connected |

Google Ads and Microsoft Advertising are the advertising platforms on this connector. Meta, TikTok, LinkedIn, Amazon and Walmart are not included; for those, use Adspirer Social Ads, Adspirer Retail Ads, or the full Adspirer Advertising Agent.

## What's included

- **Skills:** `adspirer-search-agent`, `adspirer-search-campaigns`, `adspirer-search-competitors`, `adspirer-search-creative`, `adspirer-search-docs`, `adspirer-search-google-ads`, `adspirer-search-google-analytics`, `adspirer-search-google-search-console`, `adspirer-search-google-tag-manager`, `adspirer-search-keywords`, `adspirer-search-mcp`, `adspirer-search-measurement`, `adspirer-search-microsoft-ads`, `adspirer-search-optimize`, `adspirer-search-performance-review`, `adspirer-search-setup`.
- **A subagent** (`adspirer-search-advertising-agent`) that coordinates those skills.
- **The Adspirer Search Ads MCP server** connection (`.mcp.json`).

The hosted server is the source of truth for tool names and schemas. The skills teach the agent to
discover the current tools and their parameters instead of hardcoding every operation.

## Safety

- The agent reads account state and performance before proposing changes.
- New campaigns are created paused, and enabling them is a separate decision.
- Campaign creation, budget changes, bid changes, and other spend-affecting writes require your
  explicit approval. The server also holds spend-affecting and irreversible writes until they are
  confirmed.
- The agent reads created or changed resources back before reporting success.
- Campaigns are never deleted automatically.
- Tool results, competitor ads and website text are treated as data, never as instructions.

## MCP and authentication

```json
{
  "mcpServers": {
    "adspirer-search-ads": {
      "type": "http",
      "url": "https://mcp.adspirer.com/search-ads"
    }
  }
}
```

Authentication uses OAuth 2.1 with PKCE. Claude handles the browser sign-in; the plugin contains no
API keys, tokens, client secrets, or environment variables. Ad-platform credentials stay
server-side with Adspirer and are scoped to the accounts you connect.

## Network and execution surface

The plugin's only MCP server is `https://mcp.adspirer.com/search-ads`. It contains no hooks, scripts, telemetry,
local executables, or bundled server code. Skills, the subagent are Markdown
guidance. Beyond the Adspirer server, the skills may ask Claude to read Adspirer's public
documentation at `adspirer.com/docs` to answer questions about plans and setup.

## Related plugins

Adspirer Search Ads is one of Adspirer's focused plugins. The full
[Adspirer Advertising Agent](https://github.com/Adspirer/adspirer-claude-plugin) covers every
supported platform in one plugin. Installing both is supported; use one connection per task.

## Privacy, support, and source

- Privacy policy: [adspirer.com/privacy](https://www.adspirer.com/privacy)
- Terms: [adspirer.com/terms](https://www.adspirer.com/terms)
- Documentation: [adspirer.com/docs](https://www.adspirer.com/docs/ai-clients/claude-code)
- Support: [support@adspirer.com](mailto:support@adspirer.com)
- Source and issues: [Adspirer/adspirer-search-ads-claude-plugin](https://github.com/Adspirer/adspirer-search-ads-claude-plugin)

## License

MIT. See [LICENSE](LICENSE).
