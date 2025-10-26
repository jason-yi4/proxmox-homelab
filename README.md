<!--Title of Project-->
# Proxmox Homelab Server Project

### Start Date: October 2025

This is a full documentation and history of a personal homelab server project that I started in my 3rd year of university. I began researching about hypervisors, virtualization, VMs, and server administration after a group member in a  course I took piqued my interest. Prior to this project, I had never been exposed to virtualization, RAID configurations, hypervisors, or homelabbing as a whole. I did have prior experience with UNIX commands and file structure, Linux Mint Cinnamon Edition, networking protocols and IP-reservations, basic firewall configuration, PC building and computer architecture, and rudimentary file storage using Samba.

<!--Goals Overview-->
## Goals
* Set up ProxmoxVE with two VMs running a file-server and a game-hosting-server, respectively.
  * The file-server will run on Debian Stable (ver. 13.1.0 at the time of writing) for its stability, the fixed release cycle, extensive forums and support, and for exposure to one of the most prevalent Linux distributions used today.
  * The game-hosting-server will run on Ubuntu LTS (ver. 24.04.3 at the time of writing) for its stability, 5-year fixed release cycle for less frequent updates, extensive forums and support, and for exposure to a different Linux distribution based on Debian.
* Configure two or more HDDs in RAID 1 (mirroring) for data redundancy in the event of a drive failure. This is not acting in place of a proper backup cycle, but rather solely as an extra form of protection against loss of data. Backups will still be done to external drives for long-term cold storage.
* Set up a secure VPN for accessing the server outside of my local home network via *ssh* (e.g. when I'm on campus).

<!--Navigation for repository-->
## Documentation Overview
There are two files in this repository for additional in-depth information about this project.
* See the [Full Progress Log](log.md) for the timeline of updates and progress made on this project.
* See the [Hardware Specifications Log](hardware_specs.md) for the original full spec-sheet for this project as well as a timeline of all hardware changes.



<!--Closing-->
Thanks for reading!
~ Jason Yi
