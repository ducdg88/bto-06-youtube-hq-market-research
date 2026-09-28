[🇻🇳 Tiếng Việt](README.md) · **🇬🇧 English**

# BTO-06: YOUTUBE HQ Market Research

Hoàng Văn Đức · Build to Own, Cohort 01 · September 27, 2026

## Executive summary

YOUTUBE HQ is a shared operations dashboard for small Vietnamese YouTube studios running 5 to 20 channels for overseas audiences: one screen shows real metrics, revenue and team bonuses, while each channel uses a separate sign-in.

- **Who it is for:** Vietnamese YouTube studio owners with 5 to 20 channels and teams of 2 to 6 people (editors, camera operators, analysts) who are not technically inclined. The first user is me: 10 channels and a team of 4.
- **How it differs from existing tools:** popular YouTube tools (vidIQ, TubeBuddy, Viewstats) charge per channel and focus on one channel; multi-channel tools (AgencyAnalytics, Coupler.io, Metricool) are built for agency reporting, not team operations. None of the tools reviewed combines metrics, revenue and team bonuses in one Vietnamese-language workspace with fixed plan pricing instead of per-channel pricing.
- **What to build first:** connect each channel with its own Google account, sync metrics automatically, show 10 channels on a dashboard with last-updated times, flag declining or disconnected channels, and query metrics in natural language via AI (MCP). Video publishing, competitor tracking and a mobile app are out of scope.

## Part 1. Market research

### Market overview

The YouTube analytics tool market has four groups, all of which assume either a single channel or a large agency with staff who build reports. YouTube Studio is free but shows one channel at a time, so someone managing 10 channels must switch accounts 10 times.

![Market map: four tool categories and the gap](images/ban-do-thi-truong.png)

Small multi-channel studios fall between these categories: too many channels for single-channel tools, too small and understaffed technically for agency tools and data pipelines.

### Main competitors and pricing

For 10 channels, common tools cost roughly USD 166 to 200 a month, or require a sales call for an enterprise plan. Prices come from pricing pages and reviews checked in July and August 2026.

