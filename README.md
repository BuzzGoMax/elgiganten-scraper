[Elgiganten Scraper](https://apify.com/lexis-solutions/elgiganten-scraper?fpr=data)

![banner](https://images.apifyusercontent.com/bbCse0J6csFdswlXQvwAIWR9Kbc2vqRFiNgZiC7HNbQ/w:1800/cb:1/aHR0cHM6Ly9pLmltZ3VyLmNvbS8xajdkSHY3LnBuZw.webp)

Elgiganten (elgiganten.dk / elgiganten.se) is a major Nordic electronics retailer. This scraper collects product data from search results or direct product pages, including pricing, stock, images, ratings, and brand metadata.

## Introduction

The Elgiganten scraper supports keyword search and direct product URLs. It paginates through listings, applies optional filters (price, rating, sort, country), and outputs structured product data.

## Use Cases

- **Price tracking**: Monitor price changes across products and categories.
- **Catalog building**: Create a structured product database with images and metadata.
- **Availability monitoring**: Track online stock and in-store availability flags.
- **Competitive research**: Compare products, brands, and ratings across markets.

## Input

Provide the following fields:

- `startUrls` (array, optional): Product page URLs on Elgiganten. Example: `{ "url": "https://www.elgiganten.dk/product/.../906396" }`
- `query` (string, optional): Search term used to build listing URLs.
- `country` (string, optional): `dk` or `se` (default: `dk`).
- `sort` (string, optional): Sort order for listings (e.g. `Relevancy-desc`, `ActivePrice.Amount-asc`).
- `priceMin` (number, optional): Minimum price filter.
- `priceMax` (number, optional): Maximum price filter.
- `rating` (array, optional): Filter by average rating (`1`..`5`).
- `maxItems` (integer, optional): Maximum number of items (default: 10).
- `proxyConfiguration` (object, optional): Apify proxy configuration. Example: `{ "useApifyProxy": true }`

Notes:

- You must provide either `startUrls` or `query` to run the scraper.
- Use product URLs only in `startUrls`.
- Non-product URLs (for example, search URLs with various parameters) are skipped automatically.
- The scraper supports two country sites; set `country` to match the website you want.

## Input Examples

**1) Start URLs**

```
{
  "startUrls": [
    {
      "url": "https://www.elgiganten.dk/product/tv-lyd-smart-home/tv-tilbehor/tv/samsung-55-qn85f-neo-qled-4k-miniled-smart-tv-2025/906396"
    }
  ],
  "proxyConfiguration": {
    "useApifyProxy": true
  }
}
```

**2) Query with filters**

```
{
  "query": "smart tv",
  "country": "dk",
  "sort": "ActivePrice.Amount-asc",
  "priceMin": 2000,
  "priceMax": 10000,
  "rating": ["4", "5"],
  "maxItems": 20,
  "proxyConfiguration": {
    "useApifyProxy": true
  }
}
```

## Output

Each dataset item contains fields like:

```
{
  "url": "https://elgiganten.dk/product/tv-lyd-smart-home/tv-tilbehor/tv/samsung-55-qn85f-neo-qled-4k-miniled-smart-tv-2025/906396",
  "sku": "906396",
  "familyName": "QN85F",
  "productPageUrl": "/product/tv-lyd-smart-home/tv-tilbehor/tv/samsung-55-qn85f-neo-qled-4k-miniled-smart-tv-2025/906396",
  "ratingAverage": 0,
  "ratingCount": 0,
  "taxonomyIds": ["PT104", "PT1112", "PT351"],
  "taxonomyNames": ["TV, Lyd & Smart Home", "TV & Tilbehor", "TV"],
  "taxonomyPaths": [
    "/tv-lyd-smart-home",
    "/tv-lyd-smart-home/tv-tilbehor",
    "/tv-lyd-smart-home/tv-tilbehor/tv"
  ],
  "gtin": "8806097082385",
  "articleType": "ZHAW",
  "manufacturerPartNumber": "TQ55QN85FAUXXC",
  "brandName": "Samsung",
  "title": "Samsung 55\" QN85F Neo QLED 4K MiniLED Smart TV (2025)",
  "bulletPoints": [
    "144Hz, 4x HDMI, HDMI-eArc",
    "4K AI-opskalering, AI-processor, HDR",
    "Smart TV, Mini LED, Dolby Atmos"
  ],
  "primaryImageUrl": "https://next-media.elkjop.com/image/dv_web_D18000137233848/906396/samsung-55-qn85f-neo-qled-4k-miniled-smart-tv-2025.jpg",
  "imageUrls": [
    "https://next-media.elkjop.com/image/dv_web_D18000137233848/906396/samsung-55-qn85f-neo-qled-4k-miniled-smart-tv-2025.jpg"
  ],
  "inStock": false,
  "isAvailableOnline": true,
  "currency": "DKK",
  "isDiscounted": true,
  "priceCurrent": [6999, 5599.2]
}
```

The scraper paginates through listing results and stops when `maxItems` is reached or there are no more products.

## Why use the Elgiganten Scraper?

- **Fast**: Efficient pagination and filtering.
- **Easy to use**: Search by keyword or provide product URLs.
- **Reliable**: Built on Apify Actors and Crawlee.
- **Flexible**: Supports country, sort, and price/rating filters.
- **Comprehensive**: Captures pricing, stock, and product metadata.

## FAQ

- **Can I scrape both Denmark and Sweden?**

Not in a single run. Set `country` to `dk` or `se` per run.
- **Does it support proxies?**

Yes. Configure `proxyConfiguration` to route traffic through Apify Proxy or your own proxies.
- **What if the website changes?**

Site updates may require adjustments. Please report issues or request updates.

## Need to scrape other retail sites?

Check out our other scrapers on Apify:

- [Advance Auto Parts Scraper](https://apify.com/lexis-solutions/advanceautoparts-scraper)
- [Barnes and Noble Scraper](https://apify.com/lexis-solutions/barnesandnoble-scraper)
- [Bath and Body Works Scraper](https://apify.com/lexis-solutions/bath-and-body-works)
- [Babylist Scraper](https://apify.com/lexis-solutions/babylist)
- [AutoZone Scraper](https://apify.com/lexis-solutions/auto-zone-com)
- [Alibaba Scraper](https://apify.com/lexis-solutions/alibaba-scraper)

---

# Got feedback or need an extension?

Lexis Solutions is a [certified Apify Partner](https://apify.com/partners/find). We can help you with custom solutions or data extraction projects.

Contact us over [Email](mailto:scraping@lexis.solutions) or [LinkedIn](https://www.linkedin.com/company/lexis-solutions)

## Support Our Work 💝

If you're happy with our work and scrapers, you're welcome to leave us a company review [here](https://apify.com/partners/find/lexis-solutions/review) and leave a review for the scrapers you're subscribed to. It will take you less than a minute but it will mean a lot to us!

Image Credit: Elgiganten