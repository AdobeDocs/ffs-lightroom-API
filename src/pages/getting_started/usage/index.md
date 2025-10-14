---
title: Lightroom API Usage Notes 
description: Technical usage notes for Firefly's Lightroom API including general workflow information, supported formats, and known limitations.
hideBreadcrumbNav: true
keywords:
  - video rendering
  - API usage
  - performance optimization
  - troubleshooting
  - best practices
  - API usage
  - API best practices
  - API troubleshooting
  - API best practices
  - usage notes
  - rate limits
  - known limitations
---
# Technical usage notes for Lightroom API

This page includes information about the technical requirements and support for this API. As you incorporate the Lightroom API into your workflow, consider the information below.

A typical Lightroom workflow initiates one or more calls to our API to modify PNG, JPG, or other compatible image files and generate new renditions.

## Supported input formats

All image formats compatible with Lightroom are likewise supported by the APIs. Consult the Lightroom product documentation for [a comprehensive list of these formats](https://helpx.adobe.com/lightroom-classic/help/supported-file-formats.html).

[See the Storage Solutions page to generate URLs programmatically](../storage_solutions/index.md) with the most common storage services.

## Current limitations

These are the known limitations to the API.

* Multi-part uploads and downloads are not yet supported.
* All the endpoints only support a single file input.

## Retries

For increased reliability and stability we have added a retry mechanism for all API calls, with recommendations on how to handle these:

* The service will retry status codes of 429, 502, 503, 504 three times.
* Only retry requests that have a 5xx response code. A 5xx error response indicates there was a problem processing the request on the server. Do not retry requests for any other response code.
* Implement an exponential back-off retry strategy with 3 retry attempts.
