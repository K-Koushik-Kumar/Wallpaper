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


sudo apt install libxcb-xinerama0-dev


sudo apt install libev-dev libpcre3-dev

sudo apt install libdbus-1-dev


workspace_layout default \

for_window [class=".*"] border normal \

sudo apt install i3-gaps \

# Gaps \
gaps inner 10 \
gaps outer 15 \

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


   


sudo apt install m4 xcb-proto xutils-dev libxcb-util0-dev



picom --experimental-backends --config ~/.config/picom/picom.conf &









sudo apt install autoconf automake libtool pkg-config m4 \
libxcb1-dev libxcb-util0-dev xcb-proto xutils-dev


git clone https://github.com/Airblader/xcb-util-xrm.git
cd xcb-util-xrm
./autogen.sh --prefix=/usr
make
sudo make install




Run-time dependency xkbcommon-x11 found: NO (tried pkgconfig)

meson.build:317:0: ERROR: Dependency "xkbcommon-x11" not found, tried pkgconfig

A full log can be found at /home/admin/i3-gaps/build/meson-logs/meson-log.txt
WARNING: Running the setup command as `meson [options]` instead of `meson setup [options]` is ambiguous and deprecated.
