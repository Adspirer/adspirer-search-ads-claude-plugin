---
description: Read-only scorecard for your Google Ads and Microsoft Advertising campaigns, compared with the previous period, with the top problems and next actions.
argument-hint: "[platform] [period, e.g. last 7 days]"
---

# Search performance review

Load adspirer-search-mcp and adspirer-search-performance-review.

Use the platform and period the user gave. With none given, cover every connected ad platform for
the last 30 complete days, compared with the 30 days before.

1. Call get_connections_status. Work only on connected platforms and their active accounts. If
   more than one account could be meant, ask which one.
2. Google Ads: call get_campaign_performance. For the reason behind a change, run
   explain_performance_anomaly through google_ads_read.
3. Microsoft Advertising: through bing_ads_read, run get_microsoft_campaign_performance, and
   analyze_microsoft_impression_share when impression share is part of the story.
4. Show one scorecard per platform: spend, impressions, clicks, CTR, average CPC, conversions,
   cost per conversion, ROAS where revenue is tracked, and the change against the previous period.
   Keep currencies separate. Compute ratios from totals, not from averages of rows.
5. List the three findings that matter most, each with the campaign and the numbers behind it,
   then at most three recommended actions.
6. Say what limits the numbers: partial days, conversion lag, or tracking gaps. If conversions
   look wrong, suggest audit_conversion_tracking.

This command changes nothing. If the user wants to act on a recommendation, describe the exact
change, wait for their approval, and follow adspirer-search-optimize.
