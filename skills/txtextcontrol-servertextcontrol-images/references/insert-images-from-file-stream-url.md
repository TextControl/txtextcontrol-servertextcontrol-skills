# Insert Images from File, Stream, and URL

## Goal

Insert images into a document using ServerTextControl from different data
sources: file path, `System.Drawing.Image`, `MemoryStream`, byte array, and URL.

## Source

- https://www.textcontrol.com/blog/2024/05/03/various-ways-of-inserting-images-into-tx-text-control/
- https://www.textcontrol.com/blog/2022/03/28/different-ways-to-insert-images/

## Prerequisites

- .NET 8+ console or backend project
- TX Text Control package installed (`TXTextControl.TextControl.ASP.SDK`)

## Insert from File Path

```csharp
string imagePath = "Images/signature1.jpg";

TXTextControl.Image myImage = new TXTextControl.Image()
{
    FileName = imagePath
};

textControl1.Images.Add(myImage, -1);
```

## Insert from `System.Drawing.Image`

```csharp
string imagePath = "Images/signature1.jpg";
System.Drawing.Image img = System.Drawing.Image.FromFile(imagePath);

TXTextControl.Image myImage = new TXTextControl.Image(img);

textControl1.Images.Add(myImage, -1);
```

## Insert from `MemoryStream`

```csharp
string imagePath = "Images/signature1.jpg";

MemoryStream ms = new MemoryStream();
Image img = Image.FromFile(imagePath);
img.Save(ms, img.RawFormat);

TXTextControl.Image myImage = new TXTextControl.Image(ms);

textControl1.Images.Add(myImage, -1);
```

## Insert from Byte Array

```csharp
string imagePath = "Images/signature1.jpg";

byte[] bytes = File.ReadAllBytes(imagePath);

using (MemoryStream ms = new MemoryStream(
      bytes, 0, bytes.Length, writable: false, publiclyVisible: true))
{
    TXTextControl.Image myImage = new TXTextControl.Image(ms);
    textControl1.Images.Add(myImage, -1);
}
```

## Insert from URL

```csharp
string url = "https://www.textcontrol.com/img/corporate_id/tx_logo.svg";

using (WebClient client = new WebClient())
{
    byte[] bytes = client.DownloadData(url);

    using (MemoryStream ms = new MemoryStream(
          bytes, 0, bytes.Length, writable: false, publiclyVisible: true))
    {
        TXTextControl.Image myImage = new TXTextControl.Image(ms);
        textControl1.Images.Add(myImage, -1);
    }
}
```

## Notes

- `Images.Add(image, -1)` inserts the image at the current input position.
- TX Text Control auto-detects image format in many cases.
- For stream-based images, `publiclyVisible: true` is used in blog samples.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.imagecollection.add.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.image.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.imagecollection.class.htm
