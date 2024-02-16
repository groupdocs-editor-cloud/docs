---
id: "working-with-storage"
url: "editor/working-with-storage"
title: "Working With Storage"
productName: "GroupDocs.Editor Cloud"
weight: 1
description: ""
keywords: ""
toc: True
---

## Storage existence API

This API intended for checking the existence of cloud storage with a given name from [GroupDocs Cloud Storage](https://dashboard.groupdocs.cloud).

### API Explorer

[GroupDocs.Editor Cloud API Reference](https://apireference.groupdocs.cloud/editor/#/) lets you try out [Storage existence API](https://apireference.groupdocs.cloud/editor/#/Storage/StorageExists) right away in your browser! It allows you to effortlessly interact and try out every single operation our APIs expose.

### Request parameters

|Parameter|Description
|---|---
|**storageName**|Storage name

### cURL example

{{< tabs "example1">}} {{< tab "Request" >}}

```bash
curl -X GET "https://api.groupdocs.cloud/v1.0/editor/storage/MyStorage/exist" -H  "accept: application/json" -H  "authorization: Bearer  [Access Token]"

```

{{< /tab >}} {{< tab "Response" >}}

```json
{
  "exists": true
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-editor-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-editor-cloud), it hides the [Storage existence](https://apireference.groupdocs.cloud/editor/#/Storage/StorageExists) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.

{{< tabs "example2">}} {{< tab "C#" >}}

{{< gist groupdocscloud 34f0df87ff6e7aaffef5876bdcb04a38 Editor_CSharp_Storage_Exist.cs >}}

{{< /tab >}} {{< tab "Java" >}}

{{< gist groupdocscloud cb5b0d1ae842f50f90382640823a2004 Editor_Java_Storage_Exist.java >}}

{{< /tab >}} {{< tab "PHP" >}}

{{< gist groupdocscloud 288fe44b5603cd7966fa72f293e91b88 Editor_Php_Storage_Exist.php >}}

{{< /tab >}} {{< tab "Ruby" >}}

{{< gist groupdocscloud ba011159eee59cd5a1f696ae6fadb2e4 Editor_Ruby_Working_With_Spreadsheets.rb >}}

{{< /tab >}} {{< tab "Node.js" >}}

{{< gist groupdocscloud d42190d60101442ccba939ac4db41454 Editor_Node_Storage_Exist.js >}}

{{< /tab >}} {{< tab "Python" >}}

{{< gist groupdocscloud 49c298f42348259cd85175f315d57272 Editor_Python_Storage_Exist.py >}}

{{< /tab >}} {{< /tabs >}}

## Storage object existence API

This API intended for checking the existence of a file or folder in [GroupDocs Cloud Storage](https://dashboard.groupdocs.cloud).

### API Explorer

[GroupDocs.Editor Cloud API Reference](https://apireference.groupdocs.cloud/editor/#/) lets you try out [Storage existence API](https://apireference.groupdocs.cloud/editor/#/Storage/StorageExists) right away in your browser! It allows you to effortlessly interact and try out every single operation our APIs expose.

### Request parameters

|Parameter|Description
|---|---
|**path**|Path of the file or folder. Required. Can be passed as a query string parameter or as part of the URL
|storageName|Name of the storage. If not set, then default storage used
|versionId|File version id

### cURL example

{{< tabs "example3">}} {{< tab "Request" >}}

```bash
curl -X GET "https://api.groupdocs.cloud/v1.0/editor/storage/exist/editordocs?storageName=MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"
```

{{< /tab >}} {{< tab "Response" >}}

```json
{
  "exists": true,
  "isFolder": true
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-editor-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-editor-cloud), it hides the [Storage Object existence](https://apireference.groupdocs.cloud/editor/#/Storage/ObjectExists) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.

{{< tabs "example4">}} {{< tab "C#" >}}

{{< gist groupdocscloud 34f0df87ff6e7aaffef5876bdcb04a38 Editor_CSharp_Object_Exists.cs >}}

{{< /tab >}} {{< tab "Java" >}}

{{< gist groupdocscloud cb5b0d1ae842f50f90382640823a2004 Editor_Java_Object_Exists.java >}}

{{< /tab >}} {{< tab "PHP" >}}

{{< gist groupdocscloud 288fe44b5603cd7966fa72f293e91b88 Editor_Php_Object_Exists.php >}}

{{< /tab >}} {{< tab "Ruby" >}}

{{< gist groupdocscloud ba011159eee59cd5a1f696ae6fadb2e4 Editor_Ruby_Object_Exists.rb >}}

{{< /tab >}} {{< tab "Node.js" >}}

{{< gist groupdocscloud d42190d60101442ccba939ac4db41454 Editor_Node_Object_Exists.js >}}

{{< /tab >}} {{< tab "Python" >}}

{{< gist groupdocscloud 49c298f42348259cd85175f315d57272 Editor_Python_Object_Exists.py >}}

{{< /tab >}} {{< /tabs >}}

## Storage Space Usage API

This API intended for getting total and used space of the [GroupDocs Cloud Storage](https://dashboard.groupdocs.cloud)

### API Explorer

[GroupDocs.Editor Cloud API Reference](https://apireference.groupdocs.cloud/editor/#/) lets you try out [storage space usage API](https://apireference.groupdocs.cloud/editor/#/Storage/GetDiscUsage) right away in your browser! It allows you to effortlessly interact and try out every single operation our APIs expose.

### Request parameters

|Parameter|Description
|---|---
|storageName|Name of the storage. If not set, then default storage used

### cURL example

{{< tabs "example5">}} {{< tab "Request" >}}

```bash
curl -X GET "https://api.groupdocs.cloud/v1.0/editor/storage/disc?storageName=MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"
```

{{< /tab >}} {{< tab "Response" >}}

```json
{
  "usedSize": 31032368,
  "totalSize": 3221225472
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-editor-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-editor-cloud), it hides the [storage space usage API](https://apireference.groupdocs.cloud/editor/#/Storage/GetDiscUsage) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.

{{< tabs "example6">}} {{< tab "C#" >}}

{{< gist groupdocscloud 34f0df87ff6e7aaffef5876bdcb04a38 Editor_CSharp_Get_Disc_Usage.cs >}}

{{< /tab >}} {{< tab "Java" >}}

{{< gist groupdocscloud cb5b0d1ae842f50f90382640823a2004 Editor_Java_Get_Disc_Usage.java >}}

{{< /tab >}} {{< tab "PHP" >}}

{{< gist groupdocscloud 288fe44b5603cd7966fa72f293e91b88 Editor_Php_Get_Disc_Usage.php >}}

{{< /tab >}} {{< tab "Ruby" >}}

{{< gist groupdocscloud ba011159eee59cd5a1f696ae6fadb2e4 Editor_Ruby_Get_Disc_Usage.rb >}}

{{< /tab >}} {{< tab "Node.js" >}}

{{< gist groupdocscloud d42190d60101442ccba939ac4db41454 Editor_Node_Get_Disc_Usage.js >}}

{{< /tab >}} {{< tab "Python" >}}

{{< gist groupdocscloud 49c298f42348259cd85175f315d57272 Editor_Python_Get_Disc_Usage.py >}}

{{< /tab >}} {{< /tabs >}}

## Storage File Versions API

This API intended for getting the list of file versions, stored in the [GroupDocs Cloud Storage](https://dashboard.groupdocs.cloud)

### API Explorer

[GroupDocs.Editor Cloud API Reference](https://apireference.groupdocs.cloud/editor/#/) lets you try out [Storage File Versions API](https://apireference.groupdocs.cloud/editor/#/Storage/GetFileVersions) right away in your browser! It allows you to effortlessly interact and try out every single operation our APIs expose.

### Request parameters

|Parameter|Description
|---|---
|**path**|Path of the file including file name and extension e.g. /Folder1/file.ext. Required. Can be passed as a query string parameter or as part of the URL
|storageName|Name of the storage. If not set, then default storage used

### cURL example

{{< tabs "example7">}} {{< tab "Request" >}}

```bash
curl -X GET "https://api.groupdocs.cloud/v1.0/editor/storage/version/one-page.docx?storageName=MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"
```

{{< /tab >}} {{< tab "Response" >}}

```json
{
  "value": [
    {
      "versionId": "null",
      "isLatest": true,
      "name": "one-page.docx",
      "isFolder": false,
      "modifiedDate": "2018-08-16T19:45:05+00:00",
      "size": 347612,
      "path": "/one-page.docx"
    }
  ]
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-editor-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-editor-cloud), it hides the [Storage File Versions API](https://apireference.groupdocs.cloud/editor/#/Storage/GetFileVersions) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.

{{< tabs "example8">}} {{< tab "C#" >}}

{{< gist groupdocscloud 34f0df87ff6e7aaffef5876bdcb04a38 Editor_CSharp_Get_File_Versions.cs >}}

{{< /tab >}} {{< tab "Java" >}}

{{< gist groupdocscloud cb5b0d1ae842f50f90382640823a2004 Editor_Java_Get_File_Versions.java >}}

{{< /tab >}} {{< tab "PHP" >}}

{{< gist groupdocscloud 288fe44b5603cd7966fa72f293e91b88 Editor_Php_Get_File_Versions.php >}}

{{< /tab >}} {{< tab "Ruby" >}}

{{< gist groupdocscloud ba011159eee59cd5a1f696ae6fadb2e4 Editor_Ruby_Get_File_Versions.rb >}}

{{< /tab >}} {{< tab "Node.js" >}}

{{< gist groupdocscloud d42190d60101442ccba939ac4db41454 Editor_Node_Get_File_Versions.js >}}

{{< /tab >}} {{< tab "Python" >}}

{{< gist groupdocscloud 49c298f42348259cd85175f315d57272 Editor_Python_Get_File_Versions.py >}}

{{< /tab >}} {{< /tabs >}}