| Competitor | Category | Price | Multi-channel support | Estimated cost for 10 channels |
| --- | --- | --- | --- | --- |
| [vidIQ](https://1of10.com/blog/vidiq-pricing/) | Single-channel growth | Boost USD 39/month or USD 199/year; Max USD 468/year | One channel per plan; multiple channels require Enterprise, contact sales | Ten annual Boost plans: about USD 166/month |
| [TubeBuddy](https://1of10.com/blog/tubebuddy-pricing-review/) | Single-channel growth | Pro USD 43.20/year; Legend USD 278.28/year | One license per channel; Legend offers two user seats | Ten Legend plans: about USD 232/month |
| [Viewstats](https://outlierkit.com/resources/viewstats-pricing/) | Growth and research | Pro USD 49.99/month; Business from USD 249/month | Business for teams and agencies, sales call required | Business: from USD 249/month |
| [AgencyAnalytics](https://agencyanalytics.com/pricing) | Agency reporting | USD 20 per client/month (annual billing) | Multiple clients, white-label dashboards | Ten channels counted as ten clients: about USD 200/month |
| [Metricool](https://metricool.com/pricing/) | Cross-platform reporting | Starter EUR 16 to 29/month (5 to 10 brands) | Priced by number of brands | Starter with 10 brands: about EUR 29/month |
| [Coupler.io](https://www.coupler.io/pricing) | DIY data pipeline | Starter USD 24, Active USD 99, Pro USD 199/month (annual billing) | Priced by number of source accounts | Active (15 accounts): USD 99/month, dashboard must still be built |
| YouTube Studio + Looker Studio | Free | 0 | Studio shows one channel at a time; Looker requires manual setup | USD 0, but time is spent building and maintaining it |

The 10-channel cost column extrapolates from published prices, without regional discounts. [OverseerOS](https://www.overseeros.com/blog/best-multi-channel-youtube-analytics-tools) also lists ChannelMeter, Tubular Labs, Sprout Social, Whatagraph and DashThis as multi-channel tools.

### Teardown of four existing approaches

Each solves one piece but none answers a studio owner's daily questions: how are the 10 channels doing today, which are declining, and how much bonus is owed to each team member?

**1. vidIQ (single-channel growth tool)**

- **Problem addressed:** helps a creator find ideas, keywords and video optimizations to grow a channel.
- **Main features:** keyword research, competitor channel tracking, AI title and idea suggestions; paid plans use AI credits (Boost 2,000, Max 6,000 credits/month).
- **How it works:** sign in with one channel and use the web app and browser extension. Boost and Max cover one channel; multiple channels require Enterprise.
- **Weakness for multi-channel studios:** no multi-channel dashboard on self-service plans, no team roles, focus on growth rather than operations.

**2. AgencyAnalytics (agency reporting)**

- **Problem addressed:** marketing agencies need to send periodic reports to multiple clients without doing it manually.
- **Main features:** over 85 data sources (including YouTube), unlimited dashboards and reports, white-labeling, unlimited staff and client users.
- **How it works:** each customer is a "client", source accounts are connected to that client, and pricing is USD 20 per client per month.
- **Weakness for multi-channel studios:** designed for client reporting, not team bonuses, daily workflows or studio-style decline alerts; 10 channels cost about USD 200/month.

**3. Coupler.io + Looker Studio (DIY data pipeline)**

- **Problem addressed:** bring data from 400+ sources into Google Sheets, Looker Studio or BI tools to build custom reports.
- **Main features:** scheduled daily refreshes (hourly on Pro), pricing by number of source accounts.
- **How it works:** each channel is a source account; data flows into tables, then the user builds a dashboard.
- **Weakness for multi-channel studios:** requires someone who can build dashboards; when a channel loses access, its figures may stay frozen without an alert.

**4. My current manual process (the real alternative)**

- **Today:** open YouTube Studio for each channel, receive revenue updates from a Telegram bot every three hours, use an extension to log to Google Sheets, about 30 minutes a day.
- **Weakness:** data is spread between Telegram, Sheets and the app; the bot once reported that it was running without producing a result; declining channels may go unnoticed for days. As of September 27, 2026, only 1 of 10 channels was connected to YOUTUBE HQ.

### Market gap matrix

The largest gap lies in team operations: view-based bonuses, decline alerts and Vietnamese-language support. Multi-channel aggregation itself already exists, but is expensive or requires custom setup.

| Need of a 10-channel studio | vidIQ | TubeBuddy | AgencyAnalytics | Coupler + Looker | YouTube Studio | YOUTUBE HQ |
| --- | --- | --- | --- | --- | --- | --- |
| Aggregate channels without an enterprise plan | No | No | Yes | Yes, DIY | No | Yes |
| Each channel signs in separately, no shared token | Not confirmed | Not confirmed | Not confirmed | Not confirmed | Yes | Yes |
| Team roles, admin-only revenue | Not confirmed | Two user seats | Staff users | Depends on setup | Per-channel permissions | Yes |
| Team bonuses based on video view milestones | Not confirmed | Not confirmed | Not confirmed | Not confirmed | No | Yes |
| Alerts for declining or disconnected channels | Not confirmed | Not confirmed | Not confirmed | No | No | In progress |
| Natural-language metric queries via AI (MCP) | Not confirmed | Not confirmed | Not confirmed | No | No | Yes |
| Vietnamese language and VND pricing | No | No | No | No | Vietnamese | Yes |
| Monthly cost for 10 channels (USD) | About 166 | About 232 | About 200 | From 99 plus setup work | 0 | About 20 (proposed) |

"Not confirmed" means the feature was not found on the pricing pages or in the reviews consulted, not that the tools were tested directly. The YOUTUBE HQ column reflects the app available locally at the time (Bonus page, roles, youtube-hq MCP) and ticket HOA-8 for alerts.

## Part 2. Product direction

Chosen direction: an operations dashboard for Vietnamese multi-channel YouTube studios, sold in fixed VND-denominated plans at roughly one-eighth the cost of buying vidIQ for each channel.

### ICP: ideal customer profile

- **Who:** YouTube studio owners in Vietnam running 5 to 20 channels for US and European audiences; teams of 2 to 6 including editors, camera operators and analysts.
- **Characteristics:** no developer on staff; pay salaries or bonuses based on views; want separate Google accounts for channels to avoid linking their sign-ins.
- **Not the ICP:** single-channel creators (vidIQ and TubeBuddy serve them), multi-platform marketing agencies (AgencyAnalytics serves them), and MCNs with hundreds of channels.
- **First user:** me, with 10 channels and a team of 4, currently spending about 30 minutes a day on this work.

### Problems they face

1. They have to open YouTube Studio for each channel and switch accounts repeatedly; there is no shared dashboard.
2. A channel loses views or access, and they only discover it days later.
3. They calculate view-based bonuses manually in Sheets, inviting mistakes and disputes.
4. International tools charge USD per channel: 10 channels already cost USD 166 to 232 per month.

### Proposed pricing (not yet validated with customers)

| Plan | Channels | Users | Monthly price |
| --- | --- | --- | --- |
| Free | 2 | 1 | VND 0 |
| Studio | 10 | 5 | VND 499,000 (about USD 19) |
| Team | 30 | 15 | VND 1,290,000 (about USD 50) |

Rationale: the 10-channel Studio plan costs about one-eighth of ten vidIQ Boost plans and one-tenth of AgencyAnalytics. Conversion uses about VND 26,000/USD.

### USP

**One dashboard for the entire studio: real metrics for every channel, revenue and team bonuses, separate sign-ins for each channel, Vietnamese language, and fixed-plan rather than per-channel pricing.**

### Why choose YOUTUBE HQ instead of the alternatives

1. **Affordable at multi-channel scale:** adding channels does not multiply the price; about USD 19 for 10 channels versus USD 166 to 232.
2. **Operations, not just reporting:** view-milestone bonuses, team roles, admin-only revenue.
3. **Separated channel access:** each channel is connected through its own read-only sign-in, with its token stored on the studio's own machine.
4. **Ask questions in natural language:** ask Claude "which channels dropped this week?" via MCP without building a report.

Before continuing the build, interview five studio owners to validate the bonus problem and the VND 499,000 price point.

## Part 3. Initial product spec

The first release does one thing well: when a studio owner opens the app, they can see how their 10 channels are doing today and spot anything abnormal immediately. The full seven-part spec is in the private product repo (`spec.md`).

### Main flows

**Flow 1. Daily workflow: metrics sync automatically into the dashboard**

![Flow 1: from connecting channels to team bonuses](images/flow-chinh.png)

The most important failure branch is an expired token: the channel should show "disconnected" immediately on the dashboard, not show stale metrics as if they were fresh.

**Flow 2. Connect a new channel**

![Flow 2: connect a new channel with a separate Google sign-in](images/flow-ket-noi-kenh.png)

An admin opens the connection link in the Chrome profile dedicated to that channel so different Google accounts are not signed into the same browser profile. If they choose the wrong account (without a channel) or cancel access, nothing is saved.

**Flow 3. Approve month-end bonuses**

![Flow 3: approve bonuses based on view milestones](images/flow-duyet-thuong.png)

A bonus becomes payable only after admin approval; team members see their own bonuses but not channel revenue.

### Main user stories

1. As a studio owner, I want to connect each channel with the correct Google account so channels do not share a sign-in.
2. As a studio owner, I want one screen showing views, watch time, net subscribers and 28-day revenue for all 10 channels, so I do not have to open Studio 10 times.
3. As a studio owner, I want the dashboard to flag falling channels, figures older than 12 hours or lost connections, so I can act on them that day (Telegram notifications can come later).
4. As an editor on the team, I want to see which view milestones my videos reached and how much bonus I earned, without seeing channel revenue.
5. As a studio owner, I want to ask Claude "which channels dropped this week?" and receive real metrics without building a report myself.

### User and admin features

| Feature | Who uses it | First release |
| --- | --- | --- |
| All-channel dashboard with last-updated time on each row | Admin, analyst | Yes |
| Channel details: Studio metrics, 10 latest videos | Admin, analyst | Yes |
| My view-milestone bonuses | Editor, camera operator | Yes |
| Natural-language metric queries via MCP | Admin | Yes |
| Connect and disconnect Google channels | Admin | Yes |
| Invite members, assign roles, hide revenue from staff | Admin | Yes |
| Set bonus milestones, approve month-end bonuses | Admin | Yes |
| Set alert thresholds and delivery destination (Telegram) | Admin | Later |
| View per-channel sync and error logs | Admin | Yes |
| Publish, edit, delete videos; track competitors; mobile app | Nobody | Out of scope |

### Architecture

The app runs on the studio's own machine (Electron). A local backend stores each channel's token and only responds to requests from that machine; it calls the YouTube Data API and Analytics API with read-only access. The full architecture diagram, including failure branches, is in the product repo (`docs/architecture.html`). The build was broken into eight Linear tickets (HOA-5 through HOA-12) with a target of October 4, 2026.

## Sources

Pages accessed on September 27, 2026; pricing may vary by region.

- [vidIQ Pricing 2026, 1of10](https://1of10.com/blog/vidiq-pricing/) (price check from July 2026)
- [TubeBuddy Pricing and Review, 1of10](https://1of10.com/blog/tubebuddy-pricing-review/) (price check from July 2026)
- [ViewStats Pricing, OutlierKit](https://outlierkit.com/resources/viewstats-pricing/) (price check from August 6, 2026)
- [AgencyAnalytics Pricing](https://agencyanalytics.com/pricing)
- [Metricool Pricing](https://metricool.com/pricing/)
- [Coupler.io Pricing](https://www.coupler.io/pricing)
- [10 Best Multi-Channel YouTube Analytics Tools, OverseerOS](https://www.overseeros.com/blog/best-multi-channel-youtube-analytics-tools)
- Internal figures: BTO-02 and BTO-04 drafts, youtube-hq MCP as of September 27, 2026.
