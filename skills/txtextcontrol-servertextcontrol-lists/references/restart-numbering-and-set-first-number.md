# Restart Numbering and Set First Number

## Goal

Start a new numbered list sequence and control the first visible number.

## Source

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listformat.restartnumbering.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listformat.firstnumber.property.htm

## Restart Numbering at Selection

```csharp
TXTextControl.ListFormat lf = textControl1.Selection.ListFormat;
lf.Type = TXTextControl.ListType.Numbered;
lf.RestartNumbering = true;
lf.FirstNumber = 1;

textControl1.Selection.ListFormat = lf;
```

## Continue with a Custom Start Number

```csharp
TXTextControl.ListFormat lf = new TXTextControl.ListFormat();
lf.Type = TXTextControl.ListType.Numbered;
lf.RestartNumbering = true;
lf.FirstNumber = 10;
lf.NumberFormat = TXTextControl.NumberFormat.ArabicNumbers;

textControl1.Selection.ListFormat = lf;
```

## ServerTextControl-Wide Current List Settings

```csharp
using (TXTextControl.ServerTextControl tx = new TXTextControl.ServerTextControl())
{
    tx.Create();

    TXTextControl.ListFormat lf = tx.ListFormat;
    lf.Type = TXTextControl.ListType.Numbered;
    lf.RestartNumbering = true;
    lf.FirstNumber = 1;

    tx.ListFormat = lf;
}
```

## Notes

- `RestartNumbering = true` begins a new numbered sequence.
- `FirstNumber` defines the first label in that sequence.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.servertextcontrol.listformat.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listformat.firstnumber.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listformat.restartnumbering.property.htm
