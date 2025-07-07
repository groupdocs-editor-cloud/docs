---
id: "quickstart"
url: "editor/quickstart"
title: "Quickstart"
productName: "GroupDocs.Editor Cloud"
weight: 2
description: ""
keywords: ""
toc: True
---

## Create an account

Creating an account is very simple. Go to [https://dashboard.groupdocs.cloud](https://dashboard.groupdocs.cloud/) to create a free account.

## Create an API client app

Before you can make any requests to GroupDocs Cloud API you need to get Client Id and Client Secret. This will be used to invoke the GroupDocs Cloud API.

You can get it from existing Application or create new Application from [Applications View of GroupDocs Cloud Dashboard]({{< ref "total/ui-topics/creating-and-managing-application.md" >}}).

## Install the SDK of your choice

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of making requests and handling responses and lets you focus on writing code specific to your particular project. Please check  article to learn how to add an SDK to your project.

## Make an API request from the SDK of your choice

Use the **Client Id** and **Client Secret** from the API app client you created in step one and replace in the corresponding code. Below is an example demonstrating how to edit docx document using GroupDocs.Editor Cloud.

{{< alert style="info" >}}
The GitHub repository for [GroupDocs.Editor Cloud](https://github.com/groupdocs-editor-cloud) has a complete set of examples, demonstrating our API capabilities.
{{< /alert >}}

For complete examples and data files, please go to [https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-dotnet-samples](https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-dotnet-samples)

{{< tabs "example1">}} {{< tab "C#" >}}

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
var loadOptions = new WordProcessingLoadOptions
{
    FileInfo = new FileInfo
    {
        FilePath = "WordProcessing/password-protected.docx",
        Password = "password"
    },
    OutputPath = "output"
};
var loadResult = editApi.Load(new LoadRequest(loadOptions));
 
// Download html document
var stream = fileApi.DownloadFile(new DownloadFileRequest(loadResult.HtmlPath));
var htmlString = new StreamReader(stream, Encoding.UTF8).ReadToEnd();
 
// Edit something...
htmlString = htmlString.Replace("Sample test text", "Hello world");
 
// Upload html back to storage
fileApi.UploadFile(new UploadFileRequest(loadResult.HtmlPath,
    new MemoryStream(Encoding.UTF8.GetBytes(htmlString))));
 
// Save html back to docx
var saveOptions = new WordProcessingSaveOptions
{
    FileInfo = loadOptions.FileInfo,
    OutputPath = "output/edited.docx",
    HtmlPath = loadResult.HtmlPath,
    ResourcesPath = loadResult.ResourcesPath
};
var saveResult = editApi.Save(new SaveRequest(saveOptions));
```

{{< /tab >}} {{< /tabs >}}
