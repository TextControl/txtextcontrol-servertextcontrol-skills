# Create a Table from Scratch

## Goal

Create a table programmatically using ServerTextControl, set a header row,
format all cells with borders, and export the result as a PDF file.

## Source

- https://www.textcontrol.com/blog/2024/09/30/creating-advanced-tables-in-pdf-and-docx-documents-with-csharp/

## Prerequisites

- .NET 8+ console or backend project
- TX Text Control package installed (`TXTextControl.TextControl.ASP.SDK`)

## Create a Table with a Header Row

```csharp
using TXTextControl;

using (ServerTextControl tx = new ServerTextControl())
{
    tx.Create();

    // Add a table: 5 rows, 5 columns, ID = 10
    tx.Tables.Add(5, 5, 10);

    Table table = tx.Tables.GetItem(10);

    // Set and format the header row
    table.Rows[1].IsHeader = true;
    table.Rows[1].CellFormat = new TableCellFormat()
    {
        BackColor = System.Drawing.Color.LightGray,
        BottomBorderWidth = 10,
    };

    // Set cell text and format data rows
    foreach (TableCell cell in table.Cells)
    {
        if (table.Rows[cell.Row].IsHeader) // header row
        {
            cell.Text = "Header Column " + cell.Column.ToString();
        }
        else // data rows
        {
            cell.Text = "Row " + cell.Row.ToString() + ", Column " + cell.Column.ToString();

            cell.CellFormat = new TableCellFormat()
            {
                BottomBorderWidth = 1,
                TopBorderWidth = 1,
                LeftBorderWidth = 1,
                RightBorderWidth = 1
            };
        }
    }

    // Export to PDF
    tx.Save("results.pdf", StreamType.AdobePDF);
}
```

> **Note:** Setting `IsHeader = true` makes the header row automatically repeat
> on each page when the table spans multiple pages.

## Split a Table

To split a table at the current input position:

```csharp
using TXTextControl;

using (ServerTextControl tx = new ServerTextControl())
{
    tx.Create();

    int myTableId = 10;
    tx.Tables.Add(10, 3, myTableId);

    Table myTable = tx.Tables.GetItem(myTableId);
    tx.InputPosition = new InputPosition(myTable.Cells.GetItem(3, 1).Start);

    if (myTable.CanSplit)
        myTable.Split(TableAddPosition.After);

    // Update table IDs after split
    foreach (Table myCurrentTable in tx.Tables)
        myCurrentTable.ID = myTableId++;
}
```

## Control Page Breaks in Rows

Prevent a row from breaking across pages with `AllowPageBreak = false`:

```csharp
using TXTextControl;

using (ServerTextControl tx = new ServerTextControl())
{
    tx.Create();

    tx.Tables.Add(5, 5, 10);
    Table table = tx.Tables.GetItem(10);

    foreach (TableCell cell in table.Cells)
    {
        cell.Text = "Row " + cell.Row.ToString() + ", Column " + cell.Column.ToString();

        cell.CellFormat = new TableCellFormat()
        {
            BottomBorderWidth = 1,
            TopBorderWidth = 1,
            LeftBorderWidth = 1,
            RightBorderWidth = 1
        };
    }

    // Keep the last row together on a single page
    table.Rows[5].AllowPageBreak = false;
    table.Cells[5, 1].Text = "This row will not be split across a page break.";

    tx.Save("results.pdf", StreamType.AdobePDF);
}
```

## API Reference

- [`TableCollection.Add()`](https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.tablecollection.add.method.htm)
- [`Table`](https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.table.class.htm)
- [`TableCell`](https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.tablecell.class.htm)
- [`TableRow`](https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.tablerow.class.htm)
- [`TableCollection`](https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.tablecollection.class.htm)
