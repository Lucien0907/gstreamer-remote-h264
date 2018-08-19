# Gstreamer 
Using gstreamer to stream h264 via TCP or UDP

## Prerequisites
### a. Build Gstream 1.2 from source (prefered way)
#### I. Environment Setup
Create a file called set_env.sh and source it from the terminal before executing programs or gstreamer packages. This must be done in every terminal that you want to use gstreamer in.

Create the file:
```bash
$ vim set_env.sh
```
```vim
PFX=/home/user/gst/runtime
export PATH=$PATH:$PFX/bin
export LD_RUN_PATH=$LD_RUN_PATH:$PFX/lib
export PKG_CONFIG_PATH=$PKG_CONFIG_PATH:$PFX/lib/pkgconfig
export GST_PLUGIN_PATH=$PFX/lib/gstreamer-1.0
```
Source the file
```bash
$ . set_env.sh
```

#### II. Dependencies

* libx264-dev — Provides H.264 encoder.
* libgudev-1.0-dev — Required for the new uvch264src
* libusb-1.0-0-dev — Required for the new uvch264src
* yasm — Assembler needed for gst-libav
* autoconf
* bison
* gtk-doc-tools

```bash
sudo apt-get install libx264-dev
sudo apt-get install libgudev-1.0-dev
sudo apt-get install libusb-1.0-0-dev
sudo apt-get install yasm
sudo apt-get install autoconf
sudo apt-get install flex bison
sudo apt-get install gtk-doc-tools
```

#### III. Build Order
Gstreamer source packages are available from: 
[https://gstreamer.freedesktop.org/modules/](https://gstreamer.freedesktop.org/modules/)
```bash
git clone https://cgit.freedesktop.org/gstreamer/orc
git clone https://cgit.freedesktop.org/gstreamer/gstreamer
git clone https://cgit.freedesktop.org/gstreamer/gst-plugins-base
git clone https://cgit.freedesktop.org/gstreamer/gst-plugins-good
git clone https://cgit.freedesktop.org/gstreamer/gst-plugins-bad
git clone https://cgit.freedesktop.org/gstreamer/gst-plugins-ugly
git clone https://cgit.freedesktop.org/gstreamer/gst-libav
```
1.Setup environment
```bash
. set_env.sh
```
2.Build ORC using --prefix=/home/user/gst/runtime
```bash
cd orc
./autogen.sh --prefix=/home/user/gst/runtime && make && sudo make install
```
3.Build opus 1.1 from source if you need it

4.Build gstreamer using --prefix=/home/user/gst/runtime
```bash
cd gstreamer
./autogen.sh --prefix=/home/user/gst/runtime && make && sudo make install
```
5.Build gst-plugins-base using --enable-orc --prefix=/home/user/gst/runtime
```bash
cd gat-plugins-base
./autogen.sh --enable-orc --prefix=/home/user/gst/runtime && make && sudo make install
```
6.Build gst-plugins-good using --enable-orc --prefix=/home/user/gst/runtime
```bash
cd gat-plugins-good
./autogen.sh --enable-orc --prefix=/home/user/gst/runtime && make && sudo make install
```
7.Build gst-plugins-bad using --enable-orc --prefix=/home/user/gst/runtime
```bash
cd gat-plugins-bad
./autogen.sh --enable-orc --prefix=/home/user/gst/runtime && make && sudo make install
```
8.Build gst-plugins-ugly using --enable-orc --prefix=/home/user/gst/runtime
```bash
cd gat-plugins-ugly
./autogen.sh --enable-orc --prefix=/home/user/gst/runtime && make && sudo make install
```
9.Build gst-libav using --enable-orc --prefix=/home/user/gst/runtime
```bash
cd gat-libav
./autogen.sh --enable-orc --prefix=/home/user/gst/runtime && make && sudo make install
```

### b.Install gstreamer 1.2 usinng install package(only if you) failed building from source
```bash
sudo apt-get install libgstreamer1.0-0 
sudo apt-get install gstreamer1.0-plugins-base 
sudo apt-get install gstreamer1.0-plugins-good 
sudo apt-get install gstreamer1.0-plugins-bad 
sudo apt-get install gstreamer1.0-plugins-ugly sudo apt-get install 
sudo apt-get install gstreamer1.0-libav 
sudo apt-get install gstreamer1.0-doc 
sudo apt-get install gstreamer1.0-tools
```
# gstreamer-remote-h264
Using gstreamer with c920 webcam to stream h264 video
https://answers.ros.org/question/295407/how-to-broadcast-hardware-encoded-video-from-the-logitech-c920-to-ros0
