---
id: "working-with-dsv-documents"
url: "editor/working-with-dsv-documents"
title: "Working with DSV Documents"
productName: "GroupDocs.Editor Cloud"
weight: 5
description: ""
keywords: ""
toc: True
---

[DSV](https://wiki.fileformat.com/home/) (Delimiter-Separated Values) documents are a specific form of text-based spreadsheets with delimiters (separators). There several steps that usage of [GroupDocs.Editor Cloud](https://products.groupdocs.cloud/editor) consists of:

1. Upload input document into cloud storage
1. Load the document into editable representation in the cloud storage (HTML file and resources)
1. Download HTML document (and resources, if needed) from storage
1. Edit HTML document at client side
1. Upload HTML document back into the storage
1. Save the edited document into Spreadsheet format in the storage
1. Download saved document

Steps 1, 3, 4, 5 are storage operations, please refer to this [Storage Operations]({{< ref "editor/developer-guide/storage-operations/_index.md" >}})) for usage details. Step 4 is a custom edit operation that can be performed with the programming language or 3rd party tools.

Below is a detailed description of steps 2 and 6.

## Loading DSV documents

This REST API provides an ability to load the input documents into an editable representation.

## Resources

```html
HTTP POST ~/load
```

[Swagger UI](https://apireference.groupdocs.cloud/editor/#/Edit) lets you call this REST API directly from the browser. The following properties of loading DSV documents may be customized:

|Name|Description|Comment
|---|---|---
|FileInfo.FilePath|The file path in the storage|Required property
|FileInfo.StorageName|Storage name|Could be omitted for default storage
|FileInfo.VersionId|File version Id|Useful for storages that support file versioning
|FileInfo.Password|The password to open file|Should be specified only for password-protected documents
|OutputPath|The full output path|The directory in storage, where editable files will be stored
|Separator|Allows to specify a string separator (delimiter) for text-based Spreadsheet documents|If not specified, separator determined according to file extension
|ConvertDateTimeData|Gets or sets a value that indicates whether the string in a text-based document is converted to the date data. The default is false.
|ConvertNumericData|Gets or sets a value that indicates whether the string in the text-based document is converted to numeric data. The default is false.
|TreatConsecutiveDelimitersAsOne|Defines whether consecutive delimiters should be treated as one. By default is false.|

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
    'FileInfo': { 'FilePath': 'cells/sample.tsv' },
  'OutputPath': 'Output'
 }"
```

{{< /tab >}} {{< tab "Response" >}}

```json
// Response will contain storage path to resultant documents
{
  "resourcesPath": "output\sample.files",
  "htmlPath": "output\sample.html"
}
```

{{< /tab >}} {{< /tabs >}}

## SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of making requests and handling responses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-editor-cloud) for a complete list of GroupDocs.Editor Cloud SDKs along with working examples, to get you started in no time. Please check the article to learn how to add an SDK to your project.

{{< tabs "example2">}} {{< tab "C#" >}}

```csharp
// For complete examples and data files, please go to https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-dotnet-samples
string MyAppKey = ""; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
string MyAppSid = ""; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
var configuration = new Configuration(MyAppSid, MyAppKey);
 
// Create necessary API instances
var editApi = new EditApi(configuration );
var fileApi = new FileApi(configuration );
 
// The document already uploaded into the storage.
// Load it into editable state
var loadOptions = new DelimitedTextLoadOptions
{
    FileInfo = new FileInfo
    {
        FilePath = "Spreadsheet/sample.tsv"
    },
    OutputPath = "output"
};
var loadResult = editApi.Load(new LoadRequest(loadOptions));
 
// Download html document
var stream = fileApi.DownloadFile(new DownloadFileRequest(loadResult.HtmlPath));
var htmlString = new StreamReader(stream, Encoding.UTF8).ReadToEnd();
 
// Edit something...
htmlString = htmlString.Replace("32", "66");
 
// Upload html back to storage
fileApi.UploadFile(new UploadFileRequest(loadResult.HtmlPath,
    new MemoryStream(Encoding.UTF8.GetBytes(htmlString))));
 
