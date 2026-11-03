# Security Policy

## Supported versions

| Version | Supported | Status |
| --- | --- | --- |
| 2.0.0-preview.1 | :white_check_mark: | Preview (not yet hardware-verified) |
| 0.1.0-rc.1 | :x: | Superseded — please upgrade; history is imported automatically |

## Security design (DiskLedger 2)

- **Single-PC by default.** DiskLedger does not listen on the network unless you explicitly turn on *Host the workshop*.
- **Workshop mode** uses HTTPS with a self-signed certificate that is pinned during pairing. The 24-character setup code contains part of the host's certificate fingerprint, so a computer joining the workshop verifies the host before revealing the one-time secret. Codes expire after 15 minutes; repeated wrong codes close pairing.
- **Every workshop request is authenticated** with a per-computer token (the host stores only a hash; members store it encrypted with Windows DPAPI). Access can be removed per computer.
- **Firewall:** DiskLedger only adds a Windows Firewall rule when you choose *Allow on private networks* (Windows asks for permission). The rule is limited to the DiskLedger program, its port and private networks, and is removed by the uninstaller.
- **Never expose the workshop port to the internet.** It is designed for your local network only.
- **Read-only towards drives:** DiskLedger only issues query commands; it never writes to, formats or resets a disk.
- **Privacy:** no telemetry, analytics or accounts. The only default outbound request is a daily release check against this repository (can be turned off). Logs never contain workshop codes or tokens.
- **Binaries are not code-signed yet.** Verify downloads against `SHA256SUMS.txt` from the release page.

## Reporting a vulnerability

Please do not publish exploit details. Open a GitHub issue asking for a private contact, or use the contact form on https://klowzy.com, and we will follow up.
