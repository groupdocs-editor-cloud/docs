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

{{< tabs "example1">}} {{< tab "Linux/MacOS/Bash" >}}
```bash
curl -X GET "https://api.groupdocs.cloud/v1.0/editor/storage/folder/editordocs?storageName=MyStorage" \
  -H "accept: application/json" \
  -H "authorization: Bearer $JWT_TOKEN"
```
{{< /tab >}}

{{< tab "Windows PowerShell" >}}
```powershell
curl.exe -X GET "https://api.groupdocs.cloud/v1.0/editor/storage/folder/editordocs?storageName=MyStorage" `
  -H "accept: application/json" `
  -H "authorization: Bearer $env:JWT_TOKEN"
```
{{< /tab >}}

{{< tab "Windows CMD" >}}
```cmd
curl -X GET "https://api.groupdocs.cloud/v1.0/editor/storage/folder/editordocs?storageName=MyStorage" ^
  -H "accept: application/json" ^
  -H "authorization: Bearer %JWT_TOKEN%"
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

```csharp
using System;
using GroupDocs.Editor.Cloud.Sdk.Api;
using GroupDocs.Editor.Cloud.Sdk.Client;
using GroupDocs.Editor.Cloud.Sdk.Model.Requests;

namespace GroupDocs.Editor.Cloud.Examples.CSharp
{
	// Get Files List
	class Get_Files_List
	{
		public static void Run()
		{
			var configuration = new Configuration(Common.MyAppSid, Common.MyAppKey);
			var apiInstance = new FolderApi(configuration);

			try
			{
				var request = new GetFilesListRequest("WordProcessing", Common.MyStorage);

				var response = apiInstance.GetFilesList(request);
				Console.WriteLine("Expected response type is FilesList: " + response.Value.Count.ToString());
			}
			catch (Exception e)
			{
				Console.WriteLine("Exception while calling FolderApi: " + e.Message);
			}
		}
	}
}
```

{{< /tab >}} {{< tab "Java" >}}

```java
package examples.Working_With_Folder;

import com.groupdocs.cloud.Editor.api.*;
import com.groupdocs.cloud.Editor.client.ApiException;
import com.groupdocs.cloud.Editor.model.FilesList;
import com.groupdocs.cloud.Editor.model.*;
import com.groupdocs.cloud.Editor.model.requests.*;
import examples.Utils;

public class Editor_Java_Get_Files_List {

	public static void main(String[] args) {

		FolderApi apiInstance = new FolderApi(Utils.AppSID, Utils.AppKey);
		try {
			GetFilesListRequest request = new GetFilesListRequest("Editors", Utils.MYStorage);
			FilesList response = apiInstance.getFilesList(request);
			System.out.println("Expected response type is FilesList.");
			for (StorageFile storageFile : response.getValue()) {
				System.out.println("Files: " + storageFile.getPath());
			}
		} catch (ApiException e) {
			System.err.println("Exception while calling FolderApi:");
			e.printStackTrace();
		}
	}
}
```

{{< /tab >}} {{< tab "PHP" >}}

```php
<?php

include(dirname(__DIR__) . '\CommonUtils.php');

	try {
		$apiInstance = CommonUtils::GetFolderApiInstance();

		$request = new GroupDocs\Editor\Model\Requests\GetFilesListRequest("signaturedocs", CommonUtils::$MyStorage);
		$response = $apiInstance->getFilesList($request);
		
		echo "Expected response type is FilesList.", "<br />";

		foreach($response->getValue() as $storageFile) {
          echo "Files: ", $storageFile->getPath(), "<br />";
		}
	} catch (Exception $e) {
		echo "Something went wrong: ", $e->getMessage(), "\n";
	}
?>
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
# Load the gem
require 'groupdocs_signature_cloud'
require 'common_utilities/Utils.rb'

