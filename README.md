# ipv4 proxy: what it is, when you actually need one, and how to buy clean residential IPv4 addresses

Search "ipv4 proxy" and you get two flavours of page. One is a glossary entry that defines the term in four sentences and leaves you exactly where you started. The other is a provider's landing page with a big discount badge and no explanation of why the address family matters.

The real question sitting behind that keyword is usually more specific: *do I need IPv4 specifically, or am I paying extra for something I don't use?* And then: what should a clean residential IPv4 address cost, and what should I check before handing over money?

That's what this covers. Concept first, buyer's checklist second, and a concrete price list at the end.

## What an IPv4 proxy is, mechanically

A proxy server sits between your client and the website you're hitting. You send your request to the proxy, the proxy opens the outbound connection from its own IP address, and the destination site sees that address instead of yours. Put "IPv4" in front and you've narrowed it to one thing: the address the target site sees is a 32-bit IPv4 address, the `192.0.2.14` format everybody recognises.

Two connection types matter in practice. HTTP/HTTPS proxies handle web traffic and are the default for browsers and SEO tools. SOCKS5 works at a lower level, so it carries TCP and UDP traffic and doesn't care what application is talking — scrapers, automation scripts, some desktop software. Most paid providers support both, and you'll want to confirm that before buying rather than after.

There's also the anonymity layer. A transparent proxy tells the site you're proxying. An anonymous proxy hides your real IP but still announces itself as a proxy. An elite proxy does neither. For scraping and account work, elite is the tier you care about, because a target that can see "this is a proxy" will often just serve you a CAPTCHA anyway.

One thing worth saying plainly: a proxy is not a VPN. A VPN encrypts everything leaving your machine. An IPv4 proxy typically handles traffic from one app or one protocol. If your actual goal is encrypting your whole connection, a proxy is the wrong tool and you'll be disappointed.

## IPv4 versus IPv6: why this shows up on your bill

IPv4 has about 4.3 billion addresses and they ran out years ago. New blocks trade on a secondary market, and providers buy them with real money. IPv6 has 128 bits of address space, effectively unlimited supply, which is why some providers price IPv6 plans at roughly 10 to 20% of the equivalent IPv4 plan.

So why doesn't everyone just switch? Because the internet didn't move as one. Roughly 40 to 45% of traffic now travels over IPv6, mostly driven by mobile carriers and the big platforms — Google, YouTube, Meta, anything behind Cloudflare. The rest of the web is a long tail of smaller sites, ageing e-commerce platforms, corporate domains and niche marketplaces that are still IPv4-only. Point an IPv6-only proxy at one of those and the connection simply doesn't complete. No error message that explains itself, just a failure.

Tooling has the same unevenness. Current versions of curl, Python's requests and modern browsers speak IPv6 fine. Older scrapers, hand-rolled scripts and some SEO desktop software don't, and a few behave unpredictably when the resolver picks an address family. Anti-detect browsers and multi-accounting setups usually stay on IPv4 for a different reason: account trust scores were built on IPv4 history, and a sudden jump to an IPv6 prefix is a fingerprint change.

The decision rule that falls out of all this is short. If every target and every tool in your stack handles IPv6, an IPv6 plan saves you real money. If even one link in the chain doesn't — one stubborn target, one old scraper, one anti-detect profile — stay on IPv4 and don't think about it again.

## Where an IPv4 proxy actually earns its cost

- **Scraping targets with no IPv6 support.** The most common reason people end up here. You can't negotiate with a site that never deployed AAAA records.
- **Price and stock monitoring on regional e-commerce.** Retail platforms vary wildly by country, and plenty of regional storefronts are IPv4-only.
- **Ad verification.** Confirming which creative a real user in a given city sees, usually with targeting down to city or ISP level.
- **SEO and SERP monitoring.** Search results differ by location, and the tooling ecosystem is built around HTTP proxies with IPv4 endpoints.
- **Multi-account management.** Anti-detect browsers and emulators expect an IPv4 endpoint plus stable session behaviour.
- **Web data collection where bandwidth is unpredictable.** If you're pulling page after page through the same address, per-IP billing with unlimited traffic beats per-GB billing.

