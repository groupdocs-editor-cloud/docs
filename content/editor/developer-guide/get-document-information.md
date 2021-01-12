---
id: "get-document-information"
url: "editor/get-document-information"
title: "Get Document Information"
productName: "GroupDocs.Editor Cloud"
weight: 3
description: ""
keywords: ""
---

## Introduction ##

This REST API allows us to obtain basic information about the document and it's pages properties. The endpoint accepts the document storage path as input payload.
Here is the list of properties that can be obtained for a document:

* Document file extension;
* Document size in bytes;
* Document file format.
* Pages count
* Password protection

## Resources ##

```html
HTTP POST ~/info
```

[Swagger UI](https://apireference.groupdocs.cloud/editor/#/Info/GetInfo) lets you call this REST API directly from the browser.

### cURL Example ###

{{< tabs tabTotal="2" tabID="1" tabName1="Request" tabName2="Response" >}} {{< tab tabNum="1" >}}

```html
* First get JSON Web Token
* Please get your Client Id and Client Secret from https://dashboard.groupdocs.cloud/applications. Kindly place Client Id in "client_id" and Client Secret in "client_secret" argument.
curl -v "https://api.groupdocs.cloud/connect/token" \
-X POST \
-d "grant_type=client_credentials&client_id=xxxx&client_secret=xxxx" \
-H "Content-Type: application/x-www-form-urlencoded" \
-H "Accept: application/json"

* cURL example to get document information
curl -v "https://api.groupdocs.cloud/v1.0/editor/info" \
-X POST \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer
<jwt token>"
-d "{ FilePath: 'words/four-pages.docx' }"
```

{{< /tab >}} {{< tab tabNum="2" >}}

```html
{
  "pageCount": 4,
  "size": 8651,
  "isEncrypted": false,
  "formatName": "Office Open XML WordProcessingML Macro-Free Document (DOCX)",
  "formatExtension": "docx"
}
```

{{< /tab >}} {{< /tabs >}}

## SDKs ##

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of making requests and handling responses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-editor-cloud) for a complete list of GroupDocs.Editor Cloud SDKs along with working examples, to get you started in no time. Please check the article to learn how to add an SDK to your project.

### Get Document Information Examples ###

{{< tabs tabTotal="6" tabID="10" tabName1="C#" tabName2="Java" tabName3="PHP" tabName4="Node.js" tabName5="Python" tabName6="Ruby" >}} {{< tab tabNum="1" >}}

{{< gist groupdocscloud 34f0df87ff6e7aaffef5876bdcb04a38 Editor_CSharp_Get_Document_Information.cs >}}

{{< /tab >}} {{< tab tabNum="2" >}}

{{< gist groupdocscloud cb5b0d1ae842f50f90382640823a2004 Editor_Java_Get_Document_Information.java >}}

{{< /tab >}} {{< tab tabNum="3" >}}

{{< gist groupdocscloud 288fe44b5603cd7966fa72f293e91b88 Editor_Php_Get_Document_Information.php >}}

{{< /tab >}} {{< tab tabNum="6" >}}

{{< gist groupdocscloud ba011159eee59cd5a1f696ae6fadb2e4 Editor_Ruby_Get_Document_Information.rb >}}

{{< /tab >}} {{< tab tabNum="4" >}}

{{< gist groupdocscloud d42190d60101442ccba939ac4db41454 Editor_Node_Get_Document_Information.js >}}

{{< /tab >}} {{< tab tabNum="5" >}}

{{< gist groupdocscloud 49c298f42348259cd85175f315d57272 Editor_Python_Get_Document_Information.py >}}

{{< /tab >}} {{< /tabs >}}
