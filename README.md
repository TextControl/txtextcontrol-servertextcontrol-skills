# TX Text Control Skills

## About This Repository

This repository contains AI-ready skills for TX Text Control ServerTextControl
workflows, including MailMerge and document element manipulation.

Each skill folder contains a `SKILL.md` manifest and `references/*.md` task files
backed by validated code from the Text Control blog and official documentation.

## Included Skills

### MailMerge Skill
- **txtextcontrol-servertextcontrol-mailmerge**
  - Use for ServerTextControl MailMerge tasks including JSON/template merges,
    object and list merges, XML merges, merge events, and PDF output.

### Tables Skill
- **txtextcontrol-servertextcontrol-tables**
  - Use for working with tables in ServerTextControl: creating tables
    programmatically, formatting cells and rows, populating tables from JSON,
    converting CSV to PDF, and removing empty columns after mail merge.

### Images Skill
- **txtextcontrol-servertextcontrol-images**
   - Use for image workflows in ServerTextControl: inserting images from
      file/stream/URL, controlling image positioning and insertion mode,
      configuring image export/save behavior, merging image placeholders,
      and extracting images from existing documents.

### Header/Footer Skill
- **txtextcontrol-servertextcontrol-headerfooter**
   - Use for header/footer workflows in ServerTextControl: adding headers and
      footers per section, inserting page number fields, controlling first/even
      page variants, decoupling sections with `ConnectedToPrevious`, and
      restarting page numbering per section.

### Lists Skill
- **txtextcontrol-servertextcontrol-lists**
   - Use for numbered and bulleted list workflows in ServerTextControl:
      creating numbered/bulleted lists, configuring levels and indentation,
      setting number formats and start values, restarting numbering, and
      converting plain-text bullet lines into real list formatting.

### ApplicationFields Skill
- **txtextcontrol-servertextcontrol-applicationfields**
   - Use for ApplicationField workflows in ServerTextControl: inserting and
      editing MS Word-compatible merge fields, reading/updating field
      type/parameters, retrieving fields by ID or input position, removing or
      clearing fields with keep-text behavior, and refactoring field names.

### SubTextParts Skill
- **txtextcontrol-servertextcontrol-subtextparts**
   - Use for SubTextPart workflows in ServerTextControl: creating highlighted
      named regions, retrieving by name/ID/input position, working with nested
      structures, removing with keep-text options, saving region content, and
      storing metadata in `SubTextPart.Data`.

### Track Changes Skill
- **txtextcontrol-servertextcontrol-trackchanges**
   - Use for Track Changes workflows in ServerTextControl: loading and
      filtering revisions, navigating tracked changes, accepting/rejecting
      selected changes, handling track-change events, and saving output with
      tracked-change markup omitted.

### PDF Signing Skill
- **txtextcontrol-servertextcontrol-pdfsigning**
   - Use for PDF digital-signing workflows in ServerTextControl: signing full
      PDF/PDF-A output, signing named signature fields, creating and using
      certificates (PFX/store), and secure certificate sourcing such as
      Azure Key Vault.

## Getting Started

### 1. Copy the skill folders you need

Copy one or more skill folders from this repository into your own workspace.

### 2. Install in your editor skill location

Place the selected skill folders in one of your supported skill paths.

Example workspace layout:

```text
your-workspace/
├── .github/skills/                    # or .claude/skills/ or .codestudio/skills/
│   ├── txtextcontrol-servertextcontrol-mailmerge/
│   │   ├── SKILL.md
│   │   └── references/
│   ├── txtextcontrol-servertextcontrol-tables/
│   │   ├── SKILL.md
│   │   └── references/
│   ├── txtextcontrol-servertextcontrol-images/
│   │   ├── SKILL.md
│   │   └── references/
│   ├── txtextcontrol-servertextcontrol-headerfooter/
│   │   ├── SKILL.md
│   │   └── references/
│   ├── txtextcontrol-servertextcontrol-lists/
│   │   ├── SKILL.md
│   │   └── references/
│   ├── txtextcontrol-servertextcontrol-applicationfields/
│   │   ├── SKILL.md
│   │   └── references/
│   ├── txtextcontrol-servertextcontrol-subtextparts/
│   │   ├── SKILL.md
│   │   └── references/
│   ├── txtextcontrol-servertextcontrol-trackchanges/
│   │   ├── SKILL.md
│   │   └── references/
│   └── txtextcontrol-servertextcontrol-pdfsigning/
│       ├── SKILL.md
│       └── references/
└── your-project-files...
```

