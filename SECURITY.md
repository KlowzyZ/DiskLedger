# Security Policy

## Supported Versions

| Version      | Supported          | Status             |
| ------------ | ------------------ | ------------------ |
| 0.1.0-rc.1   | :white_check_mark: | Release Candidate  |

## Security Architecture for LAN Deployments

DiskLedger is built for secure, air-gapped or internal trusted local area networks (LAN) in repair and refurbishment environments.

- **Cryptographic First-Run Key**: Mutating API endpoints (`POST /api/v1/sync` and `POST /api/v1/agents/register`) require an API key generated using `System.Security.Cryptography.RandomNumberGenerator` (256-bit entropy).
- **DPAPI Credential Protection**: On agent machines, credentials stored in `%ProgramData%\DiskLedger\Agent\agent_settings.json` are encrypted using Windows Data Protection API (DPAPI `LocalMachine` scope).
- **Network Boundaries**: DiskLedger Server listens on TCP port `5050` by default. The port should remain strictly within the private shop subnet. Never expose port 5050 to the public internet without an authenticating reverse proxy with TLS.
- **Privacy Guarantee**: DiskLedger operates 100% locally. It contains **zero telemetry, zero analytics, and zero external cloud communication**. The only outgoing HTTP traffic is the optional, user-controlled update check against public GitHub release metadata.

## Reporting a Vulnerability

If you discover a potential security vulnerability within DiskLedger, please do not disclose sensitive reproduction details publicly.
For this release candidate (RC1), please report concerns via the public repository's GitHub Issues page (requesting private contact), or hold disclosure until dedicated security contact channels are published with general availability. Reported issues will be acknowledged promptly and addressed in forthcoming releases.
