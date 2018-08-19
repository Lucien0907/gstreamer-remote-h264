# Gstreamer 
Using gstreamer to stream h264 via TCP or UDP

## Prerequisites
### a. Build Gstream 1.2 from source (prefered way)
#### I. Environment Setup
Create a file called set_env.sh and source it from the terminal before executing programs or gstreamer packages. This must be done in every terminal that you want to use gstreamer in.
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



# gstreamer-remote-h264
Using gstreamer with c920 webcam to stream h264 video
https://answers.ros.org/question/295407/how-to-broadcast-hardware-encoded-video-from-the-logitech-c920-to-ros/
