# Create a Numbered List with ListFormat

## Goal

Apply numbered list formatting to selected text and customize numbering style.

## Source

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listformat.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.selection.listformat.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.numberformat.enumeration.htm

## Apply Numbered List at Current Selection

```csharp
TXTextControl.ListFormat lf = new TXTextControl.ListFormat();
lf.Type = TXTextControl.ListType.Numbered;
lf.FirstNumber = 5;

textControl1.Selection.ListFormat = lf;
```

## Set Number Format (Letters, Roman, etc.)

```csharp
TXTextControl.ListFormat lf = new TXTextControl.ListFormat();

lf.Type = TXTextControl.ListType.Numbered;
lf.NumberFormat = TXTextControl.NumberFormat.Letters;

textControl1.Selection.ListFormat = lf;
```

## Add Prefix/Suffix Around Number

```csharp
TXTextControl.ListFormat lf = new TXTextControl.ListFormat();
lf.Type = TXTextControl.ListType.Numbered;
lf.NumberFormat = TXTextControl.NumberFormat.ArabicNumbers;
lf.TextBeforeNumber = "(";
lf.TextAfterNumber = ") ";

textControl1.Selection.ListFormat = lf;
```

## Notes

- Use `Selection.ListFormat` to apply list changes to selected paragraphs.
- `ListType.Numbered` enables numbered list behavior.
- `NumberFormat` controls rendering style (`ArabicNumbers`, `Letters`, `RomanNumbers`, etc.).

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listformat.type.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listformat.firstnumber.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listformat.numberformat.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listformat.textbeforenumber.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listformat.textafternumber.property.htm
