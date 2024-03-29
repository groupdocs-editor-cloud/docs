---
id: "get-supported-file-formats"
url: "editor/get-supported-file-formats"
title: "Get Supported File Formats"
productName: "GroupDocs.Editor Cloud"
weight: 2
description: ""
keywords: ""
toc: True
---



This REST API allows getting list of all [file formats supported ]({{< ref "editor/getting-started/supported-document-formats.md" >}})by GroupDocs.Editor Cloud product.

## Resources

The following GroupDocs.Editor Cloud REST API resource has been used in the [get supported file types](https://apireference.groupdocs.cloud/editor/#/Info/GetSupportedFileFormats) example.

```html
HTTP POST ~/formats
```

### cURL example

The following example demonstrates how to get supported file types.

{{< tabs "example1">}} {{< tab "Request" >}}

```bash
* First get JSON Web Token
* Please get your Client Id and Client Secret from https://dashboard.groupdocs.cloud/applications. Kindly place Client Id in "client_id" and Client Secret in "client_secret" argument.
curl -v "https://api.groupdocs.cloud/connect/token" \
-X POST \
-d "grant_type=client_credentials&client_id=xxxx&client_secret=xxxx" \
-H "Content-Type: application/x-www-form-urlencoded" \
-H "Accept: application/json"

* cURL example to get document information
curl -v "https://api.groupdocs.cloud/v1.0/editor/formats" \
-X GET \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer <jwt token>"

```

{{< /tab >}} {{< tab "Response" >}}

```json
{
  "formats": [
    {
      "extension": ".doc",
      "fileFormat": "Microsoft Word Document"
    },
    {
      "extension": ".docm",
      "fileFormat": "Word Open XML Macro-Enabled Document"
    },
    {
      "extension": ".docx",
      "fileFormat": "Microsoft Word Open XML Document"
    },
   ...
    {
      "extension": ".xlsx",
      "fileFormat": "Microsoft Excel Open XML Spreadsheet"
    }
  ]
}

```

{{< /tab >}} {{< /tabs >}}

[Swagger UI](https://apireference.groupdocs.cloud/editor/#/Info/GetSupportedFileFormats) lets you call this REST API directly from the browser.

### SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of making requests and handling responses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-editor-cloud) for a complete list of GroupDocs.Editor Cloud SDKs along with working examples, to get you started in no time. Please check [Available SDKs]({{< ref "editor/getting-started/available-sdks.md" >}}) article to learn how to add an SDK to your project.



{{< tabs "example2">}} {{< tab "C#" >}}

{{< gist groupdocscloud 34f0df87ff6e7aaffef5876bdcb04a38 Editor_CSharp_Get_Document_File_Types.cs >}}

{{< /tab >}} {{< tab "Java" >}}

{{< gist groupdocscloud cb5b0d1ae842f50f90382640823a2004 Editor_Java_Get_Document_File_Types.java >}}

{{< /tab >}} {{< tab "PHP" >}}

{{< gist groupdocscloud 288fe44b5603cd7966fa72f293e91b88 Editor_Php_Get_Document_File_Types.php >}}

{{< /tab >}} {{< tab "Ruby" >}}

{{< gist groupdocscloud ba011159eee59cd5a1f696ae6fadb2e4 Editor_Ruby_Get_Document_File_Types.rb >}}

{{< /tab >}} {{< tab "Node.js" >}}

{{< gist groupdocscloud d42190d60101442ccba939ac4db41454 Editor_Node_Get_Document_File_Types.js >}}

{{< /tab >}} {{< tab "Python" >}}

{{< gist groupdocscloud 49c298f42348259cd85175f315d57272 Editor_Python_Get_Document_File_Types.py >}}

{{< /tab >}} {{< /tabs >}}
