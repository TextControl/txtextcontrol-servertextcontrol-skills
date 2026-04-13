---
name: txtextcontrol-servertextcontrol-applicationfields
description: |
  Use this skill when a user asks how to create, inspect, update, and remove
  Microsoft Word-style ApplicationFields (for example MERGEFIELD) in
  TX Text Control .NET Server using ServerTextControl.

  Trigger it for requests involving ApplicationFieldCollection,
  ApplicationFieldFormat, TypeName/Parameters handling, field insertion,
  retrieval by ID, remove/clear behavior, and refactoring merge field names.
metadata:
  author: Text Control
  version: "34.3.0"
---

# TX Text Control ServerTextControl Elements: ApplicationFields

## Overview

This skill provides guidance and code snippets for working with
`ApplicationField` and `ApplicationFieldCollection` in TX Text Control
.NET Server.

It focuses on Word-compatible merge field scenarios, field updates,
and helper workflows for large template refactoring.

## Key Capabilities

- **Insert ApplicationFields:** Create and add new fields at the current input position.
- **Read and Update Fields:** Iterate through fields and modify visible text, type, and parameters.
- **Get by ID or Input Position:** Retrieve specific fields with `GetItem()` overloads.
- **Remove or Keep Text:** Remove fields with `keepText` options.
- **Clear Collections:** Remove all application fields in one call.
- **Find Container Context:** Resolve section/paragraph/subtextpart for each field.
- **Refactor Merge Names:** Programmatically rename merge field names and matching merge blocks.

## Quick Start Examples

### Example 1: Insert MERGEFIELD programmatically
**User:** "How do I insert a MERGEFIELD at the current cursor position?"

**Result:** Use `references/insert-applicationfields-and-mergefields.md`

### Example 2: Iterate and update merge field text
**User:** "How do I find MERGEFIELD Address and replace visible text?"

**Result:** Use `references/iterate-and-update-applicationfields.md`

### Example 3: Get by ID and remove field
**User:** "How do I get an ApplicationField by ID and remove it but keep text?"

**Result:** Use `references/get-and-remove-applicationfields.md`

### Example 4: Clear all application fields
**User:** "How do I remove all ApplicationFields from a document?"

**Result:** Use `references/clear-applicationfields.md`

### Example 5: Find section/paragraph/subtextpart for fields
**User:** "How can I locate which section contains each ApplicationField?"

**Result:** Use `references/find-applicationfields-in-sections-and-paragraphs.md`

## Generate ServerTextControl ApplicationField Guidance

**Trigger keywords:** "applicationfield", "applicationfields", "mergefield",
"applicationfieldcollection", "typename", "parameters", "applicationfieldformat",
"getitem", "remove", "clear", "text parts".

**Workflow:**

1. Identify whether the request is insertion, update, retrieval, deletion, or structural analysis.
2. Read the matching reference file in `references/`.
3. Use only the code and instructions from the selected file.
4. Do not invent additional APIs, classes, or method signatures.
5. Return complete guidance and code in the format requested by the user.

## Code References

| File | Task |
|------|------|
| `insert-applicationfields-and-mergefields.md` | Create and insert ApplicationFields (MERGEFIELD) |
| `iterate-and-update-applicationfields.md` | Enumerate ApplicationFields and update text/parameters |
| `get-and-remove-applicationfields.md` | Retrieve by input position/ID and remove with keepText options |
| `clear-applicationfields.md` | Remove all ApplicationFields with or without deleting visible text |
| `find-applicationfields-in-sections-and-paragraphs.md` | Determine section/paragraph/subtextpart for each ApplicationField |

## Source Articles

- https://www.textcontrol.com/blog/2024/08/02/find-applicationfields-within-sections-and-paragraphs-in-net-c-sharp/
- https://www.textcontrol.com/blog/2024/02/08/renaming-merge-blocks-and-merge-fields-programmatically-in-csharp/

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfieldcollection.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfield.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfieldformat.enumeration.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.servertextcontrol.applicationfields.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfieldcollection.add.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfieldcollection.getitem.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfieldcollection.remove.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfieldcollection.clear.method.htm