### 3. Use the skill

Two common usage patterns:

1. **Automatic loading**
   - Describe your task naturally.
   - Example: "Create a simple ServerTextControl MailMerge app with JSON data and a template."
   - Example: "How do I create a table with a header row and export it as PDF?"
   - Example: "How do I insert an image from URL and position it with text wrapping?"
   - Example: "How do I add page numbers and a logo in headers and footers?"
   - Example: "How do I convert plain text lines into bulleted and numbered lists?"
   - Example: "How do I insert and rename MERGEFIELD ApplicationFields in a template?"
   - Example: "How do I create and save named SubTextPart regions with metadata?"
   - Example: "How do I filter track changes by author and accept selected revisions?"
   - Example: "How do I sign a PDF with a PFX certificate and visible signature field?"

2. **Slash command invocation**
   - If your client supports slash-invoked skills, call the skill explicitly.
   - Example: `/txtextcontrol-servertextcontrol-mailmerge create a JSON template merge flow`
   - Example: `/txtextcontrol-servertextcontrol-tables create a table from JSON data`
   - Example: `/txtextcontrol-servertextcontrol-images merge image placeholders from JSON`
   - Example: `/txtextcontrol-servertextcontrol-headerfooter add first and even page headers`
   - Example: `/txtextcontrol-servertextcontrol-lists create multilevel numbered list formatting`
   - Example: `/txtextcontrol-servertextcontrol-applicationfields update mergefield parameters`
   - Example: `/txtextcontrol-servertextcontrol-subtextparts create and save named regions`
   - Example: `/txtextcontrol-servertextcontrol-trackchanges inspect and process revisions`
   - Example: `/txtextcontrol-servertextcontrol-pdfsigning sign pdf with certificate`

## Which Skill Should I Use?

| Task | Skill |
|------|-------|
| Build ServerTextControl MailMerge workflows | `txtextcontrol-servertextcontrol-mailmerge` |
| Create and format tables in documents | `txtextcontrol-servertextcontrol-tables` |
| Populate a table from JSON or CSV data | `txtextcontrol-servertextcontrol-tables` |
| Remove empty columns after mail merge | `txtextcontrol-servertextcontrol-tables` |
| Insert and position images in documents | `txtextcontrol-servertextcontrol-images` |
| Merge image placeholders using JSON data | `txtextcontrol-servertextcontrol-images` |
| Extract images from DOCX/PDF documents | `txtextcontrol-servertextcontrol-images` |
| Add, edit, and remove headers/footers by section | `txtextcontrol-servertextcontrol-headerfooter` |
| Add "Page X of Y" fields in header/footer | `txtextcontrol-servertextcontrol-headerfooter` |
| Use first/even page header/footer variants | `txtextcontrol-servertextcontrol-headerfooter` |
| Restart page numbering per section | `txtextcontrol-servertextcontrol-headerfooter` |
| Create and format numbered/bulleted lists | `txtextcontrol-servertextcontrol-lists` |
| Convert plain text bullets into real lists | `txtextcontrol-servertextcontrol-lists` |
| Configure multilevel list indents and numbering restart | `txtextcontrol-servertextcontrol-lists` |
| Insert and update ApplicationFields (MERGEFIELD) | `txtextcontrol-servertextcontrol-applicationfields` |
| Retrieve/remove/clear ApplicationFields with keep-text options | `txtextcontrol-servertextcontrol-applicationfields` |
| Find ApplicationFields by section or paragraph context | `txtextcontrol-servertextcontrol-applicationfields` |
| Create, retrieve, and remove SubTextParts | `txtextcontrol-servertextcontrol-subtextparts` |
| Save named document regions and store SubTextPart metadata | `txtextcontrol-servertextcontrol-subtextparts` |
| Configure merge-block SubTextParts conditionally | `txtextcontrol-servertextcontrol-subtextparts` |
| Inspect and filter Track Changes revisions | `txtextcontrol-servertextcontrol-trackchanges` |
| Accept or reject tracked changes programmatically | `txtextcontrol-servertextcontrol-trackchanges` |
| Save documents without tracked-change markup | `txtextcontrol-servertextcontrol-trackchanges` |
| Digitally sign complete PDF documents | `txtextcontrol-servertextcontrol-pdfsigning` |
| Sign named SignatureFields with certificates | `txtextcontrol-servertextcontrol-pdfsigning` |
| Use PFX, certificate store, or Key Vault for signing | `txtextcontrol-servertextcontrol-pdfsigning` |

