[Landwatch Scraper](https://apify.com/parseforge/landwatch-scraper?fpr=data)

![ParseForge Banner](https://images.apifyusercontent.com/wTxwbnRh8X878EoDysptDr1AzClsoPHSsuMaYGmWENw/w:1800/cb:1/aHR0cHM6Ly9naXRodWIuY29tL1BhcnNlRm9yZ2UvYXBpZnktYXNzZXRzL2Jsb2IvYWQzNWNjYzEzZGRkMDY4YjlkNmNiYTMzZjMyMzk2MmUzOWFlZDViMi9iYW5uZXIuanBnP3Jhdz10cnVl.webp)

# 🏡 LandWatch Scraper

> 🚀 **Collect rural land and property listings from all 50 US states.** Filter by state, property type, price range, and acreage. Extract prices, acreage, locations, broker info, and descriptions. No coding required.

> 🕒 **Last updated:** 2026-04-16 · **📊 15+ fields** per listing · **🗺️ 50 US states** · **🏡 12 property types** · **💰 Price + acreage filters**

The **LandWatch Scraper** collects property listings with titles, prices, acreage, full location details, broker information, descriptions, and property types. It covers farms, ranches, hunting land, timberland, and more across all 50 US states.

Whether you are a real estate investor tracking rural land prices, a broker building market reports, or a researcher analyzing land trends across the US, this tool delivers structured property data at scale from the leading marketplace for rural real estate.

| 🎯 Target Audience | 💡 Primary Use Cases |
| --- | --- |
| Real estate investors, land brokers, market researchers, developers, farm/ranch buyers, data analysts | Land price tracking, comparable sales analysis, market reports, parcel sourcing, county-level monitoring |

---

## 📋 What the LandWatch Scraper does

- 🏡 **Property listings.** Collect titles, prices, and acreage from thousands of listings across all 50 US states.
- 📍 **Full location data.** Get address, city, state, and county for every listing.
- 💰 **Pricing details.** Extract listing prices for market comparisons and investment analysis.
- 🏠 **Property specs.** Bedroom counts, bathroom counts, and 12 property types.
- 👤 **Broker information.** Broker names and company details for each listing.
- 🔍 **Flexible search.** Filter by state, property type, price range, acreage range, or paste any search URL.

Each record includes a property description and direct link to the original listing.

> 💡 **Why it matters:** tracking rural land prices, comparing properties across counties, and building market reports manually means browsing thousands of listing pages. This Actor exports structured land data ready for analysis.

---

## 🎬 Full Demo

*🚧 Coming soon: a 3-minute walkthrough.*

---

## ⚙️ Input

| Input | Type | Default | Behavior |
| --- | --- | --- | --- |
| `startUrl` | string | `""` | Direct LandWatch search URL (overrides all filters). |
| `maxItems` | integer | `10` | Max listings. Free: 10, Paid: up to 1,000,000. |
| `state` | string | `""` | US state filter (e.g., texas, california). |
| `propertyType` | string | `""` | Farm, ranch, hunting, timber, homesite, etc. |
| `minPrice` | integer | - | Minimum price in USD. |
| `maxPrice` | integer | - | Maximum price in USD. |
| `minAcres` | integer | - | Minimum acreage. |
| `maxAcres` | integer | - | Maximum acreage. |

**Example: Texas ranches between $100K and $5M.**

```
{
    "state": "texas",
    "propertyType": "ranch-land",
    "minPrice": 100000,
    "maxPrice": 5000000,
    "maxItems": 50
}
```

**Example: hunting land in Colorado under 100 acres.**

```
{
    "state": "colorado",
    "propertyType": "hunting-land",
    "maxAcres": 100,
    "maxItems": 25
}
```

> ⚠️ **Good to Know:** Free users are limited to 10 items per run. The Start URL field lets you paste any LandWatch search URL to use all native filters including county-level searches.

---

## 📊 Output

### 🧾 Schema

| Field | Type | Example |
| --- | --- | --- |
| 🆔 `listingId` | string | `"422917076"` |
| 📋 `title` | string | `"Brazos Bluff Ranch"` |
| 🔗 `url` | string | `"https://www.landwatch.com/..."` |
| 💰 `price` | string | `"$10,721,200"` |
| 📐 `acreage` | string | `"428 acres"` |
| 🛏️ `beds` | string | `"1"` |
| 🚿 `baths` | string | `"1"` |
| 📍 `address` | string | `"1950 Consolation Drive"` |
| 🏙️ `city` | string | `"Millsap"` |
| 🗺️ `state` | string | `"TX"` |
| 🏘️ `county` | string | `"Parker County"` |
| 📝 `description` | string | Property description |
| 🏷️ `propertyType` | string | `"Farm"` |
| 👤 `brokerName` | string | `"Mac A. Coalson"` |
| 🏢 `brokerCompany` | string | `"Coalson Real Estate"` |
| 🕒 `scrapedAt` | ISO 8601 | `"2026-04-07T16:40:17.471Z"` |

### 📦 Sample records

 
 
 

---

## ✨ Why choose this Actor

|  | Capability |
| --- | --- |
| 🗺️ | **All 50 states.** Coverage across every US state. |
| 🏡 | **12 property types.** Farms, ranches, hunting, timber, homesites, and more. |
| 💰 | **Price and acreage filters.** Target specific ranges for your search. |
| 👤 | **Broker details.** Name and company for every listing. |
| 📍 | **Full location.** Address, city, state, and county breakdown. |
| 🔗 | **URL input.** Paste any LandWatch search URL for custom filters. |
| ⚡ | **Fast.** Collects 100 listings in seconds. |

> 📊 **15+ fields per listing** with pricing, acreage, location, broker info, and property type.

---

## 📈 How it compares to alternatives

| Approach | Cost | Coverage | Filters | Broker data | Setup |
| --- | --- | --- | --- | --- | --- |
| **⭐ LandWatch Scraper** *(this Actor)* | $5 free credit | All 50 states | State, type, price, acreage | Yes | ⚡ 2 min |
| Manual browsing | Free | One at a time | UI only | Click each listing | 🕒 Hours |
| Generic web scraper | Varies | Requires setup | Custom config | Not extracted | 🕒 30+ min |
| Other property scrapers | Varies | Varies | Limited | Varies | 🕒 Varies |

---

## 🚀 How to use

1. 📝 **Sign up.** [Create a free account with $5 credit](https://console.apify.com/sign-up?fpr=vmoqkp) (takes 2 minutes).
2. 🌐 **Open the Actor.** Go to the LandWatch Scraper page on Apify.
3. 🎯 **Set input.** Pick a state, property type, and price/acreage range.
4. 🚀 **Run it.** Click **Start** and get results in seconds.
5. 📥 **Download.** Grab results in JSON, CSV, or Excel from the **Dataset** tab.

> ⏱️ Total time: **2-3 minutes.** No coding required.

---

## 💼 Business use cases

| ### 💰 Investment & Brokerage     - Track new land listings daily - Identify undervalued properties - Build comparable sales databases - Generate market reports for clients | ### 📊 Research & Development     - Analyze land pricing across regions - Find parcels matching acreage and price criteria - Create weekly market snapshots - Monitor specific counties for new listings |
| --- | --- |

---

---

## 🌟 Beyond business use cases

Data like this powers more than commercial workflows. The same structured records support research, education, civic projects, and personal initiatives.

| ### 🎓 Research and academia     - Empirical datasets for papers, thesis work, and coursework - Longitudinal studies tracking changes across snapshots - Reproducible research with cited, versioned data pulls - Classroom exercises on data analysis and ethical scraping | ### 🎨 Personal and creative     - Side projects, portfolio demos, and indie app launches - Data visualizations, dashboards, and infographics - Content research for bloggers, YouTubers, and podcasters - Hobbyist collections and personal trackers |
| --- | --- |
| ### 🤝 Non-profit and civic     - Transparency reporting and accountability projects - Advocacy campaigns backed by public-interest data - Community-run databases for local issues - Investigative journalism on public records | ### 🧪 Experimentation     - Prototype AI and machine-learning pipelines with real data - Validate product-market hypotheses before engineering spend - Train small domain-specific models on niche corpora - Test dashboard concepts with live input |

## 🤖 Ask an AI assistant about this scraper

Open a ready-to-send prompt about this ParseForge actor in the AI of your choice:

- 💬 [**ChatGPT**](https://chat.openai.com/?q=How%20do%20I%20use%20the%20LandWatch%20Scraper%20by%20ParseForge%20on%20Apify%3F%20Show%20me%20input%20examples%2C%20output%20fields%2C%20common%20use%20cases%2C%20and%20how%20to%20integrate%20it%20into%20a%20workflow.)
- 🧠 [**Claude**](https://claude.ai/new?q=How%20do%20I%20use%20the%20LandWatch%20Scraper%20by%20ParseForge%20on%20Apify%3F%20Show%20me%20input%20examples%2C%20output%20fields%2C%20common%20use%20cases%2C%20and%20how%20to%20integrate%20it%20into%20a%20workflow.)
- 🔍 [**Perplexity**](https://perplexity.ai/search?q=How%20do%20I%20use%20the%20LandWatch%20Scraper%20by%20ParseForge%20on%20Apify%3F%20Show%20me%20input%20examples%2C%20output%20fields%2C%20common%20use%20cases%2C%20and%20how%20to%20integrate%20it%20into%20a%20workflow.)
- 🅒 [**Copilot**](https://copilot.microsoft.com/?q=How%20do%20I%20use%20the%20LandWatch%20Scraper%20by%20ParseForge%20on%20Apify%3F%20Show%20me%20input%20examples%2C%20output%20fields%2C%20common%20use%20cases%2C%20and%20how%20to%20integrate%20it%20into%20a%20workflow.)

## ❓ Frequently Asked Questions

### 💳 Do I need a paid Apify plan to run this actor?

No. You can start right now on the free Apify plan, which includes **$5 in free monthly credit**. That is enough to run this actor several times and explore the output before committing to anything. Paid plans unlock higher limits, more concurrent runs, and larger datasets. [Create a free Apify account here](https://console.apify.com/sign-up?fpr=vmoqkp) to get started.

### 🚨 What happens if my run fails or returns no results?

Failed runs are not charged. If the source site changes, proxies get rate-limited, or a specific input matches nothing, re-run the actor or open our [contact form](https://tally.so/r/BzdKgA) and we will investigate. You can also check the run log in the Apify console to see why the run stopped.

### 📏 How many items can I scrape per run?

Free users are limited to **10 items per run** so you can preview the output and confirm the actor works for your use case. Paid users can raise `maxItems` up to **1,000,000** per run. [Upgrade here](https://console.apify.com/sign-up?fpr=vmoqkp) if you need full scale.

### 🕒 How fresh is the data?

Every run fetches live data at the moment of execution. There is no cache or delay: the records you get reflect what the source returned at that moment. Schedule the actor to maintain a rolling snapshot of the data you need.

### 🧑‍💻 Can I call this actor from my own code?

Yes. Apify exposes every actor as a REST endpoint and ships first-class SDKs for [Node.js](https://docs.apify.com/sdk/js) and [Python](https://docs.apify.com/sdk/python). You can start a run, read the dataset, and handle webhooks from your own app in a few lines. All you need is your Apify API token.

### 📤 How do I export the data?

Every Apify dataset can be downloaded in one click from the console as CSV, JSON, JSONL, Excel, HTML, XML, or RSS. You can also pull results programmatically via the [Apify API](https://docs.apify.com/api/v2) or stream them into BigQuery, S3, and other destinations through built-in integrations.

### 📅 Can I schedule the actor to run automatically?

Yes. Use the Apify scheduler to run the actor on any cadence, from hourly to monthly. Results are saved to your dataset and can be delivered to webhooks, email, Slack, cloud storage, or automation tools such as Zapier and Make.

---

## 🔌 Automating LandWatch Scraper

- 🟢 **Node.js.** Install the `apify-client` NPM package.
- 🐍 **Python.** Use the `apify-client` PyPI package.
- 📚 See the [Apify API documentation](https://docs.apify.com/api/v2) for full details.

## 🔌 Integrate with any app

- [**Make**](https://docs.apify.com/platform/integrations/make) - Automate land monitoring workflows
- [**Zapier**](https://docs.apify.com/platform/integrations/zapier) - Connect 5,000+ apps
- [**Slack**](https://docs.apify.com/platform/integrations/slack) - Get notifications for new listings
- [**Airbyte**](https://docs.apify.com/platform/integrations/airbyte) - Data pipelines
- [**GitHub**](https://docs.apify.com/platform/integrations/github) - Trigger from commits
- [**Google Drive**](https://docs.apify.com/platform/integrations/drive) - Export to Sheets

---

## 🔗 Recommended Actors

- [**🏠 Auction.com Scraper**](https://apify.com/parseforge/auction-com-property-scraper) - Property auctions
- [**🏘️ REMAX Scraper**](https://apify.com/parseforge/remax-scraper) - Real estate listings
- [**🏢 LoopNet Scraper**](https://apify.com/parseforge/loopnet-scraper) - Commercial real estate
- [**🏡 James Edition Scraper**](https://apify.com/parseforge/james-edition-real-estate-scraper) - Luxury real estate
- [**🚗 duPont Registry Scraper**](https://apify.com/parseforge/dupont-registry-scraper) - Luxury property and vehicles

> 💡 Browse the complete [ParseForge collection](https://apify.com/parseforge).

---

**🆘 Need Help?** [**Open our contact form**](https://tally.so/r/BzdKgA) to request a new scraper or report an issue.

---

> **⚠️ Disclaimer:** Independent tool, not affiliated with LandWatch.com or any of its subsidiaries. Only publicly available data is collected.