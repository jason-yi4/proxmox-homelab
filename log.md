<!--Title-->
# Project Log and History
This log file documents all updates and progress reports pertaining to my *Proxmox Homelab Project*. Dates are recorded to be the day that progress was made, not necessarily the day that the report was written. I will continually add to this file as my homelab expands and I take on new projects. ~ Jason Yi

<!--Begin logs-->
## 10/7/2025
A group member in one of my engineering classes mentioned that I should look into building a homelab using Proxmox. This was after I had discussed another server project that I had done by converting some old computer hardware into a PC running Linux Mint, which was acting as a backup server and a game-hosting server. No VMs were used on this machine; everything was done directly on the Linux Mint OS using a desktop environment and Samba. He told me that it would be a good introduction into virtualization and server administration, so I thought I'd research about it in my own time and give it a shot.

## 10/22/2025
I ordered a set of USB 2.0 flash drives, a flash drive organizer sleeve (because at this point I had too many flash drives loose in my desk), and some keyring labels to organize all boot drives necessary for this project. By this point, I had decided that I was going to use Debian 13.1.0 for the file-server VM and Ubuntu LTS for the game-hosting-server VM.

## 10/25/2025
* Moved the existing PC tower that was going to host my ProxmoxVE next to the router for wired LAN access (there are no ethernet ports available in my house except on the first floor).
* Updated the BIOS to the latest version, configured for UEFI-only boot mode, disabled Secure Boot for Proxmox compatibility, verified that SATA peripherals were in AHCI mode, and booted into the ProxmoxVE installation that I had on a flash drive.
* Reserved a static IPv4 address for the server to use on my home router.
* Chose a hostname for the server.

## 10/26/2025
* Completed installation of ProxmoxVE.
* Verified that ProxmoxVE was remotely accessible by directly accessing the static IP-address of the server. Server can now be configured remotely; server can now be stashed away and left powered on.
* Attempted to move server PC to permanent location. Dropped PC during attempt. Broke PC-cart (used for elevation off carpet floor) upon impact. Broke piece of window blind adjacent to permanent location.
* Opened server PC to visually diagnose any damages; none found. Checked retention of CPU cooler; cooler was still tightly secured.
* Booted server PC to BIOS to monitor CPU temps to verify that the cooler was still properly making contact with CPU IHS; temps were still sub 30 degrees Celsius.
* Made a second attempt to move server PC to permanent location; this attempt was successful.
* PC was left powered on for further configuration via remote access.
* game-server VM was created and successfully enabled.
* Realized that the wrong version of Ubuntu LTS was used with the game-server VM. Ubuntu Desktop LTS was used instead of the headless Ubuntu Server LTS as intended. game-server VM was recreated using proper disc image of Ubuntu Server LTS.
* Additional static IP-addresses were reserved for the game-server VM and file-server VM. Realized that I should've done this beforehand.
* game-server was successfully port-forwarded and is now fully setup.

## 10/27/2025
* Configured Ubuntu Server LTS .bashrc file to make directories more readable by adding a background color.
* Tested public access to game servers hosted on the game-server VM by having a friend from another U.S. state join a Minecraft server running on the game-server VM. Connection was successful and stable for a 1-hour session.
* Monitored system hardware usage while running Minecraft server, usage was within acceptable levels (less than 80% usage of the two allocated vCPU cores on average and less than 30% of allocated RAM used on average).
* Colleague suggested that I use *TrueNAS Community Edition (formerly known as FreeNAS)* instead of *Debian Stable* to run the file-server VM. I considered it an option, but ultimately chose to stay with Debian Stable due to the hardware (mainly RAM) limitations of this iteration of the homelab. Perhaps I will switch to *TrueNAS Community Edition* after some hardware upgrades.
