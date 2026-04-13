# Skip Records During the Merge Process

## Goal

Skip selected rows while merging JSON data by handling the `DataRowMerged` event.

## Source

- https://www.textcontrol.com/blog/2025/02/10/mail-merge-skipping-records-during-the-merge-process-in-net-c-sharp/

## Event Handler

```csharp
static void MailMerge_DataRowMerged(MailMerge.DataRowMergedEventArgs e, List<int> rowsToSkip, byte[] skippedRowData)
{
    if (rowsToSkip.Contains(e.DataRowNumber))
    {
        e.MergedRow = skippedRowData;
    }
}
```

## Full Merge Flow

```csharp
using TXTextControl.DocumentServer;

List<int> rowsToSkip = new List<int> { 1 }; // Example: Skip row 1
MergeDocument("template.tx", "data.json", "output.pdf", rowsToSkip);

static void MergeDocument(string templatePath, string jsonDataPath, string outputPath, List<int> rowsToSkip)
{
    using (TXTextControl.ServerTextControl tx = new TXTextControl.ServerTextControl())
    {
        tx.Create();
        tx.Load(templatePath, TXTextControl.StreamType.InternalUnicodeFormat);

        MailMerge mailMerge = new MailMerge { TextComponent = tx };
        byte[] skippedRowData = GetSkippedRowData(tx);

        mailMerge.DataRowMerged += (sender, e) => MailMerge_DataRowMerged(e, rowsToSkip, skippedRowData);

        string jsonData = File.ReadAllText(jsonDataPath);
        mailMerge.MergeJsonData(jsonData, true);

        tx.Save(outputPath, TXTextControl.StreamType.AdobePDF);
    }
}

static byte[] GetSkippedRowData(TXTextControl.ServerTextControl tx)
{
    using (TXTextControl.ServerTextControl tempTx = new TXTextControl.ServerTextControl())
    {
        tempTx.Create();
        tempTx.Save(out byte[] data, TXTextControl.BinaryStreamType.InternalUnicodeFormat);
        return data;
    }
}
```

## Notes

- `DataRowMerged` is raised after each merged row.
- Assigning a blank `MergedRow` payload removes that row content from the result.
