---
description: Connect Google Ads and Microsoft Advertising to Adspirer, choose the accounts to work on, and get a first look at what is running.
---

# Set up Adspirer Search Ads

Load adspirer-search-mcp and adspirer-search-setup.

1. Call get_connections_status. If it fails because the connector is not signed in, tell the user
   to connect the Adspirer Search Ads connector (in Claude Code: run /mcp, choose
   adspirer-search-ads and sign in), then stop and wait. Never ask for a password or token in chat.
2. List what is connected: Google Ads and Microsoft Advertising accounts, plus Google Analytics 4,
   Search Console and Tag Manager where linked. Name the active account on each platform.
3. If a platform the user wants is missing, give them https://adspirer.ai/connections and
   wait. If several accounts exist and it is unclear which to use, ask. Activating or switching
   accounts changes the active set, so call activate_ad_accounts only after the user confirms the
   exact accounts.
4. Take a first look at the last 30 days on each connected ad platform: get_campaign_performance
   for Google Ads, and get_microsoft_campaign_performance through bing_ads_read for Microsoft
   Advertising. Skip a platform that is not connected; do not invent numbers for it.
5. Finish with a short summary: what is connected, what is not, spend, conversions and cost per
   conversion for each platform, and what to try next: /adspirer-search-ads:performance-review
   for a full scorecard or /adspirer-search-ads:wasted-spend to find spend that is not converting.

This command changes no campaign and creates no files. Build a brand workspace only if the user
asks for one.
