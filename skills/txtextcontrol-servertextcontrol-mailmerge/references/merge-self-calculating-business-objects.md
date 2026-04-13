# Merge Self-Calculating Business Objects

## Goal

Merge objects with computed properties (such as totals) into a template,
including merge blocks and list scenarios.

## Source

- https://www.textcontrol.com/blog/2024/12/27/merging-self-calculating-business-objects-with-tx-text-control-mailmerge-in-csharp/

## Business Objects

```csharp
public class Invoice
{
    public string Customer { get; set; }
    public List<LineItem> LineItems { get; set; }
    public decimal Total => LineItems.Sum(x => x.Total);
}

public class LineItem
{
    public string Name { get; set; }
    public int Quantity { get; set; }
    public decimal Price { get; set; }
    public decimal Total => Quantity * Price;
}
```

## Merge a Single Object

```csharp
using TXTextControl;
using TXTextControl.DocumentServer;

Invoice invoice = new Invoice()
{
    Customer = "John Doe",
    LineItems = new List<LineItem>()
    {
        new LineItem() { Name = "Item 1", Quantity = 2, Price = 10 },
        new LineItem() { Name = "Item 2", Quantity = 3, Price = 20 },
        new LineItem() { Name = "Item 3", Quantity = 1, Price = 30 }
    }
};

using (ServerTextControl tx = new ServerTextControl())
{
    tx.Create();
    tx.Load("template.tx", StreamType.InternalUnicodeFormat);

    MailMerge mailMerge = new MailMerge()
    {
        TextComponent = tx
    };

    mailMerge.MergeObject(invoice);
}
```

## Merge a List of Objects

```csharp
using TXTextControl;
using TXTextControl.DocumentServer;

List<Invoice> invoices = new List<Invoice>()
{
    new Invoice()
    {
        Customer = "ACME Inc.",
        LineItems = new List<LineItem>()
        {
            new LineItem() { Name = "Product 1", Quantity = 2, Price = 100 },
            new LineItem() { Name = "Product 2", Quantity = 3, Price = 200 }
        }
    },
    new Invoice()
    {
        Customer = "Sample, LLC",
        LineItems = new List<LineItem>()
        {
            new LineItem() { Name = "Product 3", Quantity = 1, Price = 300 },
            new LineItem() { Name = "Product 4", Quantity = 4, Price = 400 }
        }
    },
    new Invoice()
    {
        Customer = "Test GmbH",
        LineItems = new List<LineItem>()
        {
            new LineItem() { Name = "Product 5", Quantity = 2, Price = 500 },
            new LineItem() { Name = "Product 6", Quantity = 3, Price = 600 }
        }
    }
};

using (ServerTextControl tx = new ServerTextControl())
{
    tx.Create();
    tx.Load("template.tx", StreamType.InternalUnicodeFormat);

    MailMerge mailMerge = new MailMerge()
    {
        TextComponent = tx
    };

    mailMerge.MergeObjects(invoices);
}
```

## Notes

- Merge blocks in the template repeat line items from nested object collections.
- Computed properties such as `Total` are evaluated by the object model and merged as values.
