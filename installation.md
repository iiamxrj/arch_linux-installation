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
