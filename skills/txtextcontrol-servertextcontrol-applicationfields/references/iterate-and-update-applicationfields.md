# Iterate and Update ApplicationFields

## Goal

Loop through all ApplicationFields and update specific merge fields based on
`TypeName` and `Parameters`.

## Source

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfieldcollection.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfield.parameters.property.htm

## Update Address MERGEFIELD Text

```csharp
foreach (TXTextControl.ApplicationField myApplicationField in textControl1.ApplicationFields)
{
    if (myApplicationField.TypeName == "MERGEFIELD" &&
        myApplicationField.Parameters[0] == "Address")
    {
        myApplicationField.Text = "Bakerstreet, London";
    }
}
```

## Rename Merge Field Paths Programmatically

```csharp
foreach (ApplicationField applicationField in textControl1.ApplicationFields)
{
    if (applicationField.TypeName == "MERGEFIELD" &&
        applicationField.Name.Contains("Sales_SalesOrderDetail"))
    {
        TXTextControl.DocumentServer.Fields.MergeField mergeField =
            new TXTextControl.DocumentServer.Fields.MergeField(applicationField);

        mergeField.Name = mergeField.Name.Replace(
            "Sales_SalesOrderDetail",
            "New_Sales_SalesOrderDetail");
    }
}
```

## Notes

- If you change `TypeName`, update `Parameters` accordingly.
- Refactoring field paths is useful after data model or JSON schema changes.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfield.typename.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfield.parameters.property.htm
