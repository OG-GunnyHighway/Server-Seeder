# Server Seeder User Guide

Version 1.0.0 · Publisher: GH-Experiments

## 1. Introduction

Server Seeder is a free Windows program that helps populate a game server for you. At a time you choose, it starts Squad, joins your selected server, waits until enough players have arrived, then closes Squad and puts your original game settings back.

Server Seeder is a separate companion program, not a Squad mod. It is proprietary software, free to use under its End User License Agreement (EULA). You may not redistribute it.

Squad is the only supported game in this version.

## 2. System requirements

- 64-bit Windows 10 or Windows 11.
- Steam installed and signed in to your account.
- Squad installed through Steam.
- An internet connection during a seeding session.
- Windows' built-in text recognition. Server Seeder reads Squad's menus on screen, so Windows needs a text-recognition language pack. An English language pack is the tested setup and is recommended.
- A display that can show Squad at 1024 x 768. Server Seeder sets this temporarily and restores your own resolution afterwards.
- Windows signed in and **unlocked** at the scheduled time (see section 7).

No administrator rights are needed.

## 3. Installation

1. Download `ServerSeeder-Setup-1.0.0.exe` from the official Server Seeder GitHub Releases page only: <https://github.com/OG-GunnyHighway/Server-Seeder/releases>. Do not use copies from other sites.
2. Run it and accept the EULA when asked. Server Seeder installs for your Windows account only, in a fixed folder (`%LOCALAPPDATA%\Programs\ServerSeeder`). You cannot choose another folder.
3. Open **Server Seeder** from the Start menu.

**Verify your download.** Each release lists a SHA-256 checksum for the installer. To check your copy, open PowerShell in the folder that contains the file and run:

```powershell
Get-FileHash .\ServerSeeder-Setup-1.0.0.exe -Algorithm SHA256
```

Compare the `Hash` value it shows with the SHA-256 on the official Releases page. For version 1.0.0 it should be:

```
13A466E19FA622CD48CD34899BDB14B02E2F8E8B074322632BCBD458A48A9A05
```

If the values differ, do not run the installer; download it again from the official page. A matching checksum shows that your file is the one published on that page. It does not by itself prove the file is safe, so also make sure you got it from the official Releases page.

**Windows security warning.** The installer is not code-signed, so Windows may show "Windows protected your PC" (SmartScreen) or describe the publisher as unverified or unknown. This is expected for unsigned software. If you downloaded the file from the official Releases page and the checksum matches, you can choose **More info** and then **Run anyway** if you trust the source. If anything does not match or you are unsure, do not run it. You should not need to turn off Windows Defender, SmartScreen, antivirus or any other security feature.

The installer places a copy of the EULA and the third-party notices in the install folder.

## 4. Initial setup

Opening Server Seeder does not start anything and changes nothing on its own. The first time, Dashboard asks you to open **Settings**.

1. On Dashboard, click **Settings**.
2. Choose the **Game** and the **Server** (see section 5).
3. Set **Leave server at** and **Maximum seeding duration** (see section 6).
4. Click **Save**.
5. Set up the schedule (see section 7).

Saving settings does not start a session and does not turn on the schedule.

## 5. Choosing a supported server

The **Server** list shows only the servers Server Seeder can currently seed. In this version that is **Unnamed #1**. Other servers are not available, and you cannot add your own server.

## 6. Configuring seeding behavior

- **Leave server at** – the number of players at which Server Seeder treats the server as seeded. When the server's player count reaches this number, Server Seeder closes Squad and ends the session. The count must be confirmed by more than one check in a row, so Server Seeder may stay a little longer than the moment the number is first reached.
- **Maximum seeding duration** – the longest a session may run. If the player count has not reached your number by then, Server Seeder still closes Squad and ends the session. Such a session is reported as unsuccessful, because the target was not reached, even though your settings are restored.

Changes apply to the next session, not one already running.

## 7. Scheduling sessions

Sessions run only on a schedule. There is no Start button.

In **Settings**, under **Scheduler**:

1. **Schedule time** – enter the start time in 24-hour format, for example `07:30` or `21:15`.
2. **Days** – tick the days of the week to run.
3. Optional: **Wake the computer if asleep**, so your PC wakes up for the session.
4. Optional: **Run as soon as possible if a start time is missed**, so a session starts when the PC is next available if it was off at the scheduled time.
5. Click **Activate**. To change an active schedule, edit it and click **Update Schedule**.

The **Status** line shows ACTIVE, DEACTIVATED, ATTENTION (the saved schedule and the Windows task disagree) or UNKNOWN (the status could not be checked). Dashboard shows the next run.

Once the schedule is active, sessions start by themselves, even when the Server Seeder window is closed. For a session to work:

