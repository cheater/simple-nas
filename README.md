# Simple Samba NAS based on Ubuntu 24.04.02

## Description

This repo allows you to quickly set up a server with a bunch of drives in it. They will all be shared under the share smb share on your server, eg \\MYSERVER\share. Any time you add a new drive, it will be auto mounted and will become available in the share. You can then access the files from Windows Networking, or on a Mac, or on another Linux desktop.


## Security (or: lack thereof)

The server shares the linux /mnt/ directory, and it's readable and writeable to anyone. All drives except the operating system drive are available in the share, so bear those security implications in mind: never use this on an open or untrusted network.


## Installation

1. Open the install script and configure the options at the top of the file. Save the file.

2. Execute the install script in sudo:

```
sudo ./install
```

That should be it.
