---
id: "working-with-spreadsheets"
url: "editor/working-with-spreadsheets"
title: "Working with Spreadsheets"
productName: "GroupDocs.Editor Cloud"
weight: 2
description: ""
keywords: ""
toc: True
---

[Spreadsheet](https://wiki.fileformat.com/spreadsheet/) documents are presented by many formats: XLS, XLSX, XLSM, XLSB, ODS, SXC and others, which are supported by [GroupDocs.Editor Cloud](https://products.groupdocs.cloud/editor).
There several steps that usage of GroupDocs.Editor Cloud consists of:

1. Upload input document into cloud storage
1. Load the document into editable representation in the cloud storage (HTML file and resources)
1. Download HTML document (and resources, if needed) from storage
1. Edit HTML document at client side
1. Upload HTML document back into the storage
1. Save the edited document into Spreadsheet format in the storage
1. Download saved document

Steps 1, 3, 4, 5 are storage operations, please refer to this [Storage Operations]({{< ref "editor/developer-guide/storage-operations/_index.md" >}})) for usage details. Step 4 is a custom edit operation that can be performed with the programming language or 3rd party tools.

Below is a detailed description of steps 2 and 6.

## Loading Spreadsheet documents

This REST API provides an ability to load the input documents into an editable representation.

## Resources

```html
HTTP POST ~/load
```

[Swagger UI](https://apireference.groupdocs.cloud/editor/#/Edit) lets you call this REST API directly from the browser. The following properties of loading Spreadsheet documents may be customized:

|Name|Description|Comment
|---|---|---
|FileInfo.FilePath|The file path in the storage|Required property
|FileInfo.StorageName|Storage name|Could be omitted for default storage
|FileInfo.VersionId|File version Id|Useful for storages that support file versioning
|FileInfo.Password|The password to open file|Should be specified only for password-protected documents
|OutputPath|The full output path|The directory in storage, where editable files will be stored
|WorksheetIndex|Allows to specify the 0-based index of the worksheet (tab) of the input Spreadsheet of the document, which should be converted to the HTML.|Required
|ExcludeHiddenWorksheets|Allows to exclude hidden worksheets in the input Spreadsheet document, so they will be totally ignored. Default is false - hidden worksheets are available and processed as normal.

## cURL example

{{< tabs "example1">}} {{< tab "Request" >}}

```bash
* First get JSON Web Token
* Please get your Client Id and Client Secret from https://dashboard.groupdocs.cloud/applications. Kindly place Client Id in "client_id" and Client Secret in "client_secret" argument.
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
    'FileInfo': { 'FilePath': 'Spreadsheet/four-sheets.xlsx' },
  'OutputPath': 'Output',
  'WorksheetIndex': 0
 }"
```

{{< /tab >}} {{< tab "Response" >}}

```json
* Response will contain storage path to resultant documents
{
  "resourcesPath": "output\four-pages.files",
  "htmlPath": "output\four-pages.html"
}
```

{{< /tab >}} {{< /tabs >}}

## SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of making requests and handling responses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-editor-cloud) for a complete list of GroupDocs.Editor Cloud SDKs along with working examples, to get you started in no time. Please check the article to learn how to add an SDK to your project.

{{< tabs "example2">}} {{< tab "C#" >}}

{{< gist groupdocscloud 34f0df87ff6e7aaffef5876bdcb04a38 Editor_CSharp_Working_With_Spreadsheets.cs >}}

{{< /tab >}} {{< tab "Java" >}}

{{< gist groupdocscloud cb5b0d1ae842f50f90382640823a2004 Editor_Java_Working_With_Spreadsheets.java >}}

{{< /tab >}} {{< tab "PHP" >}}

{{< gist groupdocscloud 288fe44b5603cd7966fa72f293e91b88 Editor_Php_Working_With_Spreadsheets.php >}}

{{< /tab >}} {{< tab "Ruby" >}}

{{< gist groupdocscloud ba011159eee59cd5a1f696ae6fadb2e4 Editor_Ruby_Working_With_Spreadsheets.rb >}}

{{< /tab >}} {{< tab "Node.js" >}}

{{< gist groupdocscloud d42190d60101442ccba939ac4db41454 Editor_Node_Working_With_Spreadsheets.js >}}

{{< /tab >}} {{< tab "Python" >}}

{{< gist groupdocscloud 49c298f42348259cd85175f315d57272 Editor_Python_Working_With_Spreadsheets.py >}}

{{< /tab >}} {{< /tabs >}}
