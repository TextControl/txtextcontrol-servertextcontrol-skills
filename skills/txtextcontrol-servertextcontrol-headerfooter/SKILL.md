---
name: txtextcontrol-servertextcontrol-headerfooter
description: |
  Use this skill when a user asks how to create and manage headers and
  footers in TX Text Control .NET Server using ServerTextControl.

  Trigger it for requests involving adding headers/footers per section,
  section-specific vs document-wide header/footer behavior, inserting images
  and page number fields in headers/footers, first/even page variants,
  connection to previous sections, and restarting page numbering per section.
metadata:
  author: Text Control
  version: "34.3.0"
---

# TX Text Control ServerTextControl Elements: Headers and Footers

## Overview

This skill provides guidance and code snippets for creating and managing
header/footer content in TX Text Control .NET Server.

It focuses on section-based layout scenarios, dynamic page numbering,
and repeatable header/footer content such as logos and watermarks.

## Key Capabilities

- **Add Headers/Footers:** Use `HeaderFooterCollection.Add()` for document-wide or section-level headers/footers.
- **Edit Header/Footer Content:** Set text and formatting via `HeaderFooter.Selection`.
- **Page Number Fields:** Insert current page and total page count using `PageNumberField`.
- **First/Even/Odd Variants:** Use `HeaderFooterType` for first page and even-page headers/footers.
- **Section Control:** Use `ConnectedToPrevious` to decouple section header/footer content.
- **Per-Section Numbering:** Restart page numbering by section with `SectionFormat.RestartPageNumbering`.
- **Images in Headers:** Insert logos/watermarks in headers with image insertion modes.

## Quick Start Examples

### Example 1: Add a section header
**User:** "How do I add a header with text in the first section?"

**Result:** Use `references/add-header-and-footer-to-sections.md`

### Example 2: Add page numbers
**User:** "How do I add 'Page X of Y' into the footer?"

**Result:** Use `references/add-page-numbers-in-header-footer.md`

### Example 3: Restart numbering per section
**User:** "How can I restart page numbers at each section?"

**Result:** Use `references/restart-page-numbering-per-section.md`

### Example 4: Add image/logo in header
**User:** "How do I add a logo or watermark image to headers?"

**Result:** Use `references/add-images-to-header-footer.md`

### Example 5: Control first/even/odd behavior
**User:** "How do I create first-page and even-page header variants?"

**Result:** Use `references/use-headerfootertype-variants.md`

## Generate ServerTextControl Header/Footer Guidance

**Trigger keywords:** "header", "footer", "headersandfooters", "headerfootercollection",
"headerfootertype", "connectedtoprevious", "pagenumberfield",
"first page header", "even header", "restart page numbering".

**Workflow:**

1. Identify whether the request is section setup, text/image content, numbering, or type variants.
2. Read the matching reference file in `references/`.
3. Use only the code and instructions from the selected file.
4. Do not invent additional APIs, classes, or method signatures.
5. Return complete guidance and code in the format requested by the user.

## Code References

| File | Task |
|------|------|
| `add-header-and-footer-to-sections.md` | Add and edit headers/footers for sections and control section linkage |
| `add-page-numbers-in-header-footer.md` | Insert current and total page numbers in headers/footers |
| `restart-page-numbering-per-section.md` | Restart page numbering for each section and configure independent footer fields |
| `add-images-to-header-footer.md` | Insert logos and watermark images into headers/footers |
| `use-headerfootertype-variants.md` | Work with HeaderFooterType variants: Header, Footer, First Page, Even page |

## Source Articles

- https://www.textcontrol.com/blog/2024/10/25/create-word-document-with-net-c-sharp/
- https://www.textcontrol.com/blog/2024/10/17/create-pdf-file-with-net-c-sharp/
- https://www.textcontrol.com/blog/2022/01/28/adding-svg-watermarks-to-documents/
- https://www.textcontrol.com/blog/2013/11/08/restart-the-page-numbering-fields-per-section/

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.headerfootercollection.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.headerfooter.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.headerfootertype.enumeration.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.headerfootercollection.add.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.headerfootercollection.getitem.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.headerfootercollection.remove.method.htm