Where it doesn't work: streaming. Major platforms actively block datacenter and residential proxy ranges, and this is a general pattern rather than a quirk of one provider. If your goal is watching regional Netflix, buy nothing and save the money.

## The buyer's checklist

Before you pay, get answers to these. Vague answers are your signal to walk.

**Pool size and coverage.** "Millions of IPs" is marketing until you check the country count. If you need Romania, Vietnam or Brazil specifically, ask for the actual number rather than the global total.

**Targeting granularity.** Country-level is table stakes. State, city, ZIP and ISP-level selection is what separates a usable product from an annoying one for localised testing.

**Billing model.** Per IP with unlimited bandwidth, or per GB of traffic? These suit completely different workloads, and picking wrong is the single most expensive mistake here.

**Protocol support.** HTTP, HTTPS, SOCKS5. Some tools only accept one.

**How the proxy is delivered.** Dashboard-generated `host:port:user:pass` strings work on a cloud server. A desktop app that does local port forwarding does not — that's a workstation tool, and it matters if your workloads run headless.

**IP lifetime and balance expiry.** How long does one address stay alive, and does your unused balance disappear in 30 days? For project-based work, the second question can matter more than the price.

**A trial or low entry tier.** Ten dollars to test beats two hundred to find out.

## 9Proxy, measured against that list

9Proxy is a residential-only provider: 20M+ residential IPs across 90+ countries, country/state/city/ZIP/ISP targeting, HTTP/HTTPS and SOCKS5, and a stated 99.95% uptime. Its own documentation shows IPv4 endpoints in the `38.180.149.107` format in setup guides for FoxyProxy, Proxifier and Hidemyacc, which is what you'd expect — residential pools are IPv4 in practice.

It sells the same pool through two different billing models, and this is the part worth understanding properly.

**Residential by IP** charges per address with unlimited bandwidth. Unused IPs don't expire until you activate them, so buying in bulk and drawing down over months is viable. Each address stays online for somewhere between a few hours and about 24 hours, which is normal for real residential connections. The catch: this model is managed through a desktop app that does local port forwarding, so it's a Windows workstation setup more than a server one.

**Residential by GB** charges per gigabyte and lets you generate unlimited endpoints from the dashboard. No app required. Authentication is username/password or IP whitelisting, and you get sticky sessions (same address held for a set time) or rotating (new address per request or session). Sticky windows run up to about 30 minutes. Balance validity is 180 days, or unlimited on Enterprise.

Both models share the operational features that decide whether a pool is pleasant or painful to run:

- **Today List** lets you reuse an address you already forwarded within the last 24 hours, free, as long as it's still online. Third-party write-ups put the saving in the region of 20–30% of IP spend, which lines up with how the feature works.
- **Auto Refresh** detects a dead IP and swaps it, with a 60-second replacement window.
- **Auto Rotation** cycles addresses at intervals you set, on ports you choose.
- **Port-level targeting** binds country, state, city and ISP to specific ports, so one account serves several locations at once.
- **Sub-accounts and share codes** for teams and clients, plus API access for automated provisioning.
- **Crypto payments** add a 5% bonus in extra IPs.

The limitations are worth stating too. There's no datacenter, ISP or mobile proxy product — it's a focused residential play, with datacenter listed as coming soon. If you need mobile IPs for high-risk account work, this isn't the shopping list. And if you're running headless, the GB model is the one that fits; the IP model assumes a desktop.

The other thing to know is that pricing changed on 1 June 2026. IP-based and bundle packages went up; GB-based pricing didn't move. If you find an older review quoting $20 for 100 IPs, that's the pre-adjustment figure and no longer current.

## Full plan list and current prices

### Residential by IP (unlimited bandwidth per address)

