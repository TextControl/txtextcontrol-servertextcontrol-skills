# Remove SubTextParts with Keep Options

## Goal

Remove SubTextParts while controlling whether visible text and nested parts are preserved.

## Source

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpartcollection.remove.method.htm

## Remove and Keep Visible Text

```csharp
TXTextControl.SubTextPart part = textControl1.SubTextParts.GetItem("part1");

if (part != null)
{
    bool removed = textControl1.SubTextParts.Remove(part, keepText: true, keepNested: true);
}
```

## Remove and Delete Visible Text

```csharp
TXTextControl.SubTextPart part = textControl1.SubTextParts.GetItem("part1");

if (part != null)
{
    bool removed = textControl1.SubTextParts.Remove(part, keepText: false, keepNested: false);
}
```

## Notes

- `keepText: true` removes only the SubTextPart marker but keeps text content.
- If `keepText` is `false`, `keepNested` is ignored by the API.
- The method returns `true` on successful removal.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpartcollection.remove.method.htm
