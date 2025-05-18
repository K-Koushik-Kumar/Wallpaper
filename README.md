
<h4 align="center">A minimal Markdown Editor desktop app built on top of <a href="http://electron.atom.io" target="_blank">Electron</a>.</h4>

<p align="center">
  <a href="https://badge.fury.io/js/electron-markdownify">
    <img src="https://badge.fury.io/js/electron-markdownify.svg"
         alt="Gitter">
  </a>
  <a href="https://gitter.im/amitmerchant1990/electron-markdownify"><img src="https://badges.gitter.im/amitmerchant1990/electron-markdownify.svg"></a>
  <a href="https://www.paypal.me/AmitMerchant">
    <img src="https://img.shields.io/badge/$-donate-ff69b4.svg?maxAge=2592000&amp;style=flat">
  </a>
</p>



![screenshot](https://raw.githubusercontent.com/amitmerchant1990/electron-markdownify/master/app/img/markdownify.gif)

## Key Features

* LivePreview - Make changes, See changes
  - Instantly see what your Markdown documents look like in HTML as you create them.
* Sync Scrolling
  - While you type, LivePreview will automatically scroll to the current location you're editing.
* GitHub Flavored Markdown  
* Emoji support in preview :tada:
* App will keep alive in tray for quick usage
* Full screen mode
  - Write distraction free.
* Cross platform
  - Windows, macOS and Linux ready.

## Install Display Server

<details><summary><b>Show instructions</b></summary>

```bash
sudo apt update
sudo apt install xorg xinit x11-xserver-utils
```

</details>

## Install i3 Window Manager

<details><summary><b>Show instructions</b></summary>

```bash
sudo apt install i3
# start GUI by editing xinitrc
nano ~/.xinitrc
exec i3
# now start i3 using
startx
```

>if you're using LightDM, you can completely skip exec i3 (or any WM) in your ~/.xinitrc.

</details>



## Install login manager


<details><summary><b>Show instructions</b></summary>
  
```bash
sudo apt install lightdm
sudo systemctl enable lightdm
```
Confirm the i3 session file exists:
```bash
ls /usr/share/xsessions/i3.desktop
```
```bash
[Desktop Entry]
Name=i3
Comment=Dynamic window manager
Exec=i3
Type=Application
```
>**if not then create**

>How LightDM Works:
>LightDM is a display manager — it provides a login screen (greeter).
>It doesn't use ~/.xinitrc or startx.
>Instead, it uses .desktop files in /usr/share/xsessions/ to launch desktop environments or window managers.

</details>



## Default X user groups set up

<details><summary><b>Show instructions</b></summary>

When you install a minimal OS like Ubuntu Server, it doesn’t automatically put your user into groups that give permission to use hardware devices like the graphics card, keyboard, and mouse under X11 or Wayland.
These groups are essential for running a graphical environment properly.

Check Your Groups
```bash
groups
#You should see something like:
yourusername : yourusername sudo
```
If video, input, etc. are missing, add them like this:
```bash
sudo usermod -aG video,input,audio,render yourusername
sudo reboot
```
</details>


## Set Wallpaper 

<details><summary><b>Show instructions</b></summary>
  
EDIT -> .config/i3/config :

```bash
# for wallpaper
exec_always --no-startup-id feh --bg-fill /home/anime.jpg
# FOR RESOLATION
xrandr 
xrandr --output Virtual1 --mode 1920x1080
```

> **Note**
> If you're using Linux Bash for Windows, [see this guide](https://www.howtogeek.com/261575/how-to-run-graphical-linux-desktop-applications-from-windows-10s-bash-shell/) or use `node` from the command prompt.

</details>



## Neofetch Kitty


<details><summary><b>Show instructions</b></summary>
```bash
sudo apt install neofetch
sudo apt install kitty
```

**make kitty default**

```bash
sudo update-alternartives --config x-terminal-emulator
```
</details>

## Picom i3-gaps

<details><summary><b>Show instructions</b></summary>

```bash
sudo apt install cmake libxext-dev libxcb-damage0-dev libxcb-xfixes0-dev libxcb-render0-dev libxcb-composite0-dev libxcb-image0-dev libxcb-present-dev libxcb-glx0-dev libpixman-1-dev libdbus-1-dev libconfig-dev libgl1-mesa-dev libpcre2-dev libevdev-dev uthash-dev libx11-xcb-dev

sudo apt install -y git meson ninja-build libxcb1-dev libxcb-keysyms1-dev libpango1.0-dev libxcb-util0-dev libxcb-icccm4-dev libyajl-dev libev-dev libxcb-xkb-dev libxcb-cursor-dev libxkbcommon-dev libxkbcommon-x11-dev libstartup-notification0-dev libxcb-xinerama0-dev libxcb-randr0-dev libxcb-shape0-dev libxcb-xrm-dev libxcb-render-util0-dev libxcb-ewmh-dev

sudo apt install m4 xcb-proto xutils-dev libxcb-util0-dev libpcre3-dev

sudo apt install autoconf automake libtool pkg-config m4 libxcb1-dev libxcb-util0-dev xcb-proto xutils-dev
# Dependency
git clone https://github.com/Airblader/xcb-util-xrm.git 
cd xcb-util-xrm 
./autogen.sh --prefix=/usr 
make 
sudo make install
# For picom
git clone --recursive https://github.com/ibhagwan/picom.git 
cd picom
meson setup --buildtype=release build 
ninja -C build 
sudo ninja -C build install
# For i3 gaps
git clone https://www.github.com/Airblader/i3 i3-gaps 
cd i3-gaps 
meson build 
ninja -C build 
sudo ninja -C build install
```

</details>


## Credits

This software uses the following open source packages:

- [Electron](http://electron.atom.io/)
- [Node.js](https://nodejs.org/)
- [Marked - a markdown parser](https://github.com/chjj/marked)
- [showdown](http://showdownjs.github.io/showdown/)
- [CodeMirror](http://codemirror.net/)
- Emojis are taken from [here](https://github.com/arvida/emoji-cheat-sheet.com)
- [highlight.js](https://highlightjs.org/)

## Related

[Try Web version of Markdownify](https://notepad.js.org/markdown-editor/)

---

> [amitmerchant.com](https://www.amitmerchant.com) &nbsp;&middot;&nbsp;
> GitHub [@amitmerchant1990](https://github.com/amitmerchant1990) &nbsp;&middot;&nbsp;
> Twitter [@amit_merchant](https://twitter.com/amit_merchant)
