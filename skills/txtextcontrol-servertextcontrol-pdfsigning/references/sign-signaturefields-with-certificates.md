# Sign SignatureFields with Certificates

## Goal

Create one or more named `SignatureField` elements, associate each with a
certificate-backed `DigitalSignature`, and export a signed PDF.

## Source

- https://www.textcontrol.com/blog/2022/11/29/adding-digital-signatures-to-pdf-documents-in-csharp/
- https://www.textcontrol.com/blog/2024/10/08/signing-a-pdf-document-vs-signing-signature-fields-in-a-pdf-in-csharp/

## Add Signature Field and Sign It

```csharp
using System.Drawing;
using System.Security.Cryptography.X509Certificates;
using TXTextControl;

public static void SignFields()
{
    using (ServerTextControl tx = new ServerTextControl())
    {
        tx.Create();

        SignatureField signatureField = new SignatureField(
            new Size(2000, 2000),
            "txsign",
            10)
        {
            Image = new SignatureImage("signature.svg", 0),
            SignerData = new SignerData(
                "Tim Typer",
                "Developer",
                "5652 Text Control Dr",
                "tim@textcontrol.com",
                "Contract signature")
        };

        tx.SignatureFields.Add(signatureField, -1);

        DigitalSignature digitalSignature = new DigitalSignature(
            new X509Certificate2("textcontrolself.pfx", "123", X509KeyStorageFlags.Exportable),
            null,
            "txsign");

        SaveSettings saveSettings = new SaveSettings
        {
            SignatureFields = new DigitalSignature[] { digitalSignature }
        };

        tx.Save("signed_fields.pdf", StreamType.AdobePDF, saveSettings);
    }
}
```

## Notes

- The third `DigitalSignature` constructor parameter is the target field name.
- Use one `DigitalSignature` per field for multi-signer or staged signing flows.
- Signature fields provide visible signature UI in PDF viewers.
