# Linode vs DigitalOcean vs Vultr: which is cheapest, which handles databases best, and which should you pick?

Vultr is the one to pick when your decision is driven by data-center location, bare metal, or the lowest entry price. DigitalOcean wins if you would rather not run a server at all and want App Platform, managed databases, and object storage behind one dashboard. Linode is the pick when your workload is I/O-bound or you want a support line you can actually call.

The rest of this comparison covers what the same money buys at 1, 2, 4 and 8 GB, measured latency from US East to five regions, and the two things most likely to change your bill: the 30-day clock on Vultr's $300 credit and the difference between stopping an instance and destroying it.

> **Quick picks**
>
> - **Smallest useful production box:** Vultr Cloud Compute, 1 vCPU / 1 GB / 25 GB SSD / 1 TB transfer, **$5.00/month** ($0.007/hour). Enough for a staging environment or a low-traffic site, not enough for a production database.
> - **Least ops work:** DigitalOcean, because App Platform and managed databases are the most complete of the three.
> - **Database and disk-heavy workloads:** Linode, which leads on random read IOPS in the benchmarks below.
>
> 👉 [Check Vultr's current plan list and the $300 new-account credit](https://bit.ly/VuLtr)

## Vultr's plans and what each tier is actually for

Vultr's catalog is wider than the three names people usually compare. The plans below are the ones that line up with what DigitalOcean and Linode sell at similar prices, verified against Vultr's pricing and plan data as of October 2026.

| Plan | vCPU / RAM | Price / month | Best for | Order |
| --- | --- | --- | --- | --- |
| Cloud Compute (vc2-1c-1gb) | 1 / 1 GB | $5.00 | Staging, small sites, a single small service | [Start the 1 GB plan](https://bit.ly/VuLtr) |
| Cloud Compute Regular 2 GB | 1 / 2 GB | $10.00 | A small production app with light traffic | [Start the 2 GB Regular plan](https://bit.ly/VuLtr) |
| High Performance 2 GB | 1 / 2 GB | $12.00 | Same RAM on newer CPUs and NVMe | [Start High Performance 2 GB](https://bit.ly/VuLtr) |
| High Frequency 2 GB | 1 / 2 GB | $12.00 | Latency-sensitive web servers and APIs | [Start High Frequency 2 GB](https://bit.ly/VuLtr) |
| High Performance 4 GB | 2 / 4 GB | $24.00 | App plus database on one instance | [Start High Performance 4 GB](https://bit.ly/VuLtr) |
| Optimized Cloud Compute (General Purpose) | 1 / 4 GB / 30 GB NVMe | $30.00 | Steady CPU for APIs and small clusters | [Start Optimized Cloud Compute](https://bit.ly/VuLtr) |
| Cloud Compute Regular 8 GB | 4 / 8 GB | $40.00 | Build servers and multi-service hosts | [Start the 8 GB plan](https://bit.ly/VuLtr) |

Above these sit larger regular instances, memory- and CPU-optimized lines, Bare Metal, and Cloud GPU. Those prices move more often, so check the current figures before you commit.

Two things worth knowing before you pick a row. The $2.50/month entry price quoted in several 2026 reviews is the smallest plan in the catalog, not the smallest plan you would want to run anything on. Vultr's own homepage card lists 1 vCPU / 1 GB / 25 GB SSD / 1 TB at $5.00/month, and that is the realistic floor for a working server. Second, the 1 GB plan is a staging box. Put a database with real traffic on it and you will be back here in a week.

## Price: what the same money buys at each provider

At 2 GB of RAM, Vultr's Regular plan is $10/month and DigitalOcean's Basic Droplet is $12/month. At 4 GB, Vultr's High Performance instance and Linode's Shared 4 GB instance both land at $24/month. An 8 GB / 4-core Vultr Regular instance is $40/month.

That is the whole story at the low end: the three are within a couple of dollars of each other for equivalent RAM, and the gap disappears by 4 GB. You will still find comparison tables showing Vultr at $7 for 2 GB and DigitalOcean at $24 for 4 GB, but those grids mix product lines and some of them predate current pricing. A September 2026 benchmark capture of the 2 GB tier puts Vultr Regular at $10, Vultr High Performance at $12, Vultr High Frequency at $12, DigitalOcean Basic at $12, and Linode's Shared 4 GB at $24. Compare within a product line or the numbers will mislead you.

At 16 GB, one competitor-run comparison puts Vultr at $80/month against DigitalOcean's $96/month. The publisher sells VPS hosting, so treat it as a data point rather than a verdict, but the direction matches the pattern above.

There is one piece of good news here that reviews of budget hosts rarely mention. All three list standard instances at a flat monthly rate with hourly billing behind it, so the "cheap first year, expensive renewal" pattern you see with discount hosting does not apply. Nobody is baiting you with a $3.99 intro price. What actually moves your bill is bandwidth and add-ons.

Bandwidth is where they diverge. Vultr lists 1 TB of transfer on the $5 plan and 3 TB on the 2 vCPU / 4 GB instance. A competitor-run comparison puts Linode's included transfer at 8 TB per month, well above the other two. If you serve a lot of egress, find the overage rate on the plan page before you order, because that number, not the monthly price, is what decides whether you stay.

## The $300 credit: 30 days, a linked card, and no refunds

Vultr runs several signup offers at once. The $300 credit comes through promo code FLY300VULTR, and Vultr's own coupons page lists it next to $200 (FLYTWOHUNDRED), $250 (250VULTRFLY) and a deposit match up to $100 (VULTRMATCH). Every one of them carries the same fine print: new customers only, select products only, no combining with other offers, restrictions apply.

What the banner does not emphasize is the clock. The credit applies to new accounts, requires a linked credit card or PayPal, excludes duplicate accounts, and unused credit expires after 30 days. It is not a refund and it does not convert to cash. Vultr's own documentation states that payments are final and credits are non-refundable.

The second detail is the one that generates support tickets. Cloud Compute bills up to 672 hours a month, and hourly charges begin the moment an instance is deployed, whether it is powered on or off. Stopping a server does not suspend billing. To stop the meter you have to destroy the instance from the account.

So the sensible way to use the credit: deploy exactly what you want to test, watch the credit balance in billing, and destroy every instance before day 30. If your goal is for the 1 GB plan to cost less than $5 a month after the trial, the credit does not change that price at all. It buys you a month of testing, not a discount.

👉 [Open a Vultr account and read the current credit terms before you deploy](https://bit.ly/VuLtr)

## Latency and disk: where the three actually differ

Benchmarks from mid-2026, taken from $12/month instances in US East regions, show the differences are regional and specific rather than a single winner.

Average latency in milliseconds from US East:

| Route | DigitalOcean | Linode | Vultr |
| --- | --- | --- | --- |
| US East → US West | 64 | 62 | 60 |
| US East → London | 76 | 72 | 74 |
| US East → Frankfurt | 88 | 84 | 86 |
| US East → Singapore | 198 | 190 | 184 |
| US East → Tokyo | 162 | 158 | 152 |

Vultr is fastest toward Asia and across the US, Linode is fastest into Europe. The gaps are small in absolute terms, but if your users are in Singapore, 14 ms off every request is the kind of thing that shows up in a checkout funnel.

Disk is a clearer split. On the same test setup, Linode's NVMe instances hit 62,100 random 4K read IOPS against DigitalOcean's 38,200 and Vultr's 48,500. That is roughly 60% more random read throughput than DigitalOcean, and it is the reason Linode keeps coming up in conversations about self-managed Postgres and MySQL.

CPU tells a different story, and it depends entirely on which tier you buy. High Frequency instances beat both competitors on single-core and multi-core Geekbench runs, but those results come from the High Frequency line, not the $5 plan.

Here is the part that comparison articles tend to skip. Independent grading of the cheap tiers is unflattering across the board. Vultr's Regular 2 GB instance grades E for web performance and F for raw CPU, with C for stability and disk and D for network. DigitalOcean's Basic 2 GB grades F, F, E, D and D on the same scale. Vultr's High Frequency 2 GB improves to D for web performance and C for disk and network. Linode's Shared 4 GB earns a C for web performance and the best stability grade of the group at B.

Read that as a warning about extrapolation. A $12/month benchmark tells you nothing about how an 8 GB instance will behave, and none of these three is fast at the entry tier. If you need predictable CPU, you buy a dedicated or optimized plan, not a bigger shared one.

## Data centers: 32 versus 15 versus 16, and why the Linode number is fuzzy

Vultr runs 32+ locations, DigitalOcean runs 15, and Linode's count depends on who is counting. A June 2026 review lists 16; a November 2025 comparison lists 11 core locations plus Akamai's edge network. Both can be right, because Akamai's edge footprint is not the same thing as compute regions you can deploy an instance into.

The practical difference is which cities exist. Vultr has regions in Johannesburg, Mumbai, São Paulo and Tel Aviv, places where neither competitor offers compute. If your users or your compliance requirements point at one of those, the comparison ends there.

Coverage is not just a count, though. Linode's Akamai ownership gives it a CDN and DDoS posture that Vultr and DigitalOcean match through separate products or not at all. If what you need is edge delivery rather than a server in Nairobi, the data-center tally is the wrong metric.

## Managed services and the features that decide it

|  | DigitalOcean | Linode | Vultr |
| --- | --- | --- | --- |
| Managed Kubernetes | One-click, auto-upgrade | Free HA control plane | Basic managed K8s |
| PaaS | App Platform | No | No |
| Managed databases | Postgres, MySQL, Redis | Postgres, MySQL | Postgres, MySQL |
| Object storage | Spaces | Basic | Basic |
| Bare metal | No | No | Yes, instant provisioning |
| GPU instances | No | No | Cloud GPU |

DigitalOcean's App Platform is the real differentiator. If you are deploying a web app and would rather push code than patch a kernel, it removes a category of work the other two do not address at all. Spaces is also the more mature object-storage product, and the tutorial library behind it is the largest of the three by a wide margin.

Linode's strengths are narrower and more technical: dedicated CPU cores, NodeBalancers for load balancing, free Akamai CDN integration, and object storage at $5 per 250 GB. Vultr's are Bare Metal with instant provisioning, Cloud GPU for ML workloads, and the geographic spread above. If you are running blockchain nodes, game servers, or anything that needs a dedicated box in a specific city, those two features matter more than everything else in this table.

## Support and what users actually rate

Aggregated user ratings from spring 2026 put DigitalOcean first on overall satisfaction at 4.3 out of 5, Linode at 4.2, and Vultr at 4.1. Support quality is where the gap widens: 4.2, 4.1 and 3.8 respectively. Willingness to recommend runs 86%, 83% and 79%. These are third-party aggregations with a limited sample, not an industry standard, but the ordering is consistent with the complaints you find in public forums: Vultr's documentation depth and support responsiveness come up as weaknesses more often than its hardware does.

Support channels differ as much as scores. Linode offers phone support in addition to tickets, which is unusual at this price point and matters when something is down at 2 a.m. DigitalOcean runs tickets plus a very large community knowledge base. Vultr runs 24/7 tickets. Reported response times vary by source, so treat any specific hour figure as anecdotal.

One caveat on Linode: a competitor-run blog reports new signups getting flagged by fraud detection even after payment verification, while long-term customers praise reliability and support. That comes from a single vendor citing Trustpilot reviews, so it is a pattern to be aware of, not a rule. If you are opening a Linode account with a card from an unusual country, budget time for verification.

## So which one should you pick?

Run your situation against these:

- **You need a server in a specific city outside the US and Europe, or a bare metal box today.** Vultr.
- **You want managed databases, object storage and a PaaS without hiring for ops.** DigitalOcean.
- **You are running a database that cares about random read IOPS, or you want phone support.** Linode.
- **You are deploying a staging environment or a low-traffic site and want to spend as little as possible.** Vultr's $5 plan, and move up to the $12 High Frequency tier when traffic justifies it.
- **You need predictable CPU for an API with steady load.** Skip all three shared tiers and buy a dedicated or optimized plan, whichever provider you choose.

Three things to confirm on the order page before you pay, whichever provider you land on: the current price and billing period for the exact plan you selected, the bandwidth overage rate, and the terms attached to any signup credit. Those three numbers decide your real monthly cost far more than the headline price does.

👉 [Compare Vultr's live plan pricing and start with the $300 credit](https://bit.ly/VuLtr)
