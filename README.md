![](https://img.shields.io/badge/api-v1.0-lightgrey) ![PyPI](https://img.shields.io/pypi/v/groupdocs-editor-cloud) ![PyPI - Python Version](https://img.shields.io/pypi/pyversions/groupdocs-editor-cloud) ![PyPI - Implementation](https://img.shields.io/pypi/implementation/groupdocs-editor-cloud) ![PyPI - Wheel](https://img.shields.io/pypi/wheel/groupdocs-editor-cloud) [![GitHub license](https://img.shields.io/github/license/groupdocs-editor-cloud/groupdocs-editor-cloud-python)](https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-python/blob/master/LICENSE) 

# Python SDK to Document Editor REST API

[GroupDocs.Editor Cloud SDK for Python](https://products.groupdocs.cloud/editor/python) wraps GroupDocs.Editor RESTful API so you may integrate Document Editing features in your own apps with zero initial cost.

GroupDocs.Editor Cloud API allows the developers to edit most popular document formats using front-end WYSIWYG editors - without needing the applications like OpenOffice or Microsoft Office. Just load documents via GroupDocs.Editor into any WYSIWYG editor, edit document in a way you want and save it back to original document format.

## Document Editing in the Cloud

GroupDocs.Editor Cloud provides a set of options to customize the editing process dependending on the document type.

- **Word Processing:** Edit document in a flow or paged mode, consider language information for multi-language document editing, manage font extraction to provide the same document editing and appearance behavior in different environments.
- **Spreadsheets:** Supports multi-tabbed spreadsheet editing with the ability to specify the index of the currently edited worksheet.
- **Comma-Separated & Tab-Separated Values:** Specify separator, flexible numeric and dates conversion, memory usage optimization for large files.
- **Markup:** Fix incorrect document structure, URI & e-mail address recognition, highlight and formatting options.

### Document Information Extraction

GroupDocs.Editor Cloud also provides the ability to extract basic information about the edited document.

- Document type
- Document size
- Pages count

Check out the [Developer's Guide](https://docs.groupdocs.cloud/editor/developer-guide/) to know more about GroupDocs.Editor REST API.

## Microsoft Office Formats

**Microsoft Word:** DOC, DOCX, DOCM, DOT, DOTM, DOTX, RTF, FlatOpc, WordML\
**Microsoft Excel:** XLS, XLSX, XLSM, XLT, XLTX, XLTM, XLSB, XLAM, SpreadsheetML\
**Microsoft PowerPoint:** PPT, PPTX, PPTM, PPS, PPSX, PPSM, POT, POTX, POTM

## Other Formats

**OpenDocument:** ODT, OTT, ODP, OTP, ODS, FODS\
**Markup:** HTML, XML\
**Others:** SXC, DIF, DSV, TXT, CSV, TSV

## Get Started with GroupDocs.Editor Cloud SDK for Python

First create an account at [GroupDocs for Cloud](https://dashboard.groupdocs.cloud/) and get your application information. Next, follow the installation steps as given below.

### Installation

Install `groupdocs-editor-cloud` with [PIP](https://pypi.org/project/pip/) from [PyPI](https://pypi.org/) by:

```sh
pip install groupdocs-editor-cloud
```

Or clone repository and install it via [Setuptools](http://pypi.python.org/pypi/setuptools): 

```sh
python setup.py install
```

## Edit a PowerPoint Presentation via Python

```python
# For complete examples and data files, please go to https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-python-samples
import groupdocs_editor_cloud

# Get application information from https://dashboard.groupdocs.cloud
app_sid = "XXXX-XXXX-XXXX-XXXX" 
app_key = "XXXXXXXXXXXXXXXX"
  
editApi = groupdocs_editor_cloud.EditApi.from_keys(app_sid, app_key)
fileApi = groupdocs_editor_cloud.FileApi.from_keys(app_sid, app_key)
 
# The document already uploaded into the storage.
# Load it into editable state
fileInfo = groupdocs_editor_cloud.FileInfo("Presentation/with-notes.pptx")
loadOptions = groupdocs_editor_cloud.PresentationLoadOptions()
loadOptions.file_info = fileInfo
loadOptions.output_path = "output"
loadOptions.slide_number = 0
loadResult = editApi.load(groupdocs_editor_cloud.LoadRequest(loadOptions))        
 
# Download html document
htmlFile = fileApi.download_file(groupdocs_editor_cloud.DownloadFileRequest(loadResult.html_path))
html = ""       
with open(htmlFile, 'r') as file:
    html = file.read()
 
# Edit something...    
html = html.replace("Slide sub-heading", "Hello world!")
 
# Upload html back to storage
with open(htmlFile, 'w') as file:
    file.write(html)
 
fileApi.upload_file(groupdocs_editor_cloud.UploadFileRequest(loadResult.html_path, htmlFile))
 
# Save html back to pptx
saveOptions = groupdocs_editor_cloud.PresentationSaveOptions()
saveOptions.file_info = fileInfo
saveOptions.output_path = "output/edited.pptx"
saveOptions.html_path = loadResult.html_path
saveOptions.resources_path = loadResult.resources_path
saveResult = editApi.save(groupdocs_editor_cloud.SaveRequest(saveOptions))
 
# Done
print("Document edited: " + saveResult.path)
```

## GroupDocs.Editor Cloud SDKs in Popular Languages

| .NET | Java | PHP | Python | Ruby | Node.js | Android |
|---|---|---|---|---|---|---|
| [GitHub](https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-dotnet) | [GitHub](https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-java) | [GitHub](https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-php) | [GitHub](https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-python) | [GitHub](https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-ruby)  | [GitHub](https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-node) | [GitHub](https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-android) |
| [NuGet](https://www.nuget.org/packages/GroupDocs.Editor-Cloud/) | [Maven](https://repository.groupdocs.cloud/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-editor-cloud) | [Composer](https://packagist.org/packages/groupdocscloud/groupdocs-editor-cloud) | [PIP](https://pypi.org/project/groupdocs-editor-cloud/) | [GEM](https://rubygems.org/gems/groupdocs_editor_cloud)  | [NPM](https://www.npmjs.com/package/groupdocs-editor-cloud) | [Maven](https://repository.groupdocs.cloud/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-editor-cloud-android) |

[Home](https://www.groupdocs.cloud/) | [Product Page](https://products.groupdocs.cloud/editor/python) | [Documentation](https://docs.groupdocs.cloud/editor/) | [Live Demo](https://products.groupdocs.app/editor/total) | [API Reference](https://apireference.groupdocs.cloud/editor/) | [Code Samples](https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-python-samples) | [Blog](https://blog.groupdocs.cloud/category/editor/) | [Free Support](https://forum.groupdocs.cloud/c/editor) | [Free Trial](https://dashboard.groupdocs.cloud)