- Windows must be signed in with the screen **unlocked** and the desktop available. Server Seeder works by controlling Squad's menus, so a locked screen, a sign-out or a sleeping PC will stop it. Use the wake option if your PC may be asleep.
- Steam must be running and signed in. Close any Steam or Easy Anti-Cheat pop-up windows; a session cannot start while one is open.
- Squad must not already be running.
- Do not use the mouse or keyboard during a session.

## 8. What happens during seeding

1. Server Seeder saves a complete copy of your Squad settings, then applies low-resource settings (1024 x 768, low graphics, low frame rates).
2. It starts Squad through Steam and uses the server browser to find and join the selected server. It only joins a server it can positively identify.
3. It checks the server's player count regularly.
4. When the player count reaches **Leave server at**, or the maximum duration ends, or something goes wrong, it closes Squad.
5. Once Squad has closed, it restores your original settings.

Server Seeder does not change Steam or Squad program files or Easy Anti-Cheat, and does not send chat messages in the game.

## 9. Game settings restoration

Server Seeder restores your original Squad settings automatically after each session, once Squad has closed. You do not need to do anything.

If a session is interrupted unexpectedly (for example by a power loss or a crash), automatic restoration cannot be guaranteed in every case. In that situation Dashboard shows a warning that your original settings are waiting to be restored, and Server Seeder will not start another session until that is resolved. If you see this warning, close Squad and contact support (section 14).

You can also set your Squad graphics and resolution yourself at any time from Squad's own Settings menu. Do not edit or delete Server Seeder's data files by hand.

## 10. Troubleshooting

- **A scheduled session did not start.** Check that Windows was signed in and unlocked, the PC was awake, Steam was running and signed in, Squad was not already open, and no Steam or Easy Anti-Cheat pop-up was waiting. Check that the schedule status is ACTIVE.
- **Status shows ATTENTION.** The saved schedule and the Windows task do not match. Read the explanation shown under the status. You can click **Activate** to apply your schedule again, or **Deactivate** to turn it off.
- **Status shows UNKNOWN.** Server Seeder could not check the schedule, so Activate and Deactivate are unavailable for now. Click **Reload** in Settings to check again. If it stays UNKNOWN, report it through GitHub Issues (section 14, <https://github.com/OG-GunnyHighway/Server-Seeder/issues>).
- **After reinstalling, check your schedule.** Open Settings and look at the status. If you removed the scheduled task when uninstalling, the status will not be ACTIVE, so set your schedule and click **Activate**. If you kept the task, it may still be active and nothing more is needed, but it is not guaranteed to work, so check that the status is ACTIVE and the time and days are right. If the status is DEACTIVATED, click **Activate**.
- **The session ended without reaching the target.** The maximum duration may have expired, or the server was not found. Dashboard shows the latest message.
- **Menus not recognized.** Make sure a Windows text-recognition language pack (English recommended) is installed and that no other window covers Squad during a session.
- **Dashboard shows a warning.** Follow the message shown. The **Developer** page (a link at the bottom of Dashboard) shows technical details that are useful when reporting a problem.

## 11. Disabling scheduled seeding

Open **Settings** and click **Deactivate**. No further sessions will start. Your settings are kept, and you can click **Activate** later.

## 12. Uninstalling

Use Windows **Settings > Apps > Installed apps** and uninstall Server Seeder. You are asked whether to also remove the scheduled seeding task; choose **Yes** unless you plan to reinstall.

Uninstalling removes the program but keeps your saved settings, schedule information and logs in `%LOCALAPPDATA%\ServerSeeder`, so a later reinstall can use them. After uninstalling you may delete that folder yourself if you no longer want that data. Uninstalling is refused while a session is running or while Squad settings are waiting to be restored.

## 13. Manual updates

Server Seeder does not check for or install updates by itself. To update, download the new installer from the official Releases page (<https://github.com/OG-GunnyHighway/Server-Seeder/releases>), verify its checksum as in section 3, close Server Seeder and run the installer. After updating, open Server Seeder and confirm that the schedule status is ACTIVE.

## 14. Getting support

Report problems and questions through **GitHub Issues**: <https://github.com/OG-GunnyHighway/Server-Seeder/issues>. Include your Server Seeder version (shown on the **About** page), your Windows version and a short description of what happened. Nothing is uploaded automatically, and you never need to send files you are not comfortable sharing.

Server Seeder keeps a log file at `%LOCALAPPDATA%\ServerSeeder\logs\squad_auto.log`. It stays on your PC. You may read it and, if you choose, copy relevant lines into an issue. Check it first for anything you do not want to share.

## About privacy

Server Seeder stores its settings, schedule and logs on your PC. It needs an internet connection during a session to check the player count. It has no telemetry and does not upload logs or reports.
