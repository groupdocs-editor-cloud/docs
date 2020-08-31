---
id: "features-overview"
url: "editor/features-overview"
title: "Features Overview"
productName: "GroupDocs.Editor Cloud"
weight: 1
description: ""
keywords: ""
---

## Overview ##

GroupDocs.Editor Cloud is a REST API that allows you to edit documents across a wide range of supported document types. Below, the shortlist of possible actions:

## Document Edit operations ##

The main feature of GroupDocs.Editor API is an ability to edit the most popular document formats using front-end WYSIWYG editors without any additional applications. No Open Office or MS Office is required to edit a Word Processing documents, Spreadsheets or Presentations. You can just load documents via GroupDocs.Editor into any WYSIWYG editor, edit document in a way you want and save it back to original document format.

### Editing options and output customizations ###

GroupDocs.Editor Cloud provides a set of options to customize the editing process dependent on the document type:

* Word Processing documents - the ability to edit document in a flow or paged mode; consider language information for multi-language document editing; manage font extraction to provide the same document editing and appearance behavior in different environments.
* Spreadsheets - supports multi-tabbed spreadsheets editing by the ability to specify the index of the currently edited worksheet.
* Comma-Separated Values and Tab-Separated Values - options to specify separator; flexible numeric and dates conversion; memory usage optimization for large files;
* XML files - fix incorrect document structure; URIs and e-mail addresses recognition; highlight and formatting options etc.

## Document information extraction ##

GroupDocs.Editor Cloud API provides an ability to extract basic information about edited document:

* Document type;
* Document size;
* Pages count;
* etc.

This may be quite useful for other manipulations.

## API Endpoint Groups Overview ##

|Endpoint Group|Description
|---|---
|Info|It contains endpoints for obtaining a list of formats supported by GroupDocs.Editor Cloud, and getting basic information about document and its pages
|Edit|Contains main product endpoints for document editing operations - edit, save
|File|Contains endpoints for upload, download, copy, move, delete files in the storage
|Folder|Contains endpoints for creating, copy, move, delete folders in the storage
|Storage|Contains endpoints for obtaining storage information and file information

## Security and Authentication ##

The GroupDocs.Editor Cloud API is secured and requires authentication. Two keys AppSID and AppKey are required for Authentication which can be created at the [Dashboard](http://dashboard.groupdocs.cloud/). Check [Authenticating API Requests]({{< ref "total/getting-started/overview-rest-api/authenticating-api-requests.md" >}})) article for complete example.

## SDKs ##

Check out our GitHub [repository](https://github.com/groupdocs-editor-cloud) for a complete list of GroupDocs.Editor SDKs along with working examples, to get you started in no time.

At the moment following SDKs are provided:

* .NET ([Sources](https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-dotnet), [NuGet Package](https://www.nuget.org/packages/GroupDocs.Editor-Cloud))
* Java ([Sources](https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-java), [Jar](https://repository.groupdocs.cloud/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-editor-cloud))
* PHP ([Sources](https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-php))
* Node.js ([Sources](https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-node))
* Python ([Sources](https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-python))
* Ruby ([Sources](https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-ruby))

## API Explorer ##

The easiest way to try out our API right away in your browser! With the [GroupDocs.Editor Cloud API explorer](https://apireference.groupdocs.cloud/editor/). This is a collection of Swagger documentation for the GroupDocs Cloud APIs. You can get information about all the resources in the API. It also provides testing and interactivity to our API endpoint documentation.
