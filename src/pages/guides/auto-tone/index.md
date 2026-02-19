---
title: Use Lightroom API Auto Tone
description: Learn how to use the Auto Tone feature in Adobe Lightroom API.
keywords:
  - Adobe Lightroom API
  - Auto Tone
  - photo editing API
  - image enhancement
  - automatic adjustments
  - AI photo editing
  - photo automation
contributors:
  - 'https://github.com/khound'
  - 'https://github.com/archyposada'
hideBreadcrumbNav: true
og:
  title: Auto Tone - Adobe Lightroom API
  description: Learn how to use the Auto Tone feature in Adobe Lightroom API.
twitter:
  card: summary
  title: Auto Tone - Adobe Lightroom API
  description: Learn how to use the Auto Tone feature in Adobe Lightroom API.
---

# Use Auto Tone

The Auto Tone feature in Lightroom Classic utilizes an AI/ML model trained to adjust slider values automatically, enhancing images based on their content.

This feature identifies elements within the image and adjusts those characteristics (like exposure, contrast, highlights, saturation, and more) to achieve striking photo results.

In this example, we automatically adjusted the photo using the Auto Tone API.
![An image of an island in the sea with Auto Tone applied, before and after](../../images/autotone_example.png "Auto Tone Example")

## How it works

Auto Tone analyzes the content of your image and automatically adjusts the following slider values:

- Exposure
- Contrast
- Highlights
- Shadows
- Whites
- Blacks
- Saturation
- Vibrance

The adjustments are made using an AI/ML model that has been trained to enhance images based on their specific content and characteristics.

## Example implementation

Here is a detailed implementation example.

<AccordionItem slots="heading, code" />

### Request example

```shell
curl -X POST \
  https://image.adobe.io/lrService/autoTone \
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