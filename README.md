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

