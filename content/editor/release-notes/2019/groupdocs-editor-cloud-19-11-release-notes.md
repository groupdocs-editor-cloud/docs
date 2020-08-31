---
id: "groupdocs-editor-cloud-19-11-release-notes"
url: "editor/groupdocs-editor-cloud-19-11-release-notes"
title: "GroupDocs.Editor Cloud 19.11 Release Notes"
productName: "GroupDocs.Editor Cloud"
weight: 1
description: ""
keywords: ""
---

{{< alert style="info" >}}
This page contains release notes for GroupDocs.Editor Cloud 19.11
{{< /alert >}}

## Major Features ##

The main feature of [GroupDocs.Editor Cloud API](https://products.groupdocs.cloud/editor) is an ability to edit the most popular document formats using front-end **WYSIWYG** editors without any additional applications. No Open Office or MS Office is required to edit a Word Processing documents, Spreadsheets or Presentations. You can just load documents via GroupDocs.Editor into any **WYSIWYG** editor, edit document in a way you want and save it back to original document format.

* Word Processing documents - the ability to edit document in a flow or paged mode; consider language information for multi-language document editing; manage font extraction to provide the same document editing and appearance behavior in different environments.
* Spreadsheets - supports multi-tabbed spreadsheets editing by the ability to specify the index of the currently edited worksheet.
* Comma-Separated Values and Tab-Separated Values - options to specify separator; flexible numeric and dates conversion; memory usage optimization for large files;
* XML files - fix incorrect document structure; URIs and e-mail addresses recognition; highlight and formatting options etc.
* GroupDocs.Editor Cloud API provides an ability to extract basic information about edited document:
    * Document type.
    * Document size.
    * Pages count.

# API Endpoint Groups Overview #

|Endpoint Group|Description
|---|---
|Info|It contains endpoints for obtaining a list of formats supported by GroupDocs.Editor Cloud, and getting basic information about the document and its pages
|Edit|Contains main product endpoints for document editing operations - edit, save
|File|Contains endpoints for upload, download, copy, move, delete files in the storage
|Folder|Contains endpoints for creating, copy, move, delete folders in the storage
|Storage|Contains endpoints for obtaining storage information and file information

## Public API Examples ##

* [GroupDocs Editor Cloud API examples and documentation]({{< ref "editor/_index.md" >}})
