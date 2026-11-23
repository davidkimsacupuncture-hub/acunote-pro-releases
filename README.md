# AcuNote Pro — desktop releases

This public repository only **distributes** AcuNote Pro desktop installers and the signed update feed. It contains no source code and **never contains patient data**.

Installed copies of AcuNote Pro check `releases/latest/download/latest.json` here for updates. They install only after the practice owner confirms.

## Download
Open the [latest release](../../releases/latest) and pick the installer for your computer:

| Computer | File |
|---|---|
| Windows 10/11 | `AcuNote-Pro_<version>_x64-setup.exe` (or the `.msi`) |
| macOS 10.15+ (Apple Silicon and Intel) | `AcuNote-Pro_<version>_universal.dmg` |
| Linux | `.AppImage`, `.deb` or `.rpm` |

## Verify a download
Every release includes `SHA256SUMS.txt`.

On macOS or Linux:

```bash
shasum -a 256 -c SHA256SUMS.txt --ignore-missing
```

On Windows (PowerShell), compare the result with the line for that file in `SHA256SUMS.txt`:

```powershell
Get-FileHash .\AcuNote-Pro_*_x64-setup.exe -Algorithm SHA256
```

Installers are code-signed once signing is configured. Check the publisher in the file's Properties (Windows) or with `spctl -a -vv` (macOS).

## Update security
- Each update package (`.app.tar.gz`, `-setup.exe`, `.AppImage`) has a `.sig` file: an Ed25519 signature made with the AcuNote updater key. The app verifies it against the public key built into the app before installing anything; altered packages are rejected.
- Releases here are published automatically by the AcuNote Pro build pipeline after the owner approves a release. Signatures are re-verified before and after publishing.
- Update checks download `latest.json` and the package only. No patient information or usage data is sent.

Questions or security reports: contact the practice that provided your installation.
