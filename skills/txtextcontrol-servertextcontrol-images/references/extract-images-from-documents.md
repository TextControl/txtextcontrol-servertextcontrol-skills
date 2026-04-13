# Extract Images from Existing Documents

## Goal

Extract all embedded images from documents (DOC, DOCX, RTF, PDF) using
ServerTextControl by exporting to HTML with image data and decoding base64.

## Source

- https://www.textcontrol.com/blog/2024/06/11/extracting-images-from-ms-word-documents-in-csharp/

## Helper: Parse Embedded Base64 Images from HTML

```csharp
static List<ImageData> GetImageBase64Strings(string html)
{
    var imageDatas = new List<ImageData>();
    var regex = new Regex("<img[^>]+?src=[\"']data:image/(?<format>[^;]+);base64,(?<data>[^\"']+)[\"'][^>]*>", RegexOptions.IgnoreCase);

    foreach (Match match in regex.Matches(html))
    {
        var format = match.Groups["format"].Value;
        var base64Content = match.Groups["data"].Value;
        var extension = GetFileExtension(format);

        imageDatas.Add(new ImageData
        {
            Base64Content = base64Content,
            Format = format,
            Extension = extension
        });
    }

    return imageDatas;
}

static string GetFileExtension(string format)
{
    return format.ToLower() switch
    {
        "jpeg" => ".jpg",
        "jpg" => ".jpg",
        "png" => ".png",
        "gif" => ".gif",
        "bmp" => ".bmp",
        "webp" => ".webp",
        "svg+xml" => ".svg",
        "tiff" => ".tif",
        "x-icon" => ".ico",
        _ => $".{format}"
    };
}

public class ImageData
{
    public string Base64Content { get; set; }
    public string Format { get; set; }
    public string Extension { get; set; }
}
```

## End-to-End Extraction Flow

```csharp
using (TXTextControl.ServerTextControl tx = new TXTextControl.ServerTextControl())
{
    tx.Create();

    tx.Load("invoice.docx", TXTextControl.StreamType.WordprocessingML);

    TXTextControl.SaveSettings saveSettings = new TXTextControl.SaveSettings()
    {
        ImageSaveMode = TXTextControl.ImageSaveMode.SaveAsData
    };

    string doc = "";

    tx.Save(out doc, TXTextControl.StringStreamType.HTMLFormat, saveSettings);

    var images = GetImageBase64Strings(doc);

    foreach (var image in images)
    {
        byte[] imageBytes = Convert.FromBase64String(image.Base64Content);

        using (FileStream fs = new FileStream("image" + image.Extension, FileMode.Create))
        {
            fs.Write(imageBytes, 0, imageBytes.Length);
        }
    }
}
```

This workflow loads the source document, exports HTML with embedded image data,
extracts the `data:image/...;base64` payloads, and writes each image to disk.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.servertextcontrol.load.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.servertextcontrol.save.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.savesettings.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.imagesavemode.enumeration.htm
