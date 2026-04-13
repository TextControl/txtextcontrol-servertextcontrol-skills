# Configure MergeBlock SubTextParts Conditionally

## Goal

Find merge-block SubTextParts by name (prefix `txmb_`) and apply conditional
filter instructions for MailMerge rendering.

## Source

- https://www.textcontrol.com/blog/2022/02/17/mailmerge-rendering-conditional-table-rows/

## Load Template and Configure MergeBlock Condition

```csharp
// load the template
textControl1.Load("template.tx", TXTextControl.StreamType.InternalUnicodeFormat);

// get the "outofstock" SubTextPart
SubTextPart subTextPart = textControl1.SubTextParts.GetItem("txmb_outofstock");

// create a MergeBlockInfo object
MergeBlockInfo mergeBlockInfo = new MergeBlockInfo(subTextPart);

// add the condition
mergeBlockInfo.BlockMergingCondition =
  new List<TXTextControl.DocumentServer.DataShaping.FilterInstruction>()
  {
       new TXTextControl.DocumentServer.DataShaping.FilterInstruction(
          "available",
          TXTextControl.DocumentServer.DataShaping.RelationalOperator.Equals,
          false
          )
  };

// store the condition in the SubTextPart
mergeBlockInfo.Apply();
```

## Merge JSON Data

```csharp
string data = System.IO.File.ReadAllText("data.json");

using (MailMerge mm = new MailMerge())
{
    mm.TextComponent = textControl1;
    mm.MergeJsonData(data);
}
```

## Notes

- Merge-block SubTextParts typically use the `txmb_` prefix.
- Conditions persist when saving templates in supported formats.
