# Add Page Numbers in Header/Footer

## Goal

Insert page number fields in headers/footers, including current page and total
page count, for DOCX/PDF output.

## Source

- https://www.textcontrol.com/blog/2024/10/25/create-word-document-with-net-c-sharp/
- https://www.textcontrol.com/blog/2024/10/17/create-pdf-file-with-net-c-sharp/
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.headerfooter.class.htm

## Add "Page X of Y" to Header

```csharp
using TXTextControl;

using (ServerTextControl tx = new ServerTextControl())
{
    tx.Create();

    tx.Sections.GetItem().HeadersAndFooters.Add(HeaderFooterType.Header);

    HeaderFooter headerFooter =
        tx.Sections.GetItem().HeadersAndFooters.GetItem(HeaderFooterType.Header);

    headerFooter.Selection.Text = "Page ";
    headerFooter.PageNumberFields.Add(new PageNumberField());
    headerFooter.Selection.Text = " of ";
    headerFooter.PageNumberFields.Add(new PageNumberField() { ShowNumberOfPages = true });

    tx.Selection.Text = "\f"; // add page break to demonstrate numbering

    tx.Save("results.pdf", StreamType.AdobePDF);
}
```

## Add "Page X of Y" to Footer

```csharp
footer.Selection.Text = "Page ";

PageNumberField currentPageNumber =
    new PageNumberField(1, NumberFormat.ArabicNumbers);
footer.PageNumberFields.Add(currentPageNumber);

footer.Selection.Text = " of ";

PageNumberField pageCount = new PageNumberField(1, NumberFormat.ArabicNumbers);
pageCount.ShowNumberOfPages = true;
footer.PageNumberFields.Add(pageCount);
```

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.pagenumberfield.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.pagenumberfieldcollection.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.headerfooter.pagenumberfields.property.htm
