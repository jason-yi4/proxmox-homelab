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
