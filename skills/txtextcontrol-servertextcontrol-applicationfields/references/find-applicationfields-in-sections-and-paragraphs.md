# Find ApplicationFields in Sections and Paragraphs

## Goal

Determine the section, paragraph, and subtextpart that contains each
ApplicationField by comparing character index ranges.

## Source

- https://www.textcontrol.com/blog/2024/08/02/find-applicationfields-within-sections-and-paragraphs-in-net-c-sharp/

## Extension Helper

```csharp
using TXTextControl;

public static class ApplicationFieldExtender
{
    private static bool IsFieldInContainer(int fieldStart, int fieldLength, int containerStart, int containerLength)
    {
        int fieldEnd = fieldStart + fieldLength;
        int containerEnd = containerStart + containerLength;

        return fieldStart >= containerStart && fieldEnd <= containerEnd;
    }

    public static int Section(this ApplicationField field, TextControl textControl)
    {
        foreach (Section section in textControl.Sections)
        {
            if (IsFieldInContainer(field.Start, field.Length, section.Start, section.Length))
            {
                return section.Number;
            }
        }

        return -1;
    }

    public static int Paragraph(this ApplicationField field, TextControl textControl)
    {
        foreach (TXTextControl.Paragraph paragraph in textControl.Paragraphs)
        {
            if (IsFieldInContainer(field.Start, field.Length, paragraph.Start, paragraph.Length))
            {
                return paragraph.Number;
            }
        }

        return -1;
    }

    public static int SubTextPart(this ApplicationField field, TextControl textControl)
    {
        foreach (TXTextControl.SubTextPart subTextPart in textControl.SubTextParts)
        {
            if (IsFieldInContainer(field.Start, field.Length, subTextPart.Start, subTextPart.Length))
            {
                return subTextPart.Number;
            }
        }

        return -1;
    }
}
```

## Usage

```csharp
foreach (ApplicationField field in textControl1.ApplicationFields)
{
    int sectionNumber = field.Section(textControl1);
    int paragraphNumber = field.Paragraph(textControl1);
    int subTextPartNumber = field.SubTextPart(textControl1);

    System.Diagnostics.Debug.WriteLine("Field in Section: " + sectionNumber);
    System.Diagnostics.Debug.WriteLine("Field in Paragraph: " + paragraphNumber);
    System.Diagnostics.Debug.WriteLine("Field in SubTextPart: " + subTextPartNumber);
}
```

## Notes

- This approach is useful when you need to process fields by layout region.
- It works by comparing `[Start, Length]` ranges of field and container.

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfield.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.section.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.paragraph.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpart.class.htm
