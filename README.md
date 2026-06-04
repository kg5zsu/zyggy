# Zyggy - ZFS Administration GUI

**Cross-platform Python3 GTK3 GUI for ZFS management**

Zyggy is a simple, fast, and user-friendly graphical interface for basic ZFS administration. It supports Linux and FreeBSD (any Python3 + GTK3 environment) and now also provides a native .deb package for easy installation on Debian/Ubuntu systems.

### Key Features
- Manage ZFS datasets, volumes, snapshots and pools
- Create, destroy, clone, and rollback snapshots
- Rename, promote, remove datasets and pools
- Integrated disk and pool health monitoring (including SMART data)
- View and modify ZFS properties using a clean tabbed GTK3 interface
- Uses system ZFS tools (`zfs`, `zpool`, etc.) under the hood

### Supported ZFS Operations:
- zfs create (Dataset)
- zfs create -v (Volumes)
- zfs rename
- zfs snapshot
- zfs clone
- zfs promote
- zfs rollback
- zfs remove
- zfs get all
- zpool rename
- zpool remove
- zpool get all


![zyggy screenshot](https://github.com/kg5zsu/zyggy/blob/master/screenshot/zyggy.png)




---

### Origin & Credits
Zyggy is the GTK-based successor to the original `zc` ncurses tool (“ZFS Commander”):
- https://github.com/manoeldesouza/zc

MIT Licensed. Contributions welcome! For help or issues, open an issue on GitHub.


## Requirements

**For Debian/Ubuntu (recommended):**
- Python 3
- python3-gi (PyGObject/GTK3 bindings)
- gir1.2-gtk-3.0 (GTK+ 3 introspection data)
- zfsutils-linux (ZFS support)
- [Recommended] smartmontools (for disk SMART status)

Install using:
```
sudo apt install python3 python3-gi gir1.2-gtk-3.0 zfsutils-linux smartmontools
```

**Other Platforms:**
Zyggy is a pure Python script and will run anywhere Python 3 and GTK 3 are available. Manually satisfy package dependencies for your OS.

- FreeBSD: `pkg install python37 gtk3 py37-gobject3 zfs` (and a window manager)
- Manjaro/Arch: `sudo pacman -S python python-gobject gtk3 zfs`


## Desktop Launcher

On Debian/Ubuntu, the Zyggy .deb installs a menu icon (desktop launcher). You'll find it in your Applications or System menu as "Zyggy" with a disk drive icon. The launcher will ask for your administrator password using PolicyKit (`pkexec`).

If you use a different Linux or a desktop that doesn't support .desktop launchers, just run Zyggy manually (see below).

## Installation

### Debian/Ubuntu: Native .deb package (recommended)

A `.deb` package is provided for one-step install:

```
sudo dpkg -i zyggy_0.3-1_all.deb
sudo apt-get install -f
```

You can also build it yourself:

```
sudo apt install debhelper
sudo dpkg-buildpackage -us -uc -b
```

The resulting `.deb` is placed in the parent directory.

### Universal Python script (cross-platform)
You can always run the script directly if Python3 + GTK3 is available:

```
sudo ./zyggy
```
---

## Usage

Zyggy must be run as root to manage ZFS. Start it from a terminal:
```
sudo zyggy
```
Or launch from the Applications/System menu after install — search for "Zyggy". The provided desktop launcher is PolicyKit-aware and will prompt for your password if needed.

## Troubleshooting
- If Zyggy fails to launch, check that all dependencies are installed and you are running a graphical session.
- Use `zfs` and `zpool` in the terminal if there are issues with ZFS commands.
- For GTK/GUI issues, check GTK3 and PyGObject with:
  `python3 -c 'import gi; gi.require_version("Gtk", "3.0"); from gi.repository import Gtk'`

