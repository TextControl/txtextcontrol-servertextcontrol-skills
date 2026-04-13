# Create and Highlight SubTextParts

## Goal

Create a SubTextPart from the current text selection and apply visual
highlight styling to the region.

## Source

- https://www.textcontrol.com/blog/2024/02/09/the-power-of-subtextparts-typical-use-cases/
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpartcollection.add.method.htm

## Create and Add a Highlighted SubTextPart

```csharp
// create a new SubTextPart with the name "part1" and id 1
TXTextControl.SubTextPart subTextPart = new TXTextControl.SubTextPart("part1", 1);

// set the highlight color to red
subTextPart.HighlightColor = Color.FromArgb(60, Color.Red);
subTextPart.HighlightMode = TXTextControl.HighlightMode.Always;

// add the subtext part to the SubTextParts collection
textControl1.SubTextParts.Add(subTextPart);
```

## Validate Add Result

```csharp
TXTextControl.SubTextPartCollection.AddResult result =
    textControl1.SubTextParts.Add(subTextPart);

if (result != TXTextControl.SubTextPartCollection.AddResult.Successful)
{
    // Handle AlreadyExists, Overlapping, NoSelection, etc.
}
```

## Notes

- If `SubTextPart.Length` is `0`, the current selection defines the range.
- `AddResult` helps detect overlapping or invalid insertion cases.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpart.highlightcolor.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpart.highlightmode.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpartcollection.addresult.enumeration.htm
