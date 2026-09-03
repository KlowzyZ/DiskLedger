<h1 align="center">DiskLedger</h1>

<p align="center">
  <strong>Automatic HDD &amp; SSD health history across your Windows test PCs</strong><br>
  <sub>Published by <strong>KLOWZY</strong></sub>
</p>

<p align="center">
  <img alt="Windows 10 and 11 x64" src="https://img.shields.io/badge/Windows-10%20%7C%2011%20x64-0078D4?style=flat-square&amp;logo=windows&amp;logoColor=white">
  <a href="https://github.com/KlowzyZ/DiskLedger/releases/tag/v0.1.0-rc.1"><img alt="Version v0.1.0-rc.1" src="https://img.shields.io/badge/version-v0.1.0--rc.1-2563EB?style=flat-square"></a>
  <img alt="Pre-release" src="https://img.shields.io/badge/status-pre--release-F59E0B?style=flat-square">
  <img alt="Proprietary license" src="https://img.shields.io/badge/license-proprietary-334155?style=flat-square">
</p>

<p align="center">
  <a href="https://github.com/KlowzyZ/DiskLedger/releases/tag/v0.1.0-rc.1"><img alt="Download DiskLedger RC1" src="https://img.shields.io/badge/Download-DiskLedger%20RC1-16A34A?style=for-the-badge&amp;logo=github"></a><br>
  <sub><strong>v0.1.0-rc.1</strong> · Release Candidate / Pre-release · Windows x64</sub>
</p>

---

## What is DiskLedger?

DiskLedger maintains a persistent health history for the physical HDDs and SSDs tested across multiple Windows PCs in a repair or refurbishing shop. A drive is identified by serial number, so technicians can reconnect it later and see whether it has been tested before—and how its health has changed.

Hard Disk Sentinel Professional supplies the drive status. DiskLedger records daily results, keeps working when the LAN server is temporarily unavailable, and brings the history together in one searchable desktop view.

## Key features

| | Capability | | Capability |
|---|---|---|---|
| **Automatic monitoring** | Detects connected drives and builds health history without manual record entry. | **Serial identity** | Tracks the physical drive by serial number across test PCs. |
| **Daily records** | Maintains a daily health record for each drive. | **Reconnect merging** | Merges same-day reconnects into the existing daily record. |
| **Multi-PC workflow** | Supports multiple Windows test PCs in one shop. | **Central LAN history** | Synchronizes drive history to a central server on the local network. |
| **Offline queue** | Agents queue records locally and synchronize when the server is available again. | **Search & timeline** | Finds drives and presents their recorded health history over time. |
| **Background services** | Agent and Server components run as Windows background services. | **Update checks** | Supports manual and automatic background checks for new releases. |

## How it works

<p align="center">
  <strong>Drive</strong> &nbsp;→&nbsp; <strong>Hard Disk Sentinel Professional</strong> &nbsp;→&nbsp; <strong>DiskLedger Agent</strong> &nbsp;→&nbsp; <strong>DiskLedger Server</strong> &nbsp;→&nbsp; <strong>DiskLedger Desktop</strong>
</p>

| Component | Role |
|---|---|
| **DiskLedger Agent** | Runs on each test PC, reads Sentinel status through WMI, and queues health records for synchronization. |
| **DiskLedger Server** | Centralizes synchronized drive history for the local network. |
| **DiskLedger Desktop** | Provides the main view for connected drives, search, history timelines, settings, and update checks. |

## Requirements

| Requirement | Details |
|---|---|
| **Operating system** | Windows 10 or Windows 11, x64 |
| **Drive-health provider** | A registered installation of **Hard Disk Sentinel Professional** on each test PC |
| **Sentinel setting** | **Configuration → Advanced Options → Provide status information by WMI** must be enabled |
| **Network** | LAN connectivity between the machines running DiskLedger components |

> [!IMPORTANT]
> Hard Disk Sentinel Professional is **not bundled** with DiskLedger. The current integration requires the registered Professional edition with WMI status enabled.

## Quick start

1. **Download [DiskLedger v0.1.0-rc.1](https://github.com/KlowzyZ/DiskLedger/releases/tag/v0.1.0-rc.1)** and extract the Windows x64 package.
2. On the **main PC**, set up **DiskLedger Server + DiskLedger Desktop** using the guides included in the package.
3. On each **test PC**, run a registered **Hard Disk Sentinel Professional** installation with WMI status enabled, then set up the **DiskLedger Agent**.
4. Keep the DiskLedger machines connected to the same LAN so queued Agent records can synchronize with the Server and appear in Desktop.

## Screenshots

Screenshots are coming after RC hardware validation.

## RC1 validation status

> [!NOTE]
> **v0.1.0-rc.1 is a pre-release intended for initial real-world shop hardware validation.** Broad validation across physical drive models and USB enclosures is still in progress.

## Updates

| Check type | RC1 behavior |
|---|---|
| **Manual** | Check for releases from DiskLedger Desktop settings. |
| **Automatic** | Non-blocking background checks can notify you when a newer release is available. |
| **Download & installation** | RC1 does not automatically download or install updates. |

## Privacy and networking

DiskLedger is designed for a local shop network. Its Agent, Server, and Desktop components operate across your LAN, and no DiskLedger cloud account is required. Release checks use the public GitHub release information for this repository.

For deployment boundaries and vulnerability reporting, see the [Security Policy](SECURITY.md).

## Hard Disk Sentinel disclaimer

DiskLedger is independent software by **KLOWZY** and is not affiliated with or endorsed by Hard Disk Sentinel. Hard Disk Sentinel is not included. Product names and trademarks belong to their respective owners.

## License

DiskLedger is proprietary software. See [LICENSE.txt](LICENSE.txt) for the distribution terms.

Copyright © 2026 KLOWZY. All rights reserved.

## Support and issues

Found a problem during RC validation? [Open an issue](https://github.com/KlowzyZ/DiskLedger/issues) with the relevant environment and reproduction details.
