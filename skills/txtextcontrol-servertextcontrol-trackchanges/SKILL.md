---
name: txtextcontrol-servertextcontrol-trackchanges
description: |
  Use this skill when a user asks how to inspect and process tracked changes
  in TX Text Control .NET Server using ServerTextControl.

  Trigger it for requests involving TrackedChangeCollection navigation,
  filtering by author/date/change type, accepting or rejecting changes,
  track-change events, and saving documents with tracked-change markup omitted.
metadata:
  author: Text Control
  version: "34.3.0"
---

# TX Text Control ServerTextControl Elements: Track Changes

## Overview

This skill provides guidance and code snippets for Track Changes workflows in
TX Text Control .NET Server.

It focuses on backend inspection, filtering, and automated processing of
tracked revisions in DOCX and other supported document formats.

## Key Capabilities

- **Load and inspect revisions:** Read `TrackedChangeCollection` from loaded documents.
- **Filter revisions:** Filter by `UserName`, `ChangeKind`, and `ChangeTime`.
- **Accept or reject revisions:** Use `TrackedChanges.Remove(change, accept)`.
- **Navigate changes:** Use `GetItem()`, `GetItem(true)`, `GetItem(false)`, and `ScrollTo()`.
- **Export changed text snippets:** Save a specific change using `TrackedChange.Save`.
- **Handle events:** React to `TrackedChangeCreated` and `TrackedChangeDeleted`.
- **Control output markup:** Use `SaveSettings.OmittedContent = OmittedContent.TrackedChanges`.

## Quick Start Examples

### Example 1: Enumerate tracked changes
**User:** "How do I list all tracked changes in a DOCX?"

**Result:** Use `references/load-and-enumerate-tracked-changes.md`

### Example 2: Filter by author and type
**User:** "How do I filter revisions made by Alice and only deletions?"

**Result:** Use `references/filter-tracked-changes-by-author-kind-and-date.md`

### Example 3: Accept or reject selected changes
**User:** "How do I automatically accept filtered revisions?"

**Result:** Use `references/accept-or-reject-tracked-changes.md`

### Example 4: Navigate and export one change
**User:** "How do I jump to next change and save its text?"

**Result:** Use `references/navigate-select-and-save-tracked-changes.md`

### Example 5: Track-change events and save output
**User:** "How do I react to tracked-change events and save without markup?"

**Result:** Use `references/handle-trackchange-events-and-save-without-markup.md`

## Generate ServerTextControl Track Changes Guidance

**Trigger keywords:** "track changes", "trackedchange", "trackedchanges",
"trackedchangecollection", "changekind", "changetime", "accept",
"reject", "getitem", "trackedchangecreated", "omittedcontent".

**Workflow:**

1. Identify whether the request is inspection, filtering, decisioning, navigation, event handling, or output shaping.
2. Read the matching reference file in `references/`.
3. Use only the code and instructions from the selected file.
4. Do not invent additional APIs, classes, or method signatures.
5. Return complete guidance and code in the format requested by the user.

## Code References

| File | Task |
|------|------|
| `load-and-enumerate-tracked-changes.md` | Load a DOCX and enumerate `TrackedChanges` metadata |
| `filter-tracked-changes-by-author-kind-and-date.md` | Build LINQ filters for author, change kind, and time range |
| `accept-or-reject-tracked-changes.md` | Accept or reject tracked changes programmatically |
| `navigate-select-and-save-tracked-changes.md` | Navigate current/next/previous changes and save changed text |
| `handle-trackchange-events-and-save-without-markup.md` | Handle track-change events and save with `OmittedContent.TrackedChanges` |

## Source Articles

- https://www.textcontrol.com/blog/2026/03/10/inspect-and-process-track-changes-in-docx-documents-with-tx-text-control-with-dotnet-csharp/

## API Reference

- https://docs.textcontrol.com/textcontrol/asp-dotnet/cat.trackedchange.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.servertextcontrol.trackedchanges.property.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchangecollection.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchange.class.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchangecollection.getitem.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchangecollection.remove.method.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.servertextcontrol.trackedchangecreated.event.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.servertextcontrol.trackedchangedeleted.event.htm
- https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.savesettings.omittedcontent.property.htm
