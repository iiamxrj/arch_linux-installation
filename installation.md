# Arch Linux ARM Installation Documentation

## Project Overview

For this project, I installed Arch Linux ARM in a virtual machine using VMware Fusion on my Mac. I configured a graphical desktop environment, administrator accounts, an alternative shell, SSH, and a color-coded terminal.

## 1. Virtual Machine Setup

I used VMware Fusion to create and run my virtual machine.

- Operating System: Arch Linux ARM (aarch64)
- Virtualization Software: VMware Fusion
- Installation Method: Archboot
- Bootloader: GRUB UEFI

## 2. Installing Arch Linux

I booted into the Archboot installation environment and used its setup menu to configure the system.

The installation process included preparing the storage device, installing packages, configuring the system, and installing the GRUB bootloader.

After installation, I rebooted the virtual machine and selected Arch Linux from the GRUB menu.

## 3. Installing the Desktop Environment

I chose LXQt because it is lightweight and provides a graphical interface.

I installed LXQt, the Xorg display server, the SDDM login manager, and NetworkManager using pacman.

```bash
pacman -S lxqt sddm xorg-server sudo zsh openssh networkmanager
```

I enabled the required services:

```bash
systemctl enable sddm
systemctl enable NetworkManager
systemctl enable sshd
```

These commands configure the services to start automatically when the system boots.

## 4. Configuring User Accounts

I configured two accounts, RJ and codi, and added them to the `wheel` group to allow administrator access.

```bash
usermod -aG wheel RJ
usermod -aG wheel codi
```

I configured sudo permissions using:

```bash
EDITOR=nano visudo
```

This allows authorized members of the `wheel` group to execute commands with administrator privileges.

I verified administrator access using:

```bash
sudo whoami
```

The command returned `root`, confirming sudo was working.

## 5. Installing Zsh

I installed Zsh as an alternative to the default Bash shell.

```bash
pacman -S zsh sudo
```

I changed the default shell for both users:

```bash
chsh -s /bin/zsh RJ
chsh -s /bin/zsh codi
```

I verified the shell using:

```bash
echo $SHELL
```

The output was `/bin/zsh`.

## 6. Configuring Terminal Colors

I edited the Zsh configuration file:

```bash
nano ~/.zshrc
```

I configured a color-coded prompt to display the username, hostname, and current directory.

I applied the changes using:

```bash
source ~/.zshrc
```

## 7. Enabling SSH

I installed OpenSSH and enabled the SSH service:

```bash
systemctl enable sshd
```

I checked the service configuration using:

```bash
systemctl is-enabled sshd
```

The output was `enabled`.

## 8. Installation Verification

After rebooting, I successfully logged into the LXQt desktop environment.

I confirmed that my user account had administrator privileges, Zsh was configured, terminal colors were displayed, and SSH was enabled.

The Arch Linux ARM installation was operational.
