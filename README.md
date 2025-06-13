# Simple Samba NAS based on Linux (eg Ubuntu Server 24.04.02)


## Description

This repo allows you to quickly set up a server with a bunch of drives in it. They will all be shared under the smb share on your server, eg `\\MYSERVER\share`. Any time you add a new drive, it will be automatically mounted and will become available in the share. You can then access the files from Windows Networking, or from a Mac, or from another Linux desktop.

This will work on any modern Linux distribution. The only requirements are: the `udev` system, `at`, and of course `samba`. If your Linux distro doesn't have `wsdd-server`, you'll have to enter `\\MYSERVER` in the Windows Explorer address bar to access the share. The `install` script is made to look for `apt` and Ubuntu Server 24.04.02, but is easily adapted to any other distribution.

While this code is simple, its real value comes from the fact that you don't have to spend hours doing your own research on how to make things work.

This NAS configuration will work (with some informed adjustments) on all the most popular Linux distros: Ubuntu, Mint, Raspbian aka Raspberry Pi OS, Arch, Gentoo, Debian, Pop! OS, Manjaro, Fedora, openSUSE, CachyOS, SteamOS, ...

With some more adjustment this will work on NixOS, FreeBSD, and Alpine Linux. If you're running one of those you can figure it out. Usually the difference is in `udev` support and having to use an alternative (like `eudev` on Alpine) or having to install `udev` in the first place (like on FreeBSD).


## Security (or: lack thereof)

The server shares the Linux `/mnt/` directory, and it's readable and writeable to anyone. All drives except the operating system drive are available in the share, so bear those security implications in mind: never use this on an open or untrusted network.

Any drives you add to `/etc/fstab` before triggering the automatic mount by plugging in a drive or executing `autofstab` will not be automatically added to `/mnt/` and you can mount them somewhere else, outside of the share. However, this is not what this system is intended to do - if you want security, put the data on another Linux box.


## Installation

On Ubuntu and other Linux distributions with `apt`, this should be as simple as:

1. Open the `install` script and configure the options at the top of the file. Save the file.

2. Execute the `install` script under `sudo`:

```
sudo ./install
```

On other distributions, you'll have to adjust things to use your package manager.
