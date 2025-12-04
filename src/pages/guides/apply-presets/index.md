---
title: Apply Presets
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

# Apply Presets

Apply one or more XMP Lightroom Presets to an image, by referencing Preset file(s) stored on the cloud. You can find a code sample [here.](../code-sample/index.md#apply-presets-to-an-image)

A Preset file can be created by editing an image in Lightroom and exporting it as a `.xmp` file. You can learn more about creating presets [here](https://creativecloud.adobe.com/en-LU/learn/lightroom-cc/web/create-your-own-presets)

## How to create an XMP file

If you need to create an `.xmp` file from a set of slider values obtained directly from a user, you can start with the empty `.xmp` file [here](https://github.com/AdobeDocs/cis-photoshop-api-docs/blob/main/sample-code/lr-sample-app/crs.xml) and add the corresponding slider values.

You can find a code sample [here](../code-sample/index.md#apply-edits-to-an-image).

In this example, we are applying the Preset called "Aged Photo" to automatically make the adjustments.
![alt image](../features/preset_example.png?raw=true "Original Image")

## What are Presets?

Presets are pre-configured sets of adjustments that can be applied to images. They allow you to:

- Apply consistent editing styles across multiple images
- Save time by reusing common adjustment combinations
- Share editing styles with others
- Create signature looks for your photography

## Code samples

- [Apply Presets to an Image](../code-sample/index.md#apply-presets-to-an-image)
- [Apply Edits to an Image](../code-sample/index.md#apply-edits-to-an-image)

