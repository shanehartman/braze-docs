---
nav_title: "POST: Create Multiple Catalog Items"
article_title: "POST: Create Multiple Catalog Items"
search_tag: Endpoint
page_order: 3

layout: api_page
page_type: reference
description: "This article outlines details about the Create multiple catalog items Braze endpoint."

---
{% api %}
# Create multiple catalog items
{% apimethod post %}
/catalogs/{catalog_name}/items
{% endapimethod %}

> Use this endpoint to create multiple items in your catalog. 

Each request can support up to 50 items. This endpoint is asynchronous.

{% apiref postman %}https://documenter.getpostman.com/view/4689407/SVYrsdsG?version=latest#cea18bb3-b83a-4160-81fe-8cd42aa6e7cc {% endapiref %}

## Rate limit

{% multi_lang_include rate_limits.md endpoint='asynchronous catalog item' %}

## Path parameters

| Parameter | Required | Data Type | Description |
|---|---|---|---|
| `catalog_name` | Required | String | Name of the catalog. |
{: .reset-td-br-1 .reset-td-br-2 .reset-td-br-3 .reset-td-br-4}

## Request parameters

| Parameter | Required | Data Type | Description |
|---|---|---|---|
| `items` | Required | Array | An array that contains item objects. The item objects should contain all of the fields in the catalog. Up to 50 item objects are allowed per request. |
{: .reset-td-br-1 .reset-td-br-2 .reset-td-br-3 .reset-td-br-4}

## Example request

```
curl --location --request POST 'https://rest.iad-03.braze.com/catalogs/restaurants/items' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer YOUR-REST-API-KEY' \
--data-raw '{
  "items": [
    {
      "id": "restaurant1",
      "Name": "Restaurant1",
      "City": "New York",
      "Cuisine": "American",
      "Rating": 5,
      "Loyalty_Program": true,
      "Location": {
        "Latitude": 33.6112,
        "Longitude": -117.8711
      },
      "Created_At": "2022-11-01T09:03:19.967+00:00"
    },
    {
      "id": "restaurant2",
      "Name": "Restaurant2",
      "City": "New York",
      "Cuisine": "American",
      "Rating": 10,
      "Loyalty_Program": true,
      "Location": {
        "Latitude": 40.7413,
        "Longitude": -73.9764
      },
      "Created_At": "2022-11-02T09:03:19.967+00:00"
    },
    {
      "id": "restaurant3",
      "Name": "Restaurant3",
      "City": "New York",
      "Cuisine": "American",
      "Rating": 3,
      "Loyalty_Program": false,
      "Location": {
        "Latitude": 40.7489,
        "Longitude": -73.9972
      },
      "Created_At": "2022-11-03T09:03:19.967+00:00"
    }
  ]
}'
```

## Response

There are three status code responses for this endpoint: `202`, `400`, and `404`.

### Example success response

The status code `202` could return the following response body.

```json
{
  "message": "success"
}
```

### Example error response

The status code `400` could return the following response body. Refer to [Troubleshooting](#troubleshooting) for more information about errors you may encounter.

```json
{
  "errors": [
    {
      "id": "invalid-fields",
      "message": "Some of the fields given do not exist in the catalog",
      "parameters": [
        "id"
      ],
      "parameter_values": [
        "restaurant1"
      ]
    }
  ],
  "message": "Invalid Request"
}
```

## Troubleshooting

The following table lists possible returned errors and their associated troubleshooting steps.

| Error | Troubleshooting |
| --- | --- |
| `catalog-not-found` | Check that the catalog name is valid. |
| `item-array-invalid` | `items` must be an array of objects. |
| `request-includes-too-many-items` | Your request has too many items. The item limit per request is 50. |
| `invalid-ids` | Item IDs can only include letters, numbers, hyphens, and underscores. |
| `ids-too-large` | Item IDs can't be more than 250 characters. |
| `ids-not-unique` | Item IDs must be unique in the request. |
| `ids-not-strings` | Item IDs must be of type string. |
| `items-missing-ids` | There are items that do not have item IDs. Check that each item has an item ID. |
| `items-too-large` | Item values can't exceed 5,000 characters. |
| `invalid-fields` | Confirm that the fields in the request exist in the catalog. |
| `unable-to-coerce-value` | Item types can't be converted. |
| `invalid-keys-in-value-object` | Item object keys can't include `.` or `$`. |
| `too-deep-nesting-in-value-object` | Item objects can't have more than 50 levels of nesting. |
{: .reset-td-br-1 .reset-td-br-2}

{% endapi %}