class Working_With_Folder
  def self.Editor_Ruby_Get_Files_List()

    # Getting instance of the API
    $api = Common_Utilities.Get_FolderApi_Instance()
    
    $request = GroupDocsEditorCloud::GetFilesListRequest.new("Editordocs/sample.docx", $myStorage)
    $response = $api.get_files_list($request)

    puts("Expected response type is FilesList: " + ($response).to_s)
  end
end
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
"use strict";
class Editor_Node_Get_Files_List {
	static Run() {
		// retrieve supported file-formats
		var request = new groupdocs_Editor_cloud_1.GetFilesListRequest("Editordocs/sample.docx", myStorage);
		folderApi.getFilesList(request)
			.then(function (response) {
				console.log("Expected response type is FilesList: " + response.value.length);
			})
			.catch(function (error) {
				console.log("Error: " + error.message);
			});
	}
}
module.exports = Editor_Node_Get_Files_List;

```

{{< /tab >}} {{< tab "Python" >}}

```python
# Import modules
import groupdocs_Editor_cloud

from Common_Utilities.Utils import Common_Utilities


class Editor_Python_Get_Files_List:
    
    @classmethod
    def Run(self):
        # Create instance of the API
        api = Common_Utilities.Get_FolderApi_Instance()
        
        try:
            request = groupdocs_Editor_cloud.GetFilesListRequest("Editordocs\\sample.docx", Common_Utilities.myStorage)
            response = api.get_files_list(request)
            
            print("Expected response type is FilesList: " + str(response))
        except groupdocs_Editor_cloud.ApiException as e:
            print("Exception while calling API: {0}".format(e.message))
```

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

{{< tabs "example3">}} {{< tab "Linux/MacOS/Bash" >}}
```bash
curl -X POST "https://api.groupdocs.cloud/v1.0/editor/storage/folder/editordocs?storageName=MyStorage" \
  -H "accept: application/json" \
  -H "authorization: Bearer $JWT_TOKEN"
```
{{< /tab >}}

{{< tab "Windows PowerShell" >}}
```powershell
curl.exe -X POST "https://api.groupdocs.cloud/v1.0/editor/storage/folder/editordocs?storageName=MyStorage" `
  -H "accept: application/json" `
  -H "authorization: Bearer $env:JWT_TOKEN"
```
{{< /tab >}}

{{< tab "Windows CMD" >}}
```cmd
curl -X POST "https://api.groupdocs.cloud/v1.0/editor/storage/folder/editordocs?storageName=MyStorage" ^
  -H "accept: application/json" ^
  -H "authorization: Bearer %JWT_TOKEN%"
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

```csharp
using System;
using GroupDocs.Editor.Cloud.Sdk.Api;
using GroupDocs.Editor.Cloud.Sdk.Client;
using GroupDocs.Editor.Cloud.Sdk.Model.Requests;

namespace GroupDocs.Editor.Cloud.Examples.CSharp
{
	// Create Folder
	class Create_Folder
	{
		public static void Run()
		{
			var configuration = new Configuration(Common.MyAppSid, Common.MyAppKey);
			var apiInstance = new FolderApi(configuration);

			try
			{
				var request = new CreateFolderRequest("", Common.MyStorage);

				apiInstance.CreateFolder(request);
				Console.WriteLine("Expected response type is Void: 'WordProcessing' folder created.");
			}
			catch (Exception e)
			{
				Console.WriteLine("Exception while calling FolderApi: " + e.Message);
			}
		}
	}
}
```

{{< /tab >}} {{< tab "Java" >}}

```java
package examples.Working_With_Folder;

import com.groupdocs.cloud.Editor.api.*;
import com.groupdocs.cloud.Editor.client.ApiException;
import com.groupdocs.cloud.Editor.model.requests.*;
import examples.Utils;

public class Editor_Java_Create_Folder {

	public static void main(String[] args) {

		FolderApi apiInstance = new FolderApi(Utils.AppSID, Utils.AppKey);
		try {
			CreateFolderRequest request = new CreateFolderRequest("Editors", Utils.MYStorage);
			apiInstance.createFolder(request);
			System.out.println("Expected response type is Void: 'Editors' folder created.");
		} catch (ApiException e) {
			System.err.println("Exception while calling FolderApi:");
			e.printStackTrace();
		}
	}
}
```

