# Load and Enumerate Tracked Changes

## Goal

Load a document and enumerate all tracked revisions with key metadata.

## Source

- https://www.textcontrol.com/blog/2026/03/10/inspect-and-process-track-changes-in-docx-documents-with-tx-text-control-with-dotnet-csharp/
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.servertextcontrol.trackedchanges.property.htm

## Load DOCX and List Tracked Changes

```csharp
using System;
using TXTextControl;

using var textControl = new ServerTextControl();
textControl.Create();

textControl.Load("nda.docx", StreamType.WordprocessingML);

foreach (TrackedChange change in textControl.TrackedChanges)
{
    Console.WriteLine(
        $"#{change.Number} | {change.ChangeKind} | {change.UserName} | " +
        $"Start={change.Start} | Length={change.Length} | {change.ChangeTime:u}");
}

Console.WriteLine($"Total tracked changes: {textControl.TrackedChanges.Count}");
```

## Notes

- `TrackedChanges` exposes changes in the active text part.
- `Start` is one-based.
- Tracked changes loaded from DOCX can then be accepted or rejected.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchangecollection.count.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchange.changekind.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchange.username.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchange.changetime.property.htm
