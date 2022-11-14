### Configuration (In progress)
---

The following is just a list of steps to modify minor details of the OS, functionally and also aesthetically.

This is for achieving a more comfortable environment, and better user experience overall.

---

Install some programs (long list, it's optional):

```sh
sudo pacman -S polybar picom chromium network-manager-applet git wget neofetch rofi nitrogen htop discord man-db ttf-font-awesome network-manager-applet powertop alacritty mpv zsh zsh-completions bluez bluez-utils blueman pulseaudio-bluetooth
```

Install an AUR helper - Paru:

```sh
git clone https://github.com/Morganamilo/paru.git
cd paru
makepkg -si
```

Install AUR packages:

```sh
paru -S vscodium
```

Enable colored output on Pacman:

```sh
sudo vim /etc/pacman.conf
```

and uncomment the #Color line under *Misc Options*