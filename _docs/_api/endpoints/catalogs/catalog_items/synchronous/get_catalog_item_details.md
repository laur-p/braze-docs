---
nav_title: "GET: List Catalog Item Details"
article_title: "GET: List Catalog Item Details"
search_tag: Endpoint
page_order: 2

layout: api_page
page_type: reference
description: "This article outlines details about the List Catalog Item Details Braze endpoint."

---
{% api %}
# List catalog item details
{% apimethod get %}
/catalogs/catalog_name/items/item_id
{% endapimethod %}

Use this endpoint to return a catalog item and its content.

{% alert important %}
Support for this endpoint is currently in early access. Contact your Braze account manager if you are interested in participating in the early access.
{% endalert %}

If you'd like to share your feedback on this endpoint or make a request, contact the Braze Catalogs team at [catalogs-product@braze.com](mailto:catalogs-product@braze.com)

## Rate limit

This endpoint has a shared rate limit of 50 requests per minute between all synchronous catalog item endpoints.

### Request Parameters

| Parameter | Required | Data Type | Description |
|---|---|---|---|
| `catalog_name`  | Required | String | Name of the catalog.|
| `item_id ` |  Required | String | The ID of the catalog item. |
{: .reset-td-br-1 .reset-td-br-2 .reset-td-br-3 .reset-td-br-4}

## Example request

```
https://rest.iad-03.braze.com/catalogs/catalog_name/items/item_id
```

## Response

```json
Content-Type: application/json
Authorization: Bearer YOUR-REST-API-KEY
"items": [
    {
        "id": "0",
        "count": 5,
    }
]
```

## Troubleshooting

The following table lists possible returned errors and their associated troubleshooting steps, if applicable.

| Error | Troubleshooting |
| --- | --- |
| `catalog-not-found` | Check that the catalog name is valid. |
| `item-not-found` | Check that the item is in the catalog. |
{: .reset-td-br-1 .reset-td-br-2}

{% endapi %}