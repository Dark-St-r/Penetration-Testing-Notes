# Step:1 Distrod - WSL2 Distros with Systemd!

[![CI](https://github.com/nullpo-head/wsl-distrod/actions/workflows/ci.yaml/badge.svg)](https://github.com/nullpo-head/wsl-distrod/actions)

Distrod is a systemd-based meta-distro for WSL2 that allows you to install Ubuntu, Arch Linux, Gentoo and many other distros
with systemd in a minute, or make your current distro run systemd.

Distrod also provides built-in auto-start feature and port forwarding service.
This allows you to start systemd-managed services, such as `ssh`, on Windows startup and make it accessible from outside Windows.

## Install

### Option 1: Install a New Distro.

0. Make sure that your default WSL version is 2.

   ```console
   > wsl --set-default-version 2
   ```

1. Download and unzip [the latest `distrod_wsl_launcher-x86_64.zip` from release](https://github.com/nullpo-head/wsl-distrod/releases/latest/download/distrod_wsl_launcher-x86_64.zip), and double-click the extracted `.exe` file.

2. Follow the wizard to install a new distro.

3. \[Optional\] To make your distro start on Windows startup, run the following command.

   ```bash
   sudo /opt/distrod/bin/distrod enable --start-on-windows-boot
   ```

   You also might want to forward ports of services such as `ssh` to the outside of Windows.
   In that case, you can enable the built-in port proxy service provided by Distrod.

   **NOTE**: On Windows 11, `portproxy.service` doesn't work on Windows startup, which should be fixed soon. See [Known bus](docs/references.md#know-bugs).

   ```bash
   echo 22 | sudo tee /opt/distrod/conf/tcp4_ports  # update the portproxy.service's configuration
   sudo systemctl enable --now portproxy.service  # enable and start it
   ```
   
 
## Usage

If you are using [Windows Terminal](https://github.com/microsoft/terminal),
Windows Terminal will automatically find and register Distrod for you.
Just open the tab named "Distrod".

If you are using other terminals, please update your terminal settings to launch the Distrod.
For reference, the following command launches a distro by name in WSL

```console
> wsl --distribution Distrod
```

## Update Distrod

1. Inside a Distrod session, download and run the latest installer script.

   ```bash
   curl -L -O "https://raw.githubusercontent.com/nullpo-head/wsl-distrod/main/install.sh"
   chmod +x install.sh
   sudo ./install.sh update
   ```

## How Distrod Works

In a nutshell, Distrod is a binary that creates a simple container that runs systemd as an init process,
and starts your WSL sessions within that container. To realize that, Distrod does the following things.

- Modify the rootfs of the concrete distro you chose so that it is compatible with both WSL and systemd.
  - Modify systemd services so that they are compatible with WSL
  - Configure networks for WSL
  - Put `/opt/distrod/bin/distrod` and other resources in the rootfs.
  - Register the Distrod's binary as the login shell
- When Distrod is launched by WSL's init as a login shell, Distrod
  1.  Starts systemd in a simple container
  2.  Launches your actual shell within that container
  3.  Bridges between the systemd sessions and the WSL interop environment.


# Step:2 Win-Kex - GUI Solution for Kali-Linux

Win-KeX provides a Kali Desktop Experience for Windows Subsystem for Linux (WSL 2) with the following features:
- Window mode: start a Kali Linux desktop in a dedicated window
- Seamless mode: share the Windows desktop between Windows and Kali apps and menus
- Sound support
- Unprivileged and Root session support
- Shared clipboard for cut and paste support between Kali Linux and Windows apps
- Multi-session support: root window & non-priv window & seamless sessions concurrently
- Fully compatible with WSLg

![image](https://user-images.githubusercontent.com/93423666/155871413-a63c451b-accb-421f-ac10-216a27fd7aa1.png)

## Prerequisites

- Running Windows 10 version 2004 or higher
- Using [Windows Terminal](https://github.com/microsoft/terminal)

## Installation
### Install Kali Linux in WSL2
- Open PowerShell as administrator and run:
```console
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```
- Open PowerShell as administrator and run:
```console
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```
- Restart

- Download and install the [WSL2 Linux Kernel](https://aka.ms/wsl2kernel)

- Open PowerShell as administrator and run:
```console
wsl --set-default-version 2
```

- Install Kali Linux from the Microsoft Store

Note: to upgrade an existing WSL1 kali-linux installation, type:
```console
wsl --set-version kali-linux 2
```
- Run Kali and finish the initial setup

### Install Win-KeX

- Install win-kex via:
```bash
sudo apt update
sudo apt install -y kali-win-kex
```

### Run Win-KeX
Win-KeX supports three modes:

- Window Mode:

To start Win-KeX in Window mode with sound support, run
```bash
kex --win -s
```

Refer to the Win-KeX Win usage documentation for further information.

- Enhanced Session Mode:

To start Win-KeX in Enhanced Session Mode with sound support and arm workaround, run
```bash
kex --esm --ip -s
```

Refer to the Win-KeX ESM usage documentation for further information.

- Seamless mode:

To start Win-KeX in Seamless mode with sound support, run
```bash
kex --sl -s
```

Refer to the Win-KeX SL usage documentation for further information.

### Optional Steps:
If you have the space, why not install “Kali with the lot”?:
```bash
sudo apt install -y kali-linux-large
```
or
```bash
sudo apt install -y kali-linux-everything
```

- Create a Windows Terminal Shortcut:


Choose amongst these options:

- Basic Win-KeX in window mode with sound:

```
{
      "guid": "{55ca431a-3a87-5fb3-83cd-11ececc031d2}",
      "hidden": false,
      "name": "Win-KeX",
      "commandline": "wsl -d kali-linux kex --wtstart -s",
},
```
- Advanced Win-KeX in window mode with sound - Kali icon and start in kali home directory:

Copy the kali-menu.png icon across to your windows picture directory and add the icon and start directory to your WT config:

```
{
        "guid": "{55ca431a-3a87-5fb3-83cd-11ececc031d2}",
        "hidden": false,
        "icon": "file:///c:/users/<windows user>/pictures/icons/kali-menu.png",
        "name": "Win-KeX",
        "commandline": "wsl -d kali-linux kex --wtstart -s",
        "startingDirectory" : "//wsl$/kali-linux/home/<kali user>"
},
```
- Basic Win-KeX in seamless mode with sound:

```
{
      "guid": "{55ca431a-3a87-5fb3-83cd-11ececc031d2}",
      "hidden": false,
      "name": "Win-KeX",
      "commandline": "wsl -d kali-linux kex --sl --wtstart -s",
},
```
- Advanced Win-KeX in seamless mode with sound - Kali icon and start in kali home directory:

Copy the kali-menu.png icon across to your windows picture directory and add the icon and start directory to your WT config:

```
{
        "guid": "{55ca431a-3a87-5fb3-83cd-11ececc031d2}",
        "hidden": false,
        "icon": "file:///c:/users/<windows user>/pictures/icons/kali-menu.png",
        "name": "Win-KeX",
        "commandline": "wsl -d kali-linux kex --sl --wtstart -s",
        "startingDirectory" : "//wsl$/kali-linux/home/<kali user>"
},
```
- Basic Win-KeX in ESM mode with sound:

```
{
      "guid": "{55ca431a-3a87-5fb3-83cd-11ecedc031d2}",
      "hidden": false,
      "name": "Win-KeX",
      "commandline": "wsl -d kali-linux kex --esm --wtstart -s",
},
```
- Advanced Win-KeX in ESM mode with sound - Kali icon and start in kali home directory:

Copy the kali-menu.png icon across to your windows picture directory and add the icon and start directory to your WT config:

```
{
        "guid": "{55ca431a-3a87-5fb3-83cd-11ecedd031d2}",
        "hidden": false,
        "icon": "file:///c:/users/<windows user>/pictures/icons/kali-menu.png",
        "name": "Win-KeX",
        "commandline": "wsl -d kali-linux kex --esm --wtstart -s",
        "startingDirectory" : "//wsl$/kali-linux/home/<kali user>"
},
```





### Help
For more information, ask for help via:

```bash
kex --help
```

or consult the manpage via:

```bash
man kex
```

### Known issue:
- "run-detectors: unable to find an interpreter:"
Solution:
```bash
sudo update-binfmts --disable cli
```
Only do if you get the error.

Alternately, open Powershell and run:
```console
wsl --shutdown
```
has to be Powershell for unknown reasons.

  ENJOY, Dark Lepus!!
