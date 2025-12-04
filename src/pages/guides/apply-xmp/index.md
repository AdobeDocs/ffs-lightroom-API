---
title: How to apply XMP presets
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

# Apply XMP

Apply a Lightroom preset to an image, by passing in the preset XMP contents inline through the API. Code sample [here](../code-sample/index.md#apply-xmp-to-an-image)

## What is Apply XMP?

The Apply XMP endpoint allows you to apply Lightroom adjustments by passing the XMP preset contents directly in your API request, rather than referencing a stored preset file. This is useful when you want to:

- Apply adjustments without storing preset files in cloud storage
- Dynamically generate preset values on the fly
- Integrate preset generation into your application workflow

## How it differs from Apply Presets

While [Apply Presets](../apply-presets/index.md) requires you to store XMP files in cloud storage and reference them by URL, Apply XMP allows you to pass the XMP content directly inline in your API request.

**Apply Presets**: Reference a stored `.xmp` file

```json
{
  "preset": "https://example.com/path/to/preset.xmp"
}
```

**Apply XMP**: Pass XMP content inline

```json
{
  "xmp": "<xmp content here>"
}
```

## Code samples

You can find code samples and implementation details in the [Code Sample guide](../code-sample/index.md#apply-xmp-to-an-image).

