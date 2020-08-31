---
id: "working-with-text-documents"
url: "editor/working-with-text-documents"
title: "Working with Text Documents"
productName: "GroupDocs.Editor Cloud"
weight: 4
description: ""
keywords: ""
---

## Introduction ##

[Textual](https://wiki.fileformat.com/word-processing/txt/) documents are simple Plain Text flat files (TXT), that contain no images, pages, paragraphs, lists, tables and so on. However, users can create some primitive formatting like lists with leading markers, left indents with whitespaces, tables with pseudo-graphics, paragraphs with line breaks, and so on. GroupDocs.Editor Cloud can recognize some of these structures. Other non-obvious feature, that GroupDocs.Editor Cloud provides, is the ability to save edited TXT document not only back to TXT, but also to [WordProcessing](https://wiki.fileformat.com/word-processing/). There several steps that usage of [GroupDocs.Editor Cloud](https://products.groupdocs.cloud/editor) consists of:

1. Upload input document into cloud storage
1. Load the document into editable representation in the cloud storage (HTML file and resources)
1. Download HTML document (and resources, if needed) from storage
1. Edit HTML document at client side
1. Upload HTML document back into the storage
1. Save the edited document into Spreadsheet format in the storage
1. Download saved document

Steps 1, 3, 4, 5 are storage operations, please refer to this [Storage Operations]({{< ref "editor/developer-guide/storage-operations/_index.md" >}})) for usage details. Step 4 is a custom edit operation that can be performed with the programming language or 3rd party tools.

Below is a detailed description of steps 2 and 6.

## Loading Text Documents ##

This REST API provides an ability to load the input documents into an editable representation.

## Resources ##

```html

HTTP POST ~/load

```

[Swagger UI](https://apireference.groupdocs.cloud/editor/#/Edit) lets you call this REST API directly from the browser. The following properties of loading Text documents may be customized:
|---|---

|Name|Description|Comment
|---|---|---
|FileInfo.FilePath|The file path in the storage|Required property
|FileInfo.StorageName|Storage name|Could be omitted for default storage
|FileInfo.VersionId|File version Id|Useful for storages that support file versioning
|FileInfo.Password|The password to open file|Should be specified only for password-protected documents
|OutputPath|The full output path|The directory in storage, where editable files will be stored
|LeadingSpaces|Sets the preferred option of a leading space handling. By default converts leading spaces to the left indent.
|TrailingSpaces|Sets the preferred option of a trailing space handling. By default truncates all trailing spaces.
|EnablePagination|Allows to enable or disable pagination in the resultant HTML document. By default is disabled (false).

### cURL Example ###

Request

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
    'FileInfo': { 'FilePath': 'Text/sample.txt' },
  'OutputPath': 'Output',
  'EnablePagination': true
 }"
```

Response

```html
* Response will contain storage path to resultant documents
{
  "resourcesPath": "output\sample.files",
  "htmlPath": "output\sample.html"
}
```

## SDKs ##

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of making requests and handling responses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-editor-cloud) for a complete list of GroupDocs.Editor Cloud SDKs along with working examples, to get you started in no time. Please check the article to learn how to add an SDK to your project.

### Working with Text Documents Examples ###

C#

{{< gist groupdocscloud 34f0df87ff6e7aaffef5876bdcb04a38 Editor_CSharp_Working_With_Text.cs >}}

Java

{{< gist groupdocscloud cb5b0d1ae842f50f90382640823a2004 Editor_Java_Working_With_Text.java >}}

PHP

{{< gist groupdocscloud 288fe44b5603cd7966fa72f293e91b88 Editor_Php_Working_With_Text.php >}}

Ruby

{{< gist groupdocscloud ba011159eee59cd5a1f696ae6fadb2e4 Editor_Ruby_Working_With_Text.rb >}}

Node

{{< gist groupdocscloud d42190d60101442ccba939ac4db41454 Editor_Node_Working_With_Text.js >}}

Python

{{< gist groupdocscloud 49c298f42348259cd85175f315d57272 Editor_Python_Working_With_Text.py >}}
