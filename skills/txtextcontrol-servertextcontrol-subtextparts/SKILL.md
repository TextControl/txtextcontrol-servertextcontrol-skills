---
name: txtextcontrol-servertextcontrol-subtextparts
description: |
  Use this skill when a user asks how to create, manage, and process
  SubTextParts in TX Text Control .NET Server using ServerTextControl.

  Trigger it for requests involving SubTextPartCollection add/get/remove,
  nested SubTextParts, highlight settings, saving SubTextPart content,
  storing metadata in SubTextPart.Data, and merge-block style workflows.
metadata:
  author: Text Control
  version: "34.3.0"
---

# TX Text Control ServerTextControl Elements: SubTextParts

## Overview

This skill provides guidance and code snippets for working with
`SubTextPart` and `SubTextPartCollection` in TX Text Control .NET Server.

It focuses on user-defined document regions that can be named, nested,
highlighted, saved, and processed programmatically.

## Key Capabilities

- **Create SubTextParts:** Add named and ID-based subtextparts at selected positions.
- **Handle Add Results:** Evaluate `SubTextPartCollection.AddResult` for validation and overlap cases.
- **Retrieve SubTextParts:** Access by current position, name, or ID.
- **Nested Structures:** Work with child/descendant relationships via `GetChildren`.
- **Remove Safely:** Remove with `keepText` and `keepNested` options.
- **Store Metadata:** Persist structured metadata in `SubTextPart.Data`.
- **Save Region Content:** Export subtextpart text directly without manual selection.

## Quick Start Examples

### Example 1: Create and highlight SubTextPart
**User:** "How do I turn selected text into a highlighted SubTextPart?"

**Result:** Use `references/create-and-highlight-subtextparts.md`

### Example 2: Get by name or ID
**User:** "How do I get a SubTextPart by name or ID?"

**Result:** Use `references/get-subtextparts-by-name-id-or-position.md`

### Example 3: Remove with keep text
**User:** "How do I remove a SubTextPart but keep its text?"

**Result:** Use `references/remove-subtextparts-with-keep-options.md`

### Example 4: Save part and store metadata
**User:** "How do I save a SubTextPart and attach custom JSON data?"

**Result:** Use `references/save-subtextparts-and-store-data.md`

### Example 5: Use merge-block SubTextParts
**User:** "How do I configure a merge-block SubTextPart conditionally?"

**Result:** Use `references/configure-mergeblock-subtextparts-conditionally.md`

## Generate ServerTextControl SubTextPart Guidance

**Trigger keywords:** "subtextpart", "subtextparts", "subtextpartcollection",
"addresult", "nested", "getchildren", "keepnested", "data", "txmb_",
"merge block", "highlightmode".

**Workflow:**

1. Identify whether the request is creation, retrieval, nesting, deletion, persistence, or merge-block shaping.
2. Read the matching reference file in `references/`.
3. Use only the code and instructions from the selected file.
4. Do not invent additional APIs, classes, or method signatures.
5. Return complete guidance and code in the format requested by the user.

## Code References

| File | Task |
|------|------|
| `create-and-highlight-subtextparts.md` | Create and highlight SubTextParts from the current selection |
| `get-subtextparts-by-name-id-or-position.md` | Retrieve SubTextParts via `GetItem()` overloads and inspect hierarchy |
| `remove-subtextparts-with-keep-options.md` | Remove SubTextParts with `keepText` / `keepNested` control |
| `save-subtextparts-and-store-data.md` | Save SubTextPart content and store/retrieve JSON metadata in `Data` |
| `configure-mergeblock-subtextparts-conditionally.md` | Configure conditional merge-block behavior using `txmb_` SubTextParts |

## Source Articles

- https://www.textcontrol.com/blog/2024/02/09/the-power-of-subtextparts-typical-use-cases/
- https://www.textcontrol.com/blog/2022/02/17/mailmerge-rendering-conditional-table-rows/

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpartcollection.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpart.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.servertextcontrol.subtextparts.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpartcollection.add.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpartcollection.getitem.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpartcollection.remove.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpartcollection.addresult.enumeration.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpart.getchildren.method.htm
