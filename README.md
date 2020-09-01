# GroupDocs.Editor Cloud Python SDK
Python package for communicating with the GroupDocs.Editor Cloud API

GroupDocs.Editor Cloud allows you to edit documents across wide range of supported document types:
   * Microsoft Word documents - DOC, DOCX, DOCM, DOT, DOTM, DOTX, RTF, FlatOpc, WordML, TXT;
   * Microsoft Excel spreadsheets - XLS, XLSX, XLSM, XLT, XLTX, XLTM, XLSB, SpreadsheetML, CSV, TSV;
   * Microsoft PowerPoint presentations - PPT, PPTX, PPTM, POT, PPS etc.;
   * Open Document formats - ODT, OTT, ODS, ODP, OTP;
   * Markup - HTML, MHTML, XML.
## Requirements

Python 2.7 or 3.4+

## Installation
Install `groupdocs-editor-cloud` with [PIP](https://pypi.org/project/pip/) from [PyPI](https://pypi.org/) by:

```sh
pip install groupdocs-editor-cloud
```

Or clone repository and install it via [Setuptools](http://pypi.python.org/pypi/setuptools): 

```sh
python setup.py install
```

## Getting Started

Please follow the [installation procedure](#installation) and then run following:

```python
# Import module
import groupdocs_editor_cloud

# Get your app_sid and app_key at https://dashboard.groupdocs.cloud (free registration is required).
app_sid = "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX"
app_key = "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"

# Create instance of the API
api = groupdocs_editor_cloud.InfoApi.from_keys(app_sid, app_key)

try:
    # Retrieve supported file-formats
    response = api.get_supported_file_formats()

    # Print out supported file-formats
    print("Supported file-formats:")
    for format in response.formats:
        print('{0} ({1})'.format(format.file_format, format.extension)) 
except groupdocs_editor_cloud.ApiException as e:
    print("Exception when calling get_supported_file_formats: {0}".format(e.message))
```

## Licensing
GroupDocs.Editor Cloud Python SDK licensed under [MIT License](http://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-python/LICENSE).

[Home](https://www.groupdocs.cloud/) | [Product Page](https://products.groupdocs.cloud/editor/python) | [Docs](https://docs.groupdocs.cloud/editor/) | [Demos](https://products.groupdocs.app/editor/family) | [API Reference](https://apireference.groupdocs.cloud/editor/) | [Examples](https://github.com/groupdocs-editor-cloud/groupdocs-editor-cloud-python-samples) | [Blog](https://blog.groupdocs.cloud/category/editor/) | [Free Support](https://forum.groupdocs.cloud/c/editor) | [Free Trial](https://purchase.groupdocs.cloud/trial)
