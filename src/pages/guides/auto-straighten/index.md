---
title: Use Lightroom API Auto Straighten
description: Learn how to use the Auto Straighten feature in Adobe Lightroom API.
keywords:
  - Adobe Lightroom API
  - Auto Straighten
  - Auto Upright
  - photo editing API
  - image straightening
  - automatic correction
  - photo automation
contributors:
  - 'https://github.com/khound'
  - 'https://github.com/archyposada'
hideBreadcrumbNav: true
og:
  title: Auto Straighten - Adobe Lightroom API
  description: Learn how to use the Auto Straighten feature in Adobe Lightroom API.
twitter:
  card: summary
  title: Auto Straighten - Adobe Lightroom API
  description: Learn how to use the Auto Straighten feature in Adobe Lightroom API.
---

# Use Auto Straighten

The Auto Straighten endpoint (/autoStraighten) applies the Auto Upright transformation to an image.

This feature automatically analyzes your image to easily correct those photos that have a distorted vertical or horizontal perspective, making them straight and aligned.

## Example implementation

Here is a detailed implementation example.

<AccordionItem slots="heading, code" />

### Request example

```shell
curl -X POST \
  https://image.adobe.io/lrService/autoStraighten \
  -H "Authorization: Bearer ${TOKEN}"  \
  -H "x-api-key: ${API_KEY}" \
  -H "Content-Type: application/json" \
  -d '{
    "inputs": {
        "href": "<SIGNED_GET_URL>",
        "storage": "<STORAGE_LOCATION>"
    },
    "outputs": [
        {
            "href": "<SIGNED_POST_URL>",
            "type": "<TYPE>",
            "storage": "<STORAGE_LOCATION>"
        }
    ]
}'
```

<AccordionItem slots="heading, code" />

### Response example

```json
{
    "_links": {
        "self": {
            "href": "https://image.adobe.io/lrService/status/<JOB_ID>"
        }
    }
}
```