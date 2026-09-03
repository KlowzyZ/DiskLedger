# DiskLedger

**Automatic HDD & SSD Health History for Windows Repair and Refurbishing Environments.**

DiskLedger automatically maintains a persistent historical ledger of every physical hard drive and solid-state drive tested across multiple Windows PCs in a workshop.

> **The Core Question DiskLedger Answers:**  
> *"Have we seen this physical drive before, and what was its health the last time we tested it?"*

Technicians require zero manual interaction:
1. Connect a drive.
2. Use Hard Disk Sentinel normally.
3. Disconnect the drive.
4. Walk away.

DiskLedger automatically records, persists, and synchronizes the drive's health history across the shop network.

---

## ⚠️ Important Notice & Legal Disclaimer

- **DiskLedger is independent proprietary software published by KLOWZY. All rights reserved.**
- **DiskLedger is NOT affiliated with, sponsored by, or endorsed by Hard Disk Sentinel.**
- **Hard Disk Sentinel is NOT included** with DiskLedger. Users must supply their own registered copy of Hard Disk Sentinel Professional.
- **Hard Disk Sentinel WMI integration requires a registered Hard Disk Sentinel Professional edition** (Standard edition does not provide WMI support).
- The Hard Disk Sentinel Professional WMI status option must be explicitly enabled (see setup instructions below).
- **DiskLedger does not recreate, calculate, or reverse-engineer Hard Disk Sentinel's proprietary health assessment algorithms.**
- All health percentages displayed as Sentinel Health originate directly from Hard Disk Sentinel via its documented WMI interface.
- All product and company names, logos, and trademarks are the property of their respective owners.

---

## Key Features

- **Zero-Touch Automated History**: Automatically creates a persistent daily history row for each physical drive tested.
- **Strict Same-Day Invariant**: Multiple connects, disconnects, and reconnects on the same day update the same daily record without cluttering history.
- **In-Test Health Tracking**: Captures in-test health degradation (e.g. 88% down to 71%) and records the true final and lowest health automatically.
- **Crash-Safe Local Persistence**: Writes immediately to local SQLite (`diskledger_agent.db`) via EF Core upon connection or health change. A sudden power loss or reboot does not destroy the day's record.
- **Offline-First Resilience**: If the central LAN server is offline, agents continue monitoring locally and queue updates. The queue automatically synchronizes with exponential backoff once the server returns.
- **Idempotent Central LAN Server**: ASP.NET Core Web API with central SQLite storage and database unique constraint on `(NormalizedSerial, TestDate)`. Retries and duplicate sync batches never create duplicate records.
- **Multi-PC Shop Roaming**: A drive tested on `TEST-PC-01` today will display its prior history when tested on `TEST-PC-04` months later.
- **Modern Dark WPF Desktop UI**:
  - **Live Dashboard**: Real-time connected disk cards, degradation indicators, and simulation controls.
  - **Central Known Drives**: Filterable and sortable registry of all tested drives.
  - **Drive History Timeline**: Date-by-date health progression, test computer name, and health difference from prior tests.
  - **Fast Search**: Instant search by full serial, trailing digits (e.g. last 4 digits), or model.
  - **Shop Test Computers**: Real-time status and heartbeats of all shop testing PCs.
  - **Settings & Diagnostics**: Server connectivity test, Sentinel WMI configuration checker, and release update checking.
- **No Cloud, No Telemetry**: 100% local, self-hosted, privacy-respecting LAN architecture.

---

## Enabling Hard Disk Sentinel WMI Integration

To allow DiskLedger to receive health status from Hard Disk Sentinel:

1. Open registered **Hard Disk Sentinel Professional** (WMI integration requires Professional edition; Standard edition is not supported).
2. Navigate to: **Configuration** -> **Advanced Options**.
3. Check the box: **"Provide status information by WMI"**.
4. Click **OK** to apply.
5. Ensure Hard Disk Sentinel Professional remains running (or configured to start automatically with Windows).

---

## Download & Installation

DiskLedger is distributed as pre-compiled, self-contained Windows (win-x64) packages. You do **not** need Visual Studio or the .NET SDK installed on shop PCs.

1. Download the latest release package from GitHub Releases:  
   **[Download DiskLedger-v0.1.0-rc.1-win-x64.zip](https://github.com/KlowzyZ/DiskLedger/releases/tag/v0.1.0-rc.1)**
2. Extract the ZIP archive onto your designated Server PC and Client test PCs.
3. Follow the included **`README-FIRST.txt`** and **`FIRST-TEST-CHECKLIST.md`** guides to complete LAN setup in under 5 minutes.

---

## Security & Privacy

DiskLedger operates 100% on your local shop network. It transmits no telemetry, no analytics, and no drive metrics outside your LAN.
See [SECURITY.md](SECURITY.md) for vulnerability reporting and LAN boundary guidelines.

---

## License

Copyright © 2026 KLOWZY. All rights reserved.  
DiskLedger is proprietary software. Unauthorized copying, modification, reverse engineering, redistribution, or publication of the source code is strictly prohibited.  
Binary distribution is permitted only in accordance with the official release terms provided by KLOWZY. See [LICENSE.txt](LICENSE.txt).
