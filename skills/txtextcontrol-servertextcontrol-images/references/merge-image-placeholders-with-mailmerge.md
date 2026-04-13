# Merge Image Placeholders with MailMerge

## Goal

Use named image placeholders in templates and merge them with data values from
JSON. Supports base64 content and physical file references.

## Source

- https://www.textcontrol.com/blog/2022/12/22/mailmerge-working-with-image-placeholders/

## Placeholder Concept

An image placeholder is an image object in the template with a `Name` that
matches the data field in the merge source.

Supported source formats include:

- byte array
- `System.Drawing.Image`
- file name/path
- hex string
- base64 string

## Merge Base64 Image Data

Given JSON data like:

```json
[
  {
    "image1": "iVBORw0KGgoAAAANSUhEUgAA..."
  }
]
```

Merge with MailMerge:

```csharp
using (TXTextControl.ServerTextControl tx = new TXTextControl.ServerTextControl())
{
    tx.Create();
    tx.Load("template.tx", TXTextControl.StreamType.InternalUnicodeFormat);

    using (TXTextControl.DocumentServer.MailMerge mailMerge =
        new TXTextControl.DocumentServer.MailMerge())
    {
        mailMerge.TextComponent = tx;

        var jsonData = System.IO.File.ReadAllText("data.json");
        mailMerge.MergeJsonData(jsonData);
    }
}
```

## Merge File Reference Images

Given JSON data like:

```json
[
  {
    "image1": "result.png"
  }
]
```

Use `SearchPath` so merge can resolve physical image files:

```csharp
using (TXTextControl.ServerTextControl tx = new TXTextControl.ServerTextControl())
{
    tx.Create();
    tx.Load("template.tx", TXTextControl.StreamType.InternalUnicodeFormat);

    using (TXTextControl.DocumentServer.MailMerge mailMerge =
        new TXTextControl.DocumentServer.MailMerge())
    {
        mailMerge.TextComponent = tx;
        mailMerge.SearchPath = Application.StartupPath;

        var jsonData = System.IO.File.ReadAllText("data.json");
        mailMerge.MergeJsonData(jsonData);
    }
}
```

## Remove Missing Image Placeholders

```csharp
mailMerge.RemoveEmptyImages = true;
```

By default, placeholders remain if no image is found. Enable this option to
remove them when source data is missing.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.documentserver.mailmerge.mergejsondata.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.documentserver.mailmerge.searchpath.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.documentserver.datasources.mergesettings.removeemptyimages.property.htm
