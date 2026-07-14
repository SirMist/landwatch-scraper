[Landwatch Scraper](https://apify.com/memo23/landwatch-scraper?fpr=data)

# LandWatch Property and Agent Scraper

**Unlock the Full Power of LandWatch Property and Agent Data** - The only scraper you need to track, analyze, and understand real estate listings and agent information on LandWatch with enterprise-grade reliability and precision. Whether you're monitoring property markets, tracking price trends, or conducting real estate research, our scraper delivers comprehensive, real-time insights while saving you time and resources.

*"From real-time property monitoring to deep market analysis, we turn LandWatch's property and agent data into your competitive advantage."*

## What You Can Scrape

This scraper supports two main types of scraping:

1. **Agent Lists**

- Scrape lists of agents from URLs like: `https://www.landwatch.com/find-agent/austin-county-tx`
- Extracts basic information about multiple agents in a region
- Useful for market research and finding specific agents
2. **Agent Details**

- Scrape detailed information about individual agents from URLs like: `https://www.landwatch.com/profile/homeland-properties/174024`
- Extracts comprehensive information including:

- Broker details
- Property listings
- Historical sales data
- Contact information
- Social media links
- And much more

## Supported URLs

All URLs must be on `landwatch.com`. The scraper auto-detects the URL type and applies the right handler.

**Land listings** (search results — pages produce many listing rows):

- State / county listings, with optional category and price filters

- `https://www.landwatch.com/texas-land-for-sale/price-under-6000`
- `https://www.landwatch.com/nebraska-land-for-sale/farms-ranches/price-250000-499999`
- `https://www.landwatch.com/south-carolina-land-for-sale/gray-court`
- Individual property pages

- `https://www.landwatch.com/laurens-county-south-carolina-undeveloped-land-for-sale/pid/422387154`

**Find an Agent** (broker/agent directory):

- By location: `https://www.landwatch.com/find-agent/austin-county-t/`
- By name: `https://www.landwatch.com/find-agent/name/john/`
- Individual agent profile: `https://www.landwatch.com/profile/homeland-properties/174024`

Page numbers in the URL don't matter — the scraper paginates automatically until it hits `maxItems` or the end of results.

## Overview

The LandWatch Scraper is your go-to tool for extracting property data from LandWatch.com. Ideal for real estate investors, market analysts, and property researchers, it tracks property details, pricing, and listing information. With easy setup and multiple export formats (JSON, CSV), it's perfect for anyone looking to gather comprehensive property data from LandWatch.

## What does LandWatch Scraper do?

The LandWatch Scraper is a powerful tool that enables you to:

### Comprehensive Property Data Collection

- Extract complete property details and specifications
- Scrape historical listing data and price changes
- Gather comprehensive property features and amenities
- Analyze property locations and surrounding areas
- Download property images and media

### Advanced Scraping Capabilities

- **Pagination Handling**: Automatically navigates through multiple pages of search results
- **Efficient Processing**: Processes only new or updated listings in subsequent runs
- **Change Detection**: Identifies price changes, status updates, and new listings
- **Scheduled Monitoring**: Set up automated runs to keep your property data current
- **Incremental Data Collection**: Build comprehensive property datasets over time

### Flexible Scraping Options

- **Search Results**: Extract all properties matching specific search criteria
- **Targeted Scraping**: Focus on individual property listings using direct URLs
- **Location-Based Scraping**: Target specific areas, cities, or regions
- **Custom Filters**: Apply various filters like price range, property type, and more

This tool is ideal for:

- Real estate market research and analysis
- Property investment analysis and due diligence
- Competitive market analysis
- Building property databases for investment decisions
- Tracking price trends and market movements

## Features

- **Comprehensive Data Extraction**: Detailed property information, pricing, and specifications
- **Dual Scraping Modes**:

- **Search Results**: Scrape all properties from search results (e.g., `https://www.landwatch.com/south-carolina-land-for-sale/gray-court`)
- **Individual Listings**: Target specific properties using direct URLs (e.g., `https://www.landwatch.com/laurens-county-south-carolina-undeveloped-land-for-sale/pid/422387154`)
- **Flexible Input**: Supports multiple input formats:

- Search result URLs (e.g., `https://www.landwatch.com/south-carolina-land-for-sale/gray-court`)
- Direct property URLs (e.g., `https://www.landwatch.com/laurens-county-south-carolina-undeveloped-land-for-sale/pid/422387154`)
- Custom search criteria
- **Automatic Pagination**: Handles multi-page results automatically
- **Efficient Processing**: Concurrent scraping with configurable concurrency settings
- **Reliable Performance**: Built-in retry mechanisms and proxy support
- **Structured Data Export**: Download property data in JSON or CSV format for analysis

## How to Use

### Scraping land listings

1. **Set Up**: Ensure you have an Apify account and access to the Apify platform.
2. **Configure Input**: Paste a search URL from your browser (state, county, filters, all welcome), e.g. `https://www.landwatch.com/texas-land-for-sale/price-under-6000`. You can also paste an individual `/pid/...` URL to scrape a single property.
3. **Adjust Settings**: Configure `maxItems`, `flattenOutput`, `fetchSellerAgentDetails`, and proxy as needed.
4. **Run the Scraper**: Execute the scraper on the Apify platform.
5. **Data Collection**: The scraper paginates automatically and outputs one row per property.

### Scraping agents (Find an Agent)

1. **Set Up**: Ensure you have an Apify account and access to the Apify platform.
2. **Configure Input**: Paste a Find an Agent URL — by location (`https://www.landwatch.com/find-agent/austin-county-t/`) or by name (`https://www.landwatch.com/find-agent/name/john/`). You can also paste an individual `/profile/...` URL to scrape a single agent.
3. **Run the Scraper**: Execute the scraper on the Apify platform.
4. **Data Collection**: The scraper paginates automatically and outputs one row per agent / broker.

## Input Configuration

Example input:

```
{
    "startUrls": [
        "https://www.landwatch.com/texas-land-for-sale/price-under-6000",
        "https://www.landwatch.com/find-agent/austin-county-t/",
        "https://www.landwatch.com/laurens-county-south-carolina-undeveloped-land-for-sale/pid/422387154",
        "https://www.landwatch.com/profile/homeland-properties/174024"
    ],
    "maxItems": 1000,
    "flattenOutput": false,
    "fetchSellerAgentDetails": false,
    "monitoringMode": false,
    "maxConcurrency": 10,
    "minConcurrency": 1,
    "maxRequestRetries": 100,
    "proxy": {
        "useApifyProxy": true,
        "apifyProxyGroups": ["RESIDENTIAL"]
    }
}
```

### Input Fields Explanation

- `startUrls`: Array of LandWatch URLs. Mix any of the supported types — land listings, find-agent, individual `/pid/...`, individual `/profile/...`. See Supported URLs.
- `maxItems`: Maximum number of items to scrape (default: 1000).
- `flattenOutput`: When `true`, dataset records are flattened — listing-card fields (`price`, `address`, `brokerName`, etc.) and convenience fields (`url`, `description`, `imageUrls`, `logoUrl`, `portraitUrl`) are lifted to the top level. When `false` (default), records keep the original nested API shape (`basicInfo`, `propertyData`, `brokerDetails`, etc.).
- `fetchSellerAgentDetails`: Off by default (fastest runs). When `true`, every land listing is enriched with the full seller / agent profile (`otherListings`, `soldListings`, `sellerCarouselListings`, `sellerMedia` socials, `landStarAwards`) attached as `agentProfile`. Adds one extra request per listing — roughly doubles run time and cost.
- `monitoringMode`: When `true`, only scrapes listings/agents not seen in previous runs (default: false).
- `maxConcurrency`: Maximum number of pages processed simultaneously (default: 10).
- `minConcurrency`: Minimum number of pages processed simultaneously (default: 1).
- `maxRequestRetries`: Number of retries for failed requests (default: 100).
- `proxy`: Proxy settings. Defaults to Apify Residential proxy.

## Monitoring Mode

When `monitoringMode` is enabled, the scraper only collects listings or agents that weren't seen in previous runs. This is useful for:

- Tracking new listings on a state / county search over time
- Building a historical archive of properties or agents
- Watching a market for new inventory without duplicating data

### How Monitoring Mode Works

1. The scraper maintains a record of previously scraped listing / agent IDs (in an Apify key-value store).
2. On subsequent runs with `monitoringMode: true`, each item is checked against this record.
3. Only new items (not in the record) are processed and added to the output.
4. The record is updated with any new IDs found.

## Output Listing(s) Structure

The scraper provides comprehensive information about LandWatch property listings. The output includes detailed property information, broker details, and location data. Here's a breakdown of the main components:

```
{
  "listingId": 422929612,
  "h1": "Land for sale in Marion County, Illinois",
  "basicInfo": {
    "id": 26612457,
    "siteListingId": 426016952,
    "price": 12000, "priceDisplay": "$12,000", "pricePerAcre": 36363.64,
    "address": "Lot 14 Putter Drive",
    "city": "Athens", "county": "Menard County",
    "state": "Illinois", "stateAbbreviation": "IL", "zip": "62613",
    "acres": 0.33, "acresDisplay": "0.33 acres",
    "latitude": 39.99, "longitude": -89.66,
    "brokerName": "Jessica Plummer",
    "brokerCompany": "Carolina Land Company, LLC",
    "brokerPhone": "(217) 555-0123",
    "imageIds": [5836253734, 5836253735, "..."],
    "canonicalUrl": "/menard-county-illinois-undeveloped-land-for-sale/pid/426016952",
    "...": "(many more search-card fields — see full sample below)"
  },
  "propertyData": {
    "description": ["Build your dream home in Country Lake Estates..."],
    "directions": "From I-72 take exit 88...",
    "mlsId": "11999210", "parcelId": "12-34-567-890",
    "imageDocumentIds": [5836253734, "..."],
    "...": "(detailed property fields)"
  },
  "brokerDetails": {
    "accountId": 174024, "companyName": "Carolina Land Company, LLC",
    "phoneNumbers": { "officePhone": "(217) 555-0123", "...": "..." },
    "...": "(broker card)"
  },
  "propertyAmenities": ["..."],
  "propertyMediaData": { "...": "..." },
  "listingEvents": [{ "eventDate": "2024-08-13", "newPrice": 12000 }],
  "otherListings": ["..."],
  "soldListings": ["..."],
  "citiesInCounties": ["..."],
  "contiguousCounties": ["..."],
  "paginationData": { "pageIndex": 0, "totalCount": 248 }
}
```

> **Full unabridged sample** (real captured record, every field present): readme-stuff/sample-listing.json.
> When `flattenOutput=true`, `basicInfo` keys are lifted to the top level and `url` / `description` / `imageUrls` are added with full LandWatch URLs.

## Output Fields Explanation

### Basic Property Information

- `basicInfo`: (Object) Core property listing information

- `accountId`: (Number) Broker's account ID (matches brokerDetails.accountId)
- `acres`: (Number) Total acreage of the property (e.g., 12.9)
- `acresDisplay`: (String) Formatted display of acreage (e.g., "12.9 acres")
- `adTargetingCountyId`: (Number) County ID used for ad targeting (e.g., 5592)
- `address`: (String) Street address (may be partial for privacy, e.g., "Knight Road")
- `auctionDate`: (String) Scheduled auction date ("0001-01-01T00:00:00" if not applicable)
- `baths`/`beds`: (Number) Number of bathrooms and bedrooms (0 for land)
- `bathsDisplay`/`bedsDisplay`: (String) Formatted display of room counts (empty for land)
- `brokerCanonicalUrl`: (String) URL path to broker's profile (e.g., "/profile/scott-cornelson/725569")
- `brokerCompany`: (String) Name of the brokerage firm (e.g., "Carolina Land Company, LLC")
- `brokerName`: (String) Name of the listing agent (e.g., "Scott Cornelson")
- `brokerPhone`: (String|null) Contact number for the broker (null if not provided)
- `canonicalUrl`: (String) URL path to this listing (e.g., "/laurens-county-south-carolina-undeveloped-land-for-sale/pid/422387154")
- `city`: (String) City where the property is located (e.g., "Gray Court")
- `cityID`: (Number) Internal ID for the city (e.g., 10729)
- `companyLogoDocumentId`: (Number) ID of the company logo image (0 if none)
- `county`: (String) Full county name (e.g., "Laurens County")
- `countyId`: (Number) Internal ID for the county (e.g., 5592)
- `countyLabel`: (String) Type of county designation (e.g., "County")
- `description`: (String) Truncated property description (full description in propertyData)
- `encodedBoundaryPoints`: (String) Encoded polygon data for property boundaries (empty if not available)
- `executiveSummary`: (String|null) Brief summary of the listing (null if not provided)
- `externalSourceId`: (String|null) ID from external MLS (null if not applicable)
- `halfBaths`: (Number) Number of half bathrooms (0 for land)
- `halfBathsDisplay`: (String|null) Formatted display of half baths (null for land)
- `hasCustomMap`: (Boolean) If the listing includes a custom map
- `hasHouse`: (Boolean) If the property includes a house/structure (false for land)
- `hasVideo`: (Boolean) If the listing includes video content
- `hasVirtualTour`: (Boolean) If a virtual tour is available
- `homesqft`: (Number) Size of any structures in square feet (0 for land)
- `homesqftDisplay`: (String) Formatted display of home square footage (empty for land)
- `imageAltTextDisplay`: (String) Alt text for the listing's main image
- `imageCount`: (Number) Total number of images available (e.g., 18)
- `imageIds`: (Array[Number]|null) List of image IDs (null if not loaded)
- `insertDate`: (ISO Date) When the listing was created (e.g., "2025-03-24T07:44:12.263")
- `id`: (Number) Internal listing ID (e.g., 22982658)
- `isALC`: (Boolean) If the listing is from an Accredited Land Consultant
- `isCourtesy`: (Boolean) If this is a courtesy listing
- `isDiamond`/`isGold`/`isPlatinum`: (Boolean) Premium listing status indicators
- `isFirstFreeListing`: (Boolean) If this is the broker's first free listing
- `isLiked`: (Boolean) If the current user has liked/saved this listing
- `isShowcase`: (Boolean) If this is a featured/spotlight listing
- `lafPropertyId`: (Number) Internal property ID in LAF system (e.g., 37017035)
- `lake`: (String|null) Name of nearby lake (null if not applicable)
- `lastUpdated`: (ISO Date) When the listing was last modified (e.g., "2025-06-03T05:51:51.807")
- `latitude`/`longitude`: (Number) Geographic coordinates of the property
- `listHubListingKey`: (String|null) ID for ListHub integration (null if not applicable)
- `listingLevel`: (Number) Tier/level of the listing (e.g., 30)
- `listingLevelTitle`: (String) Name of the listing level (e.g., "Signature Partner")
- `lwPropertyId`: (Number) LandWatch property ID (e.g., 422387154)
- `onMarketDate`: (ISO Date) When the property was listed ("0001-01-01T00:00:00" if not available)
- `parentAccountId`: (Number) ID of parent account (0 if none)
- `partnerId`: (Number) ID of partner organization (0 if none)
- `portraitDocumentId`: (Number) ID of the broker's profile image
- `price`: (Number) Current listing price in USD (e.g., 253485)
- `priceChangeAmount`: (Number) Absolute amount of last price change (negative for decrease, e.g., -15515)
- `priceChangeDate`: (ISO Date) When the price was last changed (e.g., "2025-06-03T05:51:51.64")
- `priceChangePercentage`: (Number) Percentage of last price change (negative for decrease, e.g., -0.0577 for -5.77%)
- `priceDisplay`: (String) Formatted price with currency symbol (e.g., "$253,485")
- `pricePerAcre`: (Number) Calculated price per acre (e.g., 19650)
- `propertyTypes`: (Number) Bitmask of property type flags (e.g., 32)
- `propertyTypesLabel`: (String) Human-readable list of property types (e.g., "Undeveloped Land")
- `regionId`: (Number) Internal ID for the region (e.g., 197)
- `salesDate`: (ISO Date) When the property sold ("0001-01-01T00:00:00" if not sold)
- `salesPrice`: (Number) Final sale price (0 if not sold)
- `schemaData`: (String) JSON-LD structured data for search engines
- `shortPrice`: (String) Abbreviated price (e.g., "$253K")
- `shortPriceChangeAmount`: (String) Formatted price change amount (e.g., "-$15.5K")
- `siteListingId`: (Number) Listing ID on the main site (matches lwPropertyId)
- `state`: (String) Full state name (e.g., "South Carolina")
- `stateAbbreviation`: (String) Two-letter state code (e.g., "SC")
- `stateCode`: (String) State code (usually same as abbreviation)
- `stateId`: (Number) Internal ID for the state (e.g., 45)
- `status`: (Number) Listing status code (1 = Active)
- `thumbnailDocumentId`: (Number) ID of the thumbnail image (e.g., 5456623288)
- `title`: (String) Listing title/headline (e.g., "12.90 +/- single family home site with acreage in Gray Court")
- `types`: (Array[String]) Property type categories (e.g., ["Undeveloped Land"])
- `upgradeLevelId`: (Number) ID of any upgrade package (0 if none)
- `zip`: (String) ZIP/postal code (e.g., "29645")

### Broker Information

- `brokerDetails`: Comprehensive information about the listing agent or brokerage

- `accountId`: (Number) Unique numeric identifier for the broker's LandWatch account (e.g., 725569)
- `accountSubTypeId`: (Number) Subclassification of the broker account type (e.g., 5)
- `accountType`: (Number) Main classification code for the broker account (e.g., 40 for standard broker)
- `active`: (Boolean) Indicates if the broker's account is currently active
- `adDesc`: (String) Advertisement description (often empty string)
- `address1`/`address2`: (String) Broker's personal address components (often empty for privacy)
- `alcCertified`: (Boolean) Indicates if broker is ALC (Accredited Land Consultant) certified
- `alcAdvancedCertified`: (Boolean) Indicates if broker holds advanced ALC certification
- `badgeId`: (Number|null) Identifier for any special achievement badges (null if none)
- `canonicalUrl`: (String) Relative URL path to the broker's profile page (e.g., "/profile/scott-cornelson/725569")
- `city`: (String) Broker's city of residence (e.g., "Greenville")
- `companyAddress1`/`companyAddress2`: (String) Business address components (e.g., "PO Box 787")
- `companyName`: (String) Legal business name (e.g., "Carolina Land Company, LLC")
- `companyCity`/`companyState`/`companyZip`: (String) Business location details (e.g., "Greenville", "SC", "29602")
- `contactName`: (String) Full name of the primary contact (e.g., "Scott Cornelson")
- `description`: (Array[String]) Professional biography and credentials (e.g., ["Land Broker with over 25 years of experience..."])
- `email`: (String|null) Contact email address (often null for privacy reasons)
- `expirationDate`: (ISO Date) When the broker's listing subscription expires (e.g., "2025-07-05T00:00:00")
- `homesContactId`: (String) Internal identifier for Homes.com integration (e.g., "0")
- `homesUserId`: (String|null) User ID for Homes.com (null if not linked)
- `insertDate`: (ISO Date) When the broker's account was created (e.g., "2014-08-26T06:56:10.543")
- `isFree`: (Boolean) Indicates if the account is a free/basic account
- `isSeller`: (Boolean) Indicates if the account can list properties for sale
- `landStarWinCount`: (Number) Number of LandStar awards received (e.g., 0)
- `leadRoutingEmail`: (String|null) Email for lead routing (null if not set)
- `licenseNumber`: (String) Real estate license number (empty string if not provided)
- `listingCount`: (Number) Number of active listings (may be 0 if not tracked here)
- `logoId`: (Number|null) Internal ID for company logo image (null if none)
- `optInLeadTargeting`: (Boolean) If broker has opted into lead targeting
- `parentAccountId`: (Number) ID of parent/umbrella account (0 if none)
- `parentAccountType`: (Number) Type of parent account (0 if none)
- `phoneCell`/`phoneOffice`/`phoneFax`/`phoneTollFree`: (String|null) Contact numbers
- `portraitId`: (Number) Internal ID for broker's profile picture (e.g., 3994781037)
- `portraitImageUpdateDate`: (ISO Date|null) When the profile picture was last updated
- `sellerListingStats`: (Object|null) Statistics about seller's listings (null if not available)
- `smsNotifications`: (Boolean) If SMS notifications are enabled
- `stateAbbreviation`: (String) Two-letter state code (e.g., "SC")
- `stripeCustomerId`: (String|null) Stripe payment processor customer ID (null if not using Stripe)
- `totalRows`: (Number) Total count of matching records (often 0 in this context)
- `trackingPhoneNumber`: (String) Call tracking number for lead attribution (e.g., "(864) 635-4557")
- `url`: (String) Company website URL (e.g., "[www.carolinalandcompany.com](http://www.carolinalandcompany.com)")
- `zip`: (String) Broker's zip code (e.g., "29602")

### Property Listing Metadata

- `h1`: (String) Primary headline/title of the listing (e.g., "12.90 +/- single family home site with acreage in Gray Court")
- `listingId`: (Number) Unique identifier for this specific property listing (e.g., 22982658)
- `lwPropertyId`: (Number) LandWatch's internal property identifier
- `canonicalUrl`: (String) Permanent URL path to this listing on LandWatch
- `status`: (Number) Current status code (1 = Active, others may indicate pending/sold)
- `insertDate`: (ISO Date) When the listing was first created
- `lastUpdated`: (ISO Date) When the listing was last modified
- `onMarketDate`: (ISO Date) When the property was listed for sale
- `salesDate`: (ISO Date|null) When the property went under contract/sold

### Listing Events & Price History

- `listingEvents`: (Array[Object]) Chronological history of all listing events including price changes

- `date`: (ISO Date) When the event occurred (e.g., "2025-06-03T00:00:00")
- `price`: (Number) Listing price in USD at that time (e.g., 253485)
- `priceDelta`: (Number|null) Percentage change from previous price (e.g., -5.77 for 5.77% decrease)
- `acres`: (Number) Property size in acres at the time of the event (e.g., 12.9)
- `acresDelta`: (Number|null) Change in acreage from previous listing (null for initial listing)
- `eventTitle`: (String) Type of event (e.g., "Price", "Listed for Sale")

### Facebook Tracking Data

- `facebookDareJavascript`: (String) JSON string containing Facebook tracking data for the listing

- `content_type`: (String) Type of content (e.g., "home_listing")
- `content_ids`: (Array[Number]) Array containing the listing ID (e.g., [422387154])
- `city`: (String) Property city (e.g., "Gray Court")
- `region`: (String) State or region (e.g., "South Carolina")
- `country`: (String) Country name (e.g., "United States")
- `currency`: (String) Currency code (e.g., "USD")
- `preferred_price_range`: (Number) Listing price in base currency (e.g., 253485)
- `property_type`: (String) Type of property (e.g., "land")
- `preferred_beds_range`: (Number) Number of bedrooms (0 for land)
- `preferred_bath_range`: (Number) Number of bathrooms (0 for land)
- `listing_type`: (String) Additional listing type information (empty if not specified)
- `availability`: (String) Current listing status (e.g., "for_sale")

### Price & Financial Information

- `priceDisplay`: (String) Formatted price string with currency symbol (e.g., "$253,485")
- `shortPrice`: (String) Abbreviated price (e.g., "$253.5K")
- `pricePerAcre`: (Number) Calculated as total price divided by acreage
- `salesPrice`: (Number) Final sale price if property has sold (0 if active)

### Broker Media Data

- `brokerMediaData`: (Object|null) Contains media assets related to the broker

- Typically `null` unless the broker has uploaded additional media beyond the standard profile picture
- When present, may include links to videos, virtual tours, or additional images

### Location & Geography

- `citiesInCounties`: (Array[Object]) Comprehensive list of cities within the property's county

- `id`: (Number) Unique numeric identifier for the city (e.g., 5253)
- `countyId`: (Number) Reference ID to the containing county (e.g., 5592)
- `countyLabelPlural`: (String|null) Plural form of the county name (null if not specified)
- `countyName`: (String|null) Name of the county (null if not specified)
- `latitude`/`longitude`: (Number) Precise geographic coordinates (WGS84)

- Example: 34.47804, -81.86399
- `name`: (String) Official city name (e.g., "Clinton", "Cross Hill")
- `regionId`: (Number) Regional identifier (0 if not specified)
- `regionName`: (String|null) Name of the region (null if not specified)
- `stateId`: (Number) Numeric identifier for the state (e.g., 45 for South Carolina)
- `stateAbbreviation`: (String) Two-letter state code (e.g., "SC")
- `stateName`: (String) Full state name (e.g., "South Carolina")
- `contiguousCounties`: (Array[Object]) List of counties that share a boundary with the property's county

- `name`: (String) Full county name (e.g., "Abbeville County")
- `stateAbbreviation`: (String) Two-letter state code (e.g., "SC")
- `stateId`: (Number) Numeric identifier for the state (e.g., 45)
- `facebookDareJavascript`: (String) JSON string containing Facebook tracking data for the listing

- Contains structured data about the property including:

- `content_type`: Type of content (e.g., "home_listing")
- `content_ids`: Array of listing IDs
- Location details (city, region, country)
- Price and property information
- Example: `{"content_type":"home_listing","content_ids":[422387154],...}`

### Physical Property Details

- `propertyData`:

- `acres`: (Number) Total land area in acres (e.g., 12.9)
- `beds`/`baths`: (Number) Number of bedrooms and bathrooms (0 for land)
- `homesqft`: (Number) Size of any structures in square feet
- `description`: (Array[String]) Detailed narrative description
- `directions`: (Array[String]) Written directions to the property
- `propertyTypes`: (Number) Bitmask of property types
- `propertyTypesLabel`: (String) Human-readable property types
- `features`: (Array[String]) Notable characteristics or improvements

### Media & Visual Content

- `propertyData.images`: (Array[Object]) Collection of property photos

- `documentId`: (Number) Internal media identifier
- `imageId`: (Number) Unique image identifier
- `url`: (String) Full URL to the high-resolution image
- `caption`: (String) Optional descriptive text
- `isPrimary`: (Boolean) Marks the featured image
- `width`/`height`: (Number) Image dimensions in pixels
- `label`: (String) Classification of the image

### Amenities & Features

- `propertyAmenities`: (Array[Object]) Categorized property characteristics

- `name`: (String) Category name (e.g., "Activities", "Lot Description")
- `categories`: (Array[Object]) Groups of related features

- `name`: (String) Subcategory name
- `amenities`: (Array[String]) Specific features in this group

### Legal & Classification

- `propertyData`:

- `mlsNumber`: (String) Multiple Listing Service identifier
- `zoning`: (String) Zoning classification
- `parcelNumber`: (String) County assessor's parcel number (APN)
- `taxAnnualAmount`: (Number) Annual property tax amount
- `taxYear`: (Number) Assessment year for the tax amount
- `zoningDescription`: (String) Detailed zoning information

### Utilities & Infrastructure

- `propertyData`:

- `utilities`: (Array[String]) Available utility connections
- `waterSource`: (String) Water supply type
- `sewer`: (String) Sewage disposal method
- `electricity`: (String) Electric service availability
- `internet`: (String) Internet service options
- `roadFrontage`: (String) Type of road access

### Environmental & Topographical

- `propertyData`:

- `topography`: (String) General land contours
- `terrain`: (String) Physical characteristics
- `waterFeatures`: (Array[String]) Presence of water bodies
- `vegetation`: (Array[String]) Types of plant life
- `mineralRights`: (String) Mineral rights status
- `floodZone`: (Boolean) If in a designated flood zone
- `wetlands`: (Boolean) If contains protected wetlands

### Financial & Investment

- `propertyData`:

- `capRate`: (Number) Capitalization rate for investments
- `cashFlow`: (Number) Projected annual income
- `grossIncome`: (Number) Total annual rental income
- `operatingExpenses`: (Number) Annual operating costs
- `zoning`: (String) Permitted uses and development potential

### Legal & Disclosures

- `propertyData`:

- `disclosures`: (Array[String]) Required legal disclosures
- `specialConditions`: (String) Any special terms
- `easements`: (String) Existing easements
- `restrictions`: (String) Deed restrictions
- `associationFee`: (Number) HOA or community fees
- `associationFeeFrequency`: (String) Payment frequency

### Pagination Data

- `paginationData`: (Object) Metadata about the current page and navigation

- `canonicalUrl`: (String|null) Canonical URL for the current page (null if not applicable)
- `locationName`: (String|null) Name of the current location being viewed (null if not applicable)
- `metaDescription`: (String) SEO meta description for the page (e.g., "View 12.9 acres priced at $253,485 in Gray Court, Laurens County, SC. Browse photos, see details, and contact the seller.")
- `nextLink`: (String|null) URL to the next page of results (null if on last page)
- `pageHeader`: (String|null) Main header text for the page (null if not applicable)
- `pageHeaderCount`: (String|null) Count indicator for the current page (e.g., "1-10 of 25")
- `pageIndex`: (Number) Zero-based index of the current page (e.g., 0 for first page)
- `pageSubHeader`: (String|null) Subheader text for the page (null if not applicable)
- `pageTitle`: (String) Full page title (e.g., "Knight Road, Gray Court, SC 29645 | MLS: 1551888 | LandWatch")
- `linkData`: (Object|null) Additional link data (null if not applicable)
- `prevLink`: (String|null) URL to the previous page of results (null if on first page)
- `relativeUrl`: (String|null) Relative URL for the current page (null if not applicable)
- `searchBarLocationText`: (String|null) Text to display in the search bar (null if not applicable)
- `siteName`: (String) Name of the website (e.g., "LandWatch")
- `siteUrl`: (String|null) Base URL of the website (null if not applicable)

### Property Data

- `propertyData`: (Object) Core information about the property listing

- `accountId`: (Number) ID of the broker/agent's account
- `acres`: (Number) Total acreage of the property (e.g., 12.9)
- `address`: (Object) Property address details

- `address1`: (String) Primary street address (e.g., "Knight Road")
- `address2`: (String) Secondary address line (usually empty)
- `city`: (String) City name (e.g., "Gray Court")
- `state`: (Number) Numeric state ID (e.g., 45)
- `stateAbbreviation`: (String) Two-letter state code (e.g., "SC")
- `stateName`: (String) Full state name (e.g., "South Carolina")
- `zip`: (String) ZIP code (e.g., "29645")
- `adTargetingPta`: (String) Property type for ad targeting (e.g., "land")
- `areaLabel`: (String) Formatted area display (e.g., "12.9 acres")
- `attachments`: (Array) List of file attachments (usually empty)
- `auctionAddress`: (String|null) Address for auction (null if not an auction)
- `auctionCity`: (String|null) City of auction (null if not an auction)
- `auctionDate`: (String) Formatted auction date ("01/01/0001, 12:00 AM" if not applicable)
- `auctionId`: (String|null) ID for the auction (null if not an auction)
- `auctionState`: (String) Auction status (e.g., "UNDEFINED" if not an auction)
- `auctionTitle`: (String|null) Title/name of the auction (null if not an auction)
- `auctionUrl`: (String|null) URL for auction details (null if not an auction)
- `baths`: (Number) Number of bathrooms (0 for land)
- `beds`: (Number) Number of bedrooms (0 for land)
- `breadcrumbSchema`: (String) JSON-LD structured data for breadcrumb navigation
- `canDisplay`: (Boolean) Whether the listing can be displayed
- `canonicalUrl`: (String) Canonical URL path for the listing (e.g., "/laurens-county-south-carolina-undeveloped-land-for-sale/pid/422387154")
- `city`: (Object) City information

- `id`: (Number) Internal city ID
- `countyId`: (Number) ID of the containing county
- `countyLabelPlural`: (String|null) Pluralized county label (null if not applicable)
- `countyName`: (String|null) Name of the county (null if not applicable)
- `latitude`: (Number) Latitude coordinate of the city
- `longitude`: (Number) Longitude coordinate of the city
- `name`: (String) City name
- `regionId`: (Number) Internal region ID (0 if not applicable)
- `regionName`: (String|null) Name of the region (null if not applicable)
- `stateId`: (Number) Numeric state ID
- `stateAbbreviation`: (String) Two-letter state code
- `stateName`: (String) Full state name
- `cityUrl`: (String) URL path for the city (e.g., "/south-carolina-land-for-sale/gray-court")
- `county`: (Object) County information

- `id`: (Number) Internal county ID
- `fips`: (Number) FIPS code for the county
- `lafCountyId`: (Number) LAF system county ID
- `latitude`: (Number) Latitude coordinate (0 if not set)
- `longitude`: (Number) Longitude coordinate (0 if not set)
- `name`: (String) County name (e.g., "Laurens County")
- `stateId`: (Number) Numeric state ID
- `stateName`: (String|null) Full state name (null if not applicable)
- `regionId`: (Number) Internal region ID (0 if not applicable)
- `regionName`: (String|null) Name of the region (null if not applicable)
- `countyUrl`: (String) URL path for the county (e.g., "/south-carolina-land-for-sale/laurens-county")
- `description`: (Array[String]) List of description paragraphs
- `directions`: (Array[String]) List of direction paragraphs (may be empty)
- `disclaimer`: (String|null) Legal disclaimer text (null if none)
- `executiveSummary`: (String|null) Brief summary of the property (null if none)
- `externalLink`: (String) URL to the listing on the broker's website
- `externalSourceId`: (String|null) ID from external MLS (null if not applicable)
- `feedLastChecked`: (String|null) Timestamp of last feed check (null if not applicable)
- `formattedDescription`: (String|null) Formatted HTML description (null if not available)
- `geocodeAccuracy`: (Number) Accuracy level of geocoding (higher is more accurate)
- `halfBaths`: (Number) Number of half bathrooms (0 for land)
- `highlight1` to `highlight4`: (String|null) Featured highlights (null if not set)
- `homesqft`: (Number) Square footage of any structures (0 for land)
- `homesUserId`: (String|null) Internal user ID (null if not applicable)
- `imageDocumentIds`: (Array[Number]) List of image document IDs
- `imageInfo`: (Array[Object]) Detailed information about each image

- `documentId`: (Number) Unique ID of the image document
- `height`: (Number) Image height in pixels
- `imageId`: (Number) Internal image ID
- `label`: (String) Caption/description of the image
- `width`: (Number) Image width in pixels
- `isDiamond`: (Boolean) Premium listing status - Diamond level
- `isGold`: (Boolean) Premium listing status - Gold level
- `isPlatinum`: (Boolean) Premium listing status - Platinum level
- `isShowcase`: (Boolean) Featured/spotlight listing status
- `isListHubListing`: (Boolean) If listed on ListHub MLS
- `isIrrigated`: (Boolean) If the property has irrigation
- `isLiked`: (Boolean) If the current user has liked/saved this listing
- `isFree`: (Boolean) If this is a free listing
- `isResidence`: (Boolean) If the property includes a residence
- `latitude`: (Number) Geographic latitude coordinate (e.g., 34.528647)
- `longitude`: (Number) Geographic longitude coordinate (e.g., -82.197185)
- `lastUpdated`: (String) Formatted last update timestamp (e.g., "June 3, 2025 at 5:51 AM")
- `leadRoutingEmail`: (String|null) Email for lead routing (null if not set)
- `linkInfos`: (Array[Object]) List of related links and categories

- `labelText`: (String) Display text for the link (e.g., "Undeveloped Land")
- `url`: (String) Relative URL path (e.g., "/undeveloped-land")
- `listhubListingStatus`: (String|null) Status from ListHub integration (null if not applicable)
- `listingDate`: (String) Date when the listing was created (ISO format, e.g., "2025-03-24")
- `listingId`: (Number) Internal listing identifier (e.g., 22982658)
- `listingLevel`: (Number) Tier/level of the listing (e.g., 30)
- `listingSchema`: (String) JSON-LD structured data for the listing in schema.org format
- `accountType`: (Number) Type of the account (e.g., 40 for standard broker)
- `mainPhotoDocumentId`: (String) Document ID of the main/featured photo
- `mlsId`: (String) MLS identifier (e.g., "1551888")
- `parentAccountId`: (Number|null) ID of parent account (null if none)
- `partnerId`: (Number|null) ID of partner organization (null if none)
- `partnerName`: (String|null) Name of partner organization (null if none)
- `participantKey`: (String) Internal participant identifier (e.g., "0")
- `price`: (Number) Listing price in USD (e.g., 253485)
- `pricingPlan`: (Object|null) Details about the pricing plan (null if not applicable)
- `region`: (Object) Geographic region information

- `countyIds`: (Array[Number]|null) List of county IDs in the region (null if not applicable)
- `id`: (Number) Internal region ID (e.g., 197)
- `name`: (String) Region name (e.g., "Upstate South Carolina")
- `stateId`: (Number) Numeric state ID (0 if not state-specific)
- `stateName`: (String|null) Full state name (null if not applicable)
- `referenceName`: (String) Internal reference name for the property (e.g., "Lott")
- `productSchema`: (String) JSON-LD structured data in schema.org/Product format
- `resAndGeoSchema`: (String) JSON-LD structured data combining Residence and GeoCoordinates schemas
- `shouldRedirectLDP`: (Boolean) Whether to redirect to listing detail page
- `siteListingId`: (Number) Unique identifier for the listing on the site (e.g., 422387154)
- `smallMapUrl`: (String) URL to a small static map image of the property location
- `siteId`: (Number) Internal site identifier (e.g., 1113)
- `state`: (Object) State information

- `countyLabel`: (String) Label for county (e.g., "County")
- `countyLabelPlural`: (String) Pluralized county label (e.g., "Counties")
- `stateId`: (Number) Numeric state ID (e.g., 45)
- `stateAbbreviation`: (String) Two-letter state code (e.g., "SC")
- `stateName`: (String) Full state name (e.g., "South Carolina")
- `taxRate`: (Number) State tax rate (e.g., 0.57 for 0.57%)
- `marketStatus`: (Number) Current market status code (e.g., 1 for active)
- `thirdPartyMapUrl`: (String) URL to third-party map service (e.g., id.land)
- `title`: (String) Display title of the listing
- `types`: (Array[String]) List of property type labels (e.g., ["Undeveloped Land"])
- `typeIds`: (Array[Number]) Internal IDs for property types (e.g., [8, 32])
- `upgradeLevelId`: (Number) ID of any upgrade package (0 if none)
- `videoSchema`: (String) JSON-LD structured data for video (empty if none)
- `youtubeVideoId`: (String|null) YouTube video ID (null if none)
- `virtualTourLink`: (String) URL to virtual tour (empty if none)
- `propertyMediaData`: (Object) Container for various media types

- `youtubeVideo`: (Object|null) YouTube video details (null if none)
- `matterportVirtualTour`: (Object|null) Matterport 3D tour details (null if none)
- `vimeoVideo`: (Object|null) Vimeo video details (null if none)
- `propertyOverlays`: (Array[Object]) List of map overlays for the property

- `description`: (String|null) Description of the overlay (null if none)
- `geometry`: (String) Comma-separated coordinates (e.g., "lat,lng")
- `mainParcel`: (Boolean) If this is the primary parcel overlay
- `name`: (String) Name of the overlay (e.g., "Custom")
- `overlayId`: (Number) Unique identifier for the overlay
- `overlayImages`: (Array) List of images associated with the overlay
- `overlayTypeId`: (Number) Type identifier for the overlay
- `propertyId`: (Number) ID of the associated property
- `ptype`: (String) Type of overlay (e.g., "custom")
- `styleString`: (String) JSON string with styling information
- `uuid`: (String) Unique identifier for the overlay
- `zIndex`: (Number) Stacking order for the overlay
- `propertyTypes`: (Array[String]) Comprehensive list of all possible property types
- `soldListings`: (Array) List of recently sold comparable properties (empty if none)
- `uploadedSellerFiles`: (Array) List of files uploaded by the seller (empty if none)

### Property Amenities & Features

- `propertyAmenities`: (Array[Object]) Categorized list of property features and amenities

- `name`: (String) Category name (e.g., "Land")
- `categories`: (Array[Object]) Groups of related features

- `name`: (String) Subcategory name (e.g., "Activities", "Game", "Lot Description")
- `amenities`: (Array[String]) List of specific features in this category

- Example activities: "Camping", "Conservation"
- Example game: "Turkey", "Whitetail Deer"
- Example lot features: "Acreage", "Heavily Treed", "Pasture", "Vacant"
- Example road types: "Asphalt", "County"
- Example utilities: "City Sewer"
- Example topography: "Level", "Rolling"

### Other Listings from Same Broker

- `otherListings`: (Array[Object]) List of other properties listed by the same broker

- `accountId`: (Number) Broker's account ID (matches brokerDetails.accountId)
- `acres`: (Number) Size of the property in acres (e.g., 11.76)
- `acresDisplay`: (String) Formatted display of acreage (e.g., "11.8 acres")
- `adTargetingCountyId`: (Number) County ID used for ad targeting
- `address`: (String) Street address (may be partial for privacy)
- `auctionDate`: (ISO Date) Scheduled auction date ("0001-01-01T00:00:00" if not applicable)
- `beds`/`baths`/`halfBaths`: (Number) Number of bedrooms, bathrooms, and half-bathrooms (0 for land)
- `bedsDisplay`/`bathsDisplay`/`halfBathsDisplay`: (String) Formatted display of room counts
- `brokerCanonicalUrl`: (String) URL path to broker's profile
- `brokerCompany`: (String) Name of the brokerage firm
- `brokerName`: (String) Name of the listing agent
- `brokerPhone`: (String|null) Contact number for the broker
- `canonicalUrl`: (String) URL path to this listing
- `city`: (String) City where the property is located
- `cityID`: (Number) Internal ID for the city
- `companyLogoDocumentId`: (Number) ID of the company logo image (0 if none)
- `county`: (String) Full county name
- `countyId`: (Number) Internal ID for the county
- `countyLabel`: (String) Type of county designation (e.g., "County")
- `description`: (String) Full property description (may be truncated)
- `encodedBoundaryPoints`: (String) Encoded polygon data for property boundaries
- `executiveSummary`: (String|null) Brief summary of the listing (null if not provided)
- `externalSourceId`: (String|null) ID from external MLS (null if not applicable)
- `hasCustomMap`: (Boolean) If the listing includes a custom map
- `hasHouse`: (Boolean) If the property includes a house/structure
- `hasVideo`: (Boolean) If the listing includes video content
- `hasVirtualTour`: (Boolean) If a 3D/virtual tour is available
- `homesqft`: (Number) Size of any structures in square feet (0 for land)
- `homesqftDisplay`: (String) Formatted display of home square footage
- `imageAltTextDisplay`: (String) Alt text for the listing's main image
- `imageCount`: (Number) Total number of images available
- `imageIds`: (Array[Number]|null) List of image IDs (null if not loaded)
- `insertDate`: (ISO Date) When the listing was created
- `id`: (Number) Internal listing ID
- `isALC`: (Boolean) If the listing is from an Accredited Land Consultant
- `isCourtesy`: (Boolean) If this is a courtesy listing
- `isDiamond`/`isGold`/`isPlatinum`: (Boolean) Premium listing status indicators
- `isFirstFreeListing`: (Boolean) If this is the broker's first free listing
- `isLiked`: (Boolean) If the current user has liked/saved this listing
- `isShowcase`: (Boolean) If this is a featured/spotlight listing
- `lafPropertyId`: (Number) Internal property ID in LAF system
- `lake`: (String|null) Name of nearby lake (null if not applicable)
- `lastUpdated`: (ISO Date) When the listing was last modified
- `latitude`/`longitude`: (Number) Geographic coordinates of the property
- `listHubListingKey`: (String|null) ID for ListHub integration
- `listingLevel`: (Number) Tier/level of the listing (e.g., 30)
- `listingLevelTitle`: (String) Name of the listing level (e.g., "Signature Partner")
- `lwPropertyId`: (Number) LandWatch property ID
- `onMarketDate`: (ISO Date) When the property was listed
- `parentAccountId`: (Number) ID of parent account (0 if none)
- `partnerId`: (Number) ID of partner organization (0 if none)
- `portraitDocumentId`: (Number) ID of the broker's profile image
- `price`: (Number) Current listing price in USD
- `priceChangeAmount`: (Number) Absolute amount of last price change (negative for decrease)
- `priceChangeDate`: (ISO Date) When the price was last changed
- `priceChangePercentage`: (Number) Percentage of last price change (negative for decrease)
- `priceDisplay`: (String) Formatted price with currency symbol (e.g., "$95,900")
- `pricePerAcre`: (Number) Calculated price per acre (e.g., 8154.76)
- `propertyTypes`: (Number) Bitmask of property type flags
- `propertyTypesLabel`: (String) Human-readable list of property types
- `regionId`: (Number) Internal ID for the region
- `salesDate`: (ISO Date) When the property sold ("0001-01-01T00:00:00" if not sold)
- `salesPrice`: (Number) Final sale price (0 if not sold)
- `schemaData`: (String) JSON-LD structured data for search engines
- `shortPrice`: (String) Abbreviated price (e.g., "$95.9K")
- `shortPriceChangeAmount`: (String) Formatted price change amount (e.g., "-$29.1K")
- `siteListingId`: (Number) Listing ID on the main site
- `state`: (String) Full state name
- `stateAbbreviation`: (String) Two-letter state code
- `stateCode`: (String) State code (usually same as abbreviation)
- `stateId`: (Number) Internal ID for the state
- `status`: (Number) Listing status code (1 = Active)
- `thumbnailDocumentId`: (Number) ID of the thumbnail image
- `title`: (String) Listing title/headline
- `types`: (Array[String]) Property type categories
- `upgradeLevelId`: (Number) ID of any upgrade package (0 if none)
- `zip`: (String) ZIP/postal code

### System & Technical Fields

- `lafPropertyId`: (Number) Internal database identifier
- `externalSourceId`: (String) Identifier from external MLS
- `geocodeAccuracy`: (Number) Precision of coordinates
- `hasCustomMap`: (Boolean) If includes custom map overlay
- `hasVideo`: (Boolean) If video content available
- `hasVirtualTour`: (Boolean) If 3D/virtual tour available

---

## Output Agent(s) Structure

The scraper provides comprehensive information about LandWatch property agents. The output includes detailed agent information, broker details, and location data. Here's a breakdown of the main components:

```
{
  "sellerId": 174024,
  "basicInfo": {
    "accountId": 174024,
    "companyName": "HomeLand Properties",
    "contactName": "Texas Ranch Sales, LLC",
    "city": "Hondo", "stateAbbreviation": "TX", "zip": "78861",
    "phoneNumbers": {
      "officePhone": "(830) 741-8906",
      "preferredPhone": "(830) 741-8906",
      "...": "..."
    },
    "url": "www.texasranchsalesllc.com",
    "canonicalUrl": "/profile/homeland-properties/174024",
    "logoId": 2703760373, "portraitId": 3832720652,
    "description": ["For over 30 years, HomeLand Properties..."],
    "...": "(same broker-card fields)"
  },
  "brokerDetails": { "...": "(broker card; same shape as basicInfo)" },
  "sellerMedia": {
    "Facebook":  { "mediaUrl": "https://www.facebook.com/HomeLandProperties", "...": "..." },
    "Instagram": { "mediaUrl": "https://www.instagram.com/...", "...": "..." },
    "Linkedin":  { "mediaUrl": "https://www.linkedin.com/company/...", "...": "..." }
  },
  "otherListings": ["..."],
  "soldListings": ["..."],
  "sellerCarouselListings": ["..."],
  "landStarAwards": [{ "quarter": 1, "year": 2024 }, "..."],
  "profileSchema": { "...": "..." },
  "uploadedSellerFiles": ["..."],
  "paginationData": { "...": "..." }
}
```

> **Full unabridged sample** (real captured record, every field present): readme-stuff/sample-agent.json.
> When `flattenOutput=true`, `basicInfo` and `brokerDetails` collapse into top-level fields and `url` / `logoUrl` / `portraitUrl` are added.

## Output Agent(s) Fields Explanation

### Basic Broker Information

- `basicInfo`: Core information about the broker/agent

- `accountId`: (Number) Unique identifier for the broker's LandWatch account
- `accountSubTypeId`: (Number) Subtype classification of the account (e.g., 5)
- `accountType`: (Number) Main account type (e.g., 41 for broker)
- `active`: (Boolean) Whether the broker account is active
- `address1`: (String) Primary business address line
- `address2`: (String) Secondary business address line
- `city`: (String) City of business location
- `country`: (String) Country of business location
- `email`: (String) Contact email address
- `firstName`: (String) First name of the broker
- `lastName`: (String) Last name of the broker
- `phone`: (String) Primary contact phone number
- `state`: (String) State abbreviation
- `title`: (String) Professional title or designation
- `url`: (String) Website URL
- `zip`: (String) Zip/postal code

### Broker Details

- `brokerDetails`: Comprehensive information about the broker

- `accountId`: (Number) Unique broker account identifier
- `accountSubTypeId`: (Number) Subtype classification of the account
- `accountType`: (Number) Main account type classification
- `active`: (Boolean) Account activation status
- `adDesc`: (String) Advertisement description
- `address1`: (String) Primary business address
- `address2`: (String) Secondary business address
- `alcCertified`: (Boolean) ALC (Accredited Land Consultant) certification status
- `alcAdvancedCertified`: (Boolean) Advanced ALC certification status
- `badgeId`: (Number) ID of the broker's badge/credential
- `canonicalUrl`: (String) Canonical URL for the broker's profile
- `city`: (String) City of business location
- `companyAddress1`: (String) Company's primary address line
- `companyAddress2`: (String) Company's secondary address line
- `companyName`: (String) Name of the broker's company
- `companyCity`: (String) Company's city location
- `companyState`: (String) Company's state location
- `companyZip`: (String) Company's zip code
- `contactName`: (String) Name for business contact
- `description`: (Array[String]) Multi-line company description
- `email`: (String|null) Contact email address
- `expirationDate`: (ISO Date) Account expiration date
- `homesContactId`: (String) Homes.com contact ID
- `homesUserId`: (String|null) Homes.com user ID
- `insertDate`: (ISO Date) Date when the broker account was created
- `isFree`: (Boolean) Whether the account is a free tier
- `isPhoneTPN`: (Boolean) Whether the phone number is a tracking phone number
- `isSeller`: (Boolean) Whether the broker is a seller
- `landStarWinCount`: (Number) Number of LandStar awards won
- `leadRoutingEmail`: (String|null) Email for lead routing
- `licenseNumber`: (String) Real estate license number
- `listingCount`: (Number) Current number of active listings
- `logoId`: (Number) ID of the company logo
- `optInLeadTargeting`: (Boolean) Whether opted into lead targeting
- `parentAccountId`: (Number) ID of parent account (0 if none)
- `parentAccountType`: (Number) Type of parent account (0 if none)
- `phoneCell`: (String) Mobile phone number
- `phoneFax`: (String|null) Fax number
- `phoneOffice`: (String) Office phone number
- `phoneTollFree`: (String|null) Toll-free phone number
- `portraitId`: (Number) ID of the broker's profile picture
- `portraitImageUpdateDate`: (ISO Date|null) Last update date of profile picture
- `sellerListingStats`: (Object) Historical listing statistics

- `allTimePriceMin`: (Number) Minimum listing price ever
- `allTimePriceMax`: (Number) Maximum listing price ever
- `allTimeAcreageMin`: (Number) Minimum acreage ever
- `allTimeAcreageMax`: (Number) Maximum acreage ever
- `allTimeListingCount`: (Number) Total listings ever
- `lastThreeYears`: (Object) Statistics for last 3 years
- `lastFiveYears`: (Object) Statistics for last 5 years
- `lastTenYears`: (Object) Statistics for last 10 years
- `smsNotifications`: (Boolean) Whether SMS notifications are enabled
- `stateAbbreviation`: (String) State abbreviation
- `stripeCustomerId`: (String|null) Stripe customer ID
- `totalRows`: (Number) Total number of rows in results
- `trackingPhoneNumber`: (String) Phone number for lead tracking
- `url`: (String) Website URL
- `zip`: (String) Zip/postal code

### LandStar Awards

- `landStarAwards`: Array of LandStar awards won by the broker

- `quarter`: (Number) Quarter of the year (0-4)
- `year`: (Number) Year the award was won

### Other Listings

- `otherListings`: Array of other properties listed by the same broker

- `accountId`: (Number) Broker's account ID
- `acres`: (Number) Size of the property in acres
- `acresDisplay`: (String) Formatted display of acreage
- `adTargetingCountyId`: (Number) County ID for ad targeting
- `address`: (String) Property address
- `auctionDate`: (ISO Date) Date of auction (if applicable)
- `baths`: (Number) Number of bathrooms
- `bathsDisplay`: (String) Formatted display of bathrooms
- `beds`: (Number) Number of bedrooms
- `bedsDisplay`: (String) Formatted display of bedrooms
- `brokerCanonicalUrl`: (String) Canonical URL for the broker's profile
- `brokerCompany`: (String) Broker's company name
- `brokerName`: (String) Broker's name
- `brokerPhone`: (String|null) Broker's phone number
- `canonicalUrl`: (String) Canonical URL for the listing
- `city`: (String) City name
- `cityID`: (Number) Internal city identifier
- `companyLogoDocumentId`: (Number) ID of company logo
- `county`: (String) County name
- `countyId`: (Number) Internal county identifier
- `countyLabel`: (String) Label for county display
- `description`: (String) Property description
- `encodedBoundaryPoints`: (String) Encoded coordinates of property boundary
- `executiveSummary`: (String|null) Executive summary of the property
- `externalSourceId`: (String|null) ID from external MLS
- `halfBaths`: (Number) Number of half bathrooms
- `halfBathsDisplay`: (String|null) Formatted display of half bathrooms
- `hasCustomMap`: (Boolean) Whether the property has a custom map
- `hasHouse`: (Boolean) Whether the property includes a house
- `hasVideo`: (Boolean) Whether the property has video content
- `hasVirtualTour`: (Boolean) Whether the property has a virtual tour
- `homesqft`: (Number) Square footage of any home
- `homesqftDisplay`: (String) Formatted display of square footage
- `imageAltTextDisplay`: (String) Alt text for images
- `imageCount`: (Number) Number of images
- `imageIds`: (Array[Number]) IDs of all property images
- `insertDate`: (ISO Date) Date the listing was created
- `id`: (Number) Internal listing identifier
- `isALC`: (Boolean) Whether the broker is ALC certified
- `isCourtesy`: (Boolean) Whether it's a courtesy listing
- `isDiamond`: (Boolean) Whether it's a Diamond level listing
- `isFirstFreeListing`: (Boolean) Whether it's the broker's first free listing
- `isGold`: (Boolean) Whether it's a Gold level listing
- `isLiked`: (Boolean) Whether the listing has been liked
- `isPlatinum`: (Boolean) Whether it's a Platinum level listing
- `isShowcase`: (Boolean) Whether it's a showcase listing
- `lafPropertyId`: (Number) Internal property identifier
- `lake`: (String|null) Name of lake (if applicable)
- `lastUpdated`: (ISO Date) Date the listing was last updated
- `latitude`: (Number) Property latitude
- `listHubListingKey`: (String|null) ListHub MLS key
- `listingLevel`: (Number) Listing level code
- `listingLevelTitle`: (String) Title of listing level
- `longitude`: (Number) Property longitude
- `lwPropertyId`: (Number) LandWatch property identifier
- `onMarketDate`: (ISO Date) Date the property went on market
- `parentAccountId`: (Number) Parent account ID (if applicable)
- `partnerId`: (Number) Partner ID (if applicable)
- `portraitDocumentId`: (Number) ID of broker's portrait
- `firstName`: (String) Broker's first name
- `lastName`: (String) Broker's last name
- `phone`: (String) Contact phone number
- `price`: (Number) Listing price
- `priceDisplay`: (String) Formatted price display
- `propertyTypes`: (Array[String]) Types of property
- `propertyTypesLabel`: (String) Human-readable property types
- `regionId`: (Number) Internal region identifier
- `salesDate`: (ISO Date) Date of sale (if sold)
- `salesPrice`: (Number) Sale price (if sold)
- `state`: (String) Property state
- `status`: (Number) Listing status code
- `thumbnailDocumentId`: (Number) ID of thumbnail image
- `title`: (String) Listing title
- `types`: (Array[String]) Property type categories
- `upgradeLevelId`: (Number) Upgrade package ID
- `zip`: (String) Property zip code

### Sold Listings

- `soldListings`: Array of previously sold properties

- Contains similar fields as otherListings but with additional sale information
- `salesDate`: (ISO Date) Date when the property was sold
- `salesPrice`: (Number) Final sale price
- `status`: (Number) Status code indicating sold status

### Pagination Data

- `paginationData`: Information for pagination and navigation

- `canonicalUrl`: (String) Canonical URL for the broker profile
- `locationName`: (String|null) Name of the broker's location
- `metaDescription`: (String) SEO meta description
- `nextLink`: (String|null) URL for next page
- `pageHeader`: (String) Page header text
- `pageHeaderCount`: (Number|null) Number displayed in page header
- `pageIndex`: (Number) Current page index
- `pageSubHeader`: (String|null) Page subheader text
- `pageTitle`: (String) Page title
- `linkData`: (Object|null) Additional link data
- `prevLink`: (String|null) URL for previous page
- `relativeUrl`: (String|null) Relative URL for the page
- `searchBarLocationText`: (String|null) Text for search bar location
- `siteName`: (String|null) Site name
- `siteUrl`: (String|null) Site URL

### Seller Media

- `sellerMedia`: Collection of media links and content for the broker

- `Video`: (Object) Video content information

- `active`: (Number) Activation status (1 = active)
- `mediaId`: (String) ID of the media content
- `mediaThumbnail`: (String|null) URL to thumbnail image
- `mediaTypeId`: (Number) Type identifier for the media
- `mediaUrl`: (String) URL to the media content
- `oEmbedResponse`: (String|null) oEmbed response data
- `providerId`: (Number) Provider identifier
- `isVideo`: (Boolean) Whether the content is video
- `Linkedin`: (Object) LinkedIn profile information

- Same fields as Video object
- `Facebook`: (Object) Facebook page information

- Same fields as Video object
- `Instagram`: (Object) Instagram profile information

- Same fields as Video object

### Seller Information

- `sellerId`: (Number) Unique identifier for the seller/broker
- `uploadedSellerFiles`: (Array) List of uploaded files by the seller (empty array if none)

### Seller Carousel Listings

- `sellerCarouselListings`: Array of featured listings in the seller's carousel

- `canonicalUrl`: (String) Canonical URL for the listing
- `imageAltTextDisplay`: (String) Alt text for images
- `imageIds`: (Array[Number]) IDs of listing images
- `id`: (Number) Internal listing identifier
- `price`: (Number) Listing price
- `status`: (Number) Listing status code

### Sold Listings

- `soldListings`: Array of properties that have been sold

- `accountId`: (Number) Broker's account ID
- `acres`: (Number) Size of the property in acres
- `acresDisplay`: (String) Formatted display of acreage
- `adTargetingCountyId`: (Number) County ID for ad targeting
- `address`: (String) Property address
- `auctionDate`: (ISO Date) Date of auction (if applicable)
- `baths`: (Number) Number of bathrooms
- `bathsDisplay`: (String) Formatted display of bathrooms
- `beds`: (Number) Number of bedrooms
- `bedsDisplay`: (String) Formatted display of bedrooms
- `brokerCanonicalUrl`: (String) Canonical URL for the broker's profile
- `brokerCompany`: (String) Broker's company name
- `brokerName`: (String) Broker's name
- `brokerPhone`: (String|null) Broker's phone number
- `canonicalUrl`: (String) Canonical URL for the listing
- `city`: (String) City name
- `cityID`: (Number) Internal city identifier
- `companyLogoDocumentId`: (Number) ID of company logo
- `county`: (String) County name
- `countyId`: (Number) Internal county identifier
- `countyLabel`: (String) Label for county display
- `description`: (String) Property description
- `encodedBoundaryPoints`: (String) Encoded coordinates of property boundary
- `executiveSummary`: (String|null) Executive summary of the property
- `externalSourceId`: (String|null) ID from external MLS
- `halfBaths`: (Number) Number of half bathrooms
- `halfBathsDisplay`: (String|null) Formatted display of half bathrooms
- `hasCustomMap`: (Boolean) Whether the property has a custom map
- `hasHouse`: (Boolean) Whether the property includes a house
- `hasVideo`: (Boolean) Whether the property has video content
- `hasVirtualTour`: (Boolean) Whether the property has a virtual tour
- `homesqft`: (Number) Square footage of any home
- `homesqftDisplay`: (String) Formatted display of square footage
- `imageAltTextDisplay`: (String) Alt text for images
- `imageCount`: (Number) Number of images
- `imageIds`: (Array[Number]|null) IDs of property images
- `insertDate`: (ISO Date) Date the listing was created
- `id`: (Number) Internal listing identifier
- `isALC`: (Boolean) Whether the broker is ALC certified
- `isCourtesy`: (Boolean) Whether it's a courtesy listing
- `isDiamond`: (Boolean) Whether it's a Diamond level listing
- `isFirstFreeListing`: (Boolean) Whether it's the broker's first free listing
- `isGold`: (Boolean) Whether it's a Gold level listing
- `isLiked`: (Boolean) Whether the listing has been liked
- `isPlatinum`: (Boolean) Whether it's a Platinum level listing
- `isShowcase`: (Boolean) Whether it's a showcase listing
- `lafPropertyId`: (Number) Internal property identifier
- `lake`: (String|null) Name of lake (if applicable)
- `lastUpdated`: (ISO Date) Date the listing was last updated
- `latitude`: (Number) Property latitude
- `listHubListingKey`: (String|null) ListHub MLS key
- `listingLevel`: (Number) Listing level code
- `listingLevelTitle`: (String) Title of listing level
- `longitude`: (Number) Property longitude
- `lwPropertyId`: (Number) LandWatch property identifier
- `onMarketDate`: (ISO Date) Date the property went on market
- `parentAccountId`: (Number) Parent account ID (if applicable)
- `partnerId`: (Number) Partner ID (if applicable)
- `portraitDocumentId`: (Number) ID of broker's portrait
- `price`: (Number) Listing price
- `priceChangeAmount`: (Number) Amount of price change
- `priceChangeDate`: (ISO Date) Date of last price change
- `priceChangePercentage`: (Number) Percentage price change
- `priceDisplay`: (String) Formatted price display
- `pricePerAcre`: (Number) Price per acre
- `propertyTypes`: (Number) Bitmask of property types
- `propertyTypesLabel`: (String) Human-readable property types
- `regionId`: (Number) Internal region identifier
- `salesDate`: (ISO Date) Date of sale
- `salesPrice`: (Number) Sale price
- `schemaData`: (String) JSON-LD schema data for SEO
- `shortPrice`: (String) Short formatted price
- `shortPriceChangeAmount`: (String) Short formatted price change
- `siteListingId`: (Number) Site-specific listing identifier
- `state`: (String) State name
- `stateAbbreviation`: (String) State abbreviation
- `stateCode`: (String) State code
- `stateId`: (Number) Internal state identifier
- `status`: (Number) Listing status code (4 = Sold)
- `thumbnailDocumentId`: (Number) ID of thumbnail image
- `title`: (String) Listing title
- `types`: (Array[String]) Property type categories
- `upgradeLevelId`: (Number) Upgrade package ID
- `zip`: (String) Zip code

### Basic Broker Information

- `basicInfo`: Core information about the broker/agent

- `accountId`: (Number) Unique identifier for the broker's LandWatch account
- `accountSubTypeId`: (Number) Subtype classification of the account
- `accountType`: (Number) Main account type classification
- `active`: (Boolean) Account activation status
- `adDesc`: (String) Advertisement description
- `address1`: (String) Primary business address line
- `address2`: (String) Secondary business address line
- `alcCertified`: (Boolean) ALC (Accredited Land Consultant) certification status
- `alcAdvancedCertified`: (Boolean) Advanced ALC certification status
- `badgeId`: (Number) ID of the broker's badge/credential
- `canonicalUrl`: (String) Canonical URL for the broker's profile
- `city`: (String) City of business location
- `companyAddress1`: (String) Company's primary address line
- `companyAddress2`: (String) Company's secondary address line
- `companyName`: (String) Name of the broker's company
- `companyCity`: (String) Company's city location
- `companyState`: (String) Company's state location
- `companyZip`: (String) Company's zip code
- `contactName`: (String) Name for business contact
- `description`: (Array[String]) Multi-line company description
- `email`: (String|null) Contact email address
- `expirationDate`: (ISO Date|null) Account expiration date
- `homesContactId`: (String|null) Homes.com contact ID
- `homesUserId`: (String|null) Homes.com user ID
- `insertDate`: (ISO Date|null) Date when the broker account was created
- `isFree`: (Boolean) Whether the account is a free tier
- `isPhoneTPN`: (Boolean) Whether the phone number is a tracking phone number
- `isSeller`: (Boolean) Whether the broker is a seller
- `landStarWinCount`: (Number) Number of LandStar awards won
- `leadRoutingEmail`: (String|null) Email for lead routing
- `licenseNumber`: (String) Real estate license number
- `listingCount`: (Number) Current number of active listings
- `logoId`: (Number) ID of the company logo
- `optInLeadTargeting`: (Boolean) Whether opted into lead targeting
- `parentAccountId`: (Number) ID of parent account (0 if none)
- `parentAccountType`: (Number) Type of parent account (0 if none)
- `phoneCell`: (String) Mobile phone number
- `phoneFax`: (String|null) Fax number
- `phoneOffice`: (String) Office phone number
- `phoneTollFree`: (String|null) Toll-free phone number
- `portraitId`: (Number) ID of the broker's profile picture
- `portraitImageUpdateDate`: (ISO Date|null) Last update date of profile picture
- `sellerListingStats`: (Object) Historical listing statistics

- `allTimePriceMin`: (Number) Minimum listing price ever
- `allTimePriceMax`: (Number) Maximum listing price ever
- `allTimeAcreageMin`: (Number) Minimum acreage ever
- `allTimeAcreageMax`: (Number) Maximum acreage ever
- `allTimeListingCount`: (Number) Total listings ever
- `lastThreeYears`: (Object) Statistics for last 3 years
- `lastFiveYears`: (Object) Statistics for last 5 years
- `lastTenYears`: (Object) Statistics for last 10 years
- `smsNotifications`: (Boolean) Whether SMS notifications are enabled
- `stateAbbreviation`: (String) State abbreviation
- `stripeCustomerId`: (String|null) Stripe customer ID
- `totalRows`: (Number) Total number of rows in results
- `trackingPhoneNumber`: (String) Phone number for lead tracking
- `url`: (String) Website URL
- `zip`: (String) Zip/postal code

## Explore More Scrapers

If you found this Apify LandWatch Profile Scraper useful, be sure to check out our other powerful scrapers and actors at [memo23's Apify profile](https://apify.com/memo23). We offer a wide range of tools to enhance your web scraping and automation needs across various platforms and use cases.

## Support

- For issues or feature requests, please use the [Issues](https://console.apify.com/actors/IWIOv7oeNxfcjTnX5/issues) section of this actor.
- If you need customization or have questions, feel free to contact the author:

- Author's website: [https://muhamed-didovic.github.io/](https://muhamed-didovic.github.io/)
- Email: [muhamed.didovic@gmail.com](mailto:muhamed.didovic@gmail.com)

## Additional Services

- Request customization or whole dataset: [muhamed.didovic@gmail.com](mailto:muhamed.didovic@gmail.com)
- If you need anything else scraped, or this actor customized, email: [muhamed.didovic@gmail.com](mailto:muhamed.didovic@gmail.com)
- For API services of this scraper (no Apify fee, just usage fee for the API), contact: [muhamed.didovic@gmail.com](mailto:muhamed.didovic@gmail.com)
- Email: [muhamed.didovic@gmail.com](mailto:muhamed.didovic@gmail.com)