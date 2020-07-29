---
id: "working-with-files"
url: "editor/working-with-files"
title: "Working With Files"
productName: "GroupDocs.Editor Cloud"
weight: 3
description: ""
keywords: ""
---





# Download File API #

This API allows you to download a file from [GroupDocs Cloud Storage](https://dashboard.groupdocs.cloud).
|---|---

## API Explorer ##

[GroupDocs.Editor Cloud API Reference](https://apireference.groupdocs.cloud/editor/) lets you try out [Download a File API](https://apireference.groupdocs.cloud/editor/#/File/DownloadFile) right away in your browser! It allows you to effortlessly interact and try out every single operation our APIs expose.
|---|---|---|---

### Request parameters ###

|#
|---
Parameter
|#
Description

|
**Path**
|
Path of the file including file name and extension e.g. /Folder1/file.ext

 Required. Can be passed as a query string parameter or as part of the URL

|
storageName
|
Name of the storage. If not set, then default storage used

|
versionId
|
File version id


## cURL Example ##


 Request

```html 
curl -X GET "https://api.groupdocs.cloud/v1.0/editor/storage/file/one-page.docx?storageName#MyStorage" -H  "accept: multipart/form-data" -H  "authorization: Bearer [Access Token]"
    
 ```


 Response

```html 
{
  "Code": 200,
  "Status": "OK"
}
 ```




## SDKs ##

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-editor-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-editor-cloud), it hides the [File API](https://apireference.groupdocs.cloud/editor/#/) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.
|---|---|---|---|---|---

### SDK Examples ###


 C#




{{< gist groupdocscloud 34f0df87ff6e7aaffef5876bdcb04a38 Editor_CSharp_Download_File.cs >}}





 Java



{{< gist groupdocscloud cb5b0d1ae842f50f90382640823a2004 Editor_Java_Download_File.java >}}





 PHP




{{< gist groupdocscloud 288fe44b5603cd7966fa72f293e91b88 Editor_Php_Download_File.php >}}





 Ruby




{{< gist groupdocscloud ba011159eee59cd5a1f696ae6fadb2e4 Editor_Ruby_Download_File.rb >}}





 Node.js




{{< gist groupdocscloud d42190d60101442ccba939ac4db41454 Editor_Node_Download_File.js >}}





 Python




{{< gist groupdocscloud 49c298f42348259cd85175f315d57272 Editor_Python_Download_File.py >}}







# Upload File API #

This API allows you to upload files to the [GroupDocs Cloud Storage](https://dashboard.groupdocs.cloud/).
|---|---

## API Explorer ##

[GroupDocs.Editor Cloud API Reference](https://apireference.groupdocs.cloud/editor/#/) lets you try out [Upload a File API](https://apireference.groupdocs.cloud/editor/#/File/UploadFile) right away in your browser! It allows you to effortlessly interact and try out every single operation our APIs expose.
|---|---|---|---


### Request Body parameters ###

|#
|---
Parameter
|#
Description

|
**path**
|
Path of the file including file name and extension e.g. /Folder1/file.ext

 Required. Can be passed as a query string parameter or as part of the URL

|
storageName
|
Name of the storage. If not set, then default storage used

|
File
|
File content


## cURL Example ##


 Request

```html 
curl -X POST "https://api.groupdocs.cloud/v1.0/editor/storage/file/editordocs%2Fone-page2.docx?storageName#MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"

 ```


 Response

```html 
Http status code: 200 (Returns OK and list of errors, which is empty if success.)
{
  "Uploaded": [
    "string"
  ],
  "Errors": [
    {
      "Code": "string",
      "Message": "string",
      "Description": "string",
      "InnerError": {
        "RequestId": "string",
        "Date": "2019-02-27T06:10:08.884Z"
      }
    }
  ]
}


 ```




## SDKs ##

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-editor-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-editor-cloud), it hides the [File API](https://apireference.groupdocs.cloud/editor/#/File) calls and lets you use GroupDocs for Cloud features in a native way for your preferred language.
|---|---|---|---|---|---

### SDK Examples ###


 C#




{{< gist groupdocscloud 34f0df87ff6e7aaffef5876bdcb04a38 Editor_CSharp_Upload_File.cs >}}





 Java




{{< gist groupdocscloud cb5b0d1ae842f50f90382640823a2004 Editor_Java_Upload_File.java >}}





 PHP




{{< gist groupdocscloud 288fe44b5603cd7966fa72f293e91b88 Editor_Php_Upload_File.php >}}





 Ruby




{{< gist groupdocscloud ba011159eee59cd5a1f696ae6fadb2e4 Editor_Ruby_Upload_File.rb >}}





 Node.js




{{< gist groupdocscloud d42190d60101442ccba939ac4db41454 Editor_Node_Upload_File.js >}}





 Python




{{< gist groupdocscloud 49c298f42348259cd85175f315d57272 Editor_Python_Upload_File.py >}}







# Delete File API #

This API allows you to delete a specific file from [GroupDocs Cloud Storage](https://dashboard.groupdocs.cloud/).
|---|---

## API Explorer ##

[GroupDocs.Editor Cloud API Reference](https://apireference.groupdocs.cloud/editor/#/) lets you try out [Delete a File](https://apireference.groupdocs.cloud/editor/#/File/DeleteFile) right away in your browser! It allows you to effortlessly interact and try out every single operation our APIs expose.
|---|---|---|---


### Request parameters ###

|#
|---
Parameter
|#
Description

|
**path**
|
Path of the file including file name and extension e.g. /Folder1/file.ext

 Required. Can be passed as query string parameter or as part of the URL

|
storageName
|
Name of the storage. If not set, then default storage used

|
versionId
|
File version id


## cURL Example ##


 Request

```html 
curl -X DELETE "https://api.groupdocs.cloud/v1.0/editor/storage/file/editordocs1%2Fone-page1.docx?storageName#MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"

 ```


 Response

```html 
{
  "Code": 200,
  "Status": "OK"
}
 ```




## SDKs ##

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-editor-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-editor-cloud), it hides the [File API](https://apireference.groupdocs.cloud/editor/#/File) calls and lets you use GroupDocs for Cloud features in a native way for your preferred language.
|---|---|---|---|---|---

### SDK Examples ###


 C#




{{< gist groupdocscloud 34f0df87ff6e7aaffef5876bdcb04a38 Editor_CSharp_Delete_File.cs >}}





 Java




{{< gist groupdocscloud cb5b0d1ae842f50f90382640823a2004 Editor_Java_Delete_File.java >}}





 PHP




{{< gist groupdocscloud 288fe44b5603cd7966fa72f293e91b88 Editor_Php_Delete_File.php >}}





 Ruby




{{< gist groupdocscloud ba011159eee59cd5a1f696ae6fadb2e4 Editor_Ruby_Delete_File.rb >}}





 Node.js




{{< gist groupdocscloud d42190d60101442ccba939ac4db41454 Editor_Node_Delete_File.js >}}





 Python




{{< gist groupdocscloud 49c298f42348259cd85175f315d57272 Editor_Python_Delete_File.py >}}







# File Copy API #

This API allows you to copy a specific file from [GroupDocs Cloud Storage](https://dashboard.groupdocs.cloud/).
|---|---

## API Explorer ##

[GroupDocs.Editor for Cloud API Reference](https://apireference.groupdocs.cloud/editor/#/) lets you try out [Copy File](https://apireference.groupdocs.cloud/editor/#/File/CopyFile) right away in your browser! It allows you to effortlessly interact and try out every single operation our APIs expose. 
|---|---|---|---

###  Request parameters ###

|#
|---
Parameter
|#
Description

|
**srcPath**
|
Path of the source file including file name and extension e.g. /Folder1/file.ext

Required. Can be passed as a query string parameter or as part of the URL

|

**destPath**
|

Path of the destination file. Required.

|
srcStorageName
|
Name of the storage of source file. If not set, then default storage used

|

destStorageName
|

Name of the storage of destination file. If not set, then default storage used

|
versionId
|
Source file version id


## cURL Example ##


 Request

```html 
curl -X PUT "https://api.groupdocs.cloud/v1.0/editor/storage/file/copy/editordocs%2Fone-page1.docx?destPath#editordocs1%2Fone-page1.docx'&#x26;srcStorageName#MyStorage&#x26;destStorageName#MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"
    
 ```


 Response

```html 
{
  "Code": 200,
  "Status": "OK"
}
 ```




## SDKs ##

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-editor-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-editor-cloud), it hides the [File API](https://apireference.groupdocs.cloud/editor/#/File) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.
|---|---|---|---|---|---

### SDK Examples ###


 C#




{{< gist groupdocscloud 34f0df87ff6e7aaffef5876bdcb04a38 Editor_CSharp_Copy_File.cs >}}





 Java




{{< gist groupdocscloud cb5b0d1ae842f50f90382640823a2004 Editor_Java_Copy_File.java >}}





 PHP




{{< gist groupdocscloud 288fe44b5603cd7966fa72f293e91b88 Editor_Php_Copy_File.php >}}





 Ruby




{{< gist groupdocscloud ba011159eee59cd5a1f696ae6fadb2e4 Editor_Ruby_Copy_File.rb >}}





 Node.js




{{< gist groupdocscloud d42190d60101442ccba939ac4db41454 Editor_Node_Copy_File.js >}}





 Python




{{< gist groupdocscloud 49c298f42348259cd85175f315d57272 Editor_Python_Copy_File.py >}}







# File Move API #

This API allows you to copy a specific file from [GroupDocs Cloud Storage](https://dashboard.groupdocs.cloud/).
|---|---

## API Explorer ##

[GroupDocs.Editor for Cloud API Reference](https://apireference.groupdocs.cloud/editor/#/) lets you try out [Move File](https://apireference.groupdocs.cloud/editor/#/File/MoveFile) right away in your browser! It allows you to effortlessly interact and try out every single operation our APIs expose. 
|---|---|---|---

###  Request parameters ###

|#
|---
Parameter
|#
Description

|
**srcPath**
|
Path of the source file including file name and extension e.g. /Folder1/file.ext

Required. Can be passed as a query string parameter or as part of the URL

|

**destPath**
|

Path of the destination file. Required.

|
srcStorageName
|
Name of the storage of source file. If not set, then default storage used

|

destStorageName
|

Name of the storage of destination file. If not set, then default storage used

|
versionId
|
Source file version id


## cURL Example ##


 Request

```html 
curl -X PUT "https://api.groupdocs.cloud/v1.0/editor/storage/file/move/editordocs%2Fone-page1.docx?destPath#editordocs1%2Fone-page1.docx'&#x26;srcStorageName#MyStorage&#x26;destStorageName#MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"
    
 ```


 Response

```html 
{
  "Code": 200,
  "Status": "OK"
}
 ```




## SDKs ##

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-editor-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-editor-cloud), it hides the [File API](https://apireference.groupdocs.cloud/editor/#/File) calls and lets you use GroupDocs for Cloud features in a native way for your preferred language.
|---|---|---|---|---|---

### SDK Examples ###


 C#




{{< gist groupdocscloud 34f0df87ff6e7aaffef5876bdcb04a38 Editor_CSharp_Move_File.cs >}}





 Java




{{< gist groupdocscloud cb5b0d1ae842f50f90382640823a2004 Editor_Java_Move_File.java >}}





 PHP




{{< gist groupdocscloud 288fe44b5603cd7966fa72f293e91b88 Editor_Php_Move_File.php >}}





 Ruby




{{< gist groupdocscloud ba011159eee59cd5a1f696ae6fadb2e4 Editor_Ruby_Move_File.rb >}}





 Node.js




{{< gist groupdocscloud d42190d60101442ccba939ac4db41454 Editor_Node_Move_File.js >}}





 Python




{{< gist groupdocscloud 49c298f42348259cd85175f315d57272 Editor_Python_Move_File.py >}}






 
