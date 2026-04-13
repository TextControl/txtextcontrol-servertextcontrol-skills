# Use HeaderFooterType Variants

## Goal

Work with specific header/footer variants such as first-page and even-page
headers/footers using `HeaderFooterType`.

## Source

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.headerfootertype.enumeration.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.headerfootercollection.class.htm

## Supported HeaderFooterType Members

- `Header`
- `FirstPageHeader`
- `Footer`
- `FirstPageFooter`
- `EvenHeader`
- `EvenFooter`

## Add and Retrieve Specific Variants

```csharp
using TXTextControl;

using (ServerTextControl tx = new ServerTextControl())
{
    tx.Create();

    // First page header
    tx.Sections.GetItem().HeadersAndFooters.Add(HeaderFooterType.FirstPageHeader);
    HeaderFooter firstHeader =
        tx.Sections.GetItem().HeadersAndFooters.GetItem(HeaderFooterType.FirstPageHeader);
    firstHeader.Selection.Text = "First Page Header";

    // Even page footer
    tx.Sections.GetItem().HeadersAndFooters.Add(HeaderFooterType.EvenFooter);
    HeaderFooter evenFooter =
        tx.Sections.GetItem().HeadersAndFooters.GetItem(HeaderFooterType.EvenFooter);
    evenFooter.Selection.Text = "Even Page Footer";

    // Default odd/all-pages footer
    tx.Sections.GetItem().HeadersAndFooters.Add(HeaderFooterType.Footer);
    HeaderFooter footer =
        tx.Sections.GetItem().HeadersAndFooters.GetItem(HeaderFooterType.Footer);
    footer.Selection.Text = "Default Footer";

    tx.Save("results.docx", StreamType.WordprocessingML);
}
```

## Remove a Variant

```csharp
tx.Sections.GetItem().HeadersAndFooters.Remove(HeaderFooterType.EvenHeader);
```

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.headerfootertype.enumeration.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.headerfootercollection.add.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.headerfootercollection.getitem.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.headerfootercollection.remove.method.htm
