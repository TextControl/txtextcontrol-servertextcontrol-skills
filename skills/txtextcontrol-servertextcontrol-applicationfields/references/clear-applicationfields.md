# Clear ApplicationFields

## Goal

Remove all ApplicationFields from a document, optionally preserving visible text.

## Source

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfieldcollection.clear.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.servertextcontrol.applicationfields.property.htm

## Remove All Fields and Keep Text

```csharp
textControl1.ApplicationFields.Clear(true);
```

## Remove All Fields and Delete Text

```csharp
textControl1.ApplicationFields.Clear(false);
```

## ServerTextControl Example

```csharp
using (TXTextControl.ServerTextControl tx = new TXTextControl.ServerTextControl())
{
    tx.Create();

    TXTextControl.LoadSettings ls = new TXTextControl.LoadSettings();
    ls.ApplicationFieldFormat = TXTextControl.ApplicationFieldFormat.MSWord;
    ls.ApplicationFieldTypeNames = new string[] { "MERGEFIELD", "PRINTDATE" };

    tx.Load("template.docx", TXTextControl.StreamType.WordprocessingML, ls);

    // Remove all imported or created ApplicationFields, keep text output
    tx.ApplicationFields.Clear(true);
}
```

## Notes

- Before loading a document, configure `LoadSettings.ApplicationFieldFormat`
  to import Word fields into `ApplicationFields`.
- `Clear(true)` is useful for flattening templates after replacement.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.loadsettings.applicationfieldformat.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.loadsettings.applicationfieldtypenames.property.htm