{{< /tab >}} {{< tab "PHP" >}}

```php
<?php

include(dirname(__DIR__) . '\CommonUtils.php');

	try {
		$apiInstance = CommonUtils::GetFolderApiInstance();

		$request = new GroupDocs\Editor\Model\Requests\CreateFolderRequest("Editordocs", CommonUtils::$MyStorage);
		$apiInstance->createFolder($request);
		
		echo "Expected response type is Void: 'Editordocs' folder created.", "<br />";
	} catch (Exception $e) {
		echo "Something went wrong: ", $e->getMessage(), "\n";
	}
?>
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
# Load the gem
require 'groupdocs_signature_cloud'
require 'common_utilities/Utils.rb'

class Working_With_Folder
  def self.Editor_Ruby_Create_Folder()

    # Getting instance of the API
    $api = Common_Utilities.Get_FolderApi_Instance()
    
    $request = GroupDocsEditorCloud::CreateFolderRequest.new("Editordocs", $myStorage)
    $response = $api.create_folder($request)

    puts("Expected response type is Void: 'Editordocs' folder created.")
  end
end
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
"use strict";
class Editor_Node_Create_Folder {
	static Run() {
		// retrieve supported file-formats
		var request = new groupdocs_Editor_cloud_1.CreateFolderRequest("Editordocs", myStorage);
		folderApi.createFolder(request)
			.then(function () {
				console.log("Expected response type is Void: 'Editordocs' folder created.");
			})
			.catch(function (error) {
				console.log("Error: " + error.message);
			});
	}
}
module.exports = Editor_Node_Create_Folder;

```

{{< /tab >}} {{< tab "Python" >}}

```python
# Import modules
import groupdocs_Editor_cloud

from Common_Utilities.Utils import Common_Utilities


class Editor_Python_Create_Folder:
    
    @classmethod
    def Run(self):
        # Create instance of the API
        api = Common_Utilities.Get_FolderApi_Instance()
        
        try:
            request = groupdocs_Editor_cloud.CreateFolderRequest("Assembler", Common_Utilities.myStorage)
            api.create_folder(request)
            
            print("Expected response type is Void: 'Assembler' folder created.")
        except groupdocs_Editor_cloud.ApiException as e:
            print("Exception while calling API: {0}".format(e.message))
```

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

{{< tabs "example5">}} {{< tab "Linux/MacOS/Bash" >}}
```bash
curl -X DELETE "https://api.groupdocs.cloud/v1.0/editor/storage/folder/editordocs?storageName=MyStorage&recursive#true" \
  -H "accept: application/json" \
  -H "authorization: Bearer $JWT_TOKEN"
```
{{< /tab >}}

{{< tab "Windows PowerShell" >}}
```powershell
curl.exe -X DELETE "https://api.groupdocs.cloud/v1.0/editor/storage/folder/editordocs?storageName=MyStorage&recursive#true" `
  -H "accept: application/json" `
  -H "authorization: Bearer $env:JWT_TOKEN"
```
{{< /tab >}}

{{< tab "Windows CMD" >}}
```cmd
curl -X DELETE "https://api.groupdocs.cloud/v1.0/editor/storage/folder/editordocs?storageName=MyStorage&recursive#true" ^
  -H "accept: application/json" ^
  -H "authorization: Bearer %JWT_TOKEN%"
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

```csharp
using System;
using GroupDocs.Editor.Cloud.Sdk.Api;
using GroupDocs.Editor.Cloud.Sdk.Client;
using GroupDocs.Editor.Cloud.Sdk.Model.Requests;

