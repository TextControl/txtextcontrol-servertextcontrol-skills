# Handle TrackChange Events and Save Without Markup

## Goal

React to track-change lifecycle events and save a document with Track Changes
markup removed while keeping final text content.

## Source

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.servertextcontrol.trackedchangecreated.event.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.servertextcontrol.trackedchangedeleted.event.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.savesettings.omittedcontent.property.htm

## Subscribe to TrackChange Events

```csharp
using TXTextControl;

textControl.TrackedChangeCreated += TextControl_TrackedChangeCreated;
textControl.TrackedChangeDeleted += TextControl_TrackedChangeDeleted;

private static void TextControl_TrackedChangeCreated(object sender, TrackedChangeEventArgs e)
{
    Console.WriteLine($"Created: #{e.TrackedChange.Number} {e.TrackedChange.ChangeKind}");
}

private static void TextControl_TrackedChangeDeleted(object sender, TrackedChangeEventArgs e)
{
    Console.WriteLine($"Deleted: #{e.TrackedChange.Number} {e.TrackedChange.ChangeKind}");
}
```

## Save Without Track Change Markup

```csharp
SaveSettings saveSettings = new SaveSettings()
{
    OmittedContent = OmittedContent.TrackedChanges
};

textControl.Save("final.docx", StreamType.WordprocessingML, saveSettings);
```

## Notes

- `OmittedContent.TrackedChanges` removes revision markup only.
- This omitted-content option is not available for Adobe PDF/PDF-A save operations.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchangeeventargs.trackedchange.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.savesettings.class.htm
