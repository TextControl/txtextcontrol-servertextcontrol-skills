# Create a Simple MailMerge Application (JSON + Template)

## Goal

Generate a merged PDF from a DOCX template by using ServerTextControl and
MailMerge with structured data.

## Source

- https://www.textcontrol.com/blog/2025/02/07/mail-merge-ms-word-docx-documents-and-convert-to-pdf-in-net-c-sharp/

## Prerequisites

- .NET 8+ console or backend project
- TX Text Control package installed (for example `TXTextControl.TextControl.ASP.SDK`)
- A template document named `template.docx`

## Data Classes

```csharp
public class Invoice
{
    public string InvoiceNumber { get; set; }
    public DateTime InvoiceDate { get; set; }
    public DateTime DueDate { get; set; }
    public decimal AmountDue { get; set; }
    public Customer Customer { get; set; } = new Customer();
    public List<LineItem> LineItems { get; set; } = new List<LineItem>();
}

public class Customer
{
    public string CustomerName { get; set; }
    public string CustomerAddress { get; set; }
}

public class LineItem
{
    public string Item { get; set; }
    public string Description { get; set; }
    public int Quantity { get; set; }
    public decimal Price { get; set; }
    public decimal Total { get; set; }
}
```

## Merge and Export

```csharp
using TXTextControl.DocumentServer;
using TXTextControl;

Invoice invoice = CreateInvoice();
GenerateInvoiceDocument(invoice, "template.docx", "output.pdf");

static Invoice CreateInvoice()
{
    return new Invoice
    {
        InvoiceNumber = "12345",
        InvoiceDate = DateTime.Parse("2020-01-01"),
        DueDate = DateTime.Parse("2020-01-31"),
        AmountDue = 123.45m,
        Customer = new Customer
        {
            CustomerName = "John Doe",
            CustomerAddress = "123 Main St., Springfield, IL 62701"
        },
        LineItems = new List<LineItem>
        {
            new LineItem
            {
                Item = "1",
                Description = "Widget",
                Quantity = 2,
                Price = 45.00m,
                Total = 90.00m
            },
            new LineItem
            {
                Item = "2",
                Description = "Gadget",
                Quantity = 1,
                Price = 78.45m,
                Total = 78.45m
            }
        }
    };
}

static void GenerateInvoiceDocument(Invoice invoice, string templatePath, string outputPath)
{
    using (ServerTextControl tx = new ServerTextControl())
    {
        tx.Create();

        var loadSettings = new LoadSettings
        {
            ApplicationFieldFormat = ApplicationFieldFormat.MSWord,
            LoadSubTextParts = true
        };

        tx.Load(templatePath, StreamType.WordprocessingML, loadSettings);

        using (MailMerge mailMerge = new MailMerge { TextComponent = tx })
        {
            mailMerge.MergeObject(invoice);
        }

        tx.Save(outputPath, StreamType.AdobePDF);
    }
}
```

## Notes

- The template can be created in MS Word and contain merge fields and merge blocks.
- The article text mentions JSON as a common source; this sample code path merges a strongly typed object.
- To switch to JSON input, use `MailMerge.MergeJsonData(...)` in the same flow.
