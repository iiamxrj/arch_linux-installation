# Arch Linux Installation — Troubleshooting

## Overview

During my Arch Linux ARM installation using VMware Fusion, I encountered several issues involving package installation, shell configuration, and system setup. This document explains the problems and how I resolved them.

## 1. Package Installation Error

**Problem:** While installing LXQt, Zsh, sudo, and other required packages, I accidentally entered an incorrect package name.

The command was:

```bash
pacman -S lxqt sddm xorg-server sudozsh openssh networkmanager
```

The terminal displayed:

```text
error: target not found: sudozsh
```

**Solution:** I corrected the command by separating `sudo` and `zsh` into two packages:

```bash
pacman -S lxqt sddm xorg-server sudo zsh openssh networkmanager
```

The installation then completed successfully.

**What I learned:** Package names must be separated by spaces when using pacman.

## 2. Zsh Configuration Error

**Problem:** After switching from Bash to Zsh, I encountered the following error:

```text
/home/RJ/.zshrc:autoload:1: bad option: -c
```

This indicated an incorrect option in my Zsh configuration.

**Solution:** I opened my configuration file:

```bash
nano ~/.zshrc
```

I corrected the configuration and saved the file.

I reloaded the configuration using:

```bash
source ~/.zshrc
```

The updated configuration loaded without displaying a new error.

**What I learned:** Small syntax errors in shell configuration files can cause startup errors.

## 3. Checking the Installed Operating System

**Problem:** I needed to verify that Arch Linux ARM had been installed successfully.

I initially entered an incorrect file path while checking the installation directory.

**Solution:** I corrected the path and ran:

```bash
cat /mnt/install/etc/os-release
```

The output identified the operating system as Arch Linux ARM.

**What I learned:** Linux file paths must be entered accurately, including capitalization.

## 4. Configuring Administrator Permissions

**Task:** I needed to ensure that my personal account could execute administrative commands.

I added the user accounts to the `wheel` group:

```bash
usermod -aG wheel RJ
usermod -aG wheel codi
```

I edited the sudo configuration using:

```bash
EDITOR=nano visudo
```

I verified the permissions with:

```bash
sudo whoami
```

The output was:

```text
root
```

This confirmed that my account had sudo access.

## 5. Verifying the Desktop Environment

After installing LXQt and enabling SDDM, I rebooted the virtual machine.

The GRUB bootloader appeared, and I selected Arch Linux.

The system successfully loaded the graphical login screen, allowing me to log in to the LXQt desktop.

## Conclusion

These issues helped me understand Linux package management, file paths, shell configuration, and administrator permissions. By correcting mistakes and testing commands, I successfully configured my Arch Linux ARM virtual machine.