// Save html back to tsv
var saveOptions = new DelimitedTextSaveOptions
{
    FileInfo = loadOptions.FileInfo,
    OutputPath = "output/edited.tsv",
    HtmlPath = loadResult.HtmlPath,
    ResourcesPath = loadResult.ResourcesPath
};
var saveResult = editApi.Save(new SaveRequest(saveOptions));
```

{{< /tab >}} {{< tab "Java" >}}

```java
// For complete examples and data files, please go to https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-java-samples
String MyAppKey = ""; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
String MyAppSid = ""; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
Configuration configuration = new Configuration(MyAppSid, MyAppKey);
 
 
// Create necessary API instances
EditApi editApi = new EditApi(configuration);
FileApi fileApi = new FileApi(configuration);
 
// The document already uploaded into the storage.
// Load it into editable state
FileInfo fileInfo = new FileInfo();
fileInfo.setFilePath("Spreadsheet/sample.tsv");
DelimitedTextLoadOptions loadOptions = new DelimitedTextLoadOptions();
loadOptions.setFileInfo(fileInfo);
loadOptions.setOutputPath("output");
LoadResult loadResult = editApi.load(new LoadRequest(loadOptions));
 
// Download html document
File file = fileApi.downloadFile(new DownloadFileRequest(loadResult.getHtmlPath(), null, null));
             
// Edit something...
List<String> lines = Files.readAllLines(file.toPath());
List<String> newLines = new ArrayList<String>();
for (String line : lines) {
    newLines.add(line.replaceAll("32", "66"));
}
Files.write(file.toPath(), newLines);
 
// Upload html back to storage
fileApi.uploadFile(new UploadFileRequest(loadResult.getHtmlPath(), file, Common.MYStorage));
 
// Save html back to tsv
DelimitedTextSaveOptions saveOptions = new DelimitedTextSaveOptions();
saveOptions.setFileInfo(fileInfo);
saveOptions.setOutputPath("output/edited.tsv"); 
saveOptions.setHtmlPath(loadResult.getHtmlPath());      
saveOptions.setResourcesPath(loadResult.getResourcesPath());
DocumentResult saveResult = editApi.save(new SaveRequest(saveOptions));
 
System.out.println("Document edited: " + saveResult.getPath());
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
 
$editApi = new GroupDocs\Editor\EditApi($configuration);
$fileApi = new GroupDocs\Editor\FileApi($configuration);
 
// The document already uploaded into the storage
// Load it into editable state
$fileInfo = new Model\FileInfo();
$fileInfo->setFilePath("Spreadsheet/sample.tsv");        
$loadOptions = new Model\DelimitedTextLoadOptions();
$loadOptions->setFileInfo($fileInfo);
$loadOptions->setOutputPath("output");
$loadResult = $editApi->load(new Requests\loadRequest($loadOptions));
 
// Download html document
$htmlFile = $fileApi->downloadFile(new Requests\downloadFileRequest($loadResult->getHtmlPath()));
$html = file_get_contents($htmlFile->getRealPath());
 
// Edit something...
$html = str_replace("32", "66", $html);
 
// Upload html back to storage
file_put_contents($htmlFile->getRealPath(), $html);
$uploadRequest = new Requests\uploadFileRequest($loadResult->getHtmlPath(), $htmlFile->getRealPath());
$fileApi->uploadFile($uploadRequest);
 
// Save html back to tsv
$saveOptions = new Model\DelimitedTextSaveOptions();
$saveOptions->setFileInfo($fileInfo);
$saveOptions->setOutputPath("output/edited.tsv");
$saveOptions->setHtmlPath($loadResult->getHtmlPath());
$saveOptions->setResourcesPath($loadResult->getResourcesPath());
$saveResult = $editApi->save(new Requests\saveRequest($saveOptions));
 
// Done.
echo "Document edited: " . $saveResult->getPath();
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
fileInfo.file_path = 'Spreadsheet/sample.tsv'       
 
loadOptions = GroupDocsEditorCloud::DelimitedTextLoadOptions.new
loadOptions.file_info = fileInfo
loadOptions.output_path = "output"
 
loadRequest = GroupDocsEditorCloud::LoadRequest.new(loadOptions)        
loadResult = editApi.load(loadRequest)
 
# Download html document
htmlFile = fileApi.download_file(GroupDocsEditorCloud::DownloadFileRequest.new loadResult.html_path)
htmlFile.open
html = htmlFile.read
htmlFile.close
 
# Edit something...
html = html.gsub("32", "66")
 