## Typical Scenarios

### MailMerge
- Creating a simple MailMerge application (JSON data + template)
- Merging self-calculating objects and object lists
- Using XML data sources for server-side merge
- Skipping selected records during merge
- Merging form fields with `Preselect` and `Replace`

### Tables
- Creating tables programmatically with header rows, borders, and cell formatting
- Inserting a table from JSON data using `DataSourceManager` and `MailMerge`
- Converting a CSV file to a formatted table and exporting as PDF
- Removing empty columns from tables after a mail merge
- Controlling page breaks within table rows

### Images
- Inserting images from files, .NET image objects, streams, byte arrays, and URLs
- Positioning images inline, anchored to paragraphs, or fixed on page
- Controlling image export quality, format, and save mode
- Merging image placeholders using MailMerge and JSON data
- Removing empty image placeholders during merge
- Extracting embedded images from DOCX/PDF by HTML export and base64 decoding

### Headers / Footers
- Adding and editing section-specific headers and footers
- Inserting current and total page number fields (`Page X of Y`)
- Using `HeaderFooterType` variants for first and even pages
- Decoupling section headers/footers with `ConnectedToPrevious = false`
- Restarting page numbering in each section with `RestartPageNumbering`

### Numbered / Bulleted Lists
- Applying bulleted and numbered list formatting with `ListFormat`
- Choosing list kind using `ListType` (`Bulleted`, `Numbered`, `None`)
- Configuring number style with `NumberFormat` (Arabic, letters, Roman)
- Setting list levels and indents for nested list structures
- Restarting numbering and setting the first number
- Converting plain-text markers (`-`, `*`, `+`) to true bulleted list formatting

### ApplicationFields
- Inserting new `ApplicationField` instances (for example `MERGEFIELD`)
- Enumerating fields and updating visible text, type names, and parameters
- Retrieving fields by current input position or field ID
- Removing fields while keeping or deleting visible text
- Clearing all fields after processing or flattening templates
- Resolving section/paragraph/subtextpart context for each field

### SubTextParts
- Creating named subtextparts from current selections
- Highlighting regions using `HighlightColor` and `HighlightMode`
- Handling insertion status via `SubTextPartCollection.AddResult`
- Retrieving subtextparts by input position, name, or ID
- Enumerating child and descendant regions with `GetChildren()`
- Removing regions with `keepText` and `keepNested` options
- Saving subtextpart content and persisting JSON metadata in `Data`

### Track Changes
- Loading tracked revisions from DOCX documents
- Enumerating changes by number, kind, user, start/length, and timestamp
- Filtering revisions by `UserName`, `ChangeKind`, and date range
- Navigating current/next/previous revisions using `GetItem(...)`
- Accepting or rejecting revisions with `TrackedChanges.Remove(change, accept)`
- Handling `TrackedChangeCreated` and `TrackedChangeDeleted` events
- Saving output while omitting tracked-change markup with `SaveSettings.OmittedContent`

