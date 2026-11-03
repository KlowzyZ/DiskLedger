# Changelog

All notable changes to DiskLedger are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.0.0-preview.1] - 2026-11-03

**Preview — not yet verified on real workshop hardware.**

DiskLedger 2 is a complete rebuild.

### Changed
- One Windows application (`DiskLedger.exe`) replaces DiskLedger Agent, Server and Desktop. No services, scripts, server, database or .NET installation required; installs per user without administrator rights.
- Works on a single PC out of the box. Workshop (multi-PC) mode is optional and set up from inside the app with a setup code; all workshop traffic is encrypted and authenticated.
- Reads drives directly through Windows (identity, interface, type, Windows health; SMART and NVMe health with full access). Hard Disk Sentinel Professional is now optional.
- New interface: Dashboard, Drives, Drive details with trends and timeline, History search, Computers, Settings. English, Turkish and Arabic.
- Official KLOWZY DiskLedger icon.

### Added
- Installer (`…-Setup.exe`) and portable ZIP; automatic import of 0.1 history; daily backups; CSV/JSON export; `--probe` hardware report.

### Removed
- The 0.1 Agent/Server Windows services, PowerShell deployment scripts and the unauthenticated v1 LAN API.

## [0.1.0-rc.1] - 2026-09-03

### Release Candidate 1 — Initial Pre-Release Distribution
*Note: This is a pre-release candidate intended for shop hardware verification.*

### Added
- **Centralized Versioning & Metadata**: Solution-wide `Directory.Build.props` establishing `0.1.0-rc.1`, KLOWZY publisher identity, and proprietary copyright notice.
- **Cryptographic First-Run Server Authentication**: Server automatically generates 256-bit secure API key on first startup and persists in `%ProgramData%\DiskLedger\Server\server_auth.json`. Universal default shop keys eliminated from production builds.
- **Standardized Machine Data Locations**: Standardized runtime storage across `%ProgramData%\DiskLedger\Server`, `%ProgramData%\DiskLedger\Agent`, `%ProgramData%\DiskLedger\Logs`, and `%LocalAppData%\DiskLedger\Desktop`.
- **Windows Service Automation**: Full Windows Service lifecycle support for both `DiskLedger.Server` and `DiskLedger.Agent`. Included administrative deployment scripts:
  - `Install-Server.ps1`, `Uninstall-Server.ps1`, `Start-Server.ps1`, `Stop-Server.ps1`, `Restart-Server.ps1`
  - `Install-Agent.ps1`, `Uninstall-Agent.ps1`, `Start-Agent.ps1`, `Stop-Agent.ps1`, `Restart-Agent.ps1`
  - `Configure-Firewall.ps1`, `Remove-Firewall-Rule.ps1`
- **Agent Provisioning Suite**: `Export-Agent-Setup.ps1` on the server and `Configure-Agent.ps1` on client PCs with DPAPI `LocalMachine` credential protection.
- **Sentinel Preflight Diagnostic Tool**: `Sentinel-Check.ps1` verifying `root\wmi:HDSentinel` accessibility for registered Hard Disk Sentinel Professional with colored drive metrics and diagnostic instructions.
- **Desktop Release & Update Checker**:
  - SemanticVersion parser conforming to SemVer 2.0.0 with pre-release precedence.
  - Non-blocking background daily update checking against public GitHub releases (`KlowzyZ/DiskLedger`).
  - Settings UI controls for manual checks, automatic checks, pre-release channel toggle, and direct browser release link.
- **Comprehensive Automated Test Suite**: Expanded test suite to 75 automated unit and integration tests (67 unit, 8 integration), validating concurrency, out-of-order merging, crash recovery, and update checking.

### Fixed
- Fixed midnight calendar date rollover in `DriveMonitoringCoordinator`.
- Fixed out-of-order packet health merging regression in `DailyDiskTestRecord` and `DriveHistoryService`.
- Fixed crash recovery for in-flight unacknowledged items in SQLite sync queue.
- Replaced universal hardcoded secrets with cryptographic machine-level storage.
