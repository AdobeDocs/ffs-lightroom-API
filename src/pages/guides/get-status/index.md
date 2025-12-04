---
title: Get Lightroom API Status and Results
description: Learn how to get the status and results of a Lightroom API job.
keywords:
  - Adobe Lightroom API
  - status
  - results
  - job
  - API
  - REST API
  - cloud processing
  - photo automation
  - bulk editing
  - preset management
contributors:
  - 'https://github.com/khound'
  - 'https://github.com/archyposada'
hideBreadcrumbNav: true
---
# Get status and results

Use the Job ID with the `href` link that's returned in the response to poll for the status of a Lightroom API job.

When a successful job completes, the output file is available at the `href` link in the response.

If the job fails due to an error, the `errorDetails` field in the response will contain the details of the failure.

```shell
curl -X GET \
  https://image.adobe.io/lrService/status/<jobId> \
  -H "Authorization: Bearer ${TOKEN}"  \
  -H "x-api-key: ${API_KEY}" \
  -H "Content-Type: application/json" \
```

**Example response**

```json
{
  "jobId":"<JOB_ID>",
  "created":"2018-01-04T12:57:15.12345:Z",
  "modified":"2018-01-04T12:58:36.12345:Z",
  "outputs":[
  {
      "input":"<INPUT_FILE_HREF>",
      "status":"succeeded",
      "_links":{
        "self":
        {
          "href":"<OUTPUT_FILE_HREF>",
          "storage":"<STORAGE_LOCATION>"
        }
      }
    }
  ],
  "_links":{
    "self":{
      "href":"https://image.adobe.io/lrService/status/<JOB_ID>"
    }
  }
}
```
