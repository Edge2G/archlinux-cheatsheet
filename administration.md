### 1. Connect to the internet (wireless)
---

Once the installation is finished, and you have rebooted, reconnect to a wireless network, this time using NetworkManager CLI interface.

(Skip this step if you are using a wired connection)

```sh
nmcli device wifi list
```

```sh
nmcli device wifi connect SSID password PASSWORD
```

Where *SSID* is the name of your network and *PASSWORD* is its password

### 2. Create a user
---

```sh
useradd -mg wheel USER-NAME
```

```sh
passwd USER-NAME
```

This creates the user *USER-NAME* with it's password

The parameters *-mg* are to create a home directory (/home/USER-NAME) and to add said user to the *wheel* group for administration privileges.

### 3. Enable *sudo*
---

Run

```sh
visudo
```

And uncomment the line with:

**% wheel all = (all)all**

This enables sudo to everyone in the *wheel* group

### 4. Install a firewall
---

```sh
pacman -S ufw
```

```sh
ufw enable
```

### 5. Install microcode and GPU drivers
---

This depends on your cpu.

For Intel CPU's:

```sh
pacman -S intel-ucode
```

Or AMD

```sh
pacman -S amd-ucode
```

You can also install GPU drivers at this point:

For Nvidia graphic cards

```sh
pacman -S nvidia nvidia-utils
```

Or AMD

```sh
pacman -S xf86-video-amdgpu
```

Or Intel

```sh
pacman -S xf86-video-intel intel-media-driver
```

\***Important**: It's recommended to consult [here](https://wiki.archlinux.org/title/Xorg#Driver_installation) for your particular set-up\*

All of this requires to reconfigure GRUB and reboot your PC

```sh
grub-mkconfig -o /boot/grub/grub.cfg
```

```sh
reboot
```
---

Now the system is ready for general command-line use, and you can log in with your own account, but it lacks a graphical environment and an audio server, which is discussed in the [media section](media.md).
