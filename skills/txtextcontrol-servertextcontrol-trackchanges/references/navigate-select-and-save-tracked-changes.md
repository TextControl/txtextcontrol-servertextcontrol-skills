# Navigate, Select, and Save Tracked Changes

## Goal

Navigate to current/next/previous changes, select them, and export changed text.

## Source

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchangecollection.getitem.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchange.select.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchange.scrollto.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchange.save.method.htm

## Get Current, Next, and Previous Change

```csharp
TrackedChange current = textControl.TrackedChanges.GetItem();
TrackedChange next = textControl.TrackedChanges.GetItem(true);
TrackedChange previous = textControl.TrackedChanges.GetItem(false);
```

## Select and Scroll to a Change

```csharp
if (next != null)
{
    next.Select();
    next.ScrollTo();
}
```

## Save Changed Text to a Binary Buffer

```csharp
if (current != null)
{
    current.Save(out byte[] changedContent, BinaryStreamType.InternalUnicodeFormat);
}
```

## Notes

- `GetItem(true)` returns the next change in text flow.
- `GetItem(false)` returns the previous change in text flow.
- Returned value is `null` when no matching change exists.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchangecollection.getitem.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchange.number.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchange.start.property.htm