| Package | Price per IP | Total | Notes |
| --- | --- | --- | --- |
| 100 IPs | $0.24 | $24 | Entry tier, good for testing |
| 500 IPs | $0.144 | $72 |  |
| 1,000 IPs + 500 bonus | $0.084 | $126 | 500 IPs added free |
| 2,500 IPs | $0.084 | $210 |  |
| 5,000 IPs | $0.072 | $360 |  |
| 15,000 IPs | $0.048 | $720 |  |
| 25,000 IPs | $0.035 | $863 |  |
| 50,000 IPs | $0.029 | $1,438 |  |
| 100,000 IPs | $0.023 | $2,300 | Business tier |
| 200,000 IPs | $0.021 | $4,140 | Business tier |
| 500,000 IPs | $0.018 | $8,625 | Business tier |
| Buy |  |  | [ Check current IP package prices](https://bit.ly/9-Proxy) |

### Residential by GB (180-day validity)

| Package | Price per GB | Total | Validity |
| --- | --- | --- | --- |
| 5 GB | $3.00 | $15 | 180 days |
| 50 GB + 5 GB | $2.10 | $105 | 180 days |
| 100 GB | $1.50 | $150 | 180 days |
| 200 GB | $1.00 | $200 | 180 days |
| 1,000 GB | $0.80 | $800 | 180 days |
| 2,000 GB | $0.75 | $1,500 | 180 days |
| Enterprise tiers | from $0.68 | varies | No expiry |
| Buy |  |  | [ Start with a GB package](https://bit.ly/9-Proxy) |

### Bundle packages (IPs + traffic)

| Bundle | Contents | Total |
| --- | --- | --- |
| Starter | 100 IPs + 5 GB | $30 |
| Popular | 1,500 IPs + 50 GB | $180 |
| Pro | 5,000 IPs + 500 GB | $720 |
| Buy |  | [ Compare bundle options](https://bit.ly/9-Proxy) |

## Which one to pick

If you're running a scraper or a monitoring job that makes thousands of requests through the same address and you can't predict monthly data volume, the IP model is the obvious fit. Per-IP billing means the cost of page ten thousand is the same as the cost of page ten. The entry point is $24 for 100 IPs, and the 5,000-IP tier at $360 works out to $0.072 per address.

If your requests each pull tiny amounts of data and you need to rotate constantly — SERP checks, ad verification, geo-sampling, API polling — the GB model wins. $15 for 5 GB gets you unlimited rotating endpoints with city and ISP targeting, which no per-IP plan can match for that spend.

Bundles exist for people running both at once. The Starter bundle at $30 gives you 100 addresses plus 5 GB, which is a reasonable way to test both models in one purchase instead of guessing. Worth noting the 180-day window on the GB portion makes bundles workable for project-based usage, rather than forcing you to burn traffic inside a month.

One practical warning: don't buy 50,000 IPs on your first order because the per-unit price is lower. Unused IPs don't expire in this model, so the money isn't lost — but you're tying up capital in an inventory you may not need for six months. Buy 500, measure your success rate on your actual targets, then scale. That's not caution for its own sake; the per-unit saving between 500 and 50,000 IPs is real, but only if the IPs get used.

## Common questions

**Do I need IPv4 if my target supports IPv6?**
No. If the target serves AAAA records and your tooling handles IPv6, an IPv6 plan does the same job for less. You need IPv4 when a target, a tool or an account history requires it.

**Is an IPv4 proxy the same as a VPN?**
No. A proxy routes specific applications or protocols and generally doesn't encrypt your traffic. A VPN tunnels and encrypts everything.

**How long does a residential IPv4 address last?**
On per-IP plans, a few hours to about 24 hours — that's what a real residential connection looks like. On per-GB plans there's no fixed lifetime; you choose sticky sessions or rotation.

**Which is cheaper, per IP or per GB?**
It depends entirely on your traffic pattern. High request volume with heavy data per request favours per-IP. Frequent rotation with light requests favours per-GB. Calculating both against your last month of usage takes ten minutes and usually saves more than any coupon.

**Is there a way to test it first?**
9Proxy offers a limited trial for new users, subject to availability, and the $24 / $15 entry tiers are small enough to serve as a paid test.

<blockquote>
Buy on workload, not on the headline rate. A cheap per-IP plan that can't hold a session, or a per-GB plan you burn through in a week, both cost more than the plan you'd have picked after ten minutes of arithmetic.
</blockquote>

[👉 Check the current 9Proxy plans and trial availability](https://bit.ly/9-Proxy)
