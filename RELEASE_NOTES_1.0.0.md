# Server Seeder 1.0.0

Publisher: GH-Experiments

Server Seeder is a free Windows companion program that automates game-server seeding. At the time you schedule, it starts Squad, joins your selected server, waits for players to arrive, then closes Squad and restores your original game settings.

Server Seeder is proprietary software, free to use under its End User License Agreement (EULA). You may not redistribute, mirror or repackage it. The EULA is shown during interactive installation, and the EULA and the third-party software notices are also installed with the program.

## Download

| | |
|---|---|
| File | `ServerSeeder-Setup-1.0.0.exe` |
| Size | 27,510,704 bytes |
| SHA-256 | `13A466E19FA622CD48CD34899BDB14B02E2F8E8B074322632BCBD458A48A9A05` |

Download only from the official Releases page: <https://github.com/OG-GunnyHighway/Server-Seeder/releases>

## Main features

- Scheduled, unattended seeding sessions on the days and 24-hour times you choose, with optional wake-from-sleep.
- Automatically launches Squad and joins your selected server.
- Monitors the server's player count during the session.
- Choose how many players to leave the server at and the longest a session may run. A session ends when the player count is confirmed at your threshold, or when the maximum duration is reached.
- Closes Squad at the end of a session, then restores your original Squad settings.
- A Dashboard showing your configuration, next run, latest session and any warning.
- Built-in quick-start instructions.

## Requirements

- 64-bit Windows 10 or 11 (no administrator rights needed).
- Steam installed and signed in, and Squad installed.
- Windows signed in and unlocked, with the desktop available, at the scheduled time.
- A Windows text-recognition language pack (English recommended and tested).
- An internet connection during a session.

## Supported servers

Squad is the only supported game, and **Unnamed #1** is the only server available for seeding in this release. You cannot add your own server.

## Installation

Download the installer from the official Releases page only, run it and accept the EULA. It installs for your Windows account. Then open Settings, choose your server and seeding options, click Save, and Activate a schedule. Full steps are in the User Guide.

**Windows security warning.** The 1.0.0 installer is not code-signed, so Windows may show "Windows protected your PC" (SmartScreen) or an unverified-publisher warning. To check your download, run `Get-FileHash .\ServerSeeder-Setup-1.0.0.exe -Algorithm SHA256` in PowerShell and compare the result with the SHA-256 above. A matching checksum shows your file is the published one; it does not by itself prove the file is safe, so use only the official Releases page. If you trust the source and the checksum matches, choose More info, then Run anyway. You should not need to disable any Windows security protection. The User Guide explains these steps in more detail.

## Updating

Server Seeder does not check for or install updates automatically. To update, download the new installer from the official Releases page and run it. Open Server Seeder afterwards and confirm your schedule is still ACTIVE.

## Uninstalling and reinstalling

Uninstall Server Seeder from Windows Settings > Apps > Installed apps. The uninstaller asks whether to also remove the scheduled seeding task. Your saved settings, schedule information, settings backups and logs are kept in `%LOCALAPPDATA%\ServerSeeder`, so a later reinstall can use them. Reinstalling does not recreate a scheduled task that was removed. After reinstalling, open Settings, check the schedule status, and click Activate to turn your saved schedule on again.

## Privacy

Settings, schedules and logs stay on your PC. Server Seeder needs an internet connection during a session to check the server's player count. It has no telemetry and does not upload logs, diagnostics or crash reports.

## Known limitations

- Windows only; Squad is the only game; Unnamed #1 is the only server.
- Sessions cannot run while Windows is locked, signed out or asleep (use the wake option for sleep), and you should not use the mouse or keyboard during a session.
- Server Seeder controls Squad's menus at a 1024 x 768 layout and reads them with Windows text recognition. It relies on Squad's current menu design.
- If a session is interrupted unexpectedly (such as a power loss), automatic settings restoration cannot be guaranteed; Dashboard warns you when settings are waiting to be restored.
- A session that ends because the maximum duration expired is reported as unsuccessful, even though your settings are restored.
- Reinstalling keeps your settings. After reinstalling, check the schedule status in Settings; if the scheduled task was removed during uninstall, click Activate again.
- No Start button: sessions begin on schedule only.

## Support

Report problems through GitHub Issues: <https://github.com/OG-GunnyHighway/Server-Seeder/issues>. Include your version (shown on the About page), your Windows version and what happened. Nothing is uploaded automatically.

See the User Guide for installation, troubleshooting, disabling the schedule and uninstalling.
