# Save SubTextParts and Store Metadata

## Goal

Save SubTextPart content directly and persist custom JSON metadata in
`SubTextPart.Data`.

## Source

- https://www.textcontrol.com/blog/2024/02/09/the-power-of-subtextparts-typical-use-cases/
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpart.save.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpart.data.property.htm

## Save SubTextPart Content

```csharp
byte[] textBlock;

textControl1.SubTextParts.GetItem("part1").Save(
    out textBlock,
    TXTextControl.BinaryStreamType.InternalUnicodeFormat);
```

## Store JSON Metadata in Data

```csharp
TXTextControl.SubTextPart subTextPart = new TXTextControl.SubTextPart("part1", 1);

UserInfo userInfo = new UserInfo()
{
    Name = "John Doe",
    Address = "123 Main Street",
    City = "Dallas",
    State = "TX",
    Zip = "75201",
    Phone = "214-555-1212"
};

subTextPart.Data = JsonSerializer.Serialize(userInfo);
textControl1.SubTextParts.Add(subTextPart);
```

## Read Metadata Back

```csharp
TXTextControl.SubTextPart part = textControl1.SubTextParts.GetItem("part1");

if (part != null && part.Data != null)
{
    UserInfo userInfo = JsonSerializer.Deserialize<UserInfo>(part.Data);
}
```

## Notes

- `Data` and SubTextPart metadata are preserved in internal TX formats.
- For external formats, verify save/load settings and compatibility.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpart.text.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpartcollection.class.htm