namespace GroupDocs.Editor.Cloud.Examples.CSharp
{
	// Delete Folder
	class Delete_Folder
	{
		public static void Run()
		{
			var configuration = new Configuration(Common.MyAppSid, Common.MyAppKey);
			var apiInstance = new FolderApi(configuration);

			try
			{
				var request = new DeleteFolderRequest("WordProcessing/WordProcessing1", Common.MyStorage, true);

				apiInstance.DeleteFolder(request);
				Console.WriteLine("Expected response type is Void: 'WordProcessing/WordProcessing1' folder deleted recusrsively.");
			}
			catch (Exception e)
			{
				Console.WriteLine("Exception while calling FolderApi: " + e.Message);
			}
		}
	}
}
```

{{< /tab >}} {{< tab "Java" >}}

```java
package examples.Working_With_Folder;

import com.groupdocs.cloud.Editor.api.*;
import com.groupdocs.cloud.Editor.client.ApiException;
import com.groupdocs.cloud.Editor.model.requests.*;
import examples.Utils;

public class Editor_Java_Delete_Folder {

	public static void main(String[] args) {

		FolderApi apiInstance = new FolderApi(Utils.AppSID, Utils.AppKey);
		try {
			DeleteFolderRequest request = new DeleteFolderRequest("Editors\\Editors1", Utils.MYStorage, true);
			apiInstance.deleteFolder(request);
			System.out
					.println("Expected response type is Void: 'Editors/Editors1' folder deleted recusrsively.");
		} catch (ApiException e) {
			System.err.println("Exception while calling FolderApi:");
			e.printStackTrace();
		}
	}
}
```

{{< /tab >}} {{< tab "PHP" >}}

```php
<?php

include(dirname(__DIR__) . '\CommonUtils.php');

	try {
		$apiInstance = CommonUtils::GetFolderApiInstance();

		$request = new GroupDocs\Editor\Model\Requests\DeleteFolderRequest("Editordocs1\\Editordocs1", CommonUtils::$MyStorage, true);
		$apiInstance->deleteFolder($request);
		
		echo "Expected response type is Void: 'Editordocs1/Editordocs1' folder deleted recursively.", "<br />";
	} catch (Exception $e) {
		echo "Something went wrong: ", $e->getMessage(), "\n";
	}
?>
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
# Load the gem
require 'groupdocs_signature_cloud'
require 'common_utilities/Utils.rb'

class Working_With_Folder
  def self.Editor_Ruby_Delete_Folder()

    # Getting instance of the API
    $api = Common_Utilities.Get_FolderApi_Instance()
    
    $request = GroupDocsEditorCloud::DeleteFolderRequest.new("Editordocs1", $myStorage, true)
    $response = $api.delete_folder($request)

    puts("Expected response type is Void: 'Editordocs/Editordocs1' folder deleted recursively.")
  end
end
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
"use strict";
class Editor_Node_Delete_Folder {
	static Run() {
		// retrieve supported file-formats
		var request = new groupdocs_Editor_cloud_1.DeleteFolderRequest("Editordocs/Editordocs1", myStorage, true);
		folderApi.deleteFolder(request)
			.then(function () {
				console.log("Expected response type is Void: 'Editordocs/Editordocs1' folder deleted recursively.");
			})
			.catch(function (error) {
				console.log("Error: " + error.message);
			});
	}
}
module.exports = Editor_Node_Delete_Folder;

```

{{< /tab >}} {{< tab "Python" >}}

```python
# Import modules
import groupdocs_Editor_cloud

from Common_Utilities.Utils import Common_Utilities


class Editor_Python_Delete_Folder:
    
    @classmethod
    def Run(self):
        # Create instance of the API
        api = Common_Utilities.Get_FolderApi_Instance()
        
        try:
            request = groupdocs_Editor_cloud.DeleteFolderRequest("Editordocs\\Editordocs1", Common_Utilities.myStorage, True)
            api.delete_folder(request)
            
            print("Expected response type is Void: 'Editordocs/Editordocs1' folder deleted recursively.")
        except groupdocs_Editor_cloud.ApiException as e:
            print("Exception while calling API: {0}".format(e.message))
