---
id: "working-with-folder"
url: "editor/working-with-folder"
title: "Working With Folder"
productName: "GroupDocs.Editor Cloud"
weight: 2
description: ""
keywords: ""
toc: True
---

## Get the File Listing of a Specific Folder

This API allows you to get a list of all files of a specific folder from the specified Cloud Storage. If you do not pass storage name API will find the folder in GroupDocs Cloud Storage.

### API Explorer

[GroupDocs.Editor Cloud API Reference](https://apireference.groupdocs.cloud/editor/) lets you try out [List Files in a Folder API](https://apireference.groupdocs.cloud/editor/#/Folder/GetFilesList) right away in your browser. It allows you to effortlessly interact and try out every single operation that our APIs expose.

### Request parameters

|Parameter|Description
|---|---
|**path**|Path of the folder. Required. Can be passed as a query string parameter or as part of the URL
|storageName|Name of the storage. If not set, then default storage used

### cURL example

{{< tabs "example1">}} {{< tab "Request" >}}

```bash
curl -X GET "https://api.groupdocs.cloud/v1.0/editor/storage/folder/editordocs?storageName=MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"

```

{{< /tab >}} {{< tab "Response" >}}

```json
{
  "value": [
    {
      "name": "four-pages.docx",
      "isFolder": false,
      "modifiedDate": "2019-03-20T12:35:38+00:00",
      "size": 8651,
      "path": "/editordocs/four-pages.docx"
    },
    {
      "name": "one-page.docx",
      "isFolder": false,
      "modifiedDate": "2019-03-20T12:17:34+00:00",
      "size": 351348,
      "path": "/editordocs/one-page.docx"
    },
    {
      "name": "password-protected.docx",
      "isFolder": false,
      "modifiedDate": "2019-03-20T12:35:40+00:00",
      "size": 10240,
      "path": "/editordocs/password-protected.docx"
    },
    {
      "name": "sample.mpp",
      "isFolder": false,
      "modifiedDate": "2019-03-20T12:29:10+00:00",
      "size": 289792,
      "path": "/editordocs/sample.mpp"
    },
    {
      "name": "three-layouts.dwf",
      "isFolder": false,
      "modifiedDate": "2019-03-20T12:26:42+00:00",
      "size": 15433,
      "path": "/editordocs/three-layouts.dwf"
    },
    {
      "name": "two-hidden-pages.vsd",
      "isFolder": false,
      "modifiedDate": "2019-03-20T12:17:36+00:00",
      "size": 457728,
      "path": "/editordocs/two-hidden-pages.vsd"
    },
    {
      "name": "uses-custom-font.pptx",
      "isFolder": false,
      "modifiedDate": "2019-03-20T12:32:30+00:00",
      "size": 39823,
      "path": "/editordocs/uses-custom-font.pptx"
    },
    {
      "name": "with-hidden-rows-and-columns.xlsx",
      "isFolder": false,
      "modifiedDate": "2019-03-20T12:17:37+00:00",
      "size": 15986,
      "path": "/editordocs/with-hidden-rows-and-columns.xlsx"
    }
  ]
}

```

{{< /tab >}} {{< /tabs >}}

### SDK examples

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-editor-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-editor-cloud), it hides the [Folder API](https://apireference.groupdocs.cloud/editor/#/Folder) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.

{{< tabs "example2">}} {{< tab "C#" >}}

{{< gist groupdocscloud 34f0df87ff6e7aaffef5876bdcb04a38 Editor_CSharp_Get_Files_List.cs >}}

{{< /tab >}} {{< tab "Java" >}}

{{< gist groupdocscloud cb5b0d1ae842f50f90382640823a2004 Editor_Java_Get_Files_List.java >}}

{{< /tab >}} {{< tab "PHP" >}}

{{< gist groupdocscloud 288fe44b5603cd7966fa72f293e91b88 Editor_Php_Get_Files_List.php >}}

{{< /tab >}} {{< tab "Ruby" >}}

{{< gist groupdocscloud ba011159eee59cd5a1f696ae6fadb2e4 Editor_Ruby_Get_Files_List.rb >}}

{{< /tab >}} {{< tab "Node.js" >}}

{{< gist groupdocscloud d42190d60101442ccba939ac4db41454 Editor_Node_Get_Files_List.js >}}

{{< /tab >}} {{< tab "Python" >}}

{{< gist groupdocscloud 49c298f42348259cd85175f315d57272 Editor_Python_Get_Files_List.py >}}

{{< /tab >}} {{< /tabs >}}

## Create a New Folder

This API allows you to create a new folder in the specified Cloud Storage. If you do not pass storage name API will create New Folder in default Cloud Storage.

### API Explorer

[GroupDocs.Editor Cloud API Reference](https://apireference.groupdocs.cloud/editor/) lets you try out [Create Folder API](https://apireference.groupdocs.cloud/editor/#/Folder/CreateFolder) right away in your browser. It allows you to effortlessly interact and try out every single operation that our APIs expose.

### Request parameters

|Parameter|Description
|---|---
|**path**|Target folder’s path e.g. Folder1/Folder2/. The folders will be created recursively. Required. Can be passed as a query string parameter or as part of the URL
|storageName|Name of the storage. If not set, then default storage used

### cURL example

{{< tabs "example3">}} {{< tab "Request" >}}

```bash
curl -X POST "https://api.groupdocs.cloud/v1.0/editor/storage/folder/editordocs?storageName=MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"

```

{{< /tab >}} {{< tab "Response" >}}

```json
{
  "code": 200,
  "status": "OK"
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-editor-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-editor-cloud), it hides the [Folder API](https://apireference.groupdocs.cloud/editor/#/Folder/) calls and lets you use GroupDocs for Cloud features in a native way for your preferred language.

{{< tabs "example4">}} {{< tab "C#" >}}

{{< gist groupdocscloud 34f0df87ff6e7aaffef5876bdcb04a38 Editor_CSharp_Create_Folder.cs >}}

{{< /tab >}} {{< tab "Java" >}}

{{< gist groupdocscloud cb5b0d1ae842f50f90382640823a2004 Editor_Java_Create_Folder.java >}}

{{< /tab >}} {{< tab "PHP" >}}

{{< gist groupdocscloud 288fe44b5603cd7966fa72f293e91b88 Editor_Php_Create_Folder.php >}}

{{< /tab >}} {{< tab "Ruby" >}}

{{< gist groupdocscloud ba011159eee59cd5a1f696ae6fadb2e4 Editor_Ruby_Create_Folder.rb >}}

{{< /tab >}} {{< tab "Node.js" >}}

{{< gist groupdocscloud d42190d60101442ccba939ac4db41454 Editor_Node_Create_Folder.js >}}

{{< /tab >}} {{< tab "Python" >}}

{{< gist groupdocscloud 49c298f42348259cd85175f315d57272 Editor_Python_Create_Folder.py >}}

{{< /tab >}} {{< /tabs >}}

## Delete a Particular Folder

This API allows you to delete a particular folder in the specified Cloud Storage. If you do not pass storage name API will create New Folder in default Cloud Storage. To remove recursively inner folder/files you need to pass true value to a recursive parameter in Request. If it is set to false and folder contains data then API throws the exception.

### API Explorer

[GroupDocs.Editor Cloud API Reference](https://apireference.groupdocs.cloud/editor/#/) lets you try out [Delete a Particular Folder API](https://apireference.groupdocs.cloud/editor/#/Folder/DeleteFolder) right away in your browser. It allows you to effortlessly interact and try out every single operation that our APIs expose.

### Request parameters

|Parameter|Description
|---|---
|**path**|Folder path e.g. /Folder1. Required. Can be passed as a query string parameter or as part of the URL
|storageName|Name of the storage. If not set, then default storage used

### cURL example

{{< tabs "example5">}} {{< tab "Request" >}}

```bash
curl -X DELETE "https://api.groupdocs.cloud/v1.0/editor/storage/folder/editordocs?storageName=MyStorage&recursive#true" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"

```

{{< /tab >}} {{< tab "Response" >}}

```json
{
  "code": 200,
  "status": "OK"
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-editor-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-editor-cloud), it hides the [Delete Folder API](https://apireference.groupdocs.cloud/editor/#/Folder/DeleteFolder) calls and lets you use GroupDocs for Cloud features in a native way for your preferred language.

{{< tabs "example6">}} {{< tab "C#" >}}

{{< gist groupdocscloud 34f0df87ff6e7aaffef5876bdcb04a38 Editor_CSharp_Delete_Folder.cs >}}

{{< /tab >}} {{< tab "Java" >}}

{{< gist groupdocscloud cb5b0d1ae842f50f90382640823a2004 Editor_Java_Delete_Folder.java >}}

{{< /tab >}} {{< tab "PHP" >}}

{{< gist groupdocscloud 288fe44b5603cd7966fa72f293e91b88 Editor_Php_Delete_Folder.php >}}

{{< /tab >}} {{< tab "Ruby" >}}

{{< gist groupdocscloud ba011159eee59cd5a1f696ae6fadb2e4 Editor_Ruby_Delete_Folder.rb >}}

{{< /tab >}} {{< tab "Node.js" >}}

{{< gist groupdocscloud d42190d60101442ccba939ac4db41454 Editor_Node_Delete_Folder.js >}}

{{< /tab >}} {{< tab "Python" >}}

{{< gist groupdocscloud 49c298f42348259cd85175f315d57272 Editor_Python_Delete_Folder.py >}}

{{< /tab >}} {{< /tabs >}}

## Copy Specific Folder

This API allows you to copy a folder to another location in the GroupDocs Cloud Storage. If you do not pass source and destination storage names API will copy Folder within default Cloud Storage.

### API Explorer

[GroupDocs.Editor Cloud API Reference](https://apireference.groupdocs.cloud/editor/#/) lets you try out [Copy Folder API](https://apireference.groupdocs.cloud/editor/#/Folder/CopyFolder) right away in your browser. It allows you to effortlessly interact and try out every single operation that our APIs expose.

### Request parameters

|Parameter|Description
|---|---
|**srcPath**|Source folder path e.g. /Folder1. Required. Can be passed as a query string parameter or as part of the URL
|**destPath**|Destination folder path. Required
|srcStorageName|Name of the storage of source folder. If not set, then default storage used
|destStorageName|Name of the storage of destination folder. If not set, then default storage used

### cURL example

{{< tabs "example7">}} {{< tab "Request" >}}

```bash
curl -X PUT "https://api.groupdocs.cloud/v1.0/editor/storage/folder/copy/editordocs?destPath#viewerdocs1&srcstorageName=MyStorage&deststorageName=MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"

```

{{< /tab >}} {{< tab "Response" >}}

```json
{
  "code": 200,
  "status": "OK"
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-editor-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-editor-cloud), it hides the [Copy Folder API](https://apireference.groupdocs.cloud/editor/#/Folder/CopyFolder) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.

{{< tabs "example8">}} {{< tab "C#" >}}

{{< gist groupdocscloud 34f0df87ff6e7aaffef5876bdcb04a38 Editor_CSharp_Copy_Folder.cs >}}

{{< /tab >}} {{< tab "Java" >}}

{{< gist groupdocscloud cb5b0d1ae842f50f90382640823a2004 Editor_Java_Copy_Folder.java >}}

{{< /tab >}} {{< tab "PHP" >}}

{{< gist groupdocscloud 288fe44b5603cd7966fa72f293e91b88 Editor_Php_Copy_Folder.php >}}

{{< /tab >}} {{< tab "Ruby" >}}

{{< gist groupdocscloud ba011159eee59cd5a1f696ae6fadb2e4 Editor_Ruby_Copy_Folder.rb >}}

{{< /tab >}} {{< tab "Node.js" >}}

{{< gist groupdocscloud d42190d60101442ccba939ac4db41454 Editor_Node_Copy_Folder.js >}}

{{< /tab >}} {{< tab "Python" >}}

{{< gist groupdocscloud 49c298f42348259cd85175f315d57272 Editor_Python_Copy_Folder.py >}}

{{< /tab >}} {{< /tabs >}}

## Move a Specific Folder

This API allows you to move a folder to another location in the GroupDocs Cloud Storage. If you do not pass source and destination storage names API will move Folder within default Cloud Storage.

### API Explorer

[GroupDocs.Editor Cloud API Reference](https://apireference.groupdocs.cloud/editor/#/) lets you try out [Move a Folder API](https://apireference.groupdocs.cloud/editor/#/Folder/MoveFolder) right away in your browser. It allows you to effortlessly interact and try out every single operation that our APIs expose.

### Request parameters

|Parameter|Description
|---|---
|**srcPath**|Source folder path e.g. /Folder1. Required. Can be passed as a query string parameter or as part of the URL
|**destPath**|Destination folder path. Required
|srcStorageName|Name of the storage of source folder. If not set, then default storage used
|destStorageName|Name of the storage of destination folder. If not set, then default storage used

### cURL example

{{< tabs "example9">}} {{< tab "Request" >}}

```bash
curl -X PUT "https://api.groupdocs.cloud/v1.0/editor/storage/folder/move/editordocs?destPath#viewerdocs1&srcstorageName=MyStorage&deststorageName=MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"
```

{{< /tab >}} {{< tab "Response" >}}

```json
{
  "code": 200,
  "status": "OK"
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-editor-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-editor-cloud), it hides the [Move Folder API](https://apireference.groupdocs.cloud/editor/#/Folder/MoveFolder) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.

{{< tabs "example10">}} {{< tab "C#" >}}

{{< gist groupdocscloud 34f0df87ff6e7aaffef5876bdcb04a38 Editor_CSharp_Move_Folder.cs >}}

{{< /tab >}} {{< tab "Java" >}}

{{< gist groupdocscloud cb5b0d1ae842f50f90382640823a2004 Editor_Java_Move_Folder.java >}}

{{< /tab >}} {{< tab "PHP" >}}

{{< gist groupdocscloud 288fe44b5603cd7966fa72f293e91b88 Editor_Php_Move_Folder.php >}}

{{< /tab >}} {{< tab "Ruby" >}}

{{< gist groupdocscloud ba011159eee59cd5a1f696ae6fadb2e4 Editor_Ruby_Move_Folder.rb >}}

{{< /tab >}} {{< tab "Node.js" >}}

{{< gist groupdocscloud d42190d60101442ccba939ac4db41454 Editor_Node_Move_Folder.js >}}

{{< /tab >}} {{< tab "Python" >}}

{{< gist groupdocscloud 49c298f42348259cd85175f315d57272 Editor_Python_Move_Folder.py >}}

{{< /tab >}} {{< /tabs >}}
