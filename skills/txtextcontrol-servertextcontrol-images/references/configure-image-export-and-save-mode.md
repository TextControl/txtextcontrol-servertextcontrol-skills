# Configure Image Export and Save Mode

## Goal

Control how images are persisted when saving documents by configuring image
`SaveMode`, export quality, output filter, and maximum resolution.

## Source

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.imagecollection.class.htm

## Configure All Images in a Document

```csharp
foreach (TXTextControl.Image myImage in textControl1.Images)
{
    myImage.SaveMode = TXTextControl.ImageSaveMode.SaveAsFileReference;
    myImage.ExportCompressionQuality = 100; // maximum quality
    myImage.ExportFilterIndex = 4;          // PNG format
    myImage.ExportMaxResolution = 96;       // max 96 DPI
}
```

This pattern configures all existing images so the next save operation exports
images as referenced files with the desired export options.

## Useful Properties

- `Image.SaveMode`
- `Image.ExportCompressionQuality`
- `Image.ExportFilterIndex`
- `Image.ExportMaxResolution`
- `ImageCollection.ExportFilters`
- `ImageCollection.ImportFilters`

## Notes

- `SaveAsFileReference` stores images externally when the document is saved.
- Exported files are placed in the generated image folder at save time.
- `ExportFilterIndex` should match one of the supported export filters.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.imagecollection.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.image.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.imagesavemode.enumeration.htm
