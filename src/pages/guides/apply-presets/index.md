---
title: Apply Lightroom API Presets
description: Learn how to apply Lightroom presets to images using Adobe Lightroom API.
keywords:
  - Adobe Lightroom API
  - Presets
  - XMP presets
  - photo editing API
  - image enhancement
  - preset application
  - photo automation
  - bulk editing
contributors:
  - 'https://github.com/khound'
  - 'https://github.com/archyposada'
hideBreadcrumbNav: true
og:
  title: Apply Presets - Adobe Lightroom API
  description: Learn how to apply Lightroom presets to images using Adobe Lightroom API.
twitter:
  card: summary
  title: Apply Presets - Adobe Lightroom API
  description: Learn how to apply Lightroom presets to images using Adobe Lightroom API.
---

# How to apply presets

Apply one or more XMP Lightroom presets to an image, by referencing preset file(s) stored on the cloud.

A preset file can be created by editing an image in Lightroom and exporting it as a `.xmp` file. [Learn more about creating presets.](https://creativecloud.adobe.com/en-LU/learn/lightroom-cc/web/create-your-own-presets)

## How to create an XMP file

To create an `.xmp` file from a set of slider values set directly by a user, [start with the empty `.xmp` file template here](https://github.com/AdobeDocs/cis-photoshop-api-docs/blob/main/sample-code/lr-sample-app/crs.xml) and add the corresponding slider values.

In this example, the preset called "Aged Photo" is applied to automatically make the adjustments to achieve the desired effect.
![A small waterfall in a forest with a waterfall in the foreground and a tree in the background, before and after](../images/preset_example.png?raw=true "Apply Presets Example")

## What are Presets?

Presets are pre-configured sets of adjustments that can be applied to images. They allow you to:

- Apply consistent editing styles across multiple images
- Save time by reusing common adjustment combinations
- Share editing styles with others
- Create signature looks for your photography

## Example implementation

Here is a detailed implementation example.

<Accordion>
<AccordionItem header="Request example" isChevronIcon position="right" iconColor="#1473E6">

```shell
curl -X POST \
  https://image.adobe.io/lrService/presets \
  -H "Authorization: Bearer ${TOKEN}"  \
  -H "x-api-key: ${API_KEY}" \
  -H "Content-Type: application/json" \
  -d '{
    "inputs": {
        "source": {
            "href": "<SIGNED_GET_URL>",
            "storage": "<STORAGE_LOCATION>"
        },
        "presets": [
            {
                "href": "<SIGNED_GET_URL>",
                "storage": "<STORAGE_LOCATION>"
            },
            {
                "href": "<SIGNED_GET_URL>",
                "storage": "<STORAGE_LOCATION>"
            }
        ]
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

</AccordionItem>
<AccordionItem header="Response example" isChevronIcon position="right" iconColor="#1473E6">

```json
{
    "_links": {
        "self": {
            "href": "https://image.adobe.io/lrService/status/<JOB_ID>"
        }
    }
}
```

</AccordionItem>
</Accordion>
