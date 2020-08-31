---
id: "working-with-wordprocessing-documents"
url: "editor/working-with-wordprocessing-documents"
title: "Working with WordProcessing Documents"
productName: "GroupDocs.Editor Cloud"
weight: 1
description: ""
keywords: ""
---

## Introduction ##

[WordProcessing](https://wiki.fileformat.com/word-processing/) is the most used and known document family format, that includes DOC, DOT, DOCX, DOCM, DOTX, ODT, RTF and much more. All these formats are supported by the [GroupDocs.Editor Cloud](https://products.groupdocs.cloud/editor). There several steps that usage of GroupDocs.Editor Cloud consists of:

1. Upload input document into cloud storage
1. Load the document into editable representation in the cloud storage (HTML file and resources)
1. Download HTML document (and resources, if needed) from storage
1. Edit HTML document at client side
1. Upload HTML document back into the storage
1. Save the edited document into WordProcessing format in the storage
1. Download saved document

Steps 1, 3, 4, 5 are storage operations, please refer to this [Storage Operations]({{< ref "editor/developer-guide/storage-operations/_index.md" >}})) for usage details. Step 4 is a custom edit operation that can be performed with the programming language or 3rd party tools.

Below is a detailed description of steps 2 and 6.

## Loading WordProcessing documents ##

This REST API provides an ability to load the input documents into an editable representation.

## Resources ##

```html
HTTP POST ~/load
```

[Swagger UI](https://apireference.groupdocs.cloud/editor/#/Edit) lets you call this REST API directly from the browser. The following properties of loading WordProcessing documents may be customized:

|Name|Description|Comment
|---|---|---
|FileInfo.FilePath|The file path in the storage|Required property
|FileInfo.StorageName|Storage name|Could be omitted for default storage
|FileInfo.VersionId|File version Id|Useful for storages that support file versioning
|FileInfo.Password|The password to open file|Should be specified only for password-protected documents
|OutputPath|The full output path|The directory in storage, where editable files will be stored
|EnablePagination|Allows to enable or disable pagination in the resultant HTML document. By default is disabled (false).
|EnableLanguageInformation|Specifies whether language information is exported to the HTML markup in a form of 'lang' HTML attributes. This option may be useful for roundtrip conversion of the multi-language documents. By default, it is disabled (false).
|FontExtraction|Responsible for extracting font resources, which are used in the input WordProcessing document. By default doesn't extract any fonts (NotExtract). Possible values are: NotExtract, ExtractAllEmbedded,ExtractEmbeddedWithoutSystem, ExtractAll

### cURL Example ###

{{< tabs tabTotal="2" tabID="1" tabName1="Request" tabName2="Response" >}} {{< tab tabNum="1" >}}

```html
* First get JSON Web Token
* Please get your App Key and App SID from https://dashboard.groupdocs.cloud/#/apps. Kindly place App Key in "client_secret" and App SID in "client_id" argument.
curl -v "https://api.groupdocs.cloud/connect/token" \
-X POST \
-d "grant_type=client_credentials&client_id=xxxx&client_secret=xxxx" \
-H "Content-Type: application/x-www-form-urlencoded" \
-H "Accept: application/json"

* cURL example to load document
curl -v "https://api.groupdocs.cloud/v1.0/editor/load" \
-X POST \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer
<jwt token>"
-d "{
    'FileInfo': { 'FilePath': 'WordProcessing/four-pages.docx' },
  'OutputPath': 'Output',
  'EnablePagination': true,
  'FontExtraction': 'ExtractAllEmbedded'
 }"
```

{{< /tab >}} {{< tab tabNum="2" >}}

```html
* Response will contain storage path to resultant documents
{
  "resourcesPath": "output\four-pages.files",
  "htmlPath": "output\four-pages.html"
}
```

{{< /tab >}} {{< /tabs >}}

## SDKs ##

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of making requests and handling responses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-editor-cloud) for a complete list of GroupDocs.Editor Cloud SDKs along with working examples, to get you started in no time. Please check  article to learn how to add an SDK to your project.

### Working with WordProcessing Documents Examples ###

{{< tabs tabTotal="6" tabID="10" tabName1="C#" tabName2="Java" tabName3="PHP" tabName4="Node.js" tabName5="Python" tabName6="Ruby" >}} {{< tab tabNum="1" >}}

{{< gist groupdocscloud 34f0df87ff6e7aaffef5876bdcb04a38 Editor_CSharp_Working_With_Wordprocessing.cs >}}

{{< /tab >}} {{< tab tabNum="2" >}}

{{< gist groupdocscloud cb5b0d1ae842f50f90382640823a2004 Editor_Java_Working_With_Wordprocessing.java >}}

{{< /tab >}} {{< tab tabNum="3" >}}

{{< gist groupdocscloud 288fe44b5603cd7966fa72f293e91b88 Editor_Php_Working_With_Wordprocessing.php >}}

{{< /tab >}} {{< tab tabNum="6" >}}

{{< gist groupdocscloud ba011159eee59cd5a1f696ae6fadb2e4 Editor_Ruby_Working_With_Wordprocessing.rb >}}

{{< /tab >}} {{< tab tabNum="4" >}}

{{< gist groupdocscloud d42190d60101442ccba939ac4db41454 Editor_Node_Working_With_Wordprocessing.js >}}

{{< /tab >}} {{< tab tabNum="5" >}}

{{< gist groupdocscloud 49c298f42348259cd85175f315d57272 Editor_Python_Working_With_Wordprocessing.py >}}

{{< /tab >}} {{< /tabs >}}
