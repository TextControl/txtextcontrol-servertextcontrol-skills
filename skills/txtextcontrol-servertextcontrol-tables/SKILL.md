---
name: txtextcontrol-servertextcontrol-tables
description: |
  Use this skill when a user asks how to work with tables in TX Text Control
  .NET Server using ServerTextControl.

  Trigger it for requests involving creating tables programmatically, formatting
  table cells and rows, inserting tables from JSON data, converting CSV to PDF
  tables, removing empty columns after mail merge, nested tables, and
  controlling table pagination and page breaks.
metadata:
  author: Text Control
  version: "34.3.0"
---

# TX Text Control ServerTextControl Tables

## Overview

This skill provides guidance and code snippets for working with tables
in TX Text Control .NET Server using ServerTextControl.

It covers the full table lifecycle: creating tables from scratch,
formatting cells and rows, populating tables from data sources, and
post-processing tables in generated documents.

## Key Capabilities

- **Create Tables:** Add tables programmatically with `Tables.Add()` and set rows, columns, and IDs.
- **Format Cells and Rows:** Use `TableCellFormat` to set borders, background colors, and text alignment.
- **Header Rows:** Mark rows with `IsHeader = true` for automatic repetition on multi-page tables.
- **Nested Tables:** Insert tables inside table cells and access them via `NestedTables`.
- **JSON Data Tables:** Use `DataSourceManager` and `MergeBlockInfo` to build dynamic table templates.
- **CSV to PDF:** Convert CSV files to formatted tables and export as PDF.
- **Remove Empty Columns:** Post-process mail merge results by removing columns with no data.
- **Pagination Control:** Use `AllowPageBreak = false` on rows to prevent unwanted page breaks.

## Quick Start Examples

### Example 1: Create a table from scratch
**User:** "How do I create a table with a header row and borders in ServerTextControl?"

**Result:** Use `references/create-a-table-from-scratch.md`

### Example 2: Format table cells
**User:** "How do I format table cell backgrounds, borders, and text alignment?"

**Result:** Use `references/format-table-cells-and-rows.md`

### Example 3: Insert table from JSON
**User:** "How do I populate a table from JSON data using MailMerge?"

**Result:** Use `references/insert-table-from-json-data.md`

### Example 4: Convert CSV to PDF
**User:** "How do I convert a CSV file into a table and export it as PDF?"

**Result:** Use `references/convert-csv-to-table-and-pdf.md`

### Example 5: Remove empty columns
**User:** "After mail merge, how do I remove columns that are entirely empty?"

**Result:** Use `references/remove-empty-columns-after-mail-merge.md`

## Generate ServerTextControl Table Guidance

**Trigger keywords:** "servertextcontrol", "table", "tablecell", "tablerow", "tablecolumn",
"tablecellformat", "isheader", "nestedtable", "csv", "json", "mergeblock",
"removeemptycolumns", "allowpagebreak", "borders", "backcolor".

**Workflow:**

1. Identify whether the request is about creating, formatting, populating from data, CSV import, or post-processing tables.
2. Read the matching reference file in `references/`.
3. Use only the code and instructions from the selected file.
4. Do not invent additional APIs, classes, or method signatures.
5. Return complete guidance and code in the format requested by the user.

## Code References

| File | Task |
|------|------|
| `create-a-table-from-scratch.md` | Create a table programmatically with header row, cell text, borders, and PDF export |
| `format-table-cells-and-rows.md` | Apply TableCellFormat: background color, borders, row height, text alignment |
| `insert-table-from-json-data.md` | Populate a table from JSON using DataSourceManager, MergeBlockInfo, and MailMerge |
| `convert-csv-to-table-and-pdf.md` | Convert a CSV file to a formatted TX Text Control table and export as PDF |
| `remove-empty-columns-after-mail-merge.md` | Detect and remove empty columns from a table after mail merge |

## Source Articles

- https://www.textcontrol.com/blog/2024/09/30/creating-advanced-tables-in-pdf-and-docx-documents-with-csharp/
- https://www.textcontrol.com/blog/2024/06/19/a-step-by-step-guide-to-formatting-table-cells-in-tx-text-control-programmatically-using-c-sharp/
- https://www.textcontrol.com/blog/2026/01/19/convert-csv-to-pdf-in-dotnet-csharp/
- https://www.textcontrol.com/blog/2023/06/08/table-extension-remove-empty-columns-after-mail-merge/

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.tablecollection.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.table.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.tablecell.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.tablerow.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.tablecolumn.class.htm