### PDF Signing
- Digitally signing full PDF or PDF/A documents with `SaveSettings.DigitalSignature`
- Signing one or more named `SignatureField` elements using `SaveSettings.SignatureFields`
- Creating visible signature appearances with `SignatureImage`
- Adding signer metadata with `SignerData`
- Using PFX certificates on Linux and Windows server workloads
- Loading certificate material from Azure Key Vault for centralized secret handling

## How The Workflow Is Intended To Work

1. Identify whether your task involves data merging (MailMerge skill),
   table/document element manipulation (Tables skill), or image processing
   workflows (Images skill), or header/footer layout and numbering
   workflows (Header/Footer skill), or list formatting workflows
   (Lists skill), or merge-field/application-field workflows
   (ApplicationFields skill), or user-defined region workflows
   (SubTextParts skill), or revision-processing workflows
   (Track Changes skill), or PDF digital-signing workflows
   (PDF Signing skill).
2. Choose one reference task in `references/` based on your scenario.
3. Use only the verified API patterns from the reference files.

## Notes

- This skill set is based on code patterns from Text Control blog entries.
- Use only validated TX Text Control APIs from the reference files.
- Do not hardcode secrets or license keys in shared code.

## References

- TX Text Control Product Site: https://www.textcontrol.com/
- TableCollection Class: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.tablecollection.class.htm
- Table Class: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.table.class.htm
- ImageCollection Class: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.imagecollection.class.htm
- Image Class: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.image.class.htm
- HeaderFooterCollection Class: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.headerfootercollection.class.htm
- HeaderFooter Class: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.headerfooter.class.htm
- HeaderFooterType Enumeration: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.headerfootertype.enumeration.htm
- ListFormat Class: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listformat.class.htm
- ListType Enumeration: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.listtype.enumeration.htm
- NumberFormat Enumeration: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.numberformat.enumeration.htm
- ApplicationFieldCollection Class: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfieldcollection.class.htm
- ApplicationField Class: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfield.class.htm
- ApplicationFieldFormat Enumeration: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.applicationfieldformat.enumeration.htm
- SubTextPartCollection Class: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpartcollection.class.htm
- SubTextPart Class: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpart.class.htm
- ServerTextControl.SubTextParts Property: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.servertextcontrol.subtextparts.property.htm
- SubTextPartCollection.AddResult Enumeration: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.subtextpartcollection.addresult.enumeration.htm
- Tracking Document Changes Category: https://docs.textcontrol.com/textcontrol/asp-dotnet/cat.trackedchange.htm
- TrackedChangeCollection Class: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchangecollection.class.htm
- TrackedChange Class: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchange.class.htm
- ServerTextControl.TrackedChanges Property: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.servertextcontrol.trackedchanges.property.htm
- TrackedChangeCollection.Remove Method: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.trackedchangecollection.remove.method.htm
- SaveSettings.OmittedContent Property: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.savesettings.omittedcontent.property.htm
- SaveSettings.DigitalSignature Property: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.savesettings.digitalsignature.property.htm
- SaveSettings.SignatureFields Property: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.savesettings.signaturefields.property.htm
- DigitalSignature Class: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.digitalsignature.class.htm
- SignatureField Class: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.signaturefield.class.htm
- SignatureFieldCollection Class: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.signaturefieldcollection.class.htm
- SignatureImage Class: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.signatureimage.class.htm
- SignerData Class: https://docs.textcontrol.com/textcontrol/asp-dotnet/ref.txtextcontrol.signerdata.class.htm
- TX Text Control Blog: https://www.textcontrol.com/blog/
- Mail Merge DOCX to PDF (.NET C#): https://www.textcontrol.com/blog/2025/02/07/mail-merge-ms-word-docx-documents-and-convert-to-pdf-in-net-c-sharp/
- Merging Business Objects: https://www.textcontrol.com/blog/2024/12/27/merging-self-calculating-business-objects-with-tx-text-control-mailmerge-in-csharp/
- ASP.NET Reporting with XML: https://www.textcontrol.com/blog/2020/01/01/creating-your-first-aspnet-reporting-application/
- Skipping Records During Merge: https://www.textcontrol.com/blog/2025/02/10/mail-merge-skipping-records-during-the-merge-process-in-net-c-sharp/
- Merging Form Fields: https://www.textcontrol.com/blog/2022/02/21/merging-form-fields-using-the-mailmerge-class/
- Various Ways of Inserting Images: https://www.textcontrol.com/blog/2024/05/03/various-ways-of-inserting-images-into-tx-text-control/
- Different Ways to Insert Images: https://www.textcontrol.com/blog/2022/03/28/different-ways-to-insert-images/
- Working with Image Placeholders: https://www.textcontrol.com/blog/2022/12/22/mailmerge-working-with-image-placeholders/
- Extracting Images from Documents: https://www.textcontrol.com/blog/2024/06/11/extracting-images-from-ms-word-documents-in-csharp/
- Create Word Document with .NET C#: https://www.textcontrol.com/blog/2024/10/25/create-word-document-with-net-c-sharp/
- Create PDF File with .NET C#: https://www.textcontrol.com/blog/2024/10/17/create-pdf-file-with-net-c-sharp/
- Adding SVG Watermarks to Documents: https://www.textcontrol.com/blog/2022/01/28/adding-svg-watermarks-to-documents/
- Restart the Page Numbering Fields Per Section: https://www.textcontrol.com/blog/2013/11/08/restart-the-page-numbering-fields-per-section/
- Convert Plain Text to Bulleted Lists in C# with .NET: https://www.textcontrol.com/blog/2025/01/21/convert-plain-text-to-bulleted-lists-in-csharp-with-dotnet/
- Find ApplicationFields within Sections and Paragraphs in .NET C#: https://www.textcontrol.com/blog/2024/08/02/find-applicationfields-within-sections-and-paragraphs-in-net-c-sharp/
- Renaming Merge Blocks and Merge Fields Programmatically in C#: https://www.textcontrol.com/blog/2024/02/08/renaming-merge-blocks-and-merge-fields-programmatically-in-csharp/
- The Power of SubTextParts: Typical Use Cases: https://www.textcontrol.com/blog/2024/02/09/the-power-of-subtextparts-typical-use-cases/
- MailMerge: Rendering Conditional Table Rows: https://www.textcontrol.com/blog/2022/02/17/mailmerge-rendering-conditional-table-rows/
- Inspect and Process Track Changes in DOCX Documents with TX Text Control with .NET C#: https://www.textcontrol.com/blog/2026/03/10/inspect-and-process-track-changes-in-docx-documents-with-tx-text-control-with-dotnet-csharp/
- Adding Digital Signatures to PDF Documents in C#: https://www.textcontrol.com/blog/2022/11/29/adding-digital-signatures-to-pdf-documents-in-csharp/
- Signing a PDF Document vs. Signing Signature Fields in C#: https://www.textcontrol.com/blog/2024/10/08/signing-a-pdf-document-vs-signing-signature-fields-in-a-pdf-in-csharp/
- Sign PDF Documents with PFX Certificates on Linux: https://www.textcontrol.com/blog/2025/03/19/how-to-sign-pdf-documents-with-pfx-certificates-in-net-c-sharp-on-linux/
- Create Self-Signed Certificates on Windows to Sign PDFs: https://www.textcontrol.com/blog/2025/02/28/how-to-create-self-signed-certificates-on-windows-to-sign-pdfs-in-net-c-sharp/
- Sign PDF Documents with PFX Certificates from Azure Key Vault: https://www.textcontrol.com/blog/2025/01/07/sign-pdf-documents-with-pfx-certificates-from-azure-key-vault-in-net-c-sharp/
