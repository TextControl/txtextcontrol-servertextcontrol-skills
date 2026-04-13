# Insert ApplicationFields and MERGEFIELDs

## Goal

Create and insert a Microsoft Word-style `MERGEFIELD` as an
`ApplicationField` at the current input position.

## Source

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfield.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfieldcollection.add.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfieldformat.enumeration.htm

## Insert a New MERGEFIELD

```csharp
TXTextControl.ApplicationField myAppField = new TXTextControl.ApplicationField(
    TXTextControl.ApplicationFieldFormat.MSWord,
    "MERGEFIELD",
    "New ApplicationField",
    new string[] { "FieldName" });

textControl1.ApplicationFields.Add(myAppField);
```

## Notes

- The format `ApplicationFieldFormat.MSWord` enables Word-compatible fields.
- For a `MERGEFIELD`, the first `Parameters` item is commonly the field name.
- `Add` returns `true` when insertion succeeds.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfield.constructor.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfield.parameters.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfield.typename.property.htm
