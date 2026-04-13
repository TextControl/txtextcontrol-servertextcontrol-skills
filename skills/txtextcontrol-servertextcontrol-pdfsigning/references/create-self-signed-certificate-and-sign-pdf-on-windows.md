# Create Self-Signed Certificate and Sign PDF on Windows

## Goal

Generate a self-signed certificate using PowerShell, export it as `.pfx`, and
use it to digitally sign a PDF.

## Source

- https://www.textcontrol.com/blog/2025/02/28/how-to-create-self-signed-certificates-on-windows-to-sign-pdfs-in-net-c-sharp/

## Create and Export Certificate in PowerShell

```powershell
$cert = New-SelfSignedCertificate `
  -Subject "CN=MyTXCert" `
  -CertStoreLocation "Cert:\CurrentUser\My" `
  -KeyExportPolicy Exportable `
  -KeySpec Signature `
  -FriendlyName "My PDF Signing Certificate" `
  -NotAfter (Get-Date).AddYears(5)

$Password = ConvertTo-SecureString -String "123" -Force -AsPlainText

Export-PfxCertificate `
  -Cert "Cert:\CurrentUser\My\$($cert.Thumbprint)" `
  -FilePath "C:\Path\To\Certificate.pfx" `
  -Password $Password
```

## Sign PDF Using Exported PFX

```csharp
using System.Security.Cryptography.X509Certificates;
using TXTextControl;

const string password = "123";
const string certificatePath = "certificate.pfx";

var cert = new X509Certificate2(
    certificatePath,
    password,
    X509KeyStorageFlags.Exportable);

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

- Self-signed certificates are useful for local testing and internal workflows.
- Use CA-issued certificates for external/legal production scenarios.
- Store PFX passwords securely and avoid plain-text secrets in source control.
