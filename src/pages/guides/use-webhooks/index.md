---
title: Using Lightroom API Webhooks through Adobe I/O Events
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

# Using webhooks through Adobe I/O Events

Use webhooks with Adobe Lightroom API through Adobe I/O Events.

Adobe I/O Events offers the possibility to build an event-driven application, based on events originating from Lightroom and Lightroom APIs. To start listening for events, your application needs to register a webhook URL, specifying the Event Types to receive. Whenever a matching event gets triggered, your application is notified through an HTTP POST request to the webhook URL.

The Event Provider for Lightroom and Lightroom APIs is `Imaging API Events`. This event provider has two event types:

1. `Lightroom API events`
2. `Lightroom API events`

As the names indicate, these event types represent events triggered by the individual APIs.

## Registering your application to our event provider

Prerequisites needed to use the Event Provider:

1. In order to use the Adobe I/O Events you will need to create a project on Adobe I/O Console. [Follow the steps listed in Getting Started page to create a project](../../getting_started/index.md) if you haven't created one yet.
1. Learn [more about creating a Webhook application.](https://www.adobe.io/apis/experienceplatform/events/docs.html#!adobedocs/adobeio-events/master/intro/webhooks_intro.md) This page provides all of the details you will need to build a basic application.
1. To register the webhook to the service integration, [use the steps in the guided introduction to Adobe I/O Events](https://developer.adobe.com/events/docs/guides/#getting-started).

After the webhook has been successfully registered, you'll receive the events for any submitted job that either succeeded or failed, from the event types that are selected. This eliminates the need for your application to poll for the status of the job using the job ID.

## Triggering an event from the APIs

To start receiving the events in your webhook application, pass your IMS organization ID in the header:

```shell
 -H 'x-gw-ims-org-id: ${IMS_ORG_ID}'  \
 ```

 The example below demonstrates using this header in an Auto Tone job and a sample event received for that job.

### Step 1: Initiating the job

This initiates the Auto Tone job using the header to trigger an event.

```shell
curl -X POST \
  https://image.adobe.io/lrService/autoTone \
  -H "Authorization: Bearer ${TOKEN}" \
  -H "Content-Type: application/json" \
  -H "x-api-key: ${API_KEY}" \
  -H "x-gw-ims-org-id: ${IMS_ORG_ID}" \
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

The asynchronous job returns a response containing the `href` to poll for the job status.

```json
{
    "_links": {
        "self": {
            "href": "https://image.adobe.io/lrService/status/eb4a9211-eb8a-4e88-b853-b9c08ba47427"
        }
    }
}
```

### Step 2: Retrieve the job's status on the webhook application when the job is complete

The `body` property in the `event` object contains the result of the job, as in this example:

```json
{
  "event_id": "7b59cc70-88d7-4895-b204-87f5350a0cce",
  "event": {
    "header": {
      "msgType": "JOB_COMPLETION_STATUS",
      "msgId": "eb4a9211-eb8a-4e88-b853-b9c08ba47427",
      "imsOrgId": "<IMS org ID>",
      "eventCode": "lightroom-job-status",
      "_pipelineMeta": {
        "pipelineMessageId": "1586290300876:944289:VA7_A1:149:0"
      },
      "_smarts": {
        "definitionId": "3ee6c9056a9d72fc40e09ddf5fdbb0af752e8e49",
        "runningSmartId": "psmart-yw6wosjksniuuathenny"
      },
      "_adobeio": {
        "imsOrgId": "<IMS org ID>",
        "providerMetadata": "di_event_code",
        "eventCode": "lightroom-job-status"
      }
    },
    "body": {
      "jobId": "eb4a9211-eb8a-4e88-b853-b9c08ba47427",
      "outputs": [
        {
          "input": "<signed GET URL>",
          "status": "succeeded",
          "_links": {
            "self": [
              {
                "href": "<signed POST URL>",
                "storage": "<storage>"
              }
            ]
          }
        }
      ],
      "_links": {
        "self": {
          "href": "https://image.adobe.io/lrService/status/eb4a9211-eb8a-4e88-b853-b9c08ba47427"
        }
      }
    }
  }
}
```
