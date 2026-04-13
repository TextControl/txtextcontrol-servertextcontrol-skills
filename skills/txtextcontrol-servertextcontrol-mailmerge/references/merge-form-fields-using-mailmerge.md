# Merge Form Fields Using MailMerge

## Goal

Merge object data into form fields and choose between preselection and flattening.

## Source

- https://www.textcontrol.com/blog/2022/02/21/merging-form-fields-using-the-mailmerge-class/

## Pre-Populate Form Fields

```csharp
HealthcareForm data = new HealthcareForm() {
  insurance_date = DateTime.Now,
  insurance_name = "Global Health",
  insurance_check = true,
  insurance_state = "North Carolina",
  notes = "Thanks for your business."
};

using (TXTextControl.ServerTextControl tx = new TXTextControl.ServerTextControl()) {
  tx.Create();
  tx.Load("App_Data/health_form.tx", TXTextControl.StreamType.InternalUnicodeFormat);

  using (TXTextControl.DocumentServer.MailMerge mm = new TXTextControl.DocumentServer.MailMerge()) {
    mm.TextComponent = tx;
    mm.FormFieldMergeType = TXTextControl.DocumentServer.FormFieldMergeType.Preselect;
    mm.MergeObject(data);
  }

  byte[] document;
  tx.Save(out document, TXTextControl.BinaryStreamType.AdobePDF);
}
```

## Flatten Form Fields

```csharp
HealthcareForm data = new HealthcareForm() {
  insurance_date = new DateTime(2020,1,1),
  insurance_name = "Health Providers",
  insurance_check = true,
  insurance_state = "Georgia",
  notes = "Thanks for your business."
};

using (TXTextControl.ServerTextControl tx = new TXTextControl.ServerTextControl()) {
  tx.Create();
  tx.Load("App_Data/health_form.tx", TXTextControl.StreamType.InternalUnicodeFormat);

  using (TXTextControl.DocumentServer.MailMerge mm = new TXTextControl.DocumentServer.MailMerge()) {
    mm.TextComponent = tx;
    mm.FormFieldMergeType = TXTextControl.DocumentServer.FormFieldMergeType.Replace;
    mm.MergeObject(data);
  }

  byte[] document;
  tx.Save(out document, TXTextControl.BinaryStreamType.AdobePDF);
}
```

## Notes

- `Preselect` keeps form fields editable with initial values.
- `Replace` flattens form fields to static content.
