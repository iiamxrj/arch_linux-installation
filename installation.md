## 1. Virtual Machine Setup

I used VMware Fusion on my MacBook to create a virtual machine for installing Arch Linux ARM.

### Virtual Machine Specifications

| Component | Configuration |
|---|---|
| Virtualization Software | VMware Fusion |
| Operating System | Arch Linux ARM (aarch64) |
| RAM | 4 GB |
| Processors | 2 |
| Virtual Hard Disk | 20 GB |
| Installation Environment | Archboot |
| Bootloader | GRUB UEFI |
| Desktop Environment | LXQt |

### Installation Process

1. Opened VMware Fusion on my Mac.
2. Created a virtual machine for an ARM-based Linux operating system.
3. Allocated 4 GB of RAM and 2 processors.
4. Configured a 20 GB virtual hard disk.
5. Booted the virtual machine using the Archboot installation environment.
6. Started the Archboot setup utility to install Arch Linux ARM.

### Why I Chose These Settings

I selected 4 GB of RAM and 2 processors to provide enough resources for the operating system and graphical desktop environment without using too many resources from my Mac.

I allocated 20 GB of storage for the operating system, desktop environment, and required packages.

## Storage Configuration and Partitioning

During installation, I configured my 20 GB virtual hard disk using the Archboot installation utility.

I used separate partitions for the EFI boot files, Linux swap, the root filesystem, and the home directory.

### Partition Layout

| Partition | Filesystem | Mount Point | Purpose |
|---|---|---|---|
| /dev/nvme0n1p1 | Not identified | None shown | Reserved or unconfigured partition |
| /dev/nvme0n1p2 | FAT32 | /boot | EFI system partition |
| /dev/nvme0n1p3 | Linux swap | [SWAP] | Virtual memory |
| /dev/nvme0n1p4 | ext4 | / | Operating system files |
| /dev/nvme0n1p5 | ext4 | /home | User files and settings |

### Verifying the Partitions

After installation, I opened the terminal and entered:

```bash
lsblk -f
```

This command lists storage devices, filesystems, filesystem labels, UUIDs, and mount points.

The output confirmed that the EFI partition was mounted at `/boot`, the root partition at `/`, and the home partition at `/home`. It also showed an active swap partition.

### Why I Used Separate Partitions

Separating the root and home directories allows user files and system files to be organized independently.

The EFI system partition stores files needed for UEFI booting, while swap provides additional virtual memory when needed.

## System Configuration

After installing the base Arch Linux ARM system, I used the Archboot setup utility to configure the operating system.

### 1. Configuring the System

In the Archboot setup menu, I selected **Configure System**.

The configuration menu included:

- User management
- Virtual console settings
- Locale configuration
- Filesystem mount points
- Kernel modules
- Initramfs configuration
- Hostname and network settings
- Pacman configuration

I used these settings to prepare the installed operating system.

### 2. Verifying the Locale

During installation, I checked the system locale configuration, which displayed:

```text
LANG=C.UTF-8
```

The locale determines the language and character encoding used by the system.

### 3. Configuring the Bootloader

I selected **Install Bootloader** from the Archboot setup menu.

The installer presented UEFI bootloader options, including EFISTUB and GRUB.

I configured GRUB for UEFI booting.

After installation, the virtual machine displayed the GNU GRUB boot menu with Arch Linux as a boot option.

### 4. Rebooting the System

I exited the installation environment and rebooted the virtual machine.

The system successfully loaded the GRUB menu, started Arch Linux ARM, and displayed the SDDM graphical login screen.

I logged into the LXQt desktop environment using my personal user account.

### 5. Verifying the Installation

After logging in, I opened a terminal and ran:

```bash
whoami
echo $SHELL
sudo whoami
systemctl is-enabled sshd
systemctl is-enabled sddm
```

These commands verify the current user, default shell, administrator permissions, SSH configuration, and graphical login manager.

The results confirmed that my user account worked with Zsh, sudo permissions were available, and SSH and SDDM were enabled.

## Final Summary

I successfully installed Arch Linux ARM in VMware Fusion with 4 GB RAM, 2 processors, and a 20 GB virtual hard disk.

I configured the LXQt desktop environment, SDDM login manager, GRUB bootloader, administrator accounts, Zsh shell, SSH service, NetworkManager, and a color-coded terminal.

The installation helped me understand Linux partitioning, package management, user permissions, system services, and command-line configuration.
