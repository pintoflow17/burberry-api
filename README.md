# Burberry API Documentation

## Introduction

This is **Unofficial Burberry API**. Get products, category and much more.

## Authentication

The URL you need to use is the following: `https://burberry-api.p.rapidapi.com/`
The API requires the headers listed below:

- **`x-rapidapi-host`**: `burberry-api.p.rapidapi.com`
- **`x-rapidapi-key`**: `YOUR_API_KEY`

Make sure to replace `YOUR_API_KEY` with your API key. You can register one [here](https://rapidapi.com/belchiorarkad-FqvHs2EDOtP/api/burberry-api/pricing).
Some frameworks automatically add extra headers, you have to make sure to remove them in order to get a response from the API.

## Endpoints

The API is configured to accept only **GET** requests. Below are the available endpoints with their descriptions and required parameters.

### 1. **`GET /products-by-category`**

- **Description**: Retrieves products belonging to a specific category.

| Parameter     | Type   | Default | Description                                 | Required |
|---------------|--------|---------|---------------------------------------------|----------|
| `categoryURL` | string | -       | The URL of the category                     | Yes      |
| `country`     | string | `US`    | The website language version to search from | No       |

Example request:

```javascript
fetch('https://burberry-api.p.rapidapi.com/products-by-category?categoryUrl=https%3A%2F%2Fus.burberry.com%2Fl%2Fchildren%2Fwinter-selection%2FF', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'burberry-api.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "data": {
    "categoryId": "cat9190022",
    "productCount": 72,
    "isOpenListing": true,
    "url": "https://us.burberry.com/l/children/winter-selection/",
    "title": "Children’s Winter Collection",
    "titleEn": "Children’s Winter Collection",
    "products": [
      {
        "id": "80894091",
        "key": "80894091",
        "url": "https://us.burberry.com/ekd-nylon-padded-coat-p80894091",
        "content": {
          "title": "EKD Nylon Padded Coat",
          "defaultTitle": "EKD Nylon Padded Coat",
          "description": "",
          "label": "3-14 Years"
        },
        "price": {
          "current": {
            "value": 1000,
            "currency": "USD",
            "formatted": "$1,000.00"
          },
          "old": null
        },
        "isOnMarkdown": null,
        "numberOfColours": 1,
        "types": {
          ...
```

### 2. **`GET /products-description`**

- **Description**: Retrieves the description of a specific product.

| Parameter | Type   | Default | Description                                 | Required |
|-----------|--------|---------|---------------------------------------------|----------|
| `url`     | string | -       | The URL of the product                      | Yes      |
| `country` | string | `US`    | The website language version to search from | No       |

Example request:

```javascript
fetch('https://burberry-api.p.rapidapi.com/product-description?url=https%3A%2F%2Fus.burberry.com%2Fcode-cat-eye-sunglasses-p40841871', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'burberry-api.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "product": {
    "id": "40841871",
    "name": "Code Cat-eye Sunglasses",
    "nameEn": "Code Cat-eye Sunglasses",
    "description": "A pair of cat-eye sunglasses made in Italy from Burberry Check acetate. The sculptural temples are printed with our logo in metallic lettering.##Scratch-resistant dark brown lenses with 100% UV protection#Printed Burberry lettering at temples#Comes with a hard leather case and cleaning cloth#Also available in an alternative fit",
    "price": {
      "current": {
        "value": 290,
        "currency": "USD",
        "formatted": "$290.00"
      },
      "old": null
    },
    "color": "Sand",
    "relatedGenders": [
      "Women"
    ],
    "sizes": [
      {
        "sku": "40841871",
        "label": "",
        "preOrderStockLevel": 0,
        "stockQuantity": 255,
        "isPreOrderStock": false,
        "isInStock": true,
        "monogramStockQuantity": 255
      }
    ],
    "features": "",
    ...
```

### 3. **`GET /search`**

- **Description**: Searches for products based on a query string.

| Parameter | Type   | Default | Description                                 | Required |
|-----------|--------|---------|---------------------------------------------|----------|
| `query`   | string | -       | The search term                             | Yes      |
| `perPage` | number | `20`    | The number of results per page              | No       |
| `page`    | number | `1`     | The page number to search products from     | No       |
| `country` | string | `US`    | The website language version to search from | No       |

Example request:

```javascript
fetch('https://burberry-api.p.rapidapi.com/search?query=bag&perPage=20&page=1', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'burberry-api.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "pagination": {
    "total": 342,
    "perPage": 20,
    "page": 1
  },
  "products": [
    {
      "id": "80906521",
      "key": "80906521",
      "url": "https://us.burberry.com/large-ekd-crochet-bag-p80906521",
      "content": {
        "title": "Large EKD Crochet Bag",
        "defaultTitle": "Large EKD Crochet Bag",
        "label": ""
      },
      "price": {
        "current": {
          "value": 2090,
          "currency": "USD",
          "formatted": "$2,090.00"
        },
        "old": null
      },
      "isOnMarkdown": null,
      "numberOfColours": 1,
      "types": {
        "isPreOrderStock": false,
        "isComingSoon": false,
        "isRegisterForInterest": false,
        ...
```

## Error Handling

The  API returns standard HTTP status codes to indicate the success or failure of API requests. Below are common errors and suggestions for handling them.

|Status Code|Message|Description|Suggested Handling|
|--|--|--|--|
| **400** | Bad Request | The request was malformed or missing required parameters (e.g., `domain` parameter not provided). | Verify that all required parameters are included and correctly formatted. |
| **401** | Unauthorized | Invalid or missing API key in the request headers. | Check that a valid API key is included in `x-rapidapi-key`. |
| **403** | Forbidden | Access to the requested resource is denied, possibly due to rate limits or restricted access. | Review rate limits and ensure API permissions. Retry after a delay if rate limit exceeded. |
| **404** | Not Found | The requested domain information could not be found (e.g., domain does not exist). | Check the spelling or availability of the domain. |
| **429** | Too Many Requests | The API rate limit has been exceeded. | Implement rate-limiting logic and retry after the specified rate limit reset time. |
| **500** | Internal Server Error | A server error occurred while processing the request. | Retry the request after a few seconds. If the error persists, contact API support. |
| **503** | Service Unavailable | The API service is temporarily unavailable (e.g., due to maintenance). | Retry the request later or check the API status page for maintenance alerts. |
