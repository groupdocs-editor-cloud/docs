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

```csharp
using System;
using GroupDocs.Editor.Cloud.Sdk.Api;
using GroupDocs.Editor.Cloud.Sdk.Client;
using GroupDocs.Editor.Cloud.Sdk.Model.Requests;

namespace GroupDocs.Editor.Cloud.Examples.CSharp
{
	// Is Storage Exist
	class Storage_Exist
	{
		public static void Run()
		{
			var configuration = new Configuration(Common.MyAppSid, Common.MyAppKey);
			var apiInstance = new StorageApi(configuration);

			try
			{
				var request = new StorageExistsRequest(Common.MyStorage);

				var response = apiInstance.StorageExists(request);
				Console.WriteLine("Expected response type is StorageExist: " + response.Exists.Value.ToString());
			}
			catch (Exception e)
			{
				Console.WriteLine("Exception while calling StorageApi: " + e.Message);
			}
		}
	}
}
```

{{< /tab >}} {{< tab "Java" >}}

```java
package examples.Working_With_Storage;

import com.groupdocs.cloud.Editor.api.*;
import com.groupdocs.cloud.Editor.client.ApiException;
import com.groupdocs.cloud.Editor.model.*;
import com.groupdocs.cloud.Editor.model.requests.*;
import examples.Utils;

public class Annotation_Java_Storage_Exist {

	public static void main(String[] args) {

		StorageApi apiInstance = new StorageApi(Utils.AppSID, Utils.AppKey);
		try {
			StorageExistsRequest request = new StorageExistsRequest(Utils.MYStorage);
			StorageExist response = apiInstance.storageExists(request);
			System.out.println("Expected response type is StorageExist: " + response.getExists());
		} catch (ApiException e) {
			System.err.println("Exception while calling StorageApi:");
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
    $apiInstance = CommonUtils::GetStorageApiInstance();

	$request = new GroupDocs\Editor\Model\Requests\StorageExistsRequest(CommonUtils::$MyStorage);
		$response = $apiInstance->storageExists($request);
		
		echo "Expected response type is StorageExist: ", $response;
} catch (Exception $e) {
    echo "Something went wrong: ", $e->getMessage(), "\n";
}
?>
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
# For complete examples and data files, please go to https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-ruby-samples
require 'groupdocs_editor_cloud'
 
$app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
$app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
# Create necessary API instances    
fileApi = GroupDocsEditorCloud::FileApi.from_keys($app_sid, $app_key)
editApi = GroupDocsEditorCloud::EditApi.from_keys($app_sid, $app_key)
 
# The document already uploaded into the storage.
# Load it into editable state
fileInfo = GroupDocsEditorCloud::FileInfo.new
fileInfo.file_path = 'Spreadsheet/four-sheets.xlsx'       
 
loadOptions = GroupDocsEditorCloud::SpreadsheetLoadOptions.new
loadOptions.file_info = fileInfo
loadOptions.output_path = "output"
loadOptions.worksheet_index = 0
 
loadRequest = GroupDocsEditorCloud::LoadRequest.new(loadOptions)        
loadResult = editApi.load(loadRequest)
 
# Download html document
htmlFile = fileApi.download_file(GroupDocsEditorCloud::DownloadFileRequest.new loadResult.html_path)
htmlFile.open
html = htmlFile.read
htmlFile.close
 
# Edit something...
html = html.gsub("This is sample sheet", "This is sample sheep")
 
# Upload html back to storage
htmlFile = File.open(htmlFile.path, "w")        
htmlFile.write(html)
htmlFile.close
uploadRequest = GroupDocsEditorCloud::UploadFileRequest.new loadResult.html_path, File.open(htmlFile.path, "r")
fileApi.upload_file(uploadRequest)
 
# Save html back to xlsx
saveOptions = GroupDocsEditorCloud::SpreadsheetSaveOptions.new
saveOptions.file_info = fileInfo
saveOptions.output_path = "output/edited.xlsx"
saveOptions.html_path = loadResult.html_path
saveOptions.resources_path = loadResult.resources_path
 
saveRequest = GroupDocsEditorCloud::SaveRequest.new(saveOptions)
saveResult = editApi.save(saveRequest)        
 
puts("Document edited: " + saveResult.path)
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
"use strict";
class Editor_Node_Storage_Exist {
	static Run() {
		// retrieve supported file-formats
		var request = new groupdocs_Editor_cloud_1.StorageExistsRequest(myStorage);
		storageApi.storageExists(request)
			.then(function (response) {
				console.log("Expected response type is StorageExist: " + response.exists);
			})
			.catch(function (error) {
				console.log("Error: " + error.message);
			});
	}
}
module.exports = Editor_Node_Storage_Exist;

```

