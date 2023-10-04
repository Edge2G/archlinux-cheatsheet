### 1. Display server (Xorg)
---

Up to this point, interaction has been performed via TTY, or virtual console.

Now we install **Xorg**, so we can display images, videos, graphical applications, and visual media in general.

```sh
sudo pacman -S xorg-server xorg-xinit sddm
```

### 2. Desktop Environment / Window manager
---

We not only need a display server, but also a program that manages our graphical applications.

This is done by a **Window manager**, which runs on top of Xorg

There are literally hundreds of options to choose from, but in this case, for a minimal installation, we use **i3wm**.

```sh
sudo pacman -S ttf-inconsolata ttf-dejavu alacritty i3-wm
```

Fonts are also needed to show text correctly, along with a terminal application.

### 3. Audio server
---

So, to hear some sound out of your computer speakers or headphones, just like the display server, we need an audio server.

We only have a handful of options, and **Pipewire** is a good choice.

```sh
sudo pacman -S pipewire pipewire-alsa pipewire-pulse pavucontrol
```

### 4. Starting it all
---

To kickstart the graphical server, it's necesary to run the *xinit* script.

Create the file *.xinitrc* at the home directory (~)

```sh
vim .xinitrc
```

And write into it:

> exec i3

Now just execute it with

```sh
startx
```

### 4.1 Alternative to starting i3
---

Another option to start i3, is to use a *Desktop Manager*, such as SDDM. The service has to be enabled on startup.

```sh
sudo systemctl enable sddm.service
```

This is a graphical way of login and account administration.


If everything went well, a menu should pop up in the middle of the screen, asking if i3 should create a config file. Just say yes.

---

With this, you should now have a generally functional, but very minimal OS, with graphical capabilities.

The [next section](configuration.md) offers a list of steps to complete the installation into a more comfortable user experience.