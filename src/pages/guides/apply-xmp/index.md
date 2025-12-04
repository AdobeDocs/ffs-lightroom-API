---
title: How to Apply XMP Presets Inline
description: Learn how to apply Lightroom presets inline using XMP contents with Adobe Lightroom API.
keywords:
  - Adobe Lightroom API
  - Apply XMP
  - XMP presets
  - photo editing API
  - inline presets
  - image enhancement
  - photo automation
contributors:
  - 'https://github.com/khound'
  - 'https://github.com/archyposada'
hideBreadcrumbNav: true
og:
  title: Apply XMP - Adobe Lightroom API
  description: Learn how to apply Lightroom presets inline using XMP contents with Adobe Lightroom API.
twitter:
  card: summary
  title: Apply XMP - Adobe Lightroom API
  description: Learn how to apply Lightroom presets inline using XMP contents with Adobe Lightroom API.
---

# Apply XMP inline

The Apply XMP endpoint allows you to apply Lightroom adjustments by passing the XMP preset contents directly in your API request, rather than referencing a stored preset file. This is useful when you want to:

- Apply adjustments without storing preset files in cloud storage
- Dynamically generate preset values on the fly
- Integrate preset generation into your application workflow

### How it differs from applying presets

While the [Apply Presets](../apply-presets/index.md) process requires you to store XMP files in cloud storage and reference them by URL, Apply XMP allows you to pass the XMP content directly inline in your API request.

**Apply Presets**: Reference a stored `.xmp` file

```json
{
  "preset": "https://example.com/path/to/preset.xmp"
}
```

**Apply XMP**: Pass XMP content inline

```json
{
  "xmp": "<xmp_content>"
}
```

## Code implementation

Here is a detailed implementation example.

<Accordion>
<AccordionItem header="Request example" isChevronIcon position="right" iconColor="#1473E6">

```shell
curl -X POST \
  https://image.adobe.io/lrService/xmp \
  -H "Authorization: Bearer ${TOKEN}"  \
  -H "x-api-key: ${API_KEY}" \
  -H "Content-Type: application/json" \
  -d '{
    "inputs": {
        "source": {
            "href": "<SIGNED_GET_URL>",
            "storage": "<STORAGE_LOCATION>"
        }
    },
    "options": {
        "xmp": "<XMP_CONTENT>",
        "orientation": "<ORIENTATION>"
    },
    "outputs": [
        {
            "href": "<SIGNED_POST_URL>",
            "storage": "<STORAGE_LOCATION>",
            "type": "<TYPE>"
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