{{< /tab >}} {{< tab "Python" >}}

```python
# Import modules
import groupdocs_Editor_cloud

from Common_Utilities.Utils import Common_Utilities


class Editor_Python_Storage_Exist:
    
    @classmethod
    def Run(self):
        # Create instance of the API
        api = Common_Utilities.Get_StorageApi_Instance()
        
        try:
            request = groupdocs_Editor_cloud.StorageExistsRequest(Common_Utilities.myStorage)
            response = api.storage_exists(request)
            
            print("Expected response type is StorageExist: " + str(response))
        except groupdocs_Editor_cloud.ApiException as e:
            print("Exception while calling API: {0}".format(e.message))
```

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

```csharp
using System;
using GroupDocs.Editor.Cloud.Sdk.Api;
using GroupDocs.Editor.Cloud.Sdk.Client;
using GroupDocs.Editor.Cloud.Sdk.Model.Requests;

namespace GroupDocs.Editor.Cloud.Examples.CSharp
{
	// Is Object Exists
	class Object_Exists
	{
		public static void Run()
		{
			var configuration = new Configuration(Common.MyAppSid, Common.MyAppKey);
			var apiInstance = new StorageApi(configuration);

			try
			{
				var request = new ObjectExistsRequest("WordProcessing/one-page.docx", Common.MyStorage);

				var response = apiInstance.ObjectExists(request);
				Console.WriteLine("Expected response type is ObjectExist: " + response.Exists.Value.ToString());
			}
			catch (Exception e)
			{
				Console.WriteLine("Exception while calling StorageApi: " + e.Message);
			}
		}
	}
}
```

{{< /tab >}} {{< tab "Java" >}}

```java
package examples.Working_With_Storage;

import com.groupdocs.cloud.Editor.api.*;
import com.groupdocs.cloud.Editor.client.ApiException;
import com.groupdocs.cloud.Editor.model.*;
import com.groupdocs.cloud.Editor.model.requests.*;
import examples.Utils;

public class Annotation_Java_Object_Exists {

	public static void main(String[] args) {

		StorageApi apiInstance = new StorageApi(Utils.AppSID, Utils.AppKey);
		try {
			ObjectExistsRequest request = new ObjectExistsRequest("Editors\\one-page.docx", Utils.MYStorage, null);
			ObjectExist response = apiInstance.objectExists(request);
			System.out.println("Expected response type is ObjectExist: " + response.getExists());
		} catch (ApiException e) {
			System.err.println("Exception while calling StorageApi:");
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
		$apiInstance = CommonUtils::GetStorageApiInstance();

		$request = new GroupDocs\Editor\Model\Requests\ObjectExistsRequest("Editordocs\one-page.docx", CommonUtils::$MyStorage);
		$response = $apiInstance->objectExists($request);
		
		echo "Expected response type is ObjectExist: ", $response;
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

class Working_With_Storage
  def self.Editor_Ruby_Object_Exists()

    # Getting instance of the API
    $api = Common_Utilities.Get_StorageApi_Instance()
    
    $request = GroupDocsEditorCloud::ObjectExistsRequest.new("Editordocs/one-page.docx", $myStorage)
    $response = $api.object_exists($request)

    puts("Expected response type is ObjectExist: " + ($response).to_s)
  end
end
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
"use strict";
class Editor_Node_Object_Exists {
	static Run() {
		// retrieve supported file-formats
		var request = new groupdocs_Editor_cloud_1.ObjectExistsRequest("Editordocs/one-page.docx", myStorage);
		storageApi.objectExists(request)
			.then(function (response) {
				console.log("Expected response type is ObjectExist: " + response.exists);
			})
			.catch(function (error) {
				console.log("Error: " + error.message);
			});
	}
}
module.exports = Editor_Node_Object_Exists;

```

