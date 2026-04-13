# Accept or Reject Tracked Changes

## Goal

Accept or reject a selected set of tracked changes programmatically.

## Source

- https://www.textcontrol.com/blog/2026/03/10/inspect-and-process-track-changes-in-docx-documents-with-tx-text-control-with-dotnet-csharp/
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchangecollection.remove.method.htm

## Accept Filtered Changes

```csharp
using System.Linq;
using TXTextControl;

var changes = textControl.TrackedChanges
    .Cast<TrackedChange>()
    .Where(c => c.UserName == "Alice Johnson")
    .ToList();

bool acceptChanges = true;

foreach (TrackedChange change in changes)
{
    textControl.TrackedChanges.Remove(change, acceptChanges);
}
```

## Reject Filtered Changes

```csharp
bool acceptChanges = false;

foreach (TrackedChange change in changes)
{
    textControl.TrackedChanges.Remove(change, acceptChanges);
}
```

## Notes

- `accept = true` accepts the revision.
- `accept = false` rejects the revision.
- Create a stable list first (`ToList`) before removing to avoid mutating while enumerating.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchangecollection.remove.method.htm
