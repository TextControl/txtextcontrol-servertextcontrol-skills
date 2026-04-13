# Sign Complete PDF Document with DigitalSignature

## Goal

Digitally sign the complete PDF output using one X.509 certificate through
`SaveSettings.DigitalSignature`.

## Source

- https://www.textcontrol.com/blog/2022/11/29/adding-digital-signatures-to-pdf-documents-in-csharp/
- https://www.textcontrol.com/blog/2024/10/08/signing-a-pdf-document-vs-signing-signature-fields-in-a-pdf-in-csharp/

## Sign Full PDF During Save

```csharp
using System.Security.Cryptography.X509Certificates;
using TXTextControl;

public static void SignDocument()
{
    using (ServerTextControl tx = new ServerTextControl())
    {
        tx.Create();
        tx.Text = "This is a signed document";

        SaveSettings saveSettings = new SaveSettings
        {
            DigitalSignature = new DigitalSignature(
                new X509Certificate2("textcontrolself.pfx", "123"),
                null)
        };

        tx.Save("signed_document.pdf", StreamType.AdobePDF, saveSettings);
    }
}
```

## Notes

- `SaveSettings.DigitalSignature` signs the entire generated PDF file.
- This server-side workflow is preferred to avoid exposing private keys.
- For production, load certificates from secure stores and never hardcode passwords.
