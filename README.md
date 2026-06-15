[Elgiganten Scraper](https://apify.com/studio-amba/elgiganten-scraper?fpr=data)

# Elgiganten Scraper

Scrapes Sweden's largest electronics retailer, Elgiganten.se (part of the Elkjop/Dixons Carphone group). The scraper reads product data from Next.js server-side rendered props, making it fast and reliable.

## Embedded data extraction

Elgiganten is a Next.js site that embeds full product search results in `__NEXT_DATA__`. The scraper extracts these directly, getting rich API-level data including online stock levels, seller names (marketplace products), campaign discounts, and energy ratings -- fields you won't find in basic HTML scraping.

For detail mode, it visits individual product pages to add specs, full descriptions, and image galleries.

## Input

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `searchQuery` | String | Conditional | e.g. `"iphone"`, `"tvattmaskin"` |
| `categoryUrl` | String | Conditional | e.g. `https://www.elgiganten.se/datorer-tillbehor/laptops` |
| `maxResults` | Integer | No | Default: 100 |
| `scrapeDetails` | Boolean | No | Fetch product pages for specs (default: false) |
| `proxyConfiguration` | Object | No | Proxy settings |

One of `searchQuery` or `categoryUrl` is required.

## Output

| Field | Type | Example |
| --- | --- | --- |
| `name` | String | `"Samsung Galaxy S24 Ultra 256GB"` |
| `brand` | String | `"Samsung"` |
| `price` | Number | `15990` |
| `currency` | String | `"SEK"` |
| `originalPrice` | Number | `17990` |
| `discount` | String | `"-2000 kr"` |
| `sku` | String | `"466312"` |
| `productId` | String | `"466312"` |
| `inStock` | Boolean | `true` |
| `onlineStockLevel` | String | `"HIGH"` |
| `rating` | Number | `4.7` |
| `seller` | String | `"Elgiganten"` |
| `category` | String | `"Mobiler > Samsung"` |
| `description` | String | Bullet point features |
| `specs` | Object | `{"Skarmstorlek": "6.8\"", "Batteri": "5000 mAh"}` |

## Cost

Listing mode: ~0.3 CU per 1,000. Detail mode: ~1.5 CU per 1,000.

## Notes

- Search mode pre-paginates (48 items per page) and fetches all pages upfront
- Marketplace products include the seller name
- The scraper handles both Elgiganten-hosted and third-party seller products
- Stock level is a qualitative indicator (`HIGH`, `MEDIUM`, `LOW`) not an exact count