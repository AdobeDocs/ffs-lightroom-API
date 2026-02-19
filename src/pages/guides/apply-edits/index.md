---
title: Apply Lightroom API Edits
description: Learn how to programmatically adjust Lightroom Edit Panel values using Adobe Lightroom API.
keywords:
  - Adobe Lightroom API
  - Apply Edits
  - photo editing API
  - image enhancement
  - programmatic editing
  - slider adjustments
  - photo automation
contributors:
  - 'https://github.com/khound'
  - 'https://github.com/archyposada'
hideBreadcrumbNav: true
og:
  title: Apply Edits - Adobe Lightroom API
  description: Learn how to programmatically adjust Lightroom Edit Panel values using Adobe Lightroom API.
twitter:
  card: summary
  title: Apply Edits - Adobe Lightroom API
  description: Learn how to programmatically adjust Lightroom Edit Panel values using Adobe Lightroom API.
---

# Apply new lightroom edits

Adjust values in the Lightroom Edit Panel programmatically.

The Apply Edits endpoint allows you to programmatically control the same adjustments you would make manually in the Lightroom Edit Panel. This gives you fine-grained control over values like:

- **Exposure controls**: Adjust overall brightness and tonal values.
- **Color adjustments**: Modify saturation, vibrance, and white balance.
- **Detail enhancement**: Control sharpness, texture, and clarity.
- **Noise reduction**: Manage both luminance and color noise.
- **Creative effects**: Apply vignetting and dehaze adjustments.

The specific values to adjust include:

| Parameter | Value Range |
|-----------|-------------|
| Exposure | -5.00 to 5.00 |
| Contrast | -100 to 100 |
| Sharpness | 0 to 150 |
| White Balance | "As Shot", "Auto", "Cloudy", "Custom", "Daylight", "Flash", "Fluorescent", "Shade", "Tungsten" |
| Saturation | -100 to 100 |
| Color Noise Reduction | 0 to 100 |
| Noise Reduction | 0 to 100 |
| Vignette Amount | -100 to 100 |
| Vibrance | -100 to 100 |
| Highlights | -100 to 100 |
| Shadows | -100 to 100 |
| Whites | -100 to 100 |
| Blacks | -100 to 100 |
| Clarity | -100 to 100 |
| Dehaze | -100 to 100 |
| Sharpen Radius | 0.5 to 3.0 |
| Sharpen Detail | 0 to 100 |
| Sharpen Edge Masking | 0 to 100 |
| Texture | -100 to 100 |

## Example implementation

Here is a detailed implementation example.

<AccordionItem slots="heading, code" />

### Request example

```shell
curl -X POST \
  https://image.adobe.io/lrService/edit \
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
        "Exposure": "<-5.00 to 5.00>",
        "Contrast": "<-100 to 100>",
        "Sharpness": "<0 to 150>",
        "WhiteBalance": "<"As Shot", "Auto", "Cloudy", "Custom", "Daylight", "Flash", "Fluorescent", "Shade", "Tungsten">",
        "Saturation": "<-100 to 100>",
        "ColorNoiseReduction": "<0 to 100>",
        "NoiseReduction": "<0 to 100>",
        "VignetteAmount": "<-100 to 100>",
        "Vibrance": "<-100 to 100>",
        "Highlights": "<-100 to 100>",
        "Shadows": "<-100 to 100>",
        "Whites": "<-100 to 100>",
        "Blacks": "<-100 to 100>",
        "Clarity": "<-100 to 100>",
        "Dehaze": "<-100 to +100>",
        "SharpenRadius": "<0.5 to 3.0>",
        "SharpenDetail": "<0 to 100>",
        "SharpenEdgeMasking": "<0 to 100>",
        "Texture": "<-100 to 100>"
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