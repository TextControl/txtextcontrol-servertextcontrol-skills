# Sign PDF with Azure Key Vault Certificate

## Goal

Retrieve certificate data from Azure Key Vault and use it to digitally sign
PDF output with ServerTextControl.

## Source

- https://www.textcontrol.com/blog/2025/01/07/sign-pdf-documents-with-pfx-certificates-from-azure-key-vault-in-net-c-sharp/

## Required NuGet Packages

- `Azure.Identity`
- `Azure.Security.KeyVault.Certificates`
- `TXTextControl.TextControl.ASP.SDK`

## Retrieve Certificate and Sign PDF

```csharp
using System;
using System.Security.Cryptography.X509Certificates;
using Azure.Identity;
using Azure.Security.KeyVault.Certificates;
using TXTextControl;

string keyVaultUrl = "https://txtestvault.vault.azure.net/";
string certificateName = "txselfcert";

var credential = new DefaultAzureCredential(true);
var client = new CertificateClient(new Uri(keyVaultUrl), credential);

var certificateWithPolicy = client.GetCertificate(certificateName);
byte[] certificateBytes = certificateWithPolicy.Value.Cer;

var cert = new X509Certificate2(
    certificateBytes,
    (string)null,
    X509KeyStorageFlags.PersistKeySet);

using (var tx = new ServerTextControl())
{
    tx.Create();
    tx.Text = "Hello, World!";

    var saveSettings = new SaveSettings
    {
        DigitalSignature = new DigitalSignature(cert, null)
    };

    tx.Save("result.pdf", StreamType.AdobePDF, saveSettings);
}
```

## Notes

- Keep credentials and tenant configuration in secure environment settings.
- Use managed identities where possible instead of local developer credentials.
- Validate that the retrieved certificate includes required key material for signing.
