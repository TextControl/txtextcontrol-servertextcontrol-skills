---
name: txtextcontrol-servertextcontrol-lists
description: |
  Use this skill when a user asks how to create and format bulleted or
  numbered lists in TX Text Control .NET Server using ServerTextControl.

  Trigger it for requests involving ListFormat, list type switching,
  number format customization, multilevel list indentation, restarting
  numbering, and converting plain text bullets to proper list formatting.
metadata:
  author: Text Control
  version: "34.3.0"
---

# TX Text Control ServerTextControl Elements: Numbered and Bulleted Lists

## Overview

This skill provides guidance and code snippets for list workflows in
TX Text Control .NET Server.

It focuses on creating, customizing, and normalizing bulleted and numbered
lists by using `ListFormat` on selections and paragraphs.

## Key Capabilities

- **Create Numbered Lists:** Apply `ListFormat` with `Type = ListType.Numbered`.
- **Create Bulleted Lists:** Apply `ListFormat` with `Type = ListType.Bulleted`.
- **Customize Numbering:** Set `NumberFormat`, `FirstNumber`, and prefix/suffix text.
- **Multilevel Lists:** Configure `Level`, `LeftIndent`, and `HangingIndent`.
- **Restart Numbering:** Use `RestartNumbering` to begin a new sequence.
- **Selection-Based Formatting:** Apply list formatting through `Selection.ListFormat`.
- **Convert Plain Text Bullets:** Detect bullet-like text and transform it into real list paragraphs.

## Quick Start Examples

### Example 1: Create numbered list
**User:** "How do I apply a numbered list to selected text?"

**Result:** Use `references/create-numbered-list-with-listformat.md`

### Example 2: Create bulleted list
**User:** "How do I create a bulleted list and customize the bullet character?"

**Result:** Use `references/create-bulleted-list-with-custom-bullet.md`

### Example 3: Configure multilevel list
**User:** "How do I set list levels and indentation for nested lists?"

**Result:** Use `references/set-multilevel-list-indentation-and-levels.md`

### Example 4: Restart numbering
**User:** "How do I restart a numbered list and set the first number?"

**Result:** Use `references/restart-numbering-and-set-first-number.md`

### Example 5: Convert plain text bullets
**User:** "How do I convert plain text lines with '-' into real bulleted lists?"

**Result:** Use `references/convert-plain-text-to-bulleted-list.md`

## Generate ServerTextControl List Guidance

**Trigger keywords:** "list", "bulleted", "numbered", "listformat",
"listtype", "numberformat", "restartnumbering", "level",
"leftindent", "hangingindent", "selection.listformat".

**Workflow:**

1. Identify whether the request is list creation, style customization, multilevel layout, numbering reset, or text conversion.
2. Read the matching reference file in `references/`.
3. Use only the code and instructions from the selected file.
4. Do not invent additional APIs, classes, or method signatures.
5. Return complete guidance and code in the format requested by the user.

## Code References

| File | Task |
|------|------|
| `create-numbered-list-with-listformat.md` | Apply numbered lists on selected text with custom number formats |
| `create-bulleted-list-with-custom-bullet.md` | Apply bulleted lists and configure bullet character/font/size |
| `set-multilevel-list-indentation-and-levels.md` | Configure nested list levels and indentation |
| `restart-numbering-and-set-first-number.md` | Restart numbering and set the initial number of a new list |
| `convert-plain-text-to-bulleted-list.md` | Convert plain text list markers into true bulleted lists |

## Source Articles

- https://www.textcontrol.com/blog/2025/01/21/convert-plain-text-to-bulleted-lists-in-csharp-with-dotnet/

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/cat.list.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listformat.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.selection.listformat.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.servertextcontrol.listformat.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listtype.enumeration.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.numberformat.enumeration.htm
