# Set Multilevel List Indentation and Levels

## Goal

Create nested list structures by setting list level and indentation attributes.

## Source

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listformat.level.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listformat.leftindent.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listformat.hangingindent.property.htm

## Configure Numbered Multilevel List

```csharp
TXTextControl.ListFormat lf = new TXTextControl.ListFormat();
lf.Type = TXTextControl.ListType.Numbered;
lf.Level = 1;
lf.LeftIndent = 720;    // 0.5 inch in twips
lf.HangingIndent = 360; // 0.25 inch in twips

textControl1.Selection.ListFormat = lf;
```

## Promote/Demote List Level

```csharp
TXTextControl.ListFormat lf = textControl1.Selection.ListFormat;

// Demote one level
if (lf.Level < TXTextControl.ListFormat.MaxLevel)
{
    lf.Level = lf.Level + 1;
}

textControl1.Selection.ListFormat = lf;
```

## Apply by Paragraph

```csharp
foreach (TXTextControl.Paragraph p in textControl1.Paragraphs)
{
    TXTextControl.ListFormat lf = p.ListFormat;

    if (lf.Type == TXTextControl.ListType.Numbered)
    {
        lf.LeftIndent = 1080;
        lf.HangingIndent = 360;
        p.ListFormat = lf;
    }
}
```

## Notes

- `Level` controls nesting depth.
- Use `ListFormat.MaxLevel` to keep level changes within supported range.
- Indents are measured in twips.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listformat.maxlevel.field.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.paragraph.listformat.property.htm
