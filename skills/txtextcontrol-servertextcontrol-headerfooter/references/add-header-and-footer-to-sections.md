# Add Headers and Footers to Sections

## Goal

Create and edit headers and footers in a section, and understand section-wide
vs document-wide header/footer behavior.

## Source

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.headerfooter.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.headerfootercollection.class.htm

## Add a Header to a Specific Section

```csharp
textControl1.Sections[1].HeadersAndFooters.Add(TXTextControl.HeaderFooterType.Header);

TXTextControl.HeaderFooter header =
    textControl1.Sections[1].HeadersAndFooters.GetItem(TXTextControl.HeaderFooterType.Header);

header.Selection.Text = "TX Text Control";
header.Selection.Start = 3;
header.Selection.Length = 4;
header.Selection.Bold = true;
```

## Add Header/Footer on Current Section (ServerTextControl)

```csharp
using TXTextControl;

using (ServerTextControl tx = new ServerTextControl())
{
    tx.Create();

    tx.Sections.GetItem().HeadersAndFooters.Add(HeaderFooterType.Header);
    tx.Sections.GetItem().HeadersAndFooters.Add(HeaderFooterType.Footer);

    HeaderFooter header = tx.Sections.GetItem().HeadersAndFooters.GetItem(HeaderFooterType.Header);
    HeaderFooter footer = tx.Sections.GetItem().HeadersAndFooters.GetItem(HeaderFooterType.Footer);

    header.Selection.Text = "Header Text";
    footer.Selection.Text = "Footer Text";

    tx.Save("results.pdf", StreamType.AdobePDF);
}
```

## Section-Specific vs Common Headers/Footers

- `TextControl.HeadersAndFooters` gives headers/footers common to all sections.
- `Section.HeadersAndFooters` gives headers/footers for a specific section.

If a section header/footer should not inherit from the previous section,
set `ConnectedToPrevious = false` on the `HeaderFooter`.

```csharp
HeaderFooter sectionFooter = sec.HeadersAndFooters.GetItem(HeaderFooterType.Footer);
sectionFooter.ConnectedToPrevious = false;
```

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.headerfootercollection.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.headerfooter.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.section.headersandfooters.property.htm
