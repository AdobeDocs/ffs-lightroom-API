---
title: Lightroom Guides Overview
description: This is an overview of the guides available with Firefly's Lightroom API.
hideBreadcrumbNav: true
keywords:
- lightroom
- api
- guides
- quickstart
- auto tone
- auto straighten
- apply presets
- apply edits
- apply xmp
- webhook
- adobe io events
- code samples
- image processing
- pre-signed urls
- authentication
- job polling
- integration
- firefly
---
# Lightroom Guides

Welcome to the Lightroom API guides. If you're new to the APIs, start with the Quickstart to set up credentials, generate pre-signed URLs, and run your first Lightroom API job. After you've tried the Quickstart, explore the features and code samples to deepen your integration.

## Quick tips

- Run the Quickstart first to verify credentials and environment before building larger workflows.
- Use pre-signed URLs for input/output storage to avoid exposing credentials in your application.
- For production workloads, add robust error handling, retries, logging, and secure secret storage.

## Guides

- [Quickstart](quickstart/index.md) — A step-by-step tutorial to modify your first image using the Lightroom APIs. Includes Bash, JavaScript, and Python examples, plus guidance on pre-signed URLs and job polling.

- [Use Auto Tone](auto-tone/index.md) — Learn how to automatically adjust exposure, contrast, highlights, shadows, and other tonal values using AI/ML-powered adjustments.

- [Use Auto Straighten](auto-straighten/index.md) — Automatically correct distorted vertical or horizontal perspectives in your images using the Auto Upright transformation.

- [Apply Presets](apply-presets/index.md) — Apply one or more XMP Lightroom presets stored in the cloud to quickly adjust image appearance with consistent editing styles.

- [Apply Edits](apply-edits/index.md) — Programmatically control Lightroom Edit Panel adjustments including exposure, color, sharpness, noise reduction, and creative effects.

- [Apply XMP](apply-xmp/index.md) — Apply Lightroom adjustments by passing XMP preset contents directly inline through the API without storing preset files.

- [Use Webhooks](use-webhooks/index.md) — Build event-driven applications using Adobe I/O Events to receive real-time notifications when Lightroom API jobs complete.