```

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

{{< tabs "example7">}} {{< tab "Linux/MacOS/Bash" >}}
```bash
curl -X PUT "https://api.groupdocs.cloud/v1.0/editor/storage/folder/copy/editordocs?destPath#viewerdocs1&srcstorageName=MyStorage&deststorageName=MyStorage" \
  -H "accept: application/json" \
  -H "authorization: Bearer $JWT_TOKEN"
```
{{< /tab >}}

{{< tab "Windows PowerShell" >}}
```powershell
curl.exe -X PUT "https://api.groupdocs.cloud/v1.0/editor/storage/folder/copy/editordocs?destPath#viewerdocs1&srcstorageName=MyStorage&deststorageName=MyStorage" `
  -H "accept: application/json" `
  -H "authorization: Bearer $env:JWT_TOKEN"
```
{{< /tab >}}

{{< tab "Windows CMD" >}}
```cmd
curl -X PUT "https://api.groupdocs.cloud/v1.0/editor/storage/folder/copy/editordocs?destPath#viewerdocs1&srcstorageName=MyStorage&deststorageName=MyStorage" ^
  -H "accept: application/json" ^
  -H "authorization: Bearer %JWT_TOKEN%"
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

```csharp
using System;
using GroupDocs.Editor.Cloud.Sdk.Api;
using GroupDocs.Editor.Cloud.Sdk.Client;
using GroupDocs.Editor.Cloud.Sdk.Model.Requests;

namespace GroupDocs.Editor.Cloud.Examples.CSharp
{
	// Copy Folder
	class Copy_Folder
	{
		public static void Run()
		{
			var configuration = new Configuration(Common.MyAppSid, Common.MyAppKey);
			var apiInstance = new FolderApi(configuration);

			try
			{
				var request = new CopyFolderRequest("WordProcessing", "WordProcessing1", Common.MyStorage, Common.MyStorage);

				apiInstance.CopyFolder(request);
				Console.WriteLine("Expected response type is Void: 'WordProcessing' folder copied as 'WordProcessing1'.");
			}
			catch (Exception e)
			{
				Console.WriteLine("Exception while calling FolderApi: " + e.Message);
			}
		}
	}
}
```

{{< /tab >}} {{< tab "Java" >}}

```java
package examples.Working_With_Folder;

import com.groupdocs.cloud.Editor.api.*;
import com.groupdocs.cloud.Editor.client.ApiException;
import com.groupdocs.cloud.Editor.model.requests.*;
import examples.Utils;

public class Editor_Java_Copy_Folder {

	public static void main(String[] args) {

		FolderApi apiInstance = new FolderApi(Utils.AppSID, Utils.AppKey);
		try {
			CopyFolderRequest request = new CopyFolderRequest("Editors", "Editors1", Utils.MYStorage,
					Utils.MYStorage);
			apiInstance.copyFolder(request);
			System.out.println("Expected response type is Void: 'Editors' folder copied as 'Editors1'.");
		} catch (ApiException e) {
			System.err.println("Exception while calling FolderApi:");
			e.printStackTrace();
		}
	}
}
```

{{< /tab >}} {{< tab "PHP" >}}

