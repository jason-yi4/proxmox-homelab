<!--Title-->
# Project Log and History
This log file documents all updates and progress reports pertaining to my *Proxmox Homelab Project*. Dates are recorded to be the day that progress was made, not necessarily the day that the report was written. The log is in order from most recent to oldest entry. ~ Jason Yi

<!--Begin logs-->
## 1/20/2026
* Conducted further research about proper storage configurations for backup cycling.
* Researched about Jellyfin media servers.
* Researched about Pterodactyl hosting for game servers and containerization.
* Drafted a plan to have 4 total VMs:
  1) game-hosting server using Pterodactyl
  2) Jellyfin media server for hosting video projects, archived personal videos, and archived personal photos
  3) basic Debian file-server for storing arbitrary documents, game mods, and other files not containing media
  4) Linux environment (distro not chosen yet) for tinkering with software development; test bench
* Drafted a hardware list needed to upgrade current server rig including additional DDR4 RAM and storage drives.
* Moved all content contained on VMs to main PC for temporary holding until new VMs are spun up.
* Deleted current file-server VM with plans to recreate from the ground up.
  * Destroyed ZFS pool associated with it to start from scratch since new Jellyfin server will use a ZFS pool.

## 12/8/2025
* Tested Proxmox built-in *snapshot* feature for VM rollbacks.
* Researched about proper backup techniques and backing up using Proxmox built-in backup features.
* Stress-tested game-server by inviting 7 additional users into a Minecraft server for a total of 9 hours.
  * No issues or latency experienced during test. 

## 10/30/2025
* Created VM of file-server using Debian Stable 13.1.0 image.
* Created a third static IP-address reservation on home network for the file server.
* Passed ZFS pool (RAID 1 drives) to file-server VM to allow VM access to drives.
* Partitioned, formatted, and mounted ZFS pool. Edited */etc/fstab* file to auto-mount drive on startup based on its UUID.
* Created a *symlink* in the */home* directory to the */mnt/*\[drive name\] directory for quick and intuitive access.
* Confirmed that both VMs and the Proxmox host client were accessible via the Wireguard VPN service while on my campus network instead of my home network.

## 10/29/2025
* Continued configuration of VPN:
  * Forwarded "listening" port of the Wireguard VPN *.conf* file within the Proxmox host through my home router under the *User Datagram Protool* (UDP).
    * Was initially concerned about opening a port to public internet access, but learned that Wireguard has end-to-end encryption that hides the open port from any scans or clients that do not have a valid private key. VPN is confirmed as a secure connection method.
  * Edited *.conf* file for my laptop (user) to contain my home network's public IPv4 address as well as the correct port.
  * Secure-copied (SCP) config to laptop and reactivated tunnel in Wireguard app on laptop.
  * Tested VPN access by connecting laptop to iPhone mobile hotspot.
  * Verified that the VPN was both sending **and receiving** bits.
  * Verified that I was able to access the Proxmox host and game-server VM while under the VPN (file-server VM not created at this point).

## 10/28/2025
* Discrepancy found from previous report regarding VPN access. The VPN tunnel was not connected properly.
* The verification of connectivity performed yesterday was done while still under the same local network as the Proxmox host, which gave a false positive response. Today, the VPN connectivity was tested at my college campus and the VPN server could not receive any bytes from the client (my laptop); there was no *handshake* at all between client and server.
* Researched on the topic to troubleshoot:
  * Determined that I must manually edit the wg0 *.conf* file Endpoint to use my home network's public IP-address as it is still using the Proxmox client's private IP-address, which is inaccessible outside of my local network.
  * Determined that I must open a singular UDP port in my router admin settings **exclusively to Wireguard** to allow the Proxmox host to send packets over open internet. Wireguard in this case is handling all security once packets are sent from my home network, which is ideal as Wireguard does not respond to any requests unless the public and private keys match.
  * Will handle this issue when I get home from classes.

## 10/27/2025
* Configured Ubuntu Server LTS .bashrc file to make directories more readable by adding a background color.
* Tested public access to game servers hosted on the game-server VM by having a friend from another U.S. state join a Minecraft server running on the game-server VM. Connection was successful and stable for a 1-hour session.
* Monitored system hardware usage while running Minecraft server, usage was within acceptable levels (less than 80% usage of the two allocated vCPU cores on average and less than 30% of allocated RAM used on average).
* Colleague suggested that I use *TrueNAS Community Edition (formerly known as FreeNAS)* instead of *Debian Stable* to run the file-server VM. I considered it an option, but ultimately chose to stay with Debian Stable due to the hardware (mainly RAM) limitations of this iteration of the homelab. Perhaps I will switch to *TrueNAS Community Edition* after some hardware upgrades.
* Wireguard VPN was successfully installed directly into Proxmox host using a script by GitHub user [angristan](https://github.com/angristan/): [wireguard-install script](https://github.com/angristan/wireguard-install).
* One user was added to the VPN tunnel, my personal laptop, an *HP Envy x360 14" es0033dx*. Wireguard client was installed onto my personal laptop and VPN functionality was verified by remotely accessing the Proxmox host using the VPN IP-address.
* Other virtual machines were confirmed accessible after connecting via the VPN tunnel by using their regular local (private) IPv4 addresses.
* Reformatted two 1TB internal HDDs using CLI *fdisk* commands.
* Created ZFS Pool in RAID 1 (mirroring) for full accessibility across Proxmox host.

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

## 10/25/2025
* Moved the existing PC tower that was going to host my ProxmoxVE next to the router for wired LAN access (there are no ethernet ports available in my house except on the first floor).
* Updated the BIOS to the latest version, configured for UEFI-only boot mode, disabled Secure Boot for Proxmox compatibility, verified that SATA peripherals were in AHCI mode, and booted into the ProxmoxVE installation that I had on a flash drive.
* Reserved a static IPv4 address for the server to use on my home router.
* Chose a hostname for the server.

## 10/22/2025
I ordered a set of USB 2.0 flash drives, a flash drive organizer sleeve (because at this point I had too many flash drives loose in my desk), and some keyring labels to organize all boot drives necessary for this project. By this point, I had decided that I was going to use Debian 13.1.0 for the file-server VM and Ubuntu LTS for the game-hosting-server VM.

## 10/7/2025
A group member in one of my engineering classes mentioned that I should look into building a homelab using Proxmox. This was after I had discussed another server project that I had done by converting some old computer hardware into a PC running Linux Mint, which was acting as a backup server and a game-hosting server. No VMs were used on this machine; everything was done directly on the Linux Mint OS using a desktop environment and Samba. He told me that it would be a good introduction into virtualization and server administration, so I thought I'd research about it in my own time and give it a shot.
