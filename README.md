
<h2 align="center">RICING</h2>

<div align="center">

[![GitHub](https://img.shields.io/github/issues/NvChad/NvChad.svg?style=flat-square&label=Github&color=d77982)](https://github.com/K-Koushik-Kumar/Wallpaper/)
[![Discord](https://img.shields.io/discord/869557815780470834?color=738adb&label=Discord&logo=discord&logoColor=white&style=flat-square)](https://discord.gg/Xm9UrGTW)
[![Telegram](https://img.shields.io/badge/Telegram-blue.svg?style=flat-square&logo=Telegram&logoColor=white)](https://t.me/koushikkodidala)

</div>

## Showcase

![screenshot](https://raw.githubusercontent.com/amitmerchant1990/electron-markdownify/master/app/img/markdownify.gif)

## Information
Here are some details about my setup:

<table>
  <tbody>
    <tr>
      <td align="center" valign="top" width="14.28%">
        <b>OS</b>
      </td>
      <td align="center" valign="top" width="14.28%">
        Linux
      </td>
    </tr>
        <tr>
      <td align="center" valign="top" width="14.28%">
        <b>WM</b>
      </td>
      <td align="center" valign="top" width="14.28%">
        i3
      </td>
    </tr>
      </tr>
        <tr>
      <td align="center" valign="top" width="14.28%">
        <b>Terminal</b>
      </td>
      <td align="center" valign="top" width="14.28%">
       kitty
      </td>
    </tr>
    </tr>
        <tr>
      <td align="center" valign="top" width="14.28%">
        <b>Shell</b>
      </td>
      <td align="center" valign="top" width="14.28%">
       bash
      </td>
    </tr>
    </tr>
          <tr>
      <td align="center" valign="top" width="14.28%">
        <b> Compositor</b>
      </td>
      <td align="center" valign="top" width="14.28%">
       picom
      </td>
    </tr>
    </tr>
          <tr>
      <td align="center" valign="top" width="14.28%">
        <b> Application Launcher</b>
      </td>
      <td align="center" valign="top" width="14.28%">
        rofi
      </td>
    </tr>
    </tr>
  </tbody>
</table>

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

---

```bash

mkdir -p ~/.config/picom
nano ~/.config/picom/picom.conf

backend = "glx";
vsync = true;

opacity-rule = [
  "90:class_g = 'Alacritty'",
  "90:class_g = 'URxvt'",
  "90:class_g = 'XTerm'",
  "90:class_g = 'kitty'",
  "90:class_g = 'gnome-terminal'",
  "90:class_g = 'xfce4-terminal'",
];

inactive-opacity = 0.9;
active-opacity = 0.95;
frame-opacity = 0.9;
blur-background = true;
blur-background-exclude = ["window_type = 'dock'", "window_type = 'desktop'"];



nano ~/.config/i3/config
exec --no-startup-id picom --experimental-backends --config ~/.config/picom/picom.conf
picom --experimental-backends --config ~/.config/picom/picom.conf &




sudo apt install rxvt-unicode lxterminal
xprop | grep WM_CLASS


backend = "glx";
vsync = true;

corner-radius = 12;
round-borders = 1;
round-borders-rule = [
  "class_g = '.*'"
];

blur-method = "dual_kawase";
blur-strength = 7;
blur-background = true;
blur-background-frame = true;

blur-background-exclude = [
  "window_type = 'dock'",
  "window_type = 'desktop'",
  "class_g = 'i3-frame'"
];

opacity-rule = [
  "90:class_g = 'x-terminal-emulator'"
];


```

