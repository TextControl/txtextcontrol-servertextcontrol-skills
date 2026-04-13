# Get SubTextParts by Name, ID, or Position

## Goal

Retrieve SubTextParts using `GetItem()` overloads and inspect nested children.

## Source

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpartcollection.getitem.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpart.getchildren.method.htm

## Get at Current Input Position

```csharp
TXTextControl.SubTextPart currentPart = textControl1.SubTextParts.GetItem();
```

## Get by Name and ID

```csharp
TXTextControl.SubTextPart namedPart = textControl1.SubTextParts.GetItem("part1");
TXTextControl.SubTextPart idPart = textControl1.SubTextParts.GetItem(1);
```

## Enumerate Children of a Parent SubTextPart

```csharp
TXTextControl.SubTextPart parent = textControl1.SubTextParts.GetItem("part1");

if (parent != null)
{
    TXTextControl.SubTextPart[] children = parent.GetChildren();

    if (children != null)
    {
        foreach (TXTextControl.SubTextPart child in children)
        {
            System.Diagnostics.Debug.WriteLine(child.Name);
        }
    }
}
```

## Notes

- `GetItem(name)` and `GetItem(id)` return `null` if not found.
- `GetChildren()` includes direct children and deeper descendants.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpart.name.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpart.id.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpart.nestedlevel.property.htm
