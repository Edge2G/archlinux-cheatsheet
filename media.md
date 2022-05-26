### 1. Display server (Xorg)
---

Up to this point, interaction has been performed via TTY, or virtual console.

Now we install **Xorg**, so we can display images, videos, graphical applications, and visual media in general.

```sh
sudo pacman -S xorg-server xorg-xinit
```

### 2. Desktop Environment / Window manager
---

We not only need a display server, but also a program that manages our graphical applications.

This is done by a **Window manager**, which runs on top of Xorg

There are literally hundreds of options to choose from, but in this case, for a minimal installation, we use **i3wm**.

```sh
sudo pacman -S ttf-inconsolata ttf-dejavu lxterminal i3-gaps
```

Fonts are also needed to show text correctly, along with a terminal application.

### 3. Audio server
---

So, to hear some sound out of your computer speakers or headphones, just like the display server, we need an audio server.

We only have a handful of options, and **Pulseaudio** is a good choice.

```sh
sudo pacman -S pulseaudio pulseaudio-alsa pavucontrol alsa-utils
```

Make sure to unmute the master sound channel with

```sh
alsamixer
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

If everything went well, a black background with some colored text should appear on the screen, meaning that *i3* has succesfully been executed.

---

With this, you should now have a generally functional, but very minimal OS, with graphical capabilities.

The [next section](configuration.md) offers a list of steps to complete the installation into a more comfortable user experience.