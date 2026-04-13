# Sign PDF with PFX Certificate on Linux

## Goal

Use a Linux-generated PFX certificate and sign a PDF document created with
ServerTextControl.

## Source

- https://www.textcontrol.com/blog/2025/03/19/how-to-sign-pdf-documents-with-pfx-certificates-in-net-c-sharp-on-linux/

## Create PFX Certificate with OpenSSL

```bash
openssl req -new -newkey rsa:2048 -nodes -keyout my_private.key -out my_request.csr
openssl x509 -req -days 365 -in my_request.csr -signkey my_private.key -out my_certificate.crt
openssl pkcs12 -export -out my_certificate.pfx -inkey my_private.key -in my_certificate.crt
```

## Load Certificate and Sign PDF

```csharp
using System.Security.Cryptography.X509Certificates;
using TXTextControl;

var cert = new X509Certificate2(
    "my_certificate.pfx",
    "123123123",
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

- TX Text Control .NET Server supports PDF signing on Linux and Windows.
- Ensure the `.pfx` file is available at runtime in your container or host.
- Protect certificate files and passwords using environment-specific secret storage.
