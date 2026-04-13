# Remove Empty Columns After Mail Merge

## Goal

After a mail merge that produces a table with repeating rows, detect and
remove any columns that contain no data across all data rows.

This is useful when JSON data does not include values for every column
defined in the template — leaving entire columns empty after the merge.

## Source

- https://www.textcontrol.com/blog/2023/06/08/table-extension-remove-empty-columns-after-mail-merge/

## Prerequisites

- .NET 8+ console or backend project
- TX Text Control package installed (`TXTextControl.TextControl.ASP.SDK`)
- A template with a merge block table (e.g., a table-row merge block)

## Sample JSON — Missing Column

When JSON data omits a field (e.g., `discount`) for all records, the merged
table will produce an empty column:

```json
[
  {
    "articles": [
      { "id": 1, "name": "Product A", "description": "Desc A", "price": 200, "qty": 5 },
      { "id": 2, "name": "Product B", "description": "Desc B", "price": 244, "qty": 50 },
      { "id": 3, "name": "Product C", "description": "Desc C", "price": 677, "qty": 2 }
    ]
  }
]
```

## Extension Method: RemoveEmptyColumns

```csharp
public static class TableExtender
{
    public static void RemoveEmptyColumns(this Table table)
    {
        List<TableColumn> columns = new List<TableColumn>();

        foreach (TableColumn col in table.Columns)
        {
            bool foundText = false;

            foreach (TableRow row in table.Rows)
            {
                // Skip the header row
                if (row.IsHeader == true) continue;

                if (table.Cells[row.Row, col.Column].Text != "")
                {
                    foundText = true;
                    break;
                }
            }

            if (!foundText) { columns.Add(col); }
        }

        foreach (TableColumn column in columns)
        {
            table.Cells[1, column.Column].Select();
            table.Columns.Remove();
        }
    }
}
```

## Apply After Mail Merge

```csharp
string jsonData = System.IO.File.ReadAllText("data.json");
textControl1.Load("template.tx", TXTextControl.StreamType.InternalUnicodeFormat);

using (MailMerge mailMerge = new MailMerge())
{
    mailMerge.TextComponent = textControl1;
    mailMerge.MergeJsonData(jsonData);
}

// Remove empty columns from all tables in the document
foreach (TXTextControl.Table table in textControl1.Tables)
{
    table.RemoveEmptyColumns();
}
```

> **Note:** The extension method loops all non-header rows for each column.
> If no cell in that column has any text, the entire column is added to the
> removal list. Removal is done in a second pass to avoid index shifts during
> iteration.

## API Reference

- [`TableColumn`](https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.tablecolumn.class.htm)
- [`TableRow.IsHeader`](https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.tablerow.isheader.property.htm)
- [`TableCell.Text`](https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.tablecell.text.property.htm)
- [`TableColumnCollection.Remove()`](https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.tablecolumncollection.remove.method.htm)
- [`MailMerge.MergeJsonData()`](https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.documentserver.mailmerge.mergejsondata.method.htm)
