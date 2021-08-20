# archlinux-cheatsheet

### Easy steps for Arch Linux installation.<br><br>

This is a simple set of steps to achieve a minimal [Arch Linux](https://archlinux.org/) install.
The starting point is assuming you already have a [bootable device](https://archlinux.org/download/) and booted under UEFI mode.

This is by no means the best, or most efficient way to do this, but its what works for me, and hopefully more people as well.<br><br>

### 1. Set the keyboard layout
---

```sh
loadkeys la-latin1
```

This one is for latin american keyboard. To search your particular layout, run

```sh
localectl list-keymaps
```

### 2. Connect to the internet
---

Wired connections work pretty much out of the box. For wireless connections, run

```sh
iwctl
```

An interactive prompt will appear.

```sh
device list
station wlan0 scan (assuming your device is wlan0)
station wlan0 get-networks
station wlan0 connect SSID
```

Where *SSID* is the name of your network. Then ping to test the connection.

```sh
ping archlinux.org
```

And update the system clock

```sh
timedatectl set-ntp true
```

### 3. Disk partitioning and formatting
---

[Partitioning](https://wiki.archlinux.org/title/Partitioning) can be done in many ways, but this is the set-up I use.

First, identify the disk (or volume) in which you want to install Arch, by issuing

```sh
lsblk
```

Second, run *cfdisk* with the desired device, for example *sda* (more info on block devices [here](https://wiki.archlinux.org/title/Device_file#Block_devices))

```sh
cfdisk /dev/sdx
```

Replace *x* with your device letter, *sda, sdb, sdc, etc*

Now, since it's a fresh install, **delete** all partitions. We want to create 2 partitions, 1 for **boot**, and the rest for the **root** partition.<br>

Select
> **new** -> 300M -> type -> efi system
>
> **new** -> Press **enter** for the rest of the device -> type -> linux filesystem
>
> **write**

**Note:** At this point, you can also create a swap partition.

For formatting, the 300M boot partition has to be a fat32 file system. The root partition, in this case, is **ext4**, but there's also [more options for file systems](https://wiki.archlinux.org/title/File_systems#Types_of_file_systems)

```sh
mkfs.fat -F32 /dev/sda1
mkfs.ext4 /dev/sda2
```

### 4. System installation
---

First create **boot** directory for mountpoint, and mount the previously created partitions

```sh
mkdir /mnt/boot
mount /dev/sda1 /mnt/boot
mount /dev/sda2 /mnt
```

Now, the **pacstrap** scripts installs the base system, and some utilities along with it

```sh
pacstrap /mnt base base-devel linux linux-headers linux-firmware vim vi
```