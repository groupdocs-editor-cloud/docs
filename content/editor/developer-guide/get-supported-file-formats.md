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

{{< tabs "example1">}} {{< tab "Linux/MacOS/Bash" >}}

```bash
# First get JSON Web Token
# Please get your Client Id and Client Secret from https://dashboard.groupdocs.cloud/applications.
# Place the values in the CLIENT_ID and CLIENT_SECRET environment variables.
curl -v "https://api.groupdocs.cloud/connect/token" \
  -X POST \
  -d "grant_type=client_credentials&client_id=$CLIENT_ID&client_secret=$CLIENT_SECRET" \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -H "Accept: application/json"

# Get document information (formats supported by the editor)
curl -v "https://api.groupdocs.cloud/v1.0/editor/formats" \
  -X GET \
  -H "Content-Type: application/json" \
  -H "Accept: application/json" \
  -H "Authorization: Bearer $JWT_TOKEN"
```

{{< /tab >}}

{{< tab "Windows PowerShell" >}}

```powershell
# First get JSON Web Token
# Please get your Client Id and Client Secret from https://dashboard.groupdocs.cloud/applications.
# Place the values in the CLIENT_ID and CLIENT_SECRET environment variables.
curl.exe -v "https://api.groupdocs.cloud/connect/token" `
  -X POST `
  -d "grant_type=client_credentials&client_id=$env:CLIENT_ID&client_secret=$env:CLIENT_SECRET" `
  -H "Content-Type: application/x-www-form-urlencoded" `
  -H "Accept: application/json"

# Get document information (formats supported by the editor)
curl.exe -v "https://api.groupdocs.cloud/v1.0/editor/formats" `
  -X GET `
  -H "Content-Type: application/json" `
  -H "Accept: application/json" `
  -H "Authorization: Bearer $env:JWT_TOKEN"
```

{{< /tab >}}

{{< tab "Windows CMD" >}}

```cmd
rem First get JSON Web Token
rem Please get your Client Id and Client Secret from https://dashboard.groupdocs.cloud/applications.
rem Place the values in the CLIENT_ID and CLIENT_SECRET environment variables.
curl -v "https://api.groupdocs.cloud/connect/token" ^
  -X POST ^
  -d "grant_type=client_credentials&client_id=%CLIENT_ID%&client_secret=%CLIENT_SECRET%" ^
  -H "Content-Type: application/x-www-form-urlencoded" ^
  -H "Accept: application/json"

rem Get document information (formats supported by the editor)
curl -v "https://api.groupdocs.cloud/v1.0/editor/formats" ^
  -X GET ^
  -H "Content-Type: application/json" ^
  -H "Accept: application/json" ^
  -H "Authorization: Bearer %JWT_TOKEN%"
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

```csharp
// For complete examples and data files, please go to https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-dotnet-samples
string MyAppKey = ""; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
string MyAppSid = ""; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
var configuration = new Configuration(MyAppSid, MyAppKey);
var apiInstance = new InfoApi(configuration);
 
var response = apiInstance.GetSupportedFileFormats();
```

{{< /tab >}} {{< tab "Java" >}}

```java
// For complete examples and data files, please go to https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-java-samples
String MyAppKey = ""; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
String MyAppSid = ""; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
Configuration configuration = new Configuration(MyAppSid, MyAppKey);
InfoApi apiInstance = new InfoApi(configuration);
 
FormatsResult response = apiInstance.getSupportedFileFormats();
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
 
$response = $infoApi->getSupportedFileFormats();
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
# For complete examples and data files, please go to https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-ruby-samples
require 'groupdocs_editor_cloud'
 
$app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
$app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
infoApi = GroupDocsEditorCloud::InfoApi.from_keys($app_sid, $app_key)
 
result = infoApi.get_supported_file_formats()
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
// For complete examples and data files, please go to https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-node-samples
global.editor_cloud = require("groupdocs-editor-cloud");
 
global.appSid = "XXXX-XXXX-XXXX-XXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
global.appKey = "XXXXXXXXXXXXXXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
global.infoApi = editor_cloud.InfoApi.fromKeys(appSid, appKey);
 
let response = await infoApi.getSupportedFileFormats();
```

{{< /tab >}} {{< tab "Python" >}}

```python
# For complete examples and data files, please go to https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-python-samples
import groupdocs_editor_cloud
 
app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
infoApi = groupdocs_editor_cloud.InfoApi.from_keys(app_sid, app_key)
 
result = infoApi.get_supported_file_formats()
```

{{< /tab >}} {{< /tabs >}}
