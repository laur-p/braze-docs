---
nav_title: "POST: Create Multiple Catalog Items"
article_title: "POST: Create Multiple Catalog Items"
search_tag: Endpoint
page_order: 3

layout: api_page
page_type: reference
description: "This article outlines details about the Create Multiple Catalog Items Braze endpoint."

---
{% api %}
# Create multiple catalog items
{% apimethod post %}
/catalogs/catalog_name/items
{% endapimethod %}

Use this endpoint to create multiple items in your catalog. Each request can support up to 50 items.

{% alert important %}
Support for this endpoint is currently in early access. Contact your Braze account manager if you are interested in participating in the early access.
{% endalert %}

If you'd like to share your feedback on this endpoint or make a request, contact the Braze Catalogs team at [catalogs-product@braze.com](mailto:catalogs-product@braze.com)

## Rate limit

This endpoint has a shared rate limit of 100 requests per minute between all asynchronous catalog item endpoints.

## Request body

```
Content-Type: application/json
Authorization: Bearer YOUR-REST-API-KEY
```

```json
{
    "items": [ (max of 50 items)
        {
            "id": (required, item id),
            "count": (required, item count),
        },
        {
            "id": (required, item id),
            "count": (required, item count),
        },
        {
            "id": (required, item id),
            "count": (required, item count),
        }
    ]
}
```

### Request parameters

| Parameter | Required | Data Type | Description |
|---|---|---|---|
| `item_id`  | Required | String | Item ID for a catalog item. |
{: .reset-td-br-1 .reset-td-br-2 .reset-td-br-3 .reset-td-br-4}

## Example request
```
curl --location --request POST 'https://rest.iad-01.braze.com/catalogs/catalog_name/items' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer YOUR-REST-API-KEY' \
--data-raw '{
    "items": [
        {
            "id": "item_0",
            "count": 1,
        },
        {
            "id": "item_1",
            "count": 2,
        },
        {
            "id": "item_2",
            "count": 3,
        }
    ]
}
```

## Example error response 

```json
{
  "errors": [
    {
        "id": "catalog-not-found",
        "message": "Could not find catalog",
        "parameters": ["catalog_name"],
        "parameter_values": ["catalog_name"]
    }
  ]
}
```

## Troubleshooting

The following table lists possible returned errors and their associated troubleshooting steps.

| Error | Troubleshooting |
| --- | --- |
| `catalog-not-found` | Check that the catalog name is valid. |
| `invalid-ids` | Item IDs can only include letters, numbers, hyphens, and underscores. |
| `ids-too-large` | Item IDs can't be more than 250 characters. |
| `ids-not-unique` | Item IDs must be unique in the request. |
| `items-missing-ids` | There are items that do not have item IDs. Check that each item has an item ID. |
| `items-too-large` | Item values can't exceed 5,000 characters. |
| `request-includes-too-many-items` | Your request has too many items. The maximum is 50. |
| `invalid-fields` | Confirm that the fields in the request exist in the catalog. |
| `fields-do-not-match` | Updated fields must match the fields in the catalog. |
| `unable-to-coerce-value` | Item types can't be converted. |
{: .reset-td-br-1 .reset-td-br-2}

{% endapi %}