```php
<?php

include(dirname(__DIR__) . '\CommonUtils.php');

	try {
		$apiInstance = CommonUtils::GetFolderApiInstance();

		$request = new GroupDocs\Editor\Model\Requests\CopyFolderRequest("Editordocs", "Editordocs1", CommonUtils::$MyStorage, CommonUtils::$MyStorage);
		$apiInstance->copyFolder($request);
		
		echo "Expected response type is Void: 'Editordocs' folder copied as 'Editordocs1'.", "<br />";
	} catch (Exception $e) {
		echo "Something went wrong: ", $e->getMessage(), "\n";
	}
?>
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
# Load the gem
require 'groupdocs_signature_cloud'
require 'common_utilities/Utils.rb'

class Working_With_Folder
  def self.Editor_Ruby_Copy_Folder()

    # Getting instance of the API
    $api = Common_Utilities.Get_FolderApi_Instance()
    
    $request = GroupDocsEditorCloud::CopyFolderRequest.new("Editordocs", "Editordocs1", $myStorage, $myStorage)
    $response = $api.copy_folder($request)

    puts("Expected response type is Void: 'Editordocs' folder copied as 'Editordocs1'.")
  end
end
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
"use strict";
class Editor_Node_Copy_Folder {
	static Run() {
		// retrieve supported file-formats
		var request = new groupdocs_Editor_cloud_1.CopyFolderRequest("Editordocs", "Editordocs1", myStorage, myStorage);
		folderApi.copyFolder(request)
			.then(function () {
				console.log("Expected response type is Void: 'Editordocs' folder copied as 'Editordocs1'.");
			})
			.catch(function (error) {
				console.log("Error: " + error.message);
			});
	}
}
module.exports = Editor_Node_Copy_Folder;

```

{{< /tab >}} {{< tab "Python" >}}

```python
# Import modules
import groupdocs_Editor_cloud

from Common_Utilities.Utils import Common_Utilities


class Editor_Python_Copy_Folder:
    
    @classmethod
    def Run(self):
        # Create instance of the API
        api = Common_Utilities.Get_FolderApi_Instance()
        
        try:
            request = groupdocs_Editor_cloud.CopyFolderRequest("Editordocs", "Editordocs1", Common_Utilities.myStorage, Common_Utilities.myStorage)
            api.copy_folder(request)
            
            print("Expected response type is Void: 'Editordocs' folder copied as 'Editordocs1'.")
        except groupdocs_Editor_cloud.ApiException as e:
            print("Exception while calling API: {0}".format(e.message))
```

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

{{< tabs "example9">}} {{< tab "Linux/MacOS/Bash" >}}
```bash
curl -X PUT "https://api.groupdocs.cloud/v1.0/editor/storage/folder/move/editordocs?destPath#viewerdocs1&srcstorageName=MyStorage&deststorageName=MyStorage" \
  -H "accept: application/json" \
  -H "authorization: Bearer $JWT_TOKEN"
```
{{< /tab >}}

{{< tab "Windows PowerShell" >}}
```powershell
curl.exe -X PUT "https://api.groupdocs.cloud/v1.0/editor/storage/folder/move/editordocs?destPath#viewerdocs1&srcstorageName=MyStorage&deststorageName=MyStorage" `
  -H "accept: application/json" `
  -H "authorization: Bearer $env:JWT_TOKEN"
```
{{< /tab >}}

{{< tab "Windows CMD" >}}
```cmd
curl -X PUT "https://api.groupdocs.cloud/v1.0/editor/storage/folder/move/editordocs?destPath#viewerdocs1&srcstorageName=MyStorage&deststorageName=MyStorage" ^
  -H "accept: application/json" ^
  -H "authorization: Bearer %JWT_TOKEN%"
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

```csharp
using GroupDocs.Editor.Cloud.Sdk.Api;
using GroupDocs.Editor.Cloud.Sdk.Client;
using GroupDocs.Editor.Cloud.Sdk.Model.Requests;
using System;

namespace GroupDocs.Editor.Cloud.Examples.CSharp
{
	// Move Folder
	class Move_Folder
	{
		public static void Run()
		{
			var configuration = new Configuration(Common.MyAppSid, Common.MyAppKey);
			var apiInstance = new FolderApi(configuration);

			try
			{
				var request = new MoveFolderRequest("WordProcessing1", "WordProcessing\\WordProcessing1", Common.MyStorage, Common.MyStorage);

				apiInstance.MoveFolder(request);
				Console.WriteLine("Expected response type is Void: 'WordProcessing1' folder moved to 'WordProcessing/WordProcessing1'.");
			}
			catch (Exception e)
			{
				Console.WriteLine("Exception while calling FolderApi: " + e.Message);
			}
		}
	}
}
```

{{< /tab >}} {{< tab "Java" >}}

```java
package examples.Working_With_Folder;

