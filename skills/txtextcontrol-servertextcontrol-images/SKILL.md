---
name: txtextcontrol-servertextcontrol-images
description: |
  Use this skill when a user asks how to work with images in TX Text Control
  .NET Server using ServerTextControl.

  Trigger it for requests involving inserting images from file, stream,
  System.Drawing.Image, byte arrays, and URLs; positioning images inline,
  anchored, or fixed; configuring image export and save mode behavior;
  merging image placeholders with MailMerge; and extracting images from
  existing documents.
metadata:
  author: Text Control
  version: "34.3.0"
---

# TX Text Control ServerTextControl Elements: Images

## Overview

This skill provides guidance and code snippets for image workflows
in TX Text Control .NET Server using ServerTextControl.

It covers insertion, positioning, export behavior, merge-time placeholders,
and extraction scenarios.

## Key Capabilities

- **Insert Images:** Add images from file paths, `System.Drawing.Image`, streams, byte arrays, and URLs.
- **Position Images:** Insert inline, anchored to paragraph, or fixed on page/document.
- **Configure Save Behavior:** Control `SaveMode`, compression quality, export format, and max resolution.
- **Image Placeholders:** Merge placeholders with JSON data and file references.
- **Remove Empty Placeholder Images:** Enable `RemoveEmptyImages` in MailMerge.
- **Extract Images:** Export documents as HTML with embedded image data and decode to files.

## Quick Start Examples

### Example 1: Insert image from file or stream
**User:** "How do I insert an image from file, memory stream, or URL in ServerTextControl?"

**Result:** Use `references/insert-images-from-file-stream-url.md`

### Example 2: Position image in document
**User:** "How do I anchor an image to a paragraph and control text flow around it?"

**Result:** Use `references/position-images-inline-anchored-fixed.md`

### Example 3: Configure export and save mode
**User:** "How do I save images as external references with PNG export settings?"

**Result:** Use `references/configure-image-export-and-save-mode.md`

### Example 4: Merge image placeholders
**User:** "How do I merge named image placeholders using JSON and MailMerge?"

**Result:** Use `references/merge-image-placeholders-with-mailmerge.md`

### Example 5: Extract images from existing documents
**User:** "How do I extract all images from DOCX or PDF using ServerTextControl?"

**Result:** Use `references/extract-images-from-documents.md`

## Generate ServerTextControl Image Guidance

**Trigger keywords:** "servertextcontrol", "image", "imagecollection", "insert image",
"imageinsertionmode", "savemode", "exportfilter", "placeholder", "mailmerge",
"removeemptyimages", "extract images", "base64".

**Workflow:**

1. Identify whether the request is insertion, positioning, export configuration, placeholder merge, or extraction.
2. Read the matching reference file in `references/`.
3. Use only the code and instructions from the selected file.
4. Do not invent additional APIs, classes, or method signatures.
5. Return complete guidance and code in the format requested by the user.

## Code References

| File | Task |
|------|------|
| `insert-images-from-file-stream-url.md` | Insert images from files, .NET image objects, memory streams, byte arrays, and URLs |
| `position-images-inline-anchored-fixed.md` | Position images using insertion modes: inline, anchored, and fixed |
| `configure-image-export-and-save-mode.md` | Configure image save mode, compression quality, format, and max resolution |
| `merge-image-placeholders-with-mailmerge.md` | Merge image placeholders with JSON/base64 or file references using MailMerge |
| `extract-images-from-documents.md` | Extract embedded images from DOCX/PDF by exporting to HTML and decoding base64 |

## Source Articles

- https://www.textcontrol.com/blog/2024/05/03/various-ways-of-inserting-images-into-tx-text-control/
- https://www.textcontrol.com/blog/2022/03/28/different-ways-to-insert-images/
- https://www.textcontrol.com/blog/2022/12/22/mailmerge-working-with-image-placeholders/
- https://www.textcontrol.com/blog/2024/06/11/extracting-images-from-ms-word-documents-in-csharp/

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.imagecollection.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.image.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.servertextcontrol.images.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.imageinsertionmode.enumeration.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.imagesavemode.enumeration.htm
