﻿﻿# OpenXmlPowerTools

Fork of https://github.com/Codeuctivity/OpenXmlPowerTools with .net framework 4.8 compatibility

## Known missing features - Conversion of DOCX to HTML/CSS

- [floating settings of images are ignored](https://stackoverflow.com/questions/70277539/how-to-handle-floating-images-in-openxml-and-convert-to-html-equivalent/73639409#73639409)
- [W.oMath](https://github.com/Codeuctivity/OpenXmlToHtml/issues/74)
- many more


## Example - Convert DOCX to HTML

``` csharp
var sourceDocxFileContent = File.ReadAllBytes("./source.docx");
using var memoryStream = new MemoryStream();
await memoryStream.WriteAsync(sourceDocxFileContent, 0, sourceDocxFileContent.Length);
using var wordProcessingDocument = WordprocessingDocument.Open(memoryStream, true);
var settings = new WmlToHtmlConverterSettings("htmlPageTitle");
var html = WmlToHtmlConverter.ConvertToHtml(wordProcessingDocument, settings);
var htmlString = html.ToString(SaveOptions.DisableFormatting);
File.WriteAllText("./target.html", htmlString, Encoding.UTF8);
```

### Other features

- Splitting DOCX/PPTX files into multiple files.
- Combining multiple DOCX files into a single file.
- Populating content in template DOCX files with data from XML.
- Conversion of HTML/CSS to DOCX.
- Searching and replacing content in DOCX/PPTX using regular expressions.
- Managing tracked-revisions, including detecting tracked revisions, and accepting tracked revisions.
- Updating Charts in DOCX/PPTX files, including updating cached data, as well as the embedded XLSX.
- Retrieving metrics from DOCX files, including the hierarchy of styles used, the languages used, and the fonts used.
- Writing XLSX files using far simpler code than directly writing the markup, including a streaming approach that
  enables writing XLSX files with millions of rows.
- Extracting data (along with formatting) from spreadsheets.

## Development

- Run `dotnet build OpenXmlPowerTools.sln`