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

## Recommended first step

1. Quickstart — a hands-on tutorial that walks you through retrieving an access token, calling the Auto Straighten API, polling job status, and viewing the output. It's the fastest way to confirm your environment is working.

## Guides

- [Quickstart](./quickstart/) — A step-by-step tutorial to modify your first image using the Lightroom APIs. Includes Bash, JavaScript, and Python examples, plus guidance on pre-signed URLs and job polling.

- [Features (Feature reference)](./features/) — Detailed descriptions of supported Lightroom features such as Auto Tone, Auto Straighten, Apply Presets, Apply Edits, Apply XMP, and webhook integration via Adobe I/O Events.

- [Code Samples](./code-sample/) — Copy-ready curl, Python, and JavaScript snippets for common tasks (Auto Tone, Auto Straighten, Apply Presets, Apply Edits, Apply XMP) and examples for polling job status and triggering events.

## Quick tips

- Run the Quickstart first to verify credentials and environment before building larger workflows.
- Use pre-signed URLs for input/output storage to avoid exposing credentials in your application.
- For production workloads, add robust error handling, retries, logging, and secure secret storage.
