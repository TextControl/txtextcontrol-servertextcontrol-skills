# Get and Remove ApplicationFields

## Goal

Retrieve ApplicationFields by current input position or by ID, then remove
them with control over whether visible text is preserved.

## Source

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfieldcollection.getitem.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfieldcollection.remove.method.htm

## Get Field at Current Input Position

```csharp
TXTextControl.ApplicationField field = textControl1.ApplicationFields.GetItem();

if (field != null)
{
    // Use field properties, for example field.TypeName or field.Text
}
```

## Get Field by ID

```csharp
int fieldId = 25;
TXTextControl.ApplicationField field = textControl1.ApplicationFields.GetItem(fieldId);

if (field != null)
{
    // Found field with matching ID
}
```

## Remove Field and Keep Visible Text

```csharp
if (field != null)
{
    bool removed = textControl1.ApplicationFields.Remove(field, true);
}
```

## Remove Field and Delete Visible Text

```csharp
if (field != null)
{
    bool removed = textControl1.ApplicationFields.Remove(field, false);
}
```

## Notes

- `GetItem(id)` returns `null` when no field exists for that ID.
- `keepText = true` removes field markup but keeps rendered text.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfieldcollection.item.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfieldcollection.getitem.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfieldcollection.remove.method.htm