{{< /tab >}} {{< tab "Python" >}}

```python
# Import modules
import groupdocs_Editor_cloud

from Common_Utilities.Utils import Common_Utilities


class Editor_Python_Object_Exists:
    
    @classmethod
    def Run(self):
        # Create instance of the API
        api = Common_Utilities.Get_StorageApi_Instance()
        
        try:
            request = groupdocs_Editor_cloud.ObjectExistsRequest("Editordocs\\one-page.docx", Common_Utilities.myStorage)
            response = api.object_exists(request)
            
            print("Expected response type is ObjectExist: " + str(response))
        except groupdocs_Editor_cloud.ApiException as e:
            print("Exception while calling API: {0}".format(e.message))
```

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

```csharp
using System;
using GroupDocs.Editor.Cloud.Sdk.Api;
using GroupDocs.Editor.Cloud.Sdk.Client;
using GroupDocs.Editor.Cloud.Sdk.Model.Requests;

namespace GroupDocs.Editor.Cloud.Examples.CSharp
{
	// Get Get Disc Usage
	class Get_Disc_Usage
	{
		public static void Run()
		{
			var configuration = new Configuration(Common.MyAppSid, Common.MyAppKey);
			var apiInstance = new StorageApi(configuration);

			try
			{
				var request = new GetDiscUsageRequest(Common.MyStorage);

				var response = apiInstance.GetDiscUsage(request);
				Console.WriteLine("Expected response type is DiscUsage: " + response.UsedSize.ToString());
			}
			catch (Exception e)
			{
				Console.WriteLine("Exception while calling StorageApi: " + e.Message);
			}
		}
	}
}
```

{{< /tab >}} {{< tab "Java" >}}

```java
package examples.Working_With_Storage;

import com.groupdocs.cloud.Editor.api.*;
import com.groupdocs.cloud.Editor.client.ApiException;
import com.groupdocs.cloud.Editor.model.*;
import com.groupdocs.cloud.Editor.model.requests.*;
import examples.Utils;

public class Editor_Java_Get_Disc_Usage {

	public static void main(String[] args) {

		StorageApi apiInstance = new StorageApi(Utils.AppSID, Utils.AppKey);
		try {
			GetDiscUsageRequest request = new GetDiscUsageRequest(Utils.MYStorage);
			DiscUsage response = apiInstance.getDiscUsage(request);
			System.out.println("Expected response type is DiscUsage: " + response.getUsedSize());
		} catch (ApiException e) {
			System.err.println("Exception while calling StorageApi:");
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
		$apiInstance = CommonUtils::GetStorageApiInstance();

		$request = new GroupDocs\Editor\Model\Requests\GetDiscUsageRequest(CommonUtils::$MyStorage);
		$response = $apiInstance->getDiscUsage($request);
			
		echo "Expected response type is DiscUsage: ", $response;
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

class Working_With_Storage
  def self.Editor_Ruby_Get_Disc_Usage()

    # Getting instance of the API
    $api = Common_Utilities.Get_StorageApi_Instance()
    
    $request = GroupDocsEditorCloud::GetDiscUsageRequest.new($myStorage)
    $response = $api.get_disc_usage($request)

    puts("Expected response type is DiscUsage: " + ($response).to_s)
  end
end
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
"use strict";
class Editor_Node_Get_Disc_Usage {
	static Run() {
		// retrieve supported file-formats
		var request = new groupdocs_Editor_cloud_1.GetDiscUsageRequest(myStorage);
		storageApi.getDiscUsage(request)
			.then(function (response) {
				console.log("Expected response type is DiscUsage: " + response.usedSize);
			})
			.catch(function (error) {
				console.log("Error: " + error.message);
			});
	}
}
module.exports = Editor_Node_Get_Disc_Usage;

```

{{< /tab >}} {{< tab "Python" >}}

```python
# Import modules
import groupdocs_Editor_cloud

from Common_Utilities.Utils import Common_Utilities


class Editor_Python_Get_Disc_Usage:
    
    @classmethod
    def Run(self):
        # Create instance of the API
        api = Common_Utilities.Get_StorageApi_Instance()
        
        try:
            request = groupdocs_Editor_cloud.GetDiscUsageRequest(Common_Utilities.myStorage)
            response = api.get_disc_usage(request)
            
            print("Expected response type is DiscUsage: " + str(response))
        except groupdocs_Editor_cloud.ApiException as e:
            print("Exception while calling API: {0}".format(e.message))
```

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