# Upload html back to storage
htmlFile = File.open(htmlFile.path, "w")        
htmlFile.write(html)
htmlFile.close
uploadRequest = GroupDocsEditorCloud::UploadFileRequest.new loadResult.html_path, File.open(htmlFile.path, "r")
fileApi.upload_file(uploadRequest)
 
# Save html back to tsv
saveOptions = GroupDocsEditorCloud::DelimitedTextSaveOptions.new
saveOptions.file_info = fileInfo
saveOptions.output_path = "output/edited.tsv"
saveOptions.html_path = loadResult.html_path
saveOptions.resources_path = loadResult.resources_path
 
saveRequest = GroupDocsEditorCloud::SaveRequest.new(saveOptions)
saveResult = editApi.save(saveRequest)        
 
puts("Document edited: " + saveResult.path)
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
// For complete examples and data files, please go to https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-node-samples
global.editor_cloud = require("groupdocs-editor-cloud");
 
global.appSid = "XXXX-XXXX-XXXX-XXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
global.appKey = "XXXXXXXXXXXXXXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
global.editApi = editor_cloud.EditApi.fromKeys(appSid, appKey);
global.fileApi = editor_cloud.FileApi.fromKeys(appSid, appKey);
 
 
// The document already uploaded into the storage.
// Load it into editable state      
let fileInfo = new editor_cloud.FileInfo();
fileInfo.filePath = "Spreadsheet/sample.tsv";       
let loadOptions = new editor_cloud.DelimitedTextLoadOptions();
loadOptions.fileInfo = fileInfo;
loadOptions.outputPath = "output";
let loadResult = await editApi.load(new editor_cloud.LoadRequest(loadOptions));
 
// Download html document
let buf = await fileApi.downloadFile(new editor_cloud.DownloadFileRequest(loadResult.htmlPath));
let htmlString = buf.toString("utf-8");
 
// Edit something...
htmlString = htmlString.replace("32", "66");
 
// Upload html back to storage
await fileApi.uploadFile(new editor_cloud.UploadFileRequest(loadResult.htmlPath, new Buffer(htmlString, "utf-8")));
 
// Save html back to docx
let saveOptions = new editor_cloud.DelimitedTextSaveOptions();
saveOptions.fileInfo = fileInfo;
saveOptions.outputPath = "output/edited.tsv";
saveOptions.htmlPath = loadResult.htmlPath;
saveOptions.resourcesPath = loadResult.resourcesPath;
let saveResult = await editApi.save(new editor_cloud.SaveRequest(saveOptions));
 
// Done.
console.log("Document edited: " + saveResult.path);
```

{{< /tab >}} {{< tab "Python" >}}

```python
# For complete examples and data files, please go to https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-python-samples
import groupdocs_editor_cloud
 
app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
editApi = groupdocs_editor_cloud.EditApi.from_keys(app_sid, app_key)
fileApi = groupdocs_editor_cloud.FileApi.from_keys(app_sid, app_key)
 
# The document already uploaded into the storage.
# Load it into editable state
fileInfo = groupdocs_editor_cloud.FileInfo("Spreadsheet/sample.tsv")
loadOptions = groupdocs_editor_cloud.DelimitedTextLoadOptions()
loadOptions.file_info = fileInfo
loadOptions.output_path = "output"       
loadResult = editApi.load(groupdocs_editor_cloud.LoadRequest(loadOptions))        
 
# Download html document
htmlFile = fileApi.download_file(groupdocs_editor_cloud.DownloadFileRequest(loadResult.html_path))
html = ""       
with open(htmlFile, 'r') as file:
    html = file.read()
 
# Edit something...    
html = html.replace("32", "66")
 
# Upload html back to storage
with open(htmlFile, 'w') as file:
    file.write(html)
 
fileApi.upload_file(groupdocs_editor_cloud.UploadFileRequest(loadResult.html_path, htmlFile))
 
# Save html back to tsv
saveOptions = groupdocs_editor_cloud.DelimitedTextSaveOptions()
saveOptions.file_info = fileInfo
saveOptions.output_path = "output/edited.tsv"
saveOptions.html_path = loadResult.html_path
saveOptions.resources_path = loadResult.resources_path
saveResult = editApi.save(groupdocs_editor_cloud.SaveRequest(saveOptions))
 
# Done
print("Document edited: " + saveResult.path)
```

{{< /tab >}} {{< /tabs >}}
