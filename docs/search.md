---
sidebar_position: 1
---

# Search

Let's discover **Anvere in less than 5 minutes**.
## Get your API keys
Your API requests are authenticated using API keys. Any request that doesn't include an API key will return an error.
You can get an API key from your [Dashboard](https://anvere.net) at any time.
## Search
Start search with Anvere with a simple request

- Host: `https://search-{region}.anvere.net`
- Method: `GET`
- Header:  
`X-Anvere-Api-Key: {YOUR_API_KEY}`
- Params

| Param     | Type   | Description                                           |
|-----------|--------|-------------------------------------------------------|
| input     | String | Some words you are searching for (Required)           |
| highlight | Bool   | Highlight results, defaults to `true`                 |
| app_id    | String | Your application ID                                   |
| index_id  | String | Your index ID                                         |
| filters   | String | Filter by attributes (ex: filters=product_type:shoes) |
| sort_by   | String | Sort search results by attribute                      |
| page      | Number | Result page to display                                |
| page_size | Number | Number of results per page                            |
| fields    | String | Attributes to search in, delimited by commas Header   |

- Request example  
```shell
curl --request GET \
  --url 'https://demo-search.anvere.net/docs?app_id=amazon&index_id=amazon&input=Barbie+dolphin+magic+&highlight=true&page=0&page_size=10' \
  --header 'X-Anvere-Api-Key: e25e7e53db6f3656c19cc01471709561'
```
- Response example
```json
{
  "hits": [
    {
      "Product Name": "Barbie Dolphin Magic Snorkel Fun Friends",
      "Category": "Toys & Games | Dolls & Accessories | Playsets",
      "Selling Price": "$17.62",
      "Model Number": "FBD63",
      "Shipping Weight": "10.6 ounces",
      "Product Url": "https://www.amazon.com/Barbie-Dolphin-Snorkel-Friends-Playset/dp/B01MRV4ET4",
      "objectID": "pe0gwAQWZSdeqiqWNuA5f",
      "_highlightResult": {
        "Product Name": {
          "value": "<mark>barbie</mark> <mark>dolphin</mark> <mark>magic</mark> snorkel fun friends"
        }
      }
    }
  ],
  "nbHits": 1,
  "page": 0,
  "hitsPerPage": 1,
  "nbPages": 1,
  "total_docs": 10002,
  "processingTimeMS": 0.051
}
```