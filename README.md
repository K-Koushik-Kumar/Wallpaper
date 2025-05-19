<h2 align="center">RICING</h2>

<div align="center">

[![GitHub](https://img.shields.io/github/issues/NvChad/NvChad.svg?style=flat-square&label=Github&color=d77982)](https://github.com/K-Koushik-Kumar/Wallpaper/)
[![Discord](https://img.shields.io/discord/869557815780470834?color=738adb&label=Discord&logo=discord&logoColor=white&style=flat-square)](https://discord.gg/Xm9UrGTW)
[![Telegram](https://img.shields.io/badge/Telegram-blue.svg?style=flat-square&logo=Telegram&logoColor=white)](https://t.me/koushikkodidala)

</div>

## Showcase

![screenshot](https://github.com/K-Koushik-Kumar/Wallpaper/blob/main/Screenshot%202025-05-19%20191129.png)

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

```bash
sudo apt update
sudo apt install xorg xinit x11-xserver-utils
```

## Install i3 Window Manager

```bash
sudo apt install i3
# start GUI by editing xinitrc
nano ~/.xinitrc
exec i3
# now start i3 using
startx
```
>if you're using LightDM, you can completely skip exec i3 (or any WM) in your ~/.xinitrc.

## Install login manager

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

## Default X user groups set up

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

## Set Wallpaper 
  
EDIT -> .config/i3/config :

```bash
# for wallpaper
exec_always --no-startup-id feh --bg-fill /home/anime.jpg
# FOR RESOLATION
xrandr 
xrandr --output Virtual1 --mode 1920x1080 --pos 0x0
```

> **Note**
> If you're using Linux Bash for Windows, [see this guide](https://www.howtogeek.com/261575/how-to-run-graphical-linux-desktop-applications-from-windows-10s-bash-shell/) or use `node` from the command prompt.

## Neofetch Kitty

 ```bash
sudo apt install neofetch
sudo apt install kitty
```

**make kitty default**

```bash
sudo update-alternartives --config x-terminal-emulator
```

## Picom i3-gaps

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

Edit for gaps
```bash
nano ~/.config/i3/config
# Gaps 
gaps inner 10 
gaps outer 15 
```

Edit picom for blur transprency round border
```bash
mkdir -p ~/.config/picom
nano ~/.config/picom/picom.conf

backend = "glx";
vsync = true;

round-borders = 1;
corner-radius = 12;
round-borders-rule = [
  "10:class_g = 'Gnome-terminal'",
  "10:class_g = 'rofi'",
  "10:class_g = '.*'"
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


#Edit i3/config
exec --no-startup-id picom --experimental-backends --config ~/.config/picom/picom.conf
#for manual
picom --experimental-backends --config ~/.config/picom/picom.conf &
```

>**Note**
>Edit terminal tranparency through preference also if it didnt work

## hide window title bars
Edit nano ~/.config/i3/config
```bash
for_window [class=".*"] border pixel 0
for_window [class="Gnome-terminal"] border pixel 0
for_window [class="Firefox"] border pixel 0
```

>note:
>find any app’s class with:
>xprop | grep WM_CLASS

## Issue:
Screen shifting to the bottom-left corner

```bash
backend = "xrender";
```

## Remove the menu bar 
Preferences → [Your Profile] → General → Uncheck “Show menubar by default in new terminals”

## Change the terminal prompt
Your terminal prompt is controlled by the PS1 variable in your shell.
```bash
nano ~/.bashrc
#find a line like:
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
#Replace it with
PS1='> '
```
>**note** sudo apt install rxvt-unicode lxterminal

TO edit i3status
Find and open:
nano ~/.config/i3status/config
/etc/i3status.conf

## i3 bar
edit picom config:

```bash
opacity-rule = [
  "100:class_g = 'i3bar'"
];
```

Edit ~/.config/i3/config

```bash
bar {
    position top
    status_command i3status
    tray_output primary
    font pango:JetBrains Mono 10

    colors {
        background #ffffff
        statusline #000000
        separator  #888888

        focused_workspace  #ffffff #ffffff #000000
        inactive_workspace #f0f0f0 #f0f0f0 #888888
        urgent_workspace   #ff0000 #ffffff #000000
    }
}
```

## Shadow Box Config

```bash
shadow = true;
shadow-radius = 12;
shadow-offset-x = -10;
shadow-offset-y = -10;
shadow-opacity = 0.4;
shadow-exclude = [
  "class_g = 'i3-frame'",
  "class_g = 'i3bar'",
  "window_type = 'desktop'",
  "_NET_WM_STATE@:32a *= '_NET_WM_STATE_HIDDEN'"
];
shadow-exclude-reg = [];
```
---