import com.groupdocs.cloud.Editor.api.*;
import com.groupdocs.cloud.Editor.client.ApiException;
import com.groupdocs.cloud.Editor.model.requests.*;
import examples.Utils;

public class Editor_Java_Move_Folder {

	public static void main(String[] args) {

		FolderApi apiInstance = new FolderApi(Utils.AppSID, Utils.AppKey);
		try {
			MoveFolderRequest request = new MoveFolderRequest("Editors1", "Editors\\Editors1",
					Utils.MYStorage, Utils.MYStorage);
			apiInstance.moveFolder(request);
			System.out.println(
					"Expected response type is Void: 'Editors1' folder moved to 'Editors/Editors1'.");
		} catch (ApiException e) {
			System.err.println("Exception while calling FolderApi:");
			e.printStackTrace();
		}
	}
}
```

{{< /tab >}} {{< tab "PHP" >}}

```php
<?php

include(dirname(__DIR__) . '\CommonUtils.php');

	try {
		$apiInstance = CommonUtils::GetFolderApiInstance();

		$request = new GroupDocs\Editor\Model\Requests\MoveFolderRequest("Editordocs1", "Editordocs1\\Editordocs1", CommonUtils::$MyStorage, CommonUtils::$MyStorage, true);
		$apiInstance->moveFolder($request);
		
		echo "Expected response type is Void: 'Editordocs1' folder moved to 'Editordocs1/Editordocs1'.", "<br />";
	} catch (Exception $e) {
		echo "Something went wrong: ", $e->getMessage(), "\n";
	}
?>
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
# Load the gem
require 'groupdocs_signature_cloud'
require 'common_utilities/Utils.rb'

class Working_With_Folder
  def self.Editor_Ruby_Move_Folder()

    # Getting instance of the API
    $api = Common_Utilities.Get_FolderApi_Instance()

    $request = GroupDocsEditorCloud::MoveFolderRequest.new("Editordocs1", "Editordocs/Editordocs1", $myStorage, $myStorage)
    $response = $api.move_folder($request)

    puts("Expected response type is Void: 'Editordocs1' folder moved to 'Editordocs/Editordocs1'.")
  end
end
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
"use strict";
class Editor_Node_Move_Folder {
	static Run() {
		// retrieve supported file-formats
		var request = new groupdocs_Editor_cloud_1.MoveFolderRequest("Editordocs1", "Editordocs/Editordocs1", myStorage, myStorage);
		folderApi.moveFolder(request)
			.then(function () {
				console.log("Expected response type is Void: 'Editordocs1' folder moved to 'Editordocs/Editordocs1'.");
			})
			.catch(function (error) {
				console.log("Error: " + error.message);
			});
	}
}
module.exports = Editor_Node_Move_Folder;

```

{{< /tab >}} {{< tab "Python" >}}

```python
# Import modules
import groupdocs_Editor_cloud

from Common_Utilities.Utils import Common_Utilities


class Editor_Python_Move_Folder:
    
    @classmethod
    def Run(self):
        # Create instance of the API
        api = Common_Utilities.Get_FolderApi_Instance()
        
        try:
            request = groupdocs_Editor_cloud.MoveFolderRequest("Editordocs1", "Editordocs1\\Editordocs", Common_Utilities.myStorage, Common_Utilities.myStorage)
            api.move_folder(request)
            
            print("Expected response type is Void: 'Editordocs1' folder moved to 'Editordocs/Editordocs1'.")
        except groupdocs_Editor_cloud.ApiException as e:
            print("Exception while calling API: {0}".format(e.message))
```

{{< /tab >}} {{< /tabs >}}
