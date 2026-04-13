# Format Table Cells and Rows

## Goal

Apply visual formatting to table cells and rows using `TableCellFormat`,
including background colors, borders, row height, and text alignment.

## Source

- https://www.textcontrol.com/blog/2024/06/19/a-step-by-step-guide-to-formatting-table-cells-in-tx-text-control-programmatically-using-c-sharp/
- https://www.textcontrol.com/blog/2024/09/30/creating-advanced-tables-in-pdf-and-docx-documents-with-csharp/

## Prerequisites

- .NET 8+ console or backend project
- TX Text Control package installed (`TXTextControl.TextControl.ASP.SDK`)

## Add a Table and Set Cell Text

```csharp
// Set table identifier
int tableID = 10;

// Add a new table with number of rows and columns
tx.Tables.Add(2, 5, tableID);

// Retrieve the newly added table using the tableID
TXTextControl.Table table = tx.Tables.GetItem(tableID);
```

## Format Header Cells with Text and Alignment

```csharp
// Initialize table headers
string[] headers = { "Date", "Description", "Credit", "Debit", "Balance" };

for (int i = 1; i <= headers.Length; i++)
{
    // Assign header text to each cell in the first row
    table.Cells.GetItem(1, i).Text = headers[i - 1];

    // Retrieve and select the cell for formatting
    TableCell cell = table.Cells.GetItem(1, i);
    cell.Select();

    // Center align text and set bold
    tx.Selection.ParagraphFormat.Alignment = TXTextControl.HorizontalAlignment.Center;
    tx.Selection.Bold = true;

    // Change the text color
    tx.Selection.ForeColor = Color.Navy;
}
```

## Apply Background Color and Borders via TableCellFormat

```csharp
// Create a new TableCellFormat object
TXTextControl.TableCellFormat myCellFormat = new TXTextControl.TableCellFormat();

// Set the background color
myCellFormat.BackColor = Color.LightGray;

// Specify a bottom border width
myCellFormat.BottomBorderWidth = 50;

// Apply the formatting to all header cells
for (int i = 1; i <= 5; i++)
{
    table.Cells.GetItem(1, i).CellFormat = myCellFormat;
}
```

## Apply Consistent Borders to All Data Cells

```csharp
TableCellFormat dataCellFormat = new TableCellFormat()
{
    BottomBorderWidth = 1,
    TopBorderWidth = 1,
    LeftBorderWidth = 1,
    RightBorderWidth = 1
};

foreach (TableCell cell in table.Cells)
{
    if (!table.Rows[cell.Row].IsHeader)
        cell.CellFormat = dataCellFormat;
}
```

## Format an Entire Row

`CellFormat` can be set directly on a `TableRow` to apply uniform formatting
to all cells in that row at once:

```csharp
TXTextControl.TableCellFormat rowFormat = new TXTextControl.TableCellFormat();
rowFormat.BackColor = System.Drawing.Color.LightGreen;
rowFormat.BottomBorderWidth = 40;

TXTextControl.TableRow myRow = table.Rows.GetItem(1);
myRow.MinimumHeight = 1440; // 1 inch in twips
myRow.AllowPageBreak = false;
myRow.CellFormat = rowFormat;
```

## TableCellFormat Properties Reference

| Property | Description |
|---|---|
| `BackColor` | Background fill color of the cell |
| `BottomBorderWidth` | Width of the bottom border in twips |
| `TopBorderWidth` | Width of the top border in twips |
| `LeftBorderWidth` | Width of the left border in twips |
| `RightBorderWidth` | Width of the right border in twips |
| `BottomBorderColor` | Color of the bottom border |
| `TopBorderColor` | Color of the top border |
| `LeftBorderColor` | Color of the left border |
| `RightBorderColor` | Color of the right border |
| `VerticalAlignment` | Vertical alignment of cell content |
| `NumberFormat` | Number format string for cell values |
| `BottomTextDistance` | Space between cell bottom and text |
| `TopTextDistance` | Space between cell top and text |
| `LeftTextDistance` | Space between cell left edge and text |
| `RightTextDistance` | Space between cell right edge and text |

## API Reference

- [`TableCellFormat`](https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.tablecellformat.class.htm)
- [`TableCell`](https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.tablecell.class.htm)
- [`TableRow`](https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.tablerow.class.htm)
