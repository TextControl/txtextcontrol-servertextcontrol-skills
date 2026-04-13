# Convert Plain Text to a Bulleted List

## Goal

Convert selected plain text lines with bullet-like markers (`-`, `*`, `+`, etc.)
into proper bulleted list formatting.

## Source

- https://www.textcontrol.com/blog/2025/01/21/convert-plain-text-to-bulleted-lists-in-csharp-with-dotnet/

## Conversion Method

```csharp
void ApplyBulletedListFormatting(ServerTextControl textControl, int baseLeftMargin)
{
    // Define the set of valid bullet characters
    var bulletChars = new HashSet<char> { '\u2022', 'o', 'O', '0', '-', '\u2013', '\u2014', '*', '+' };

    TXTextControl.Selection selection = textControl.Selection;

    int offset = 0;

    // Iterate through all paragraphs in the TextControl
    foreach (Paragraph paragraph in textControl1.Paragraphs)
    {
        // Check if the paragraph is within the selection
        if (paragraph.Start < selection.Start - offset || paragraph.Start > selection.Start + selection.Length - offset)
            continue;

        string text = paragraph.Text;
        int textLength = text.Length;

        if (textLength > 1)
        {
            int tabCount = 0;

            // Count the number of leading tab characters
            while (tabCount < textLength && text[tabCount] == '\t')
            {
                tabCount++;
            }

            // Check if there's a bullet character followed by a space
            if (tabCount < textLength - 1 &&
                bulletChars.Contains(text[tabCount]) &&
                text[tabCount + 1] == ' ')
            {

                textControl1.Selection.Length = textControl1.Selection.Length - 1;

                // Set list type to bulleted
                paragraph.ListFormat.Type = ListType.Bulleted;

                // Remove the leading tabs and bullet character
                textControl1.Select(paragraph.Start - 1, tabCount + 2);
                textControl1.Selection.Text = string.Empty;

                // Adjust the selection offset
                offset += tabCount + 2;

                // Configure list level and indentation
                paragraph.ListFormat.Level = tabCount + 1;
                paragraph.ListFormat.LeftIndent = tabCount > 0 ? baseLeftMargin * tabCount : 0;
            }
        }
    }
}
```

## Example Input

```text
- First item
- Second item
    - Sub-item 1
    - Sub-item 2
```

## Notes

- The routine preserves nested list depth by mapping leading tabs to `ListFormat.Level`.
- It normalizes plain text markers into real list formatting so users can continue editing with list tools.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.paragraph.listformat.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listformat.level.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listformat.leftindent.property.htm
