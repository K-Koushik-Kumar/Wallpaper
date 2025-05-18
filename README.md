sudo apt update
sudo apt install git meson ninja-build libxext-dev libxcb1-dev libxcb-damage0-dev \
libxcb-xfixes0-dev libxcb-shape0-dev libxcb-render-util0-dev libxcb-render0-dev \
libxcb-randr0-dev libxcb-composite0-dev libxcb-image0-dev libxcb-present-dev \
libxcb-glx0-dev libpixman-1-dev libdbus-1-dev libconfig-dev libgl1-mesa-dev \
libpcre2-dev libevdev-dev uthash-dev libev-dev libx11-xcb-dev


git clone --recursive https://github.com/ibhagwan/picom.git
cd picom

meson setup --buildtype=release build
ninja -C build
sudo ninja -C build install

sudo apt install git meson ninja-build cmake \
libxext-dev libxcb1-dev libxcb-damage0-dev libxcb-xfixes0-dev \
libxcb-shape0-dev libxcb-render-util0-dev libxcb-render0-dev \
libxcb-randr0-dev libxcb-composite0-dev libxcb-image0-dev libxcb-present-dev \
libxcb-glx0-dev libpixman-1-dev libdbus-1-dev libconfig-dev libgl1-mesa-dev \
libpcre2-dev libevdev-dev uthash-dev libev-dev libx11-xcb-dev


Run-time dependency xcb-xinerama found: NO (tried pkgconfig and cmake)

src/meson.build:31:1: ERROR: Dependency "xcb-xinerama" not found, tried pkgconfig and cmake

A full log can be found at /home/admin/picom/build/meson-logs/meson-log.txt

sudo apt install libxcb-xinerama0-dev


============
Run-time dependency libev found: NO (tried pkgconfig and cmake)
Run-time dependency libpcre found: NO (tried pkgconfig and cmake)

src/meson.build:47:1: ERROR: Dependency "libpcre" not found, tried pkgconfig and cmake

A full log can be found at /home/admin/picom/build/meson-logs/meson-log.txt

sudo apt install libev-dev libpcre3-dev


Run-time dependency dbus-1 found: NO (tried pkgconfig and cmake)

src/meson.build:68:1: ERROR: Dependency "dbus-1" not found, tried pkgconfig and cmake

A full log can be found at /home/admin/picom/build/meson-logs/meson-log.txt

sudo apt install libdbus-1-dev

admin@vbox:~/picom$ sudo ninja -C build install
ninja: Entering directory `build'
[0/1] Installing files.
Installing src/picom to /usr/local/bin
Installing /home/admin/picom/bin/picom-trans to /usr/local/bin
Installing /home/admin/picom/picom.desktop to /usr/local/share/applications
Installing /home/admin/picom/compton.desktop to /usr/local/share/applications
Installing /home/admin/picom/media/icons/48x48/compton.png to /usr/local/share/icons/hicolor/48x48/apps
Installing /home/admin/picom/media/compton.svg to /usr/local/share/icons/hicolor/scalable/apps
Running custom install script '/bin/sh /home/admin/picom/meson/install.sh'

workspace_layout default \

for_window [class=".*"] border normal \

sudo apt install i3-gaps \

# Gaps \
gaps inner 10 \
gaps outer 15 \

# Optional: Smart gaps \
smart_gaps on \


git clone https://www.github.com/Airblader/i3 i3-gaps
cd i3-gaps
meson build
ninja -C build
sudo ninja -C build install


sudo apt install -y \
    git meson ninja-build \
    libxcb1-dev libxcb-keysyms1-dev libpango1.0-dev \
    libxcb-util0-dev libxcb-icccm4-dev libyajl-dev \
    libev-dev libxcb-xkb-dev libxcb-cursor-dev libxkbcommon-dev \
    libxkbcommon-x11-dev libstartup-notification0-dev \
    libxcb-xinerama0-dev libxcb-randr0-dev libxcb-shape0-dev \
    libxcb-xrm-dev libxcb-render-util0-dev libxcb-ewmh-dev


    Library iconv found: NO
Found pkg-config: /usr/bin/pkg-config (1.8.1)
Run-time dependency libstartup-notification-1.0 found: NO (tried pkgconfig)

meson.build:305:0: ERROR: Dependency "libstartup-notification-1.0" not found, tried pkgconfig

A full log can be found at /home/admin/i3-gaps/build/meson-logs/meson-log.txt
WARNING: Running the setup command as `meson [options]` instead of `meson setup [options]` is ambiguous and deprecated.
