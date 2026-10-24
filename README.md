# Enshrouded Dedicated Server Scripts
An automated Enshrouded dedicated server manager featuring auto-updates via SteamCMD, player-triggered automatic wake-ups, and a background watchdog script that suspends the server when idle to save system resources.

This are two scripts for running an Enshrouded Dedicated Server, which also "fix" the lack of a feature to pause the server when no one is connected.

**The Launcher (run_server.bat)**:
- Every time it runs, it logs into SteamCMD anonymously, checks the Enshrouded dedicated server files against Steam's master server, and automatically downloads any updates or patches if they are missing or outdated.
- Once it confirms the game files are perfectly validated and up to date, it launches the actual Enshrouded server executable with your custom network port and settings.
- Verifies if pause_server.ps1 is running, if not, it launch it.


**The Watchdog (pause_server.ps1)**:
*This script sits in the background acting as an automated power-saver so your server isn't running 24/7 when nobody is playing.*
- When the server is empty, it puts the Enshrouded server process into a suspended state and closes it.
- It listens closely to network traffic hitting your server port. It is smart enough to ignore people who are just refreshing their server lists or browsing games, so it doesn't wake up by accident.
- The moment it detects an actual player clicking "Connect" to join the game, it instantly triggers the The Launcher script to make sure the server is fully updated, starts it back up, and lets the player log right in.
