# Add Images to Headers and Footers

## Goal

Insert logos or watermark images into headers/footers and control placement
relative to page text.

## Source

- https://www.textcontrol.com/blog/2024/10/25/create-word-document-with-net-c-sharp/
- https://www.textcontrol.com/blog/2022/01/28/adding-svg-watermarks-to-documents/

## Add a Logo to Header

```csharp
using TXTextControl;

using (ServerTextControl tx = new ServerTextControl())
{
    tx.Create();

    tx.Sections.GetItem().HeadersAndFooters.Add(HeaderFooterType.Header);

    HeaderFooter headerFooter =
        tx.Sections.GetItem().HeadersAndFooters.GetItem(HeaderFooterType.Header);

    Image image = new Image("tx_logo.svg", 0);
    headerFooter.Images.Add(image, HorizontalAlignment.Right, 1, ImageInsertionMode.AboveTheText);

    headerFooter.Selection.Text = "Header Text\r\n\r\n";

    tx.Save("results.docx", StreamType.WordprocessingML);
}
```

## Add Section Watermark via Header

```csharp
public void AddWatermark(TXTextControl.ServerTextControl tx, string imagePath)
{
    tx.PageUnit = MeasuringUnit.Twips;

    foreach (TXTextControl.Section section in tx.Sections)
    {
        section.HeadersAndFooters.Remove(TXTextControl.HeaderFooterType.All);
        section.HeadersAndFooters.Add(TXTextControl.HeaderFooterType.Header);

        TXTextControl.HeaderFooter hf =
            section.HeadersAndFooters.GetItem(TXTextControl.HeaderFooterType.Header);

        TXTextControl.Image image = new TXTextControl.Image();
        image.FileName = imagePath;

        hf.Images.Add(
            image,
            1,
            new System.Drawing.Point(0, 0),
            TXTextControl.ImageInsertionMode.FixedOnPage |
            TXTextControl.ImageInsertionMode.BelowTheText);

        var pageWidth = (int)section.Format.PageSize.Width;
        var pageMarginsHorizontal = (int)(section.Format.PageMargins.Left +
            section.Format.PageMargins.Right);
        var imageWidth = image.Size.Width;
        int locationX = (pageWidth - imageWidth - pageMarginsHorizontal) / 2;

        var pageHeight = (int)section.Format.PageSize.Height;
        var pageMarginsVertical = (int)(section.Format.PageMargins.Top +
            section.Format.PageMargins.Bottom);
        var imageHeight = image.Size.Height;
        int locationY = (pageHeight - imageHeight - pageMarginsVertical) / 2;

        image.Location = new System.Drawing.Point(locationX, locationY);
    }
}
```

## Notes

- Headers/footers repeat per page, which makes them ideal for logos/watermarks.
- For watermark behavior, use `FixedOnPage | BelowTheText`.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.headerfooter.images.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.imagecollection.add.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.imageinsertionmode.enumeration.htm
