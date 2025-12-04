---
title: Using Webhooks through Adobe I/O Events
description: Learn how to use webhooks with Adobe Lightroom API through Adobe I/O Events.
keywords:
  - Adobe Lightroom API
  - Webhooks
  - Adobe I/O Events
  - event-driven
  - API events
  - notifications
  - job status
  - real-time updates
contributors:
  - 'https://github.com/khound'
  - 'https://github.com/archyposada'
hideBreadcrumbNav: true
og:
  title: Using Webhooks - Adobe Lightroom API
  description: Learn how to use webhooks with Adobe Lightroom API through Adobe I/O Events.
twitter:
  card: summary
  title: Using Webhooks - Adobe Lightroom API
  description: Learn how to use webhooks with Adobe Lightroom API through Adobe I/O Events.
---

# Using Webhooks through Adobe I/O Events

Adobe I/O Events offers the possibility to build an event-driven application, based on events originating from Lightroom and Lightroom APIs. To start listening for events, your application needs to register a webhook URL, specifying the Event Types to receive. Whenever a matching event gets triggered, your application is notified through an HTTP POST request to the webhook URL.

The Event Provider for Lightroom and Lightroom APIs is `Imaging API Events`.

## Event Types

This event provider has two event types:

1. `Lightroom API events`
2. `Lightroom API events`

As the names indicate, these event types represent events triggered by the individual APIs.

## Registering your application to our Event Provider

Prerequisites needed to use the Event Provider:

1. In order to use the Adobe I/O Events you will need to create a project on Adobe I/O Console.
2. You can follow the steps listed in [Getting Started](../../getting_started/) page if you haven't created one yet.
3. You can learn more about creating a Webhook application [here.](https://www.adobe.io/apis/experienceplatform/events/docs.html#!adobedocs/adobeio-events/master/intro/webhooks_intro.md) This page provides all of the details you will need to build a basic application.

## Registering the Webhook

Once the above prerequisites are met, you can now proceed to register the webhook to the service integration. The steps to do that can be found [here](https://developer.adobe.com/events/docs/guides/#getting-started).

After the webhook has been successfully registered, you will start to receive the events for any submitted job that either succeeded or failed, from the Event Types selected. This eliminates the need for your application to poll for the status of the job using the jobID.

## Benefits of using Webhooks

Using webhooks with the Lightroom API provides several advantages:

- **Real-time notifications**: Receive instant updates when jobs complete
- **Reduced polling**: Eliminate the need to continuously check job status
- **Efficient resource usage**: Only process events when they occur
- **Scalable architecture**: Build event-driven applications that scale

## Code samples

Here are some code samples that can you help you get started:
[Using Adobe I/O Events](../code-sample/index.md#triggering-an-event-from-the-apis)

