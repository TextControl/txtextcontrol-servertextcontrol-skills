# Insert a Table from JSON Data

## Goal

Populate a table inside a document from a JSON data source using
`DataSourceManager`, `MergeBlockInfo`, and the `MailMerge` class.
This approach dynamically generates a table template and merges rows
from structured JSON.

## Source

- https://www.textcontrol.com/blog/2024/09/30/creating-advanced-tables-in-pdf-and-docx-documents-with-csharp/

## Prerequisites

- .NET 8+ console or backend project
- TX Text Control packages installed:
  - `TXTextControl.TextControl.ASP.SDK`

## Sample JSON Data

```json
[
  {
    "invoice": "12345",
    "date": "2019-01-01",
    "customer": "John Doe",
    "items": [
      { "product": "apple",  "price": 1.00, "quantity": 10 },
      { "product": "banana", "price": 0.50, "quantity": 20 },
      { "product": "cherry", "price": 0.25, "quantity": 30 }
    ]
  }
]
```

## Insert and Merge a Table from JSON

```csharp
using TXTextControl;
using TXTextControl.DocumentServer;
using TXTextControl.DocumentServer.DataSources;

using (ServerTextControl tx = new ServerTextControl())
{
    tx.Create();

    string jsonData = File.ReadAllText("tabledata.json");

    // Load JSON into the DataSourceManager to introspect its structure
    DataSourceManager dataSourceManager = new DataSourceManager();
    dataSourceManager.LoadJson(jsonData);

    // Define which block and which columns to include
    MergeBlockInfo mergeBlockInfo = new MergeBlockInfo("items");
    mergeBlockInfo.ColumnNames.Add("product");
    mergeBlockInfo.ColumnNames.Add("price");
    mergeBlockInfo.ColumnNames.Add("quantity");

    // Use TableRow template type: each data record becomes a table row
    MergeBlockSettings mergeBlockSettings = new MergeBlockSettings(
        BlockTemplateType.TableRow, true);

    // Insert the merge block template (creates the table structure)
    dataSourceManager.InsertMergeBlock(tx, mergeBlockInfo, mergeBlockSettings);

    // Merge the actual data into the generated table template
    MailMerge mailMerge = new MailMerge()
    {
        TextComponent = tx
    };

    mailMerge.MergeJsonData(jsonData);

    // Export to PDF
    tx.Save("results.pdf", StreamType.AdobePDF);
}
```

> **Note:** `InsertMergeBlock` builds the table template with merge fields.
> `MergeJsonData` then fills the template rows with actual data.
> The `BlockTemplateType.TableRow` setting tells the engine that each
> repeating data record maps to a table row.

## Create a Nested Table

Tables can be inserted inside other table cells. TX Text Control supports
unlimited nesting levels.

```csharp
using TXTextControl;

using (ServerTextControl tx = new ServerTextControl())
{
    tx.Create();

    TableCellFormat tableCellFormat = new TableCellFormat()
    {
        BottomBorderWidth = 1,
        TopBorderWidth = 1,
        LeftBorderWidth = 1,
        RightBorderWidth = 1
    };

    // Add the outer (parent) table
    tx.Tables.Add(5, 5, 10);
    Table table = tx.Tables.GetItem(10);

    // Select the first cell and place the cursor inside it
    table.Cells[1, 1].Select();
    tx.Selection.Length = 0;

    // Insert a nested table inside cell (1,1)
    tx.Tables.Add(2, 2);

    // Fill and format the nested table
    foreach (TableCell cell in table.NestedTables[1].Cells)
    {
        cell.Text = "nested";
        cell.CellFormat = tableCellFormat;
    }

    // Fill and format the outer table
    foreach (TableCell cell in table.Cells)
    {
        if (cell.Text == "")
            cell.Text = "main";

        cell.CellFormat = tableCellFormat;
    }

    tx.Save("results.pdf", StreamType.AdobePDF);
}
```

> **Note:** Access nested tables via `table.NestedTables[index]`. Nesting is
> achieved by placing the cursor inside the target cell before calling
> `tx.Tables.Add()`.

## API Reference

- [`DataSourceManager`](https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.documentserver.datasources.datasourcemanager.class.htm)
- [`MergeBlockInfo`](https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.documentserver.datasources.mergeblockinfo.class.htm)
- [`MergeBlockSettings`](https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.documentserver.datasources.mergeblocksettings.class.htm)
- [`MailMerge.MergeJsonData()`](https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.documentserver.mailmerge.mergejsondata.method.htm)
- [`Table.NestedTables`](https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.table.nestedtables.property.htm)
