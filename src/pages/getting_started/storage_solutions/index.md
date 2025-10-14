---
title: Lightroom File Storage Solutions
description: This page explains the input and output storage solutions that are acceptable for use with Lightroom API.
---
# Input and output file storage

The Lightroom API works with any public or signed URL. We've documented a few of the most common storage services and how to generate the URLs programmatically.

**AWS S3:** Pre-signed GET/PUT URL. See Amazon's documentation for [more information about pre-signed URLs on S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/PresignedUrlUploadObject.html). Below are code samples that show you how to generate your pre-signed URLs programmatically:

* [Node.js](https://github.com/AdobeDocs/cis-photoshop-api-docs/tree/main/sample-code/storage-app/aws-s3/presignedURLs.js) Please note that creating pre-signed URLs for AWS S3 requires signature version S3V4. This is demonstrated in the sample code.
* [Python](https://github.com/AdobeDocs/cis-photoshop-api-docs/tree/main/sample-code/storage-app/azure/presignedURLs.py)

We also have [a Python application](https://github.com/AdobeDocs/cis-photoshop-api-docs/tree/main/sample-code/storage-app/aws-s3/example.py) that provides a working example of how to call our API using assets stored in AWS S3.  

**Google Drive:** Signed GET/PUT URL. Learn [how to set up your Google drive account for access to creating a signed URL](https://www.labnol.org/google-api-service-account-220404). Here are some code samples for getting signed URLs.

* [Node.js](https://github.com/AdobeDocs/cis-photoshop-api-docs/tree/main/sample-code/storage-app/googledrive/presignedURLs.js)

**Azure:** SAS (Shared Access Signature) for upload/download. Learn [how to generate a Shared Access Signature](https://azuresdkdocs.blob.core.windows.net/$web/python/azure-storage-blob/12.9.0/index.html). Here are some code samples for generating a URL with Shared Access Signature.

* [Node.js](https://github.com/AdobeDocs/cis-photoshop-api-docs/tree/main/sample-code/storage-app/azure/presignedURLs.js)
* [Python](https://github.com/AdobeDocs/cis-photoshop-api-docs/tree/main/sample-code/storage-app/azure/presignedURLs.py)

**Dropbox:** Temporary upload/download URLs. See [how to generate an upload/download](https://www.dropbox.com/developers/documentation). You can also [create a file upload link for Dropbox](https://www.dropbox.com/developers/documentation/http/documentation#files-get_temporary_upload_link).

You can test to see if your public URL or pre-signed URL is working.
Run the cURL command below to see if your input file path is working:

```bash
  curl -X GET <Your file path> --output <some-file.jpg>
  ```

If you are using a pre-signed URL, put your file path within "":

```bash
  curl -X GET "<Your file path>" --output <some-file.jpg>
  ```

Run the cURL command below to see if your output file path is working:

```bash
  curl -X PUT <Your file path> -d <some-file.txt>
  ```

If you are using a pre-signed URL, put your file path within "":

```bash
  curl -X PUT "<Your file path>" -d <some-file.txt>
  ```
