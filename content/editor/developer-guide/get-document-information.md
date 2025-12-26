---
id: "get-document-information"
url: "editor/get-document-information"
title: "Get Document Information"
productName: "GroupDocs.Editor Cloud"
weight: 3
description: ""
keywords: ""
toc: True
---



This REST API allows us to obtain basic information about the document and it's pages properties. The endpoint accepts the document storage path as input payload.
Here is the list of properties that can be obtained for a document:

* Document file extension;
* Document size in bytes;
* Document file format.
* Pages count
* Password protection

## Resources

```html
HTTP POST ~/info
```

[Swagger UI](https://apireference.groupdocs.cloud/editor/#/Info/GetInfo) lets you call this REST API directly from the browser.

### cURL example

{{< tabs "example1">}} {{< tab "Linux/MacOS/Bash" >}}

```bash
# First, get JSON Web Token
# Please get your Client Id and Client Secret from https://dashboard.groupdocs.cloud/applications.
# Place them in the environment variables CLIENT_ID and CLIENT_SECRET.
curl -v "https://api.groupdocs.cloud/connect/token" \
  -X POST \
  -d "grant_type=client_credentials&client_id=$CLIENT_ID&client_secret=$CLIENT_SECRET" \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -H "Accept: application/json"

# cURL example to get document information
curl -v "https://api.groupdocs.cloud/v1.0/editor/info" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Accept: application/json" \
  -H "Authorization: Bearer $JWT_TOKEN" \
  -d "{\"FilePath\": \"words/four-pages.docx\"}"
```

{{< /tab >}}

{{< tab "Windows PowerShell" >}}

```powershell
# First, get JSON Web Token
# Please get your Client Id and Client Secret from https://dashboard.groupdocs.cloud/applications.
# Place them in the environment variables $env:CLIENT_ID and $env:CLIENT_SECRET.
curl.exe -v "https://api.groupdocs.cloud/connect/token" `
  -X POST `
  -d "grant_type=client_credentials&client_id=$env:CLIENT_ID&client_secret=$env:CLIENT_SECRET" `
  -H "Content-Type: application/x-www-form-urlencoded" `
  -H "Accept: application/json"

# cURL example to get document information
curl.exe -v "https://api.groupdocs.cloud/v1.0/editor/info" `
  -X POST `
  -H "Content-Type: application/json" `
  -H "Accept: application/json" `
  -H "Authorization: Bearer $env:JWT_TOKEN" `
  -d '{ "FilePath": "words/four-pages.docx" }'
```

{{< /tab >}}

{{< tab "Windows CMD" >}}

```cmd
:: First, get JSON Web Token
:: Please get your Client Id and Client Secret from https://dashboard.groupdocs.cloud/applications.
:: Place them in the environment variables %CLIENT_ID% and %CLIENT_SECRET%.
curl -v "https://api.groupdocs.cloud/connect/token" ^
  -X POST ^
  -d "grant_type=client_credentials&client_id=%CLIENT_ID%&client_secret=%CLIENT_SECRET%" ^
  -H "Content-Type: application/x-www-form-urlencoded" ^
  -H "Accept: application/json"

:: cURL example to get document information
curl -v "https://api.groupdocs.cloud/v1.0/editor/info" ^
  -X POST ^
  -H "Content-Type: application/json" ^
  -H "Accept: application/json" ^
  -H "Authorization: Bearer %JWT_TOKEN%" ^
  -d "{\"FilePath\": \"words/four-pages.docx\"}"
```

{{< /tab >}} {{< tab "Response" >}}

```json
{
  "pageCount": 4,
  "size": 8651,
  "isEncrypted": false,
  "formatName": "Office Open XML WordProcessingML Macro-Free Document (DOCX)",
  "formatExtension": "docx"
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of making requests and handling responses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-editor-cloud) for a complete list of GroupDocs.Editor Cloud SDKs along with working examples, to get you started in no time. Please check the article to learn how to add an SDK to your project.

{{< tabs "example2">}} {{< tab "C#" >}}

```csharp
// For complete examples and data files, please go to https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-dotnet-samples
string MyAppKey = ""; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
string MyAppSid = ""; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
var configuration = new Configuration(MyAppSid, MyAppKey);
  
var apiInstance = new InfoApi(configuration);
var fileInfo = new FileInfo
{
    FilePath = "wordprocessing/four-pages.docx",
    Password = "password",
    StorageName = Common.MyStorage
};
  
var request = new GetInfoRequest(fileInfo);
var response = apiInstance.GetInfo(request);
```

{{< /tab >}} {{< tab "Java" >}}

```java
// For complete examples and data files, please go to https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-java-samples
String MyAppKey = ""; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
String MyAppSid = ""; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
Configuration configuration = new Configuration(MyAppSid, MyAppKey);
  
InfoApi apiInstance = new InfoApi(configuration);
 
FileInfo fileInfo = new FileInfo();         
fileInfo.setFilePath("WordProcessing/password-protected.docx");
fileInfo.setPassword("password");
 
GetInfoRequest request = new GetInfoRequest(fileInfo);
InfoResult response = apiInstance.getInfo(request);
```

{{< /tab >}} {{< tab "PHP" >}}

```php
// For complete examples and data files, please go to https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-php-samples
use GroupDocs\Editor\Model;
use GroupDocs\Editor\Model\Requests;
 
 
$AppSid = ""; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
$AppKey = ""; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
$configuration = new GroupDocs\Editor\Configuration();
$configuration->setAppSid($AppSid);
$configuration->setAppKey($AppKey);
 
$infoApi = new GroupDocs\Editor\InfoApi($configuration);
 
$fileInfo = new Model\FileInfo();
$fileInfo->setFilePath("WordProcessing/password-protected.docx");
$fileInfo->setPassword("password");
 
 
$response = $infoApi->getInfo(new Requests\getInfoRequest($fileInfo));
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
# For complete examples and data files, please go to https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-ruby-samples
require 'groupdocs_editor_cloud'
 
$app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
$app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
infoApi = GroupDocsEditorCloud::InfoApi.from_keys($app_sid, $app_key)
 
fileInfo = GroupDocsEditorCloud::FileInfo.new
fileInfo.file_path = 'WordProcessing/password-protected.docx'
fileInfo.password = 'password'
request = GroupDocsEditorCloud::GetInfoRequest.new(fileInfo)
response = infoApi.get_info(request)
puts("Pages count = " + response.page_count.to_s)
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
// For complete examples and data files, please go to https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-node-samples
global.editor_cloud = require("groupdocs-editor-cloud");
 
global.appSid = "XXXX-XXXX-XXXX-XXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
global.appKey = "XXXXXXXXXXXXXXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
global.infoApi = editor_cloud.InfoApi.fromKeys(appSid, appKey);
 
let fileInfo = new editor_cloud.FileInfo();
fileInfo.filePath = "WordProcessing/password-protected.docx";
fileInfo.password = "password";
 
let request = new editor_cloud.GetInfoRequest(fileInfo);
let response = await infoApi.getInfo(request);
 
console.log("GetDocumentInfo: Page Count = " + response.pageCount);
```

{{< /tab >}} {{< tab "Python" >}}

```python
# For complete examples and data files, please go to https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-python-samples
import groupdocs_editor_cloud
 
app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
infoApi = groupdocs_editor_cloud.InfoApi.from_keys(app_sid, app_key)
 
fileInfo = groupdocs_editor_cloud.FileInfo("WordProcessing/password-protected.docx", None, None, "password")
result = infoApi.get_info(groupdocs_editor_cloud.GetInfoRequest(fileInfo))        
print("Page count = " + str(result.page_count))
```

{{< /tab >}} {{< /tabs >}}
