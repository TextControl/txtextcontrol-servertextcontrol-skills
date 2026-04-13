# Restart Page Numbering Per Section

## Goal

Start page numbering from 1 for each new section and keep section footer
numbering independent from previous sections.

## Source

- https://www.textcontrol.com/blog/2013/11/08/restart-the-page-numbering-fields-per-section/

## Restart Numbering and Add Footer Fields

```csharp
textControl1.Sections.Add(SectionBreakKind.BeginAtNewPage);

Section sec = textControl1.Sections.GetItem();

sec.Format.RestartPageNumbering = true;
sec.HeadersAndFooters.Add(HeaderFooterType.Footer);

HeaderFooter footer =
    sec.HeadersAndFooters.GetItem(HeaderFooterType.Footer);
footer.ConnectedToPrevious = false;

footer.Selection.Text = "Page ";

PageNumberField currentPageNumber =
    new PageNumberField(1, NumberFormat.ArabicNumbers);
footer.PageNumberFields.Add(currentPageNumber);

footer.Selection.Text = " of ";

PageNumberField pageCount = new PageNumberField(1, NumberFormat.ArabicNumbers);
pageCount.ShowNumberOfPages = true;

footer.PageNumberFields.Add(pageCount);
```

## Notes

- `SectionFormat.RestartPageNumbering = true` enables per-section numbering.
- `footer.ConnectedToPrevious = false` avoids inheriting footer content.
- This pattern is useful when concatenating multiple logical documents.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.sectionformat.restartpagenumbering.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.headerfooter.connectedtoprevious.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.headerfootercollection.add.method.htm
