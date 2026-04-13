# Filter Tracked Changes by Author, Kind, and Date

## Goal

Build filtered revision sets using `UserName`, `ChangeKind`, and `ChangeTime`.

## Source

- https://www.textcontrol.com/blog/2026/03/10/inspect-and-process-track-changes-in-docx-documents-with-tx-text-control-with-dotnet-csharp/
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchange.class.htm

## Filter with LINQ

```csharp
using System;
using System.Linq;
using TXTextControl;

string filterAuthor = "Alice Johnson";
ChangeKind? filterKind = null; // example: ChangeKind.InsertedText
DateTime? fromDate = null;
DateTime? toDate = null;

var changes = textControl.TrackedChanges
    .Cast<TrackedChange>()
    .Where(c =>
        (filterAuthor == null || c.UserName == filterAuthor) &&
        (filterKind == null || c.ChangeKind == filterKind) &&
        (fromDate == null || c.ChangeTime >= fromDate) &&
        (toDate == null || c.ChangeTime <= toDate))
    .ToList();

Console.WriteLine($"Filtered changes: {changes.Count}");
```

## Report Filtered Changes

```csharp
foreach (TrackedChange c in changes)
{
    Console.WriteLine($"{c.ChangeKind} | {c.UserName} | {c.ChangeTime:u} | {c.Text}");
}
```

## Notes

- Convert to `ToList()` before accept/reject operations.
- Use this pattern to build audit outputs before modifying the document.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchange.changekind.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchange.username.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchange.changetime.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchange.text.property.htm
