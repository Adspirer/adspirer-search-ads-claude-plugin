---
description: Find Google Ads and Microsoft Advertising spend that is not converting, such as search terms, keywords and campaigns, and propose fixes that are applied only after you approve.
argument-hint: "[platform] [period, e.g. last 30 days]"
---

# Wasted-spend review

Load adspirer-search-mcp and adspirer-search-optimize.

Use the platform and period the user gave. With none given, cover every connected ad platform for
the last 30 complete days.

1. Call get_connections_status. Work only on connected platforms and their active accounts.
2. Google Ads, through google_ads_read: run analyze_wasted_spend and analyze_search_terms. For
   Performance Max campaigns use analyze_pmax_search_terms.
3. Microsoft Advertising, through bing_ads_read: run analyze_microsoft_wasted_spend and
   analyze_microsoft_search_terms.
4. Separate rows with spend and no conversions from rows with a high cost per conversion. Do not
   call a row wasted when the sample is small, when conversions are still arriving, or when
   conversion tracking looks broken. Never propose brand terms as negatives.
5. Report the top items by spend with the evidence, and the total at stake per currency. For each
   one propose the smallest fix: a negative keyword with its match type and level, a bid change,
   or a pause of the narrowest resource.
6. Stop and wait. Apply only the changes the user explicitly approves, through google_ads_write
   or bing_ads_write, with confirm set only after that approval. Then read the changed resources
   back and report what was applied and anything the platform rejected.

Nothing is changed until the user approves a specific change.
