### Configuration (In progress)
---

The following is just a list of steps to modify minor details of the OS, functionally and also aesthetically.

This is for achieving a more comfortable environment, and better user experience overall.

---

Install some programs from pkglist.txt (long list, it's optional)

Install an AUR helper - Paru:

```sh
git clone https://github.com/Morganamilo/paru.git
cd paru
makepkg -si
```

Enable colored output on Pacman:

```sh
sudo vim /etc/pacman.conf
```

and uncomment the #Color line under *Misc Options*