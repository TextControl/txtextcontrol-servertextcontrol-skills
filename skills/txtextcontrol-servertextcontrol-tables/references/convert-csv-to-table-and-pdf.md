# Convert CSV to a Table and Export as PDF

## Goal

Read a CSV file and insert its data as a formatted TX Text Control table
into a document using ServerTextControl, then export the result as a PDF.

## Source

- https://www.textcontrol.com/blog/2026/01/19/convert-csv-to-pdf-in-dotnet-csharp/

## Prerequisites

- .NET 8+ console or backend project
- TX Text Control package installed (`TXTextControl.TextControl.ASP.SDK`)
- A CSV file with column headers in the first row

## Sample CSV Input

```
Company,Contact,Email,Country,Amount,Status,DueDate
Acme Corp,Jane Doe,jane.doe@acme.com,USA,12500.75,Approved,2026-02-15
Contoso GmbH,Max Mustermann,max.mustermann@contoso.de,Germany,9800.0,Pending,2026-03-01
Northwind Traders,Emily Stone,emily.stone@northwind.com,UK,4500.5,Overdue,2026-01-10
```

## End-to-End: CSV to PDF

```csharp
using TXTextControl;

const string csvPath = "sample-data.csv";
const string pdfPath = "test.pdf";

using var tx = new ServerTextControl();
tx.Create();

var importer = new CsvToTextControlTableImporter();

var options = new CsvToTextControlTableImporter.Options
{
    FirstRowIsHeader = true,
    Separator = ','
};

importer.InsertTableFromCsvFile(tx, csvPath, options);

tx.Save(pdfPath, StreamType.AdobePDF);
```

## How the Table Importer Works

TX Text Control inserts tables at the current input position. The importer
follows a specific pattern to keep formatting consistent and avoid processing
each row individually:

### Step 1: Insert the Table

```csharp
tx.Tables.Add(initialRows, columnCount);

// Move selection back to get a reference to the inserted table
tx.Selection.Start -= 1;
var table = tx.Tables.GetItem();
```

### Step 2: Fill and Style the Header Row

```csharp
for (int c = 1; c <= columnCount; c++)
    table.Cells[1, c].Text = (c - 1) < header.Count ? header[c - 1] : string.Empty;

table.Rows[1].CellFormat = new TableCellFormat()
{
    BackColor = System.Drawing.Color.LightGray,
    BottomBorderWidth = 10
};

// Repeat header row on each PDF page
table.Rows[1].IsHeader = true;
```

### Step 3: Create a Template Data Row

Format only the template row — all subsequent rows inserted after it
inherit its formatting automatically:

```csharp
table.Rows[templateDataRow].CellFormat = new TableCellFormat()
{
    BottomBorderWidth = 10,
    TopBorderWidth = 10,
    RightBorderWidth = 10,
    LeftBorderWidth = 10
};
```

### Step 4: Insert Remaining Rows

Place the cursor explicitly in the template row, then add the remaining rows.
TX Text Control inserts from the current input position and inherits formatting:

```csharp
table.Cells[templateDataRow, 1].Select();
tx.Selection.Length = 0;

table.Rows.Add(TableAddPosition.After, dataRowCount - 1);
```

### Step 5: Fill Data Cells

```csharp
for (int r = 0; r < dataRowCount; r++)
{
    int targetRow = templateDataRow + r;
    var record = records[dataStartRowIndexInRecords + r];

    for (int c = 1; c <= columnCount; c++)
    {
        string value = (c - 1) < record.Count ? record[c - 1] : string.Empty;
        table.Cells[targetRow, c].Text = value;
    }
}
```

> **Key pattern:** Insert one template row, apply formatting to it, then
> add all remaining rows at once so they inherit the template formatting.
> This produces consistent, scalable output without per-row formatting loops.

## API Reference

- [`TableCollection.Add()`](https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.tablecollection.add.method.htm)
- [`TableRow.IsHeader`](https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.tablerow.isheader.property.htm)
- [`TableRowCollection.Add()`](https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.tablerowcollection.add.method.htm)
- [`TableCell.Text`](https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.tablecell.text.property.htm)
- [`TableCellFormat`](https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.tablecellformat.class.htm)