```csharp
using System;
using GroupDocs.Editor.Cloud.Sdk.Api;
using GroupDocs.Editor.Cloud.Sdk.Client;
using GroupDocs.Editor.Cloud.Sdk.Model.Requests;

namespace GroupDocs.Editor.Cloud.Examples.CSharp
{
	// Get File Versions
	class Get_File_Versions
	{
		public static void Run()
		{
			var configuration = new Configuration(Common.MyAppSid, Common.MyAppKey);
			var apiInstance = new StorageApi(configuration);

			try
			{
				var request = new GetFileVersionsRequest("one-page.docx", Common.MyStorage);

				var response = apiInstance.GetFileVersions(request);
				Console.WriteLine("Expected response type is FileVersions: " + response.Value.Count.ToString());
			}
			catch (Exception e)
			{
				Console.WriteLine("Exception while calling StorageApi: " + e.Message);
			}
		}
	}
}
```

{{< /tab >}} {{< tab "Java" >}}

```java
package examples.Working_With_Storage;

import com.groupdocs.cloud.Editor.api.*;
import com.groupdocs.cloud.Editor.client.ApiException;
import com.groupdocs.cloud.Editor.model.*;
import com.groupdocs.cloud.Editor.model.requests.*;
import examples.Utils;

public class Editor_Java_Get_File_Versions {

	public static void main(String[] args) {

		StorageApi apiInstance = new StorageApi(Utils.AppSID, Utils.AppKey);
		try {
			GetFileVersionsRequest request = new GetFileVersionsRequest("Editors\\one-page.docx", Utils.MYStorage);
			FileVersions response = apiInstance.getFileVersions(request);
			System.out.println("Expected response type is FileVersions: " + response.getValue().size());
		} catch (ApiException e) {
			System.err.println("Exception while calling StorageApi:");
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
		$apiInstance = CommonUtils::GetStorageApiInstance();

		$request = new GroupDocs\Editor\Model\Requests\GetFileVersionsRequest("Editordocs\one-page.docx", CommonUtils::$MyStorage);
		$response = $apiInstance->getFileVersions($request);
		
		echo "Expected response type is FileVersions: ", $response;
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

class Working_With_Storage
  def self.Editor_Ruby_Get_File_Versions()

    # Getting instance of the API
    $api = Common_Utilities.Get_StorageApi_Instance()
    
    $request = GroupDocsEditorCloud::GetFileVersionsRequest.new("Editordocs/one-page.docx", $myStorage)
    $response = $api.get_file_versions($request)

    puts("Expected response type is FileVersions: " + ($response).to_s)
  end
end
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
"use strict";
class Editor_Node_Get_File_Versions {
	static Run() {
		// retrieve supported file-formats
		var request = new groupdocs_Editor_cloud_1.GetFileVersionsRequest("Editordocs/one-page.docx", myStorage);
		storageApi.getFileVersions(request)
			.then(function (response) {
				console.log("Expected response type is FileVersions: " + response.value.length);
			})
			.catch(function (error) {
				console.log("Error: " + error.message);
			});
	}
}
module.exports = Editor_Node_Get_File_Versions;

```

{{< /tab >}} {{< tab "Python" >}}

```python
# Import modules
import groupdocs_Editor_cloud

from Common_Utilities.Utils import Common_Utilities


class Editor_Python_Get_File_Versions:
    
    @classmethod
    def Run(self):
        # Create instance of the API
        api = Common_Utilities.Get_StorageApi_Instance()
        
        try:
            request = groupdocs_Editor_cloud.GetFileVersionsRequest("Editordocs\\one-page.docx", Common_Utilities.myStorage)
            response = api.get_file_versions(request)
            
            print("Expected response type is FileVersions: " + str(response))
        except groupdocs_Editor_cloud.ApiException as e:
            print("Exception while calling API: {0}".format(e.message))
```

{{< /tab >}} {{< /tabs >}}
