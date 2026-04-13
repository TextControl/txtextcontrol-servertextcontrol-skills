# Create a Bulleted List with Custom Bullet Settings

## Goal

Apply bulleted lists to text and customize bullet symbol and appearance.

## Source

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listformat.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listformat.bulletcharacter.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listformat.bulletsize.property.htm

## Apply Bulleted List

```csharp
TXTextControl.ListFormat lf = new TXTextControl.ListFormat();
lf.Type = TXTextControl.ListType.Bulleted;

textControl1.Selection.ListFormat = lf;
```

## Customize Bullet Character and Font

```csharp
TXTextControl.ListFormat lf = new TXTextControl.ListFormat();
lf.Type = TXTextControl.ListType.Bulleted;
lf.BulletCharacter = '\u2022';
lf.FontName = "Symbol";
lf.BulletSize = 240; // twips

textControl1.Selection.ListFormat = lf;
```

## Remove List Formatting

```csharp
TXTextControl.ListFormat lf = new TXTextControl.ListFormat();
lf.Type = TXTextControl.ListType.None;

textControl1.Selection.ListFormat = lf;
```

## Notes

- `BulletSize = 0` uses the text font size.
- `ListType.None` removes bulleted/numbered formatting from the selected text.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listtype.enumeration.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listformat.bulletcharacter.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listformat.fontname.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listformat.bulletsize.property.htm
