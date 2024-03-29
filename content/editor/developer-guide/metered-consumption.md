---
id: "metered-consumption"
url: "editor/metered-consumption"
title: "Getting metered license consumption"
productName: "GroupDocs.Editor Cloud"
description: ""
keywords: ""
toc: True
---


{{< alert style="info" >}}
This example related to Docker version of GroupDocs.Editor-Cloud only
{{< /alert >}}

The metered license can be used in Docker version of GroupDocs.Editor-Cloud.
Here is an example how to retrieve metered license consumption.

You can find more information about Docker version at [How to self-host GroupDocs.Editor Cloud with Docker]({{< ref "editor/getting-started/self-host-with-docker.md" >}})

## Note about credits consumption when using metered license in docker version

+ Storage calls are not charged
+ Editor API calls charge is based on document size: 1 credit per call per 20MB
+ Not about /join method: if page options, like page number, are set for first of joined documents, there may be extra credit consumed, because of internal implementation. If page number not provided for 1st document than it should consume as 1 operation.If you not provide page number for 1st document than it should consume as 1 operation.

## Resource URI

```HTTP GET ~/editor/consumption```

## cURL example

{{< tabs "example1">}} {{< tab "Request" >}}

```bash

* cURL example to get metered license consumption
curl -v "http://<base url>/v2.0/editor/consumption" \
-X GET \
-H "Accept: application/json" \
-H "Authorization: Bearer <jwt token>"
```

{{< /tab >}} {{< tab "Response" >}}

```json
{
  "credit": 487848,
  "quantity": 6061570985.37938
}
```
{{< /tab >}} {{< /tabs >}}

## Response

The response structure contains metered license consumption information:

| Name | Type | Comment
|---|---|---
|Credit|decimal|Amount of used credits.
|Quantity|decimal|Amount of MBs processed.

## SDK examples

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-editor-cloud) in many development languages in order to make it easier to integrate with us.

{{< tabs "example2">}} {{< tab "C#" >}}

```csharp
// For complete examples and data files, please go to https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-dotnet-samples
string MyClientSecret = ""; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
string MyClientId = ""; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
  
var configuration = new Configuration(MyClientId, MyClientSecret);
  
// Create necessary API instances
var apiInstance = new LicenseApi(configuration);

var response = apiInstance.GetConsumptionCredit();

Console.WriteLine($"Credits: {response.Credit}");
Console.WriteLine($"Quantity: {response.Quantity}");
```

{{< /tab >}} {{< tab "Java" >}}

```java
// For complete examples and data files, please go to https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-java-samples
String MyClientSecret = ""; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
String MyClientId = ""; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
  
Configuration configuration = new Configuration(MyClientId, MyClientSecret);
  
// Create API instance
LicenseApi apiInstance = new LicenseApi(configuration);

ConsumptionResult response = apiInstance.getConsumptionCredit();
System.out.println("Credit: " + response.getCredit());
System.out.println("Quantity: " + response.getQuantity());
```

{{< /tab >}} {{< tab "PHP" >}}

```php
// For complete examples and data files, please go to https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-php-samples
use GroupDocs\Editor\Model;
use GroupDocs\Editor\Model\Requests;

$ClientId = ""; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
$ClientSecret = ""; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
  
$configuration = new GroupDocs\Editor\Configuration();
$configuration->setAppSid($ClientId);
$configuration->setAppKey($ClientSecret);

$apiInstance = new GroupDocs\Editor\LicenseApi($configuration);

// Prepare request
$filePath = dirname(realpath(__DIR__)) . '\Resources\WordProcessing\four-pages.docx';
$request = new Requests\ConvertDocumentDirectRequest("pdf", $filePath);

// Get consumption
$result = $apiInstance->getConsumptionCredit();

// Done
echo "Credit: " . $result->getCredit();
```

{{< /tab >}} {{< tab "Node.js" >}}

```node
// For complete examples and data files, please go to https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-node-samples
global.editor_cloud = require("groupdocs-editor-cloud");

global.clientId = "XXXX-XXXX-XXXX-XXXX"; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
global.clientSecret = "XXXXXXXXXXXXXXXX"; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
  
global.licenseApi = editor_cloud.LicenseApi.fromKeys(clientId, clientSecret);

let response = await licenseApi.getConsumptionCredit();
console.log("GetLicenseConsumption: Credit = " + response.credit);
```

{{< /tab >}} {{< tab "Python" >}}

```python
# For complete examples and data files, please go to https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-python-samples
import groupdocs_editor_cloud

client_id = "XXXX-XXXX-XXXX-XXXX" # Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
client_secret = "XXXXXXXXXXXXXXXX" # Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
  
# Create necessary API instances
apiInstance = groupdocs_editor_cloud.LicenseApi.from_keys(Common.client_id, Common.client_secret)

# Get consumption
result = apiInstance.get_consumption_credit()

print("Credit: " + result.credit)
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
# For complete examples and data files, please go to https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-ruby-samples
require 'groupdocs_editor_cloud'

$client_id = "XXXX-XXXX-XXXX-XXXX" # Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
$client_secret = "XXXXXXXXXXXXXXXX" # Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
  
# Create necessary API instances
apiInstance = GroupDocsEditorCloud::LicenseApi.from_keys($client_id, $client_secret)

# Get consumption
result = apiInstance.get_consumption_credit()

puts("Credit: " + result.credit)
```

{{< /tab >}} {{< /tabs >}}
