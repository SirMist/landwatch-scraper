[Landwatch Scraper](https://apify.com/fatihtahta/landwatch-scraper?fpr=data)

# LandWatch.com Scraper

**Slug:** `fatihtahta/lanswatch-com-scraper`

## Overview

LandWatch.com Scraper collects structured public real estate listing data from LandWatch, including listing identity, title, description, pricing, acreage, residential attributes, location, broker details, media, features, listing history, and related listing context. [LandWatch](https://www.landwatch.com) is a public marketplace for land, acreage, farms, ranches, homesites, recreational property, and other rural real estate, making its listings useful for market research, lead qualification, investment screening, and inventory monitoring. The actor converts search and filter configurations into repeatable dataset outputs that are easier to analyze than manual browsing. It is designed for automated, recurring data acquisition where consistent JSON records, predictable limits, and operational review matter. Use it to support dependable collection workflows without assuming that every listing, field, or source-side attribute will be available in every run.

## Why Use This Actor

- **Market research and analytics teams:** build market intelligence datasets for supply, price, acreage, property-type mix, broker activity, and regional inventory trends.
- **Product and content teams:** populate internal directories, comparison experiences, editorial research, or property discovery workflows with normalized listing data.
- **Developers and data engineering teams:** feed structured extraction results into downstream systems, ETL jobs, warehouses, enrichment pipelines, and operational reporting.
- **Lead generation and enrichment teams:** identify public broker, seller, and property attributes that can support qualification, segmentation, and CRM enrichment.
- **Monitoring and competitive tracking teams:** schedule repeatable collection to detect changes in pricing, availability, listing updates, and market movement over time.

## Common Use Cases

- **Market intelligence:** monitor land supply, pricing, price-per-acre movement, acreage bands, listing availability, and geographic coverage.
- **Lead generation:** build targeted prospect lists from public land, farm, ranch, residential, and broker listing data.
- **Competitive monitoring:** track changes in listings, pricing, property categories, broker inventory, and recently updated records.
- **Catalog and directory building:** populate internal real estate databases with structured public listing records.
- **Data enrichment:** add current public property, location, broker, media, and feature attributes to CRM, BI, or analytics datasets.
- **Recurring reporting:** schedule periodic runs for dashboards, alerts, market summaries, and trend analysis.

## Quick Start

1. Choose the listing scope with `deal_type` and `availability`.
2. Add a `location`, `property_type`, keyword, pricing, acreage, timing, or feature filters when you need a narrower dataset.
3. Set a small `limit`, such as 25 or 50, for the first validation run.
4. Run the actor in Apify Console.
5. Inspect the first dataset records to confirm that the output shape and field coverage match your use case.
6. Increase coverage, adjust filters, enable scheduling, or use `maximize_coverage` and `enrich_data` once the output is verified.

## Input Parameters

This actor accepts LandWatch search scope, location, property, timing, feature, price, acreage, building, bedroom, bathroom, sorting, limit, coverage, and enrichment controls.

| Parameter | Type | Description | Default |
| --- | --- | --- | --- |
| `deal_type` | string | Listing deal type. Allowed values: `for_sale`, `auction`. Leave empty to avoid limiting by deal type. | – |
| `availability` | array of strings | Listing statuses to include. Allowed values: `buy`, `under_contract`, `off_market`, `sold`. | `["buy", "under_contract"]` |
| `location` | string | Free-text location such as `California`, `Los Angeles County CA`, or `Ramona CA`. | – |
| `property_type` | string | Property category. Allowed values: `commercial`, `farms_and_ranches`, `homesite`, `horse`, `house`, `hunting`, `lakefront`, `oceanfront`, `recreational`, `riverfront`, `timberland`, `undeveloped`, `waterfront`. | – |
| `price_reduction_period` | string | Only include listings with a price reduction in the selected window. Allowed values: `3_days`, `7_days`, `30_days`, `60_days`, `90_days`. | – |
| `publication_date` | string | Only include listings first published in the selected window. Allowed values: `1_day`, `7_days`, `30_days`, `60_days`. | – |
| `keyword` | string | Keyword or phrase used to focus matching listings. | – |
| `owner_financing` | boolean | Include only listings that offer owner financing. | `false` |
| `mineral_rights` | boolean | Include only listings that mention mineral rights. | `false` |
| `virtual_tour` | boolean | Include only listings that provide a virtual tour. | `false` |
| `exterior_tour` | boolean | Include only listings that provide an exterior tour. | `false` |
| `property_video` | boolean | Include only listings that provide a property video. | `false` |
| `custom_map` | boolean | Include only listings that provide a custom map. | `false` |
| `min_price` | integer | Minimum listing price in USD. Must be 0 or greater. | – |
| `max_price` | integer | Maximum listing price in USD. Must be 0 or greater. | – |
| `min_area_parcel` | number | Minimum parcel size in acres. Must be 0 or greater. | – |
| `max_area_parcel` | number | Maximum parcel size in acres. Must be 0 or greater. | – |
| `min_area_building` | number | Minimum building size in square feet. Must be 0 or greater. | – |
| `max_area_building` | number | Maximum building size in square feet. Must be 0 or greater. | – |
| `min_bedroom` | integer | Minimum number of bedrooms. Must be 0 or greater. | – |
| `max_bedroom` | integer | Maximum number of bedrooms. Must be 0 or greater. | – |
| `min_bathroom` | integer | Minimum number of bathrooms. Must be 0 or greater. | – |
| `max_bathroom` | integer | Maximum number of bathrooms. Must be 0 or greater. | – |
| `sort_by` | string | Result order. Allowed values: `default`, `acres_small_to_large`, `acres_large_to_small`, `newest`, `price_low_to_high`, `price_high_to_low`, `price_per_acre_low_to_high`, `price_per_acre_high_to_low`, `recently_changed`. | `default` |
| `limit` | integer | Maximum number of listings to save for each location. Must be 1 or greater. Leave empty to collect all available matching listings. | – |
| `maximize_coverage` | boolean | Collect a broader set of matching listings for production-style runs. Disable for faster exploratory runs. | `true` |
| `enrich_data` | boolean | Include richer listing details such as descriptions, parcel identifiers, amenities, listing history, media, and broker contact details when available. | `true` |

## Choosing Inputs

Use `location` when you need a state, county, city, or local-market view. Add `property_type`, price, parcel acreage, building size, bedroom, bathroom, feature, and timing filters when the goal is a targeted dataset; leave optional filters empty when the goal is broader discovery. Narrower filters produce cleaner, more focused output, while broader filters improve coverage and are better for exploratory market analysis. Use `publication_date`, `price_reduction_period`, and `sort_by` for monitoring workflows where freshness, recent changes, or ordered review matters. Start with a small `limit` to validate record shape and field coverage, then increase the limit or enable broader collection once the output is ready for downstream use.

## Example Inputs

### Location and category validation run

```
{
  "deal_type": "for_sale",
  "availability": ["buy", "under_contract"],
  "location": "Bland County VA",
  "property_type": "farms_and_ranches",
  "sort_by": "newest",
  "limit": 25,
  "enrich_data": true
}
```

### Recently changed price monitoring

```
{
  "availability": ["buy"],
  "location": "Virginia",
  "price_reduction_period": "30_days",
  "min_price": 100000,
  "max_price": 750000,
  "sort_by": "recently_changed",
  "limit": 100
}
```

### Broad discovery with conservative output

```
{
  "deal_type": "for_sale",
  "availability": ["buy"],
  "keyword": "waterfront",
  "min_area_parcel": 10,
  "property_type": "waterfront",
  "limit": 50,
  "maximize_coverage": true,
  "enrich_data": false
}
```

## Output

### Output destination

The actor writes results to an Apify dataset as JSON records. The dataset is designed for direct consumption by analytics tools, ETL pipelines, and downstream APIs with minimal post-processing.

The provided Example Output contains one primary record shape: a LandWatch listing record. If future runs expose additional entity shapes, document and validate each shape separately before relying on it in production workflows.

### Record envelope and stable identifiers

Each dataset item is a listing record with top-level listing identity fields such as `id`, `url`, `title`, and `description`, plus nested objects for identifiers, pricing, property attributes, location, broker information, listing metadata, features, media, history, maps, source schemas, related listings, SEO metadata, source context, and `fingerprint`.

Recommended idempotency key: use `id` as the primary stable key, with `url` and `fingerprint` as secondary checks when syncing repeated runs. For deduplication or upserts, merge records by `id` first and compare `fingerprint` when you need to detect record-level changes. Stable identifiers make records easier to merge, deduplicate, and sync across repeated runs. The `fingerprint` field appears in the output and can be used as a compact change-detection value for repeated collection.

### Examples

Example: LandWatch listing record

```
{
  "id": 423149960,
  "url": "https://www.landwatch.com/bland-county-virginia-farms-and-ranches-for-sale/pid/423149960",
  "title": "4149 NE Suiter Rd Bastian, VA 24314",
  "description": "This is a must see home. It has everything from a 24 foot vaulted ceiling to your own private library. This home has some beautifully designed stain glass windows which allows radiant sunlight into the home. You will enjoy the view of the valley from your wrap around porch. For anyone who enjoys the outdoors and nature this property joins the National Forest. There is a metal building for projects and also a pole barn for horses or cattle. The property boarders Hunting Camp Creek. You will have to see this property to appreciate all that it has to offer.",
  "identifiers": {
    "landwatch_property_id": 423149960,
    "site_listing_id": 423149960,
    "listing_id": 23745464,
    "source_record_id": 23745464,
    "laf_property_id": 37779841,
    "account_id": 9722,
    "account_type": 40,
    "site_id": 1113,
    "parent_account_id": 0,
    "partner_id": 0,
    "parcel_id": "0|2822|74-A-10A|1",
    "mls_id": "99072"
  },
  "pricing": {
    "price": 605000,
    "price_text": "$605,000",
    "short_price": "$605K",
    "price_per_acre": 12648.97,
    "price_change_amount": -34000,
    "price_change_text": "-$34K",
    "price_change_date": "2025-12-15T08:53:06.267",
    "price_change_percentage": -0.0532,
    "sales_price": 0
  },
  "property": {
    "acres": 47.83,
    "acres_text": "47.83 acres",
    "beds": 3,
    "beds_text": "3 beds",
    "baths": 2,
    "baths_text": "2 baths",
    "half_baths": 1,
    "home_sqft": 2564,
    "home_sqft_text": "2,564 sqft",
    "types": [
      "Farms and Ranches",
      "House"
    ],
    "types_text": "Farms and Ranches, House",
    "type_code": 8195,
    "type_ids": [
      1,
      2,
      8192
    ],
    "ad_targeting_property_type": "farms and ranches",
    "has_house": true,
    "is_residence": true,
    "is_irrigated": false,
    "is_listhub_listing": false,
    "can_display": false,
    "should_redirect_detail_page": false,
    "link_infos": [
      {
        "label": "Farms and Ranches",
        "url": "https://www.landwatch.com/virginia-land-for-sale/bland-county/farms-ranches"
      },
      {
        "label": "House",
        "url": "https://www.landwatch.com/virginia-land-for-sale/bland-county/homes"
      }
    ]
  },
  "location": {
    "address": "4149 Suiter Rd",
    "city": "Bastian",
    "city_id": 1604,
    "city_url": "https://www.landwatch.com/virginia-land-for-sale/bastian",
    "county": "Bland County",
    "county_id": 5105,
    "county_fips": 51021,
    "county_laf_id": 1936,
    "county_url": "https://www.landwatch.com/virginia-land-for-sale/bland-county",
    "county_label": "County",
    "state": "Virginia",
    "state_code": "VA",
    "state_id": 51,
    "state_tax_rate": 0.8,
    "postal_code": "24314",
    "region_id": 222,
    "region": "Mountain Virginia",
    "ad_targeting_county_id": 5105,
    "coordinates": {
      "latitude": 37.116016,
      "longitude": -81.211655
    },
    "geocode_accuracy": 9,
    "cities_in_county": [
      "Bastian",
      "Bland",
      "Ceres",
      "Rocky Gap",
      "Grapefield",
      "Hicksville",
      "Byron",
      "Carnot",
      "Clear Fork",
      "Crandon",
      "Eagle Oak",
      "Effna",
      "Groseclose Store",
      "Holly Brook",
      "Kimberling",
      "Mechanicsburg",
      "Niday",
      "North Gap",
      "Point Pleasant",
      "Pumpkin Center",
      "Round Bottom",
      "Sharon Springs",
      "South Gap",
      "Stowersville",
      "Suiter"
    ],
    "contiguous_counties": [
      {
        "name": "Giles County",
        "state_code": "VA",
        "state_id": 51
      },
      {
        "name": "Mercer County",
        "state_code": "WV",
        "state_id": 54
      },
      {
        "name": "Pulaski County",
        "state_code": "VA",
        "state_id": 51
      },
      {
        "name": "Smyth County",
        "state_code": "VA",
        "state_id": 51
      },
      {
        "name": "Tazewell County",
        "state_code": "VA",
        "state_id": 51
      },
      {
        "name": "Wythe County",
        "state_code": "VA",
        "state_id": 51
      }
    ]
  },
  "broker": {
    "name": "Berkshire Hathaway HomeServices Mountain Sky Properties",
    "company": "Berkshire Hathaway HomeServices Mountain Sky Properties",
    "phone": "(276) 262-4013",
    "phones": {
      "preferred": "(276) 262-4013",
      "office": "(276) 500-0032",
      "cell": "(276) 500-0032",
      "fax": "(276) 228-8883",
      "tracking_for_account": "(276) 242-2938",
      "tracking_for_listing": "(276) 262-4013",
      "associated_account_id": 9722,
      "associated_listing_id": 23745464
    },
    "profile_url": "https://www.landwatch.com/profile/berkshire-hathaway-homeservices-mountain-sky-properties/9722",
    "website": "www.bhhsmountainsky.com",
    "city": "Wytheville",
    "state": "VA",
    "state_code": "VA",
    "postal_code": "24382",
    "account_id": 9722,
    "account_type": 40,
    "account_subtype_id": 4,
    "active": true,
    "alc_certified": false,
    "alc_advanced_certified": false,
    "is_seller": true,
    "expiration_date": "2027-03-05T00:00:00",
    "created_at": "2007-08-09T15:56:42.037",
    "portrait_document_id": 5550799688,
    "logo_document_id": 5550799693,
    "sms_notifications": false
  },
  "listing": {
    "listing_id": 23745464,
    "listing_date": "2025-06-04",
    "status": 1,
    "level": 30,
    "level_title": "Signature Partner",
    "upgrade_level_id": 0,
    "market_status": 1,
    "parcel_id": "0|2822|74-A-10A|1",
    "external_url": "https://keithgore.livesouthwestvirginia.com/property/305-99072-4149-ne-suiter-rd-VA-24314",
    "created_at": "2025-06-04T06:37:03.26",
    "updated_at": "December 15, 2025 at 8:53 AM",
    "auction": {
      "is_online_only": false
    }
  },
  "listing_flags": {
    "is_alc": false,
    "is_courtesy": false,
    "is_diamond": false,
    "is_first_free_listing": false,
    "is_gold": false,
    "is_liked": false,
    "is_platinum": false,
    "is_showcase": false
  },
  "features": {
    "has_custom_map": true,
    "has_exterior_matterport": false,
    "has_video": false,
    "has_virtual_tour": true,
    "amenities": [
      "Siding",
      "Ceiling Fans",
      "Forced Air",
      "Covered Porch(es)",
      "Storage Building",
      "Gas Logs",
      "Carpet",
      "Vinyl",
      "Wood Floor",
      "Ramp",
      "Central Air-Elec",
      "Central Heat- Elec",
      "Propane",
      "None",
      "Stain Glass Windows",
      "Vaulted Ceilings",
      "Built in Refrigerator/Freezer",
      "Dishwasher",
      "Granite/Granite Type Cntrtop",
      "Island",
      "Propane Gas",
      "No",
      "Fire/Smoke",
      "Library/Study",
      "Traditional",
      "Hunting",
      "Mountain",
      "Rural",
      "Acreage",
      "Creek",
      "Horses Permitted",
      "Pasture",
      "Some Trees",
      "Waterfront/Riverfront",
      "Hobby Farm",
      "Homestead",
      "Residential Single",
      "Farm/Ranch",
      "Single Family",
      "Agriculture",
      "Asphalt",
      "Hilly",
      "Rolling",
      "Sloped",
      "Varied"
    ],
    "amenity_groups": [
      {
        "name": "Housing",
        "categories": [
          {
            "name": "Construction",
            "amenities": [
              "Siding"
            ]
          },
          {
            "name": "Energy Efficiency",
            "amenities": [
              "Ceiling Fans",
              "Forced Air"
            ]
          },
          {
            "name": "Exterior Features",
            "amenities": [
              "Covered Porch(es)",
              "Storage Building"
            ]
          },
          {
            "name": "Fireplace Type",
            "amenities": [
              "Gas Logs"
            ]
          },
          {
            "name": "Flooring",
            "amenities": [
              "Carpet",
              "Vinyl",
              "Wood Floor"
            ]
          },
          {
            "name": "Handicap Amenities",
            "amenities": [
              "Ramp"
            ]
          },
          {
            "name": "Heating/Cooling",
            "amenities": [
              "Central Air-Elec",
              "Central Heat- Elec",
              "Forced Air",
              "Propane"
            ]
          },
          {
            "name": "HOA",
            "amenities": [
              "None"
            ]
          },
          {
            "name": "Interior Features",
            "amenities": [
              "Stain Glass Windows",
              "Vaulted Ceilings"
            ]
          },
          {
            "name": "Kitchen Equipment",
            "amenities": [
              "Built in Refrigerator/Freezer",
              "Dishwasher"
            ]
          },
          {
            "name": "Kitchen Other",
            "amenities": [
              "Granite/Granite Type Cntrtop",
              "Island"
            ]
          },
          {
            "name": "Other Utilities",
            "amenities": [
              "Propane Gas"
            ]
          },
          {
            "name": "Pool",
            "amenities": [
              "No"
            ]
          },
          {
            "name": "Security/Alarm Type",
            "amenities": [
              "Fire/Smoke"
            ]
          },
          {
            "name": "Specialty Rooms",
            "amenities": [
              "Library/Study"
            ]
          },
          {
            "name": "Style of House",
            "amenities": [
              "Traditional"
            ]
          }
        ]
      },
      {
        "name": "Land",
        "categories": [
          {
            "name": "Activities",
            "amenities": [
              "Hunting"
            ]
          },
          {
            "name": "Geography",
            "amenities": [
              "Mountain",
              "Rural"
            ]
          },
          {
            "name": "Lot Description",
            "amenities": [
              "Acreage",
              "Creek",
              "Horses Permitted",
              "Pasture",
              "Some Trees",
              "Waterfront/Riverfront"
            ]
          },
          {
            "name": "Present Use",
            "amenities": [
              "Hobby Farm",
              "Homestead",
              "Residential Single"
            ]
          },
          {
            "name": "Property Type",
            "amenities": [
              "Farm/Ranch",
              "Single Family"
            ]
          },
          {
            "name": "Proposed Use",
            "amenities": [
              "Agriculture",
              "Hobby Farm",
              "Homestead",
              "Residential Single"
            ]
          },
          {
            "name": "Street/Utilities",
            "amenities": [
              "Asphalt"
            ]
          },
          {
            "name": "Topography",
            "amenities": [
              "Hilly",
              "Rolling",
              "Sloped",
              "Varied"
            ]
          }
        ]
      }
    ]
  },
  "media": {
    "thumbnail_url": "https://assets.landwatch.com/resizedimages/394/0/h/80/5553603300",
    "thumbnail_document_id": "5553603300",
    "main_photo_document_id": "5553603300",
    "image_count": 17,
    "image_alt_text": "Land for sale in Bland County, Virginia",
    "image_document_ids": [
      5553603300,
      5553603303,
      5553603306,
      5553603308,
      5553603309,
      5553603310,
      5553603312,
      5553603313,
      5553603314,
      5553603315,
      5553603316,
      5553603317,
      5553603319,
      5553603320,
      5553603325,
      5553603330,
      5553603335
    ],
    "images": [
      {
        "document_id": 5553603300,
        "url": "https://assets.landwatch.com/resizedimages/394/0/h/80/5553603300",
        "image_id": 1026104839,
        "label": "bastian-1",
        "width": 2515,
        "height": 1677
      },
      {
        "document_id": 5553603303,
        "url": "https://assets.landwatch.com/resizedimages/394/0/h/80/5553603303",
        "image_id": 1026104842,
        "label": "bastian-4",
        "width": 4024,
        "height": 3018
      },
      {
        "document_id": 5553603306,
        "url": "https://assets.landwatch.com/resizedimages/394/0/h/80/5553603306",
        "image_id": 1026104845,
        "label": "bastian-17",
        "width": 3015,
        "height": 2010
      },
      {
        "document_id": 5553603308,
        "url": "https://assets.landwatch.com/resizedimages/394/0/h/80/5553603308",
        "image_id": 1026104847,
        "label": "bastian-32",
        "width": 3015,
        "height": 2010
      },
      {
        "document_id": 5553603309,
        "url": "https://assets.landwatch.com/resizedimages/394/0/h/80/5553603309",
        "image_id": 1026104848,
        "label": "bastian-24",
        "width": 3015,
        "height": 2010
      },
      {
        "document_id": 5553603310,
        "url": "https://assets.landwatch.com/resizedimages/394/0/h/80/5553603310",
        "image_id": 1026104850,
        "label": "bastian-38",
        "width": 3015,
        "height": 2010
      },
      {
        "document_id": 5553603312,
        "url": "https://assets.landwatch.com/resizedimages/394/0/h/80/5553603312",
        "image_id": 1026104851,
        "label": "bastian-41",
        "width": 3015,
        "height": 2010
      },
      {
        "document_id": 5553603313,
        "url": "https://assets.landwatch.com/resizedimages/394/0/h/80/5553603313",
        "image_id": 1026104852,
        "label": "bastian-46",
        "width": 3015,
        "height": 2010
      },
      {
        "document_id": 5553603314,
        "url": "https://assets.landwatch.com/resizedimages/394/0/h/80/5553603314",
        "image_id": 1026104853,
        "label": "bastian-55",
        "width": 3015,
        "height": 2010
      },
      {
        "document_id": 5553603315,
        "url": "https://assets.landwatch.com/resizedimages/394/0/h/80/5553603315",
        "image_id": 1026104854,
        "label": "bastian-57",
        "width": 3015,
        "height": 2010
      },
      {
        "document_id": 5553603316,
        "url": "https://assets.landwatch.com/resizedimages/394/0/h/80/5553603316",
        "image_id": 1026104855,
        "label": "bastian-62",
        "width": 3015,
        "height": 2010
      },
      {
        "document_id": 5553603317,
        "url": "https://assets.landwatch.com/resizedimages/394/0/h/80/5553603317",
        "image_id": 1026104856,
        "label": "bastian-65",
        "width": 3015,
        "height": 2010
      },
      {
        "document_id": 5553603319,
        "url": "https://assets.landwatch.com/resizedimages/394/0/h/80/5553603319",
        "image_id": 1026104858,
        "label": "bastian-70",
        "width": 3015,
        "height": 2010
      },
      {
        "document_id": 5553603320,
        "url": "https://assets.landwatch.com/resizedimages/394/0/h/80/5553603320",
        "image_id": 1026104859,
        "label": "bastian-100",
        "width": 3012,
        "height": 2008
      },
      {
        "document_id": 5553603325,
        "url": "https://assets.landwatch.com/resizedimages/394/0/h/80/5553603325",
        "image_id": 1026104864,
        "label": "bastian-103",
        "width": 3006,
        "height": 2004
      },
      {
        "document_id": 5553603330,
        "url": "https://assets.landwatch.com/resizedimages/394/0/h/80/5553603330",
        "image_id": 1026104869,
        "label": "bastian-147",
        "width": 4024,
        "height": 3018
      },
      {
        "document_id": 5553603335,
        "url": "https://assets.landwatch.com/resizedimages/394/0/h/80/5553603335",
        "image_id": 1026104874,
        "label": "bastian-127",
        "width": 4024,
        "height": 3018
      }
    ],
    "third_party_map_url": "id.land/ranching/maps/c4b9543dbaf834894cdd4ed46cc9c87b/embed/unbranded/",
    "matterport_virtual_tour": {
      "mediaTypeId": 2,
      "mediaId": "kRYypYjbyWq",
      "mediaUrl": "https://my.matterport.com/show/?m=kRYypYjbyWq",
      "mediaThumbnail": "https://my.matterport.com/api/v2/player/models/kRYypYjbyWq/thumb/",
      "mediaType": "Virtual Tour",
      "documentType": 90
    },
    "attachments": [
      {
        "caption": "4149_suiter_road_bastian_va_24314-3d.pdf",
        "docsPath": "/documents/5553603390/4149_suiter_road_bastian_va_24314-3d.pdf",
        "documentId": 5553603390,
        "documentTypeId": 20,
        "filename": "4149_suiter_road_bastian_va_24314-3d.pdf",
        "isExternal": false,
        "uploadedAccountFileId": 0,
        "uploadedPropertyFileId": 2715184,
        "url": "https://www.landwatch.com/api/documents/5553603390/4149_suiter_road_bastian_va_24314-3d.pdf"
      },
      {
        "caption": "4149_suiter_road_bastian_va_24314-2d.pdf",
        "docsPath": "/documents/5553603391/4149_suiter_road_bastian_va_24314-2d.pdf",
        "documentId": 5553603391,
        "documentTypeId": 20,
        "filename": "4149_suiter_road_bastian_va_24314-2d.pdf",
        "isExternal": false,
        "uploadedAccountFileId": 0,
        "uploadedPropertyFileId": 2715185,
        "url": "https://www.landwatch.com/api/documents/5553603391/4149_suiter_road_bastian_va_24314-2d.pdf"
      },
      {
        "caption": "4149 Suiter Rd - Aerial.pdf",
        "docsPath": "/documents/5553603392/4149SuiterRd-Aerial.pdf",
        "documentId": 5553603392,
        "documentTypeId": 20,
        "filename": "4149 Suiter Rd - Aerial.pdf",
        "isExternal": false,
        "uploadedAccountFileId": 0,
        "uploadedPropertyFileId": 2715186,
        "url": "https://www.landwatch.com/api/documents/5553603392/4149SuiterRd-Aerial.pdf"
      },
      {
        "caption": "Deed Laban.pdf",
        "docsPath": "/documents/5553603431/DeedLaban.pdf",
        "documentId": 5553603431,
        "documentTypeId": 20,
        "filename": "Deed Laban.pdf",
        "isExternal": false,
        "uploadedAccountFileId": 0,
        "uploadedPropertyFileId": 2715188,
        "url": "https://www.landwatch.com/api/documents/5553603431/DeedLaban.pdf"
      },
      {
        "caption": "summary of rights-2.pdf",
        "docsPath": "/documents/5553603543/summaryofrights-2.pdf",
        "documentId": 5553603543,
        "documentTypeId": 20,
        "filename": "summary of rights-2.pdf",
        "isExternal": false,
        "uploadedAccountFileId": 0,
        "uploadedPropertyFileId": 2715189,
        "url": "https://www.landwatch.com/api/documents/5553603543/summaryofrights-2.pdf"
      },
      {
        "caption": "Survey Laban.pdf",
        "docsPath": "/documents/5553603544/SurveyLaban.pdf",
        "documentId": 5553603544,
        "documentTypeId": 20,
        "filename": "Survey Laban.pdf",
        "isExternal": false,
        "uploadedAccountFileId": 0,
        "uploadedPropertyFileId": 2715190,
        "url": "https://www.landwatch.com/api/documents/5553603544/SurveyLaban.pdf"
      }
    ]
  },
  "history": {
    "events": [
      {
        "date": "2025-12-15T00:00:00",
        "price": 605000,
        "price_delta": -5.32,
        "acres": 47.83,
        "acres_delta": 0,
        "event_title": "Price"
      },
      {
        "date": "2025-07-30T00:00:00",
        "price": 639000,
        "price_delta": -5.33,
        "acres": 47.83,
        "acres_delta": 0,
        "event_title": "Price"
      },
      {
        "date": "2025-06-04T00:00:00",
        "price": 675000,
        "acres": 47.83,
        "event_title": "Listed for Sale"
      }
    ]
  },
  "map": {
    "static_map_url": "https://maps.googleapis.com/maps/api/staticmap?key=AIzaSyCvtvmtxTW9V3N4SW7-QvFPV5k1O6pmkds&channel=land&size=100x100&maptype=roadmap&center=37.116016%2c-81.211655&markers=color:blue%7C37.116016%2c-81.211655&zoom=10&signature=hQqB4e1IEWToNYoYN7_bhboJ_Bo=",
    "overlays": [
      {
        "id": 166457936,
        "property_id": 23745464,
        "uuid": "7A185B7B-D3FB-49ED-851E-22317DA236B3",
        "name": "Custom Land Default Marker",
        "geometry": "37.116016,-81.211655",
        "main_parcel": false,
        "overlay_type_id": 1,
        "type": "custom"
      }
    ]
  },
  "source_schemas": {
    "schema_data": {
      "@context": "http://schema.org",
      "@type": "SingleFamilyResidence",
      "name": "4149 Suiter Rd, Bastian, VA, 24314",
      "description": "This is a must see home. It has everything from a 24 foot vaulted ceiling to your own private librar",
      "address": {
        "@type": "PostalAddress",
        "streetAddress": "4149 Suiter Rd",
        "addressLocality": "Bastian",
        "addressRegion": "VA",
        "postalCode": "24314"
      }
    },
    "breadcrumb": {
      "@context": "https://schema.org",
      "@type": "BreadcrumbList",
      "itemListElement": [
        {
          "@type": "ListItem",
          "position": 1,
          "item": {
            "@id": "https://www.landwatch.com",
            "name": "Home"
          }
        },
        {
          "@type": "ListItem",
          "position": 2,
          "item": {
            "@id": "https://www.landwatch.com/land",
            "name": "United States Land for Sale"
          }
        },
        {
          "@type": "ListItem",
          "position": 3,
          "item": {
            "@id": "https://www.landwatch.com/virginia-land-for-sale",
            "name": "Virginia Land for Sale"
          }
        },
        {
          "@type": "ListItem",
          "position": 4,
          "item": {
            "@id": "https://www.landwatch.com/virginia-land-for-sale/mountain-region",
            "name": "Mountain Virginia Land for Sale"
          }
        },
        {
          "@type": "ListItem",
          "position": 5,
          "item": {
            "@id": "https://www.landwatch.com/virginia-land-for-sale/bland-county",
            "name": "Bland County Virginia Land for Sale"
          }
        },
        {
          "@type": "ListItem",
          "position": 6,
          "item": {
            "@id": "https://www.landwatch.com/virginia-land-for-sale/bastian",
            "name": "Bastian Virginia Land for Sale"
          }
        },
        {
          "@type": "ListItem",
          "position": 7,
          "item": {
            "@id": "https://www.landwatch.com/bland-county-virginia-farms-and-ranches-for-sale/pid/423149960",
            "name": "47.83 Acres - Bastian Virginia Land for Sale"
          }
        }
      ]
    },
    "listing": {
      "@context": "https://schema.org",
      "@type": [
        "RealEstateListing",
        "Product"
      ],
      "url": "https://www.landwatch.com/bland-county-virginia-farms-and-ranches-for-sale/pid/423149960",
      "@id": "https://www.landwatch.com/bland-county-virginia-farms-and-ranches-for-sale/pid/423149960#listingdetailpage",
      "description": "This is a must see home. It has everything from a 24 foot vaulted ceiling to your own private library. This home has some beautifully designed stain glass windows which allows radiant sunlight into the home. You will enjoy the view of the valley from your wrap around porch. For anyone who enjoys the outdoors and nature this property joins the National Forest. There is a metal building for projects and also a pole barn for horses or cattle. The property boarders Hunting Camp Creek. You will have to see this property to appreciate all that it has to offer.",
      "datePosted": "2025-06-04",
      "image": {
        "@type": "ImageObject",
        "url": "https://assets.landwatch.com/resizedimages/394/0/h/80/1-5553603300"
      },
      "name": "Bastian, Bland County, VA Farms and Ranches, House for sale Property ID: 423149960",
      "lastReviewed": "December 15, 2025 at 8:53 AM",
      "mainEntity": {
        "@type": "Residence",
        "@id": "https://www.landwatch.com/bland-county-virginia-farms-and-ranches-for-sale/pid/423149960#residence",
        "name": "Bastian, Bland County, VA Farms and Ranches, House for sale Property ID: 423149960",
        "address": {
          "@type": "PostalAddress",
          "streetAddress": "4149 Suiter Rd",
          "addressLocality": "Bastian",
          "addressRegion": "VA",
          "postalCode": "24314",
          "addressCountry": "US"
        },
        "image": {
          "@type": "ImageObject",
          "url": "https://assets.landwatch.com/resizedimages/394/0/h/80/1-5553603300"
        },
        "additionalProperty": [
          {
            "@type": "PropertyValue",
            "name": "Acreage",
            "value": "47.83 acres"
          },
          {
            "@type": "PropertyValue",
            "name": "Construction",
            "value": "Siding"
          },
          {
            "@type": "PropertyValue",
            "name": "Energy Efficiency",
            "value": [
              "Ceiling Fans",
              "Forced Air"
            ]
          },
          {
            "@type": "PropertyValue",
            "name": "Exterior Features",
            "value": [
              "Covered Porch(es)",
              "Storage Building"
            ]
          },
          {
            "@type": "PropertyValue",
            "name": "Fireplace Type",
            "value": "Gas Logs"
          },
          {
            "@type": "PropertyValue",
            "name": "Flooring",
            "value": [
              "Carpet",
              "Vinyl",
              "Wood Floor"
            ]
          },
          {
            "@type": "PropertyValue",
            "name": "Handicap Amenities",
            "value": "Ramp"
          },
          {
            "@type": "PropertyValue",
            "name": "Heating/Cooling",
            "value": [
              "Central Air-Elec",
              "Central Heat- Elec",
              "Forced Air",
              "Propane"
            ]
          },
          {
            "@type": "PropertyValue",
            "name": "HOA",
            "value": "None"
          },
          {
            "@type": "PropertyValue",
            "name": "Interior Features",
            "value": [
              "Stain Glass Windows",
              "Vaulted Ceilings"
            ]
          },
          {
            "@type": "PropertyValue",
            "name": "Kitchen Equipment",
            "value": [
              "Built in Refrigerator/Freezer",
              "Dishwasher"
            ]
          },
          {
            "@type": "PropertyValue",
            "name": "Kitchen Other",
            "value": [
              "Granite/Granite Type Cntrtop",
              "Island"
            ]
          },
          {
            "@type": "PropertyValue",
            "name": "Other Utilities",
            "value": "Propane Gas"
          },
          {
            "@type": "PropertyValue",
            "name": "Pool",
            "value": "No"
          },
          {
            "@type": "PropertyValue",
            "name": "Security/Alarm Type",
            "value": "Fire/Smoke"
          },
          {
            "@type": "PropertyValue",
            "name": "Specialty Rooms",
            "value": "Library/Study"
          },
          {
            "@type": "PropertyValue",
            "name": "Style of House",
            "value": "Traditional"
          },
          {
            "@type": "PropertyValue",
            "name": "Activities",
            "value": "Hunting"
          },
          {
            "@type": "PropertyValue",
            "name": "Geography",
            "value": [
              "Mountain",
              "Rural"
            ]
          },
          {
            "@type": "PropertyValue",
            "name": "Lot Description",
            "value": [
              "Acreage",
              "Creek",
              "Horses Permitted",
              "Pasture",
              "Some Trees",
              "Waterfront/Riverfront"
            ]
          },
          {
            "@type": "PropertyValue",
            "name": "Present Use",
            "value": [
              "Hobby Farm",
              "Homestead",
              "Residential Single"
            ]
          },
          {
            "@type": "PropertyValue",
            "name": "Property Type",
            "value": [
              "Farm/Ranch",
              "Single Family"
            ]
          },
          {
            "@type": "PropertyValue",
            "name": "Proposed Use",
            "value": [
              "Agriculture",
              "Hobby Farm",
              "Homestead",
              "Residential Single"
            ]
          },
          {
            "@type": "PropertyValue",
            "name": "Street/Utilities",
            "value": "Asphalt"
          },
          {
            "@type": "PropertyValue",
            "name": "Topography",
            "value": [
              "Hilly",
              "Rolling",
              "Sloped",
              "Varied"
            ]
          }
        ]
      },
      "offers": {
        "@type": "Offer",
        "@id": "https://www.landwatch.com/bland-county-virginia-farms-and-ranches-for-sale/pid/423149960#offer",
        "price": 605000,
        "priceCurrency": "USD",
        "availability": "https://schema.org/InStock",
        "itemOffered": {
          "@type": "Residence",
          "@id": "https://www.landwatch.com/bland-county-virginia-farms-and-ranches-for-sale/pid/423149960#residence"
        },
        "seller": {
          "@type": "RealEstateAgent",
          "@id": "https://www.landwatch.com/profile/berkshire-hathaway-homeservices-mountain-sky-properties/9722#agentbroker",
          "name": "Berkshire Hathaway HomeServices Mountain Sky Properties",
          "url": "https://www.landwatch.com/profile/berkshire-hathaway-homeservices-mountain-sky-properties/9722",
          "image": {
            "@type": "ImageObject",
            "url": "https://assets.landwatch.com/resizedimages/150/150/l/80/w/1-5550799688"
          },
          "telephone": "(276) 262-4013",
          "address": {
            "@type": "PostalAddress",
            "streetAddress": "305 N. 4th Street, Suite B",
            "addressLocality": "Wytheville",
            "addressRegion": "VA",
            "postalCode": "24382",
            "addressCountry": "US"
          },
          "memberOf": {
            "@type": "Organization",
            "name": "Berkshire Hathaway HomeServices Mountain Sky Properties",
            "address": {
              "@type": "PostalAddress",
              "streetAddress": "305 N. 4th Street",
              "addressLocality": "Wytheville",
              "addressRegion": "VA",
              "postalCode": "24382",
              "addressCountry": "US"
            }
          },
          "areaServed": [
            {
              "@type": "State",
              "name": "Virginia"
            }
          ]
        },
        "offeredBy": {
          "@id": "https://www.landwatch.com/profile/berkshire-hathaway-homeservices-mountain-sky-properties/9722#agentbroker"
        }
      }
    },
    "product": {
      "@context": "https://schema.org",
      "@type": "Product",
      "url": "https://www.landwatch.com/bland-county-virginia-farms-and-ranches-for-sale/pid/423149960",
      "image": "https://assets.landwatch.com/resizedimages/394/0/h/80/1-5553603300",
      "name": "Bastian, Bland County, VA Farms and Ranches, House for sale Property ID: 423149960",
      "offers": {
        "@type": "Offer",
        "price": 605000,
        "priceCurrency": "USD",
        "availability": "https://schema.org/InStock",
        "url": "https://www.landwatch.com/bland-county-virginia-farms-and-ranches-for-sale/pid/423149960"
      },
      "Brand": "LandWatch",
      "Sku": "423149960"
    },
    "residence_and_geo": {
      "@context": "https://schema.org",
      "@type": "SingleFamilyResidence",
      "url": "/bland-county-virginia-farms-and-ranches-for-sale/pid/423149960",
      "description": "This is a must see home. It has everything from a 24 foot vaulted ceiling to your own private library. This home has some beautifully designed stain glass windows which allows radiant sunlight into the home. You will enjoy the view of the valley from your wrap around porch. For anyone who enjoys the outdoors and nature this property joins the National Forest. There is a metal building for projects and also a pole barn for horses or cattle. The property boarders Hunting Camp Creek. You will have to see this property to appreciate all that it has to offer.",
      "name": "47.83 acres in Bland County, Virginia",
      "image": "https://assets.landwatch.com/resizedimages/394/0/h/80/1-5553603300",
      "hasMap": "https://www.google.com/maps/place/37.116016,-81.211655",
      "geo": {
        "@type": "GeoCoordinates",
        "latitude": 37.116016,
        "longitude": -81.211655
      },
      "address": {
        "@type": "PostalAddress",
        "streetAddress": "4149 Suiter Rd",
        "addressLocality": "Bastian",
        "addressRegion": "VA",
        "postalCode": "24314"
      }
    }
  },
  "related_listings": {
    "other": [
      {
        "id": 423166305,
        "url": "https://www.landwatch.com/russell-county-virginia-farms-and-ranches-for-sale/pid/423166305",
        "title": "123 Luttie Banner Rd Castlewood, VA 24224",
        "description": "This 224 acre property will be sold for the first time since the days of Colonial America. Originally granted by the King of England to the Banner family, this land has remained in continuous ownership for over 300 years a true testament to its legac",
        "identifiers": {
          "source_record_id": 23761809,
          "landwatch_property_id": 423166305,
          "site_listing_id": 423166305,
          "laf_property_id": 37796186,
          "account_id": 9722
        },
        "pricing": {
          "price": 2500000,
          "price_text": "$2,500,000",
          "short_price": "$2.5M",
          "price_per_acre": 11160.71,
          "price_change_amount": 0,
          "price_change_percentage": 0
        },
        "property": {
          "acres": 224,
          "acres_text": "224 acres",
          "types": [
            "Farms and Ranches",
            "Riverfront Property",
            "Waterfront Property",
            "House"
          ],
          "types_text": "Farms and Ranches, Riverfront Property, Waterfront Property, House"
        },
        "location": {
          "address": "123 Luttie Banner Dr",
          "city": "Castlewood",
          "county": "Russell County",
          "state": "Virginia",
          "state_code": "VA",
          "postal_code": "24224",
          "coordinates": {
            "latitude": 36.89384078979492,
            "longitude": -82.27678680419922
          }
        },
        "broker": {
          "name": "Berkshire Hathaway HomeServices Mountain Sky Properties",
          "company": "Berkshire Hathaway HomeServices Mountain Sky Properties",
          "profile_url": "https://www.landwatch.com/profile/berkshire-hathaway-homeservices-mountain-sky-properties/9722"
        },
        "media": {
          "image_count": 17,
          "thumbnail_document_id": 5555678421,
          "thumbnail_url": "https://assets.landwatch.com/resizedimages/394/0/h/80/5555678421"
        },
        "listing": {
          "status": 1,
          "level": 30,
          "level_title": "Signature Partner",
          "updated_at": "2025-11-19T10:18:00.02"
        }
      },
      {
        "id": 425298612,
        "url": "https://www.landwatch.com/wythe-county-virginia-farms-and-ranches-for-sale/pid/425298612",
        "title": "4722 Ivanhoe Rd Ivanhoe, VA 24350",
        "description": "Take a look at this charming Cottage on 3+ Acres perfect for the horse & outdoor enthusiast! Situated on over 3 acres of beautiful mixed pasture and woodlands, this inviting cottage-style home offers the perfect blend of comfort and outdoor recreatio",
        "identifiers": {
          "source_record_id": 25894116,
          "landwatch_property_id": 425298612,
          "site_listing_id": 425298612,
          "laf_property_id": 39928493,
          "account_id": 9722
        },
        "pricing": {
          "price": 176000,
          "price_text": "$176,000",
          "short_price": "$176K",
          "price_per_acre": 53658.54,
          "price_change_amount": 0,
          "price_change_percentage": 0
        },
        "property": {
          "acres": 3.28,
          "acres_text": "3.28 acres",
          "types": [
            "Farms and Ranches",
            "House"
          ],
          "types_text": "Farms and Ranches, House"
        },
        "location": {
          "address": "4722 Ivanhoe Rd",
          "city": "Ivanhoe",
          "county": "Wythe County",
          "state": "Virginia",
          "state_code": "VA",
          "postal_code": "24350",
          "coordinates": {
            "latitude": 36.838302,
            "longitude": -80.958545
          }
        },
        "broker": {
          "name": "Berkshire Hathaway HomeServices Mountain Sky Properties",
          "company": "Berkshire Hathaway HomeServices Mountain Sky Properties",
          "profile_url": "https://www.landwatch.com/profile/berkshire-hathaway-homeservices-mountain-sky-properties/9722"
        },
        "media": {
          "image_count": 75,
          "thumbnail_document_id": 5921674980,
          "thumbnail_url": "https://assets.landwatch.com/resizedimages/394/0/h/80/5921674980"
        },
        "listing": {
          "status": 1,
          "level": 30,
          "level_title": "Signature Partner",
          "updated_at": "2026-01-09T11:53:46.263"
        }
      },
      {
        "id": 426487570,
        "url": "https://www.landwatch.com/mecklenburg-county-virginia-farms-and-ranches-for-sale/pid/426487570",
        "title": "2842 Goodes Ferry Rd South Hill, VA 23970",
        "description": "Set beyond a tree-lined drive on over 20 acres of beautiful pastureland, this exceptional all-brick Colonial estate offers luxury living w/ remarkable privacy & functionality. A paved circular drive w/ flagpole & streetside lighting welcomes you to t",
        "identifiers": {
          "source_record_id": 27083075,
          "landwatch_property_id": 426487570,
          "site_listing_id": 426487570,
          "laf_property_id": 41117451,
          "account_id": 9722
        },
        "pricing": {
          "price": 1100000,
          "price_text": "$1,100,000",
          "short_price": "$1.1M",
          "price_per_acre": 52961,
          "price_change_amount": 0,
          "price_change_percentage": 0
        },
        "property": {
          "acres": 20.77,
          "acres_text": "20.8 acres",
          "types": [
            "Farms and Ranches",
            "House"
          ],
          "types_text": "Farms and Ranches, House"
        },
        "location": {
          "address": "2842 Goodes Ferry Road",
          "city": "South Hill",
          "county": "Mecklenburg County",
          "state": "Virginia",
          "state_code": "VA",
          "postal_code": "23970",
          "coordinates": {
            "latitude": 36.69645690917969,
            "longitude": -78.15299224853516
          }
        },
        "broker": {
          "name": "Berkshire Hathaway HomeServices Mountain Sky Properties",
          "company": "Berkshire Hathaway HomeServices Mountain Sky Properties",
          "profile_url": "https://www.landwatch.com/profile/berkshire-hathaway-homeservices-mountain-sky-properties/9722"
        },
        "media": {
          "image_count": 241,
          "thumbnail_document_id": 6140705868,
          "thumbnail_url": "https://assets.landwatch.com/resizedimages/394/0/h/80/6140705868"
        },
        "listing": {
          "status": 1,
          "level": 30,
          "level_title": "Signature Partner",
          "updated_at": "2026-04-26T13:25:19.123"
        }
      },
      {
        "id": 426490158,
        "url": "https://www.landwatch.com/grayson-county-virginia-farms-and-ranches-for-sale/pid/426490158",
        "title": "434 Glenwood Rd. Troutdale, VA 24378",
        "description": "This rare, turnkey property blends modern comfort with peaceful country living. The fully remodeled and furnished historic farmhouse features high-speed fiber optic internet, ideal for remote work and entertainment. A stunning spring-fed pond is stoc",
        "identifiers": {
          "source_record_id": 27085663,
          "landwatch_property_id": 426490158,
          "site_listing_id": 426490158,
          "laf_property_id": 41120039,
          "account_id": 9722
        },
        "pricing": {
          "price": 675000,
          "price_text": "$675,000",
          "short_price": "$675K",
          "price_per_acre": 56250,
          "price_change_amount": 0,
          "price_change_percentage": 0
        },
        "property": {
          "acres": 12,
          "acres_text": "12 acres",
          "types": [
            "Farms and Ranches",
            "House"
          ],
          "types_text": "Farms and Ranches, House"
        },
        "location": {
          "address": "434 Glenwood Road",
          "city": "Troutdale",
          "county": "Grayson County",
          "state": "Virginia",
          "state_code": "VA",
          "postal_code": "24378",
          "coordinates": {
            "latitude": 36.71719741821289,
            "longitude": -81.34957885742188
          }
        },
        "broker": {
          "name": "Berkshire Hathaway HomeServices Mountain Sky Properties",
          "company": "Berkshire Hathaway HomeServices Mountain Sky Properties",
          "profile_url": "https://www.landwatch.com/profile/berkshire-hathaway-homeservices-mountain-sky-properties/9722"
        },
        "media": {
          "image_count": 117,
          "thumbnail_document_id": 6144160179,
          "thumbnail_url": "https://assets.landwatch.com/resizedimages/394/0/h/80/6144160179"
        },
        "listing": {
          "status": 1,
          "level": 30,
          "level_title": "Signature Partner",
          "updated_at": "2026-04-26T13:25:03.77"
        }
      }
    ]
  },
  "seo": {
    "title": "4149 Suiter Rd, Bastian, VA 24314 | MLS: 99072 | LandWatch",
    "description": "View 47.83 acres priced at $605,000 in Bastian, Bland County, VA. Browse photos, see details, and contact the seller."
  },
  "source_context": {
    "source_url": "https://www.landwatch.com/api/property/search/1113/land/price-600001-608000",
    "detail_api_url": "https://www.landwatch.com/api/property/423149960",
    "seed_id": "3d56106dbde3",
    "seed_type": "url",
    "seed_value": "https://www.landwatch.com/api/property/search/1113/land",
    "page_index": 0,
    "domain": "www.landwatch.com",
    "breadcrumbs": [
      {
        "path": "/",
        "location_text": "Home"
      },
      {
        "path": "/land",
        "location_text": "United States"
      },
      {
        "path": "/virginia-land-for-sale",
        "location_text": "Virginia"
      },
      {
        "path": "/virginia-land-for-sale/mountain-region",
        "location_text": "Mountain Virginia"
      },
      {
        "path": "/virginia-land-for-sale/bland-county",
        "location_text": "Bland County"
      },
      {
        "path": "/virginia-land-for-sale/bastian",
        "location_text": "Bastian"
      },
      {
        "path": "/bland-county-virginia-farms-and-ranches-for-sale/pid/423149960",
        "location_text": "47.83 Acres - Bastian Virginia"
      }
    ],
    "finance_center": {
      "active": true,
      "checkbox_default_state": false,
      "checkbox_label": "Click here to learn more about financing this property with Farm Credit of the Virginias",
      "finance_id": 40,
      "logo_document_id": "5209604069",
      "logo_url_part": "40.jpg",
      "map_trackable_link": "https://www.land.com/financing/?fcid=40",
      "min_acres": 0,
      "min_price": 0,
      "name": "Farm Credit of the Virginias",
      "query_string": "state=VA",
      "show_on_laf": true,
      "show_on_loa": true,
      "show_on_lw": true,
      "url_part": "FarmCreditVirginias"
    }
  },
  "fingerprint": "903031fcb395f6b08ebd"
}
```

## Field Reference

### LandWatch listing record

**id** *(integer, required)*: LandWatch property identifier and recommended primary idempotency key.

**url** *(string, required)*: Public listing URL.

**title** *(string, required)*: Listing title or address-style display title.

**description** *(string, optional)*: Public listing description.

**identifiers.landwatch_property_id / site_listing_id / listing_id / source_record_id / laf_property_id** *(integer, optional)*: Source listing and property identifiers useful for matching records.

**identifiers.account_id / account_type / site_id / parent_account_id / partner_id** *(integer, optional)*: Public account and site identifiers when available.

**identifiers.parcel_id / mls_id** *(string, optional)*: Parcel and MLS identifiers when supplied by the listing.

**pricing.price / sales_price** *(number, optional)*: Listing price and sales price in USD when available.

**pricing.price_text / short_price** *(string, optional)*: Human-readable price labels.

**pricing.price_per_acre** *(number, optional)*: Price per acre in USD.

**pricing.price_change_amount / price_change_text / price_change_date / price_change_percentage** *(number or string, optional)*: Recent price-change values when provided.

**property.acres / acres_text** *(number or string, optional)*: Parcel acreage.

**property.beds / beds_text / baths / baths_text / half_baths** *(number or string, optional)*: Residential bedroom and bathroom attributes.

**property.home_sqft / home_sqft_text** *(number or string, optional)*: Building size in square feet.

**property.types / types_text / type_code / type_ids / ad_targeting_property_type** *(array, string, or number, optional)*: Property category labels and category identifiers.

**property.has_house / is_residence / is_irrigated / is_listhub_listing / can_display / should_redirect_detail_page** *(boolean, optional)*: Listing-level property flags.

**property.link_infos[].label / url** *(string, optional)*: Public category links related to the listing.

**location.address / city / county / state / state_code / postal_code / region** *(string, optional)*: Postal and regional location fields.

**location.city_id / county_id / county_fips / county_laf_id / state_id / region_id / ad_targeting_county_id** *(integer, optional)*: Location identifiers when available.

**location.city_url / county_url / county_label** *(string, optional)*: Public location links and labels.

**location.state_tax_rate / geocode_accuracy** *(number, optional)*: Region-level tax and geocoding indicators when available.

**location.coordinates.latitude / longitude** *(number, optional)*: Listing coordinates.

**location.cities_in_county[]** *(array of strings, optional)*: Public city names associated with the county.

**location.contiguous_counties[].name / state_code / state_id** *(string or integer, optional)*: Nearby county references.

**broker.name / company / phone / profile_url / website / city / state / state_code / postal_code** *(string, optional)*: Broker or company contact and profile fields.

**broker.phones.preferred / office / cell / fax / tracking_for_account / tracking_for_listing** *(string, optional)*: Phone values exposed for the listing or account.

**broker.phones.associated_account_id / associated_listing_id** *(integer, optional)*: Broker phone association identifiers.

**broker.account_id / account_type / account_subtype_id** *(integer, optional)*: Broker account identifiers when available.

**broker.active / alc_certified / alc_advanced_certified / is_seller / sms_notifications** *(boolean, optional)*: Broker account flags.

**broker.expiration_date / created_at** *(string, optional)*: Public account lifecycle timestamps when available.

**broker.portrait_document_id / logo_document_id** *(integer, optional)*: Media document identifiers for broker profile assets.

**listing.listing_id / status / level / upgrade_level_id / market_status** *(integer, optional)*: Listing status and placement metadata.

**listing.listing_date / created_at / updated_at / external_url / parcel_id** *(string, optional)*: Listing dates, update label, public external link, and parcel identifier.

**listing.auction.is_online_only** *(boolean, optional)*: Auction-specific listing flag when applicable.

**listing_flags.is_alc / is_courtesy / is_diamond / is_first_free_listing / is_gold / is_liked / is_platinum / is_showcase** *(boolean, optional)*: Public listing badge and placement flags.

**features.has_custom_map / has_exterior_matterport / has_video / has_virtual_tour** *(boolean, optional)*: Media and feature availability flags.

**features.amenities[]** *(array of strings, optional)*: Listing amenity labels.

**features.amenity_groups[].name** *(string, optional)*: Amenity group name.

**features.amenity_groups[].categories[].name / amenities[]** *(string or array, optional)*: Amenity category names and values.

**media.thumbnail_url / thumbnail_document_id / main_photo_document_id / image_alt_text / third_party_map_url** *(string, optional)*: Primary media references.

**media.image_count** *(integer, optional)*: Number of images reported for the listing.

**media.image_document_ids[]** *(array of integers, optional)*: Image document identifiers.

**media.images[].document_id / url / image_id / label / width / height** *(string or number, optional)*: Detailed image records.

**media.matterport_virtual_tour.mediaTypeId / mediaId / mediaUrl / mediaThumbnail / mediaType / documentType** *(string or number, optional)*: Virtual tour metadata when present.

**media.attachments[].caption / docsPath / documentId / documentTypeId / filename / isExternal / uploadedAccountFileId / uploadedPropertyFileId / url** *(string, number, or boolean, optional)*: Public attachment metadata.

**history.events[].date / price / price_delta / acres / acres_delta / event_title** *(string or number, optional)*: Listing history events such as listing and price changes.

**map.static_map_url** *(string, optional)*: Static map image URL when available.

**map.overlays[].id / property_id / uuid / name / geometry / main_parcel / overlay_type_id / type** *(string, number, or boolean, optional)*: Map overlay metadata.

**source_schemas.schema_data** *(object, optional)*: Structured listing metadata exposed by the source page.

**source_schemas.schema_data.address.streetAddress / addressLocality / addressRegion / postalCode** *(string, optional)*: Postal address fields in source schema data.

**source_schemas.breadcrumb.itemListElement[]** *(array, optional)*: Breadcrumb schema entries with position, item identifier, and display name.

**source_schemas.listing** *(object, optional)*: Source-provided real estate listing schema, including description, date, image, residence, offer, seller, and area-served values.

**source_schemas.product** *(object, optional)*: Source-provided product schema with URL, image, name, offer, brand, and SKU.

**source_schemas.residence_and_geo** *(object, optional)*: Source-provided residence and geolocation schema.

**related_listings.other[]** *(array, optional)*: Related listing summaries when available.

**related_listings.other[].id / url / title / description** *(string or integer, optional)*: Related listing identity and summary fields.

**related_listings.other[].identifiers** *(object, optional)*: Related listing identifiers.

**related_listings.other[].pricing** *(object, optional)*: Related listing price, price text, short price, price per acre, and price-change values.

**related_listings.other[].property** *(object, optional)*: Related listing acreage and property type values.

**related_listings.other[].location** *(object, optional)*: Related listing address, city, county, state, postal code, and coordinates.

**related_listings.other[].broker** *(object, optional)*: Related listing broker name, company, and profile URL.

**related_listings.other[].media** *(object, optional)*: Related listing image count, thumbnail document identifier, and thumbnail URL.

**related_listings.other[].listing** *(object, optional)*: Related listing status, level, level title, and update timestamp.

**seo.title / description** *(string, optional)*: Public SEO title and description associated with the listing.

**source_context.source_url / detail_api_url / seed_id / seed_type / seed_value / domain** *(string, optional)*: Source-context values included with the record when available.

**source_context.page_index** *(integer, optional)*: Page index associated with the collected record.

**source_context.breadcrumbs[].path / location_text** *(string, optional)*: Breadcrumb context for the record.

**source_context.finance_center.active / checkbox_default_state / show_on_laf / show_on_loa / show_on_lw** *(boolean, optional)*: Finance-center visibility flags when present.

**source_context.finance_center.checkbox_label / logo_document_id / logo_url_part / map_trackable_link / name / query_string / url_part** *(string, optional)*: Finance-center labels and public references.

**source_context.finance_center.finance_id / min_acres / min_price** *(number, optional)*: Finance-center numeric values.

**fingerprint** *(string, optional)*: Compact stable fingerprint useful for change detection across repeated runs.

## Data Quality, Guarantees, And Handling

- **Structured records:** results are normalized into predictable JSON objects for downstream use.
- **Best-effort extraction:** fields may vary by region, session, availability, account visibility, listing type, source data quality, or UI experiments.
- **Optional fields:** null-check optional values in downstream code, especially broker, media, feature, history, schema, and related-listing fields.
- **Deduplication:** use `id` as the strongest stable key available from the output, with `url` and `fingerprint` as secondary checks.
- **Freshness:** results reflect the publicly available data at run time.
- **Repeated runs:** use the recommended idempotency key when syncing data into warehouses, CRMs, or search indexes.

## Tips For Best Results

- Start with a small `limit` to validate the output shape before scaling up.
- Use one geography, property category, or market segment per run when you need cleaner segmentation.
- Leave optional filters empty when the goal is broad discovery.
- Add filters gradually to understand how each field changes coverage.
- Use `publication_date`, `price_reduction_period`, and `sort_by` for monitoring newly published or recently changed listings.
- Schedule recurring runs for monitoring workflows instead of relying on manual one-off collection.
- Store records by `id` and compare `fingerprint` when tracking changes over time.

## How to Run on Apify

1. Open the Actor in Apify Console.
2. Configure the available input fields for the target scope.
3. Set the maximum number of outputs to collect with `limit`.
4. Click **Start** and wait for the run to finish.
5. Inspect the dataset preview.
6. Download results in JSON, CSV, Excel, or another supported format.

## Scheduling & Automation

### Scheduling

**Automated Data Collection**

Schedule recurring runs to keep LandWatch listing datasets fresh for monitoring, reporting, and enrichment workflows. Use the same validated input configuration for consistent collection over time.

- Navigate to **Schedules** in Apify Console
- Create a new schedule, such as daily, weekly, or custom cron
- Configure input parameters
- Enable notifications for run completion
- Add webhooks for automated processing

### Integration Options

- **CRM enrichment:** sync public listing, broker, location, acreage, and pricing attributes into account or lead records.
- **BI dashboards:** monitor pricing, availability, property-type movement, acreage bands, and geographic coverage over time.
- **Data warehouses:** retain historical listing snapshots for market intelligence, trend analysis, and operational reporting.
- **Webhooks:** trigger validation, notification, or ingestion workflows after each completed run.
- **Google Sheets or Airtable:** review smaller datasets, qualify leads, and coordinate lightweight market research workflows.
- **Alerts:** notify teams when new, recently changed, or price-reduced listings match a saved scope.

## Export Formats And Downstream Use

Apify datasets can be exported or consumed by downstream systems for analysis, review, and operational use.

- **JSON:** for APIs, applications, and data pipelines
- **CSV or Excel:** for spreadsheet workflows and manual review
- **API access:** for automated ingestion into internal systems
- **BI and warehouses:** for reporting, dashboards, and historical analysis

## Performance

Estimated run times:

- **Small runs (< 1,000 outputs):** ~3-5 minutes
- **Medium runs (1,000-5,000 outputs):** ~5-15 minutes
- **Large runs (5,000+ outputs):** ~15-30 minutes

Execution time varies based on filters, result volume, and how much information is returned per record. Highly filtered runs can finish faster, while broad discovery or detail-rich records may take longer.

## Limitations

- Availability depends on what [LandWatch](https://www.landwatch.com) publicly exposes at run time.
- Some optional fields may be missing on sparse listings, regional pages, older records, or records with limited broker or media information.
- Very broad searches may take longer or require higher limits to collect the desired volume.
- Target-side changes can affect field availability, labels, or naming.
- Regional, account, or availability differences may change which records are visible for the same input scope.
- Listing freshness reflects the public source state at the time the actor runs.

## Troubleshooting

- **No results returned:** check filters, location or category spelling, and whether LandWatch has matching public records for the selected scope.
- **Fewer results than expected:** broaden filters, raise `limit`, or verify that the target contains enough matching records.
- **Some fields are empty:** optional fields depend on what each record publicly provides.
- **Run takes longer than expected:** reduce scope, lower `limit` for validation, or split broad collection into smaller segments.
- **Output changed:** compare the current output with the field reference and report a small sample if support is needed.

## FAQ

### What data does this actor collect?

It collects public LandWatch listing records, including listing identity, URLs, descriptions, pricing, acreage, property details, location, broker details, media, amenities, listing history, related listings, SEO metadata, and stable identifiers when available.

### Can I filter by location, category, date, price, or other criteria?

Yes. The input schema supports `location`, `property_type`, `publication_date`, `price_reduction_period`, keyword search, feature flags, price range, parcel size, building size, bedroom and bathroom counts, availability, deal type, and sorting.

### Why did I receive fewer results than my limit?

`limit` is a maximum, not a guarantee. The final count depends on how many public listings match the configured scope and filters at run time.

### Can I schedule recurring runs?

Yes. Use Apify schedules to run the actor daily, weekly, or with a custom cron expression for monitoring and reporting workflows.

### How do I avoid duplicates across runs?

Use `id` as the primary idempotency key. You can also compare `url` and `fingerprint` when detecting changes or validating repeated runs.

### Can I export the data to CSV, Excel, or JSON?

Yes. Apify datasets support exports such as JSON, CSV, Excel, and other platform-supported formats.

### Does this actor collect private data?

No. The actor is intended to collect publicly available listing information from LandWatch. Users are responsible for using the data lawfully and appropriately.

### What should I include when reporting an issue?

Include the input used with sensitive values removed, the run ID, expected versus actual behavior, and a small output sample if it helps illustrate the problem.

## Compliance & Ethics

### Responsible Data Collection

This actor collects publicly available real estate listing information from **[https://www.landwatch.com](https://www.landwatch.com)** for legitimate business purposes, including:

- **Real estate and land market** research and market analysis
- **Lead qualification and enrichment** for public property and broker records
- **Inventory monitoring and reporting** for pricing, availability, and regional trends

This section is informational and not legal advice. Users are responsible for ensuring that their collection, storage, and use of data comply with applicable laws, regulations, and contractual obligations.

### Best Practices

- Use collected data in accordance with applicable laws, regulations, and the target site’s terms
- Respect individual privacy and personal information
- Use data responsibly and avoid disruptive or excessive collection
- Do not use this actor for spamming, harassment, or other harmful purposes
- Follow relevant data protection requirements where applicable, such as GDPR and CCPA

## Support

For help, use the actor page or Issues section. Include the input used with any sensitive values redacted, the run ID, expected versus actual behavior, and a small output sample when it helps explain the issue. Avoid including private, confidential, or unnecessary personal data in support requests.