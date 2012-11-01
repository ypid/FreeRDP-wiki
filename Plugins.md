**This page is not completed**

# Plugins list
* audin - Audio Input Redirection Virtual Channel Extension
* cliprdr - Clipboard Virtual Channel Extension
* drdynvc - Dynamic Virtual Channel Extension
* rdpdr - Device Redirection Virtual Channel Extension
* rdpsnd - Audio Output Virtual Channel Extension
* tsmf - Video Redirection Virtual Channel Extension

# Plugins usage

All plugins can be used by adding parameter `--plugin <plugin name>` in command line. But some plugins has extra parameters.

## cliprdr

* `--plugin cliprdr` - Synchronize client and server clipboard data

## rdpsnd

* `--plugin rdpsnd --data alsa --` - use ALSA system
* `--plugin --data pulse --` - use PulseAudio

## rdpdr

* disk

`--plugin rdpdr --data disk:<Name>:<Path> --` - redirect system **\<Path\>** as disk with name **\<Name\>**

* smartcard

`--plugin rdpdr --data smartcard:<name> --` - redirect smartcard with name \<name\>

* serial
* parallel

## tsmf

* `--plugin drdynvc --data tsmf:decoder:gstreamer` - use gstreamer as media decoder
That tsmf can be used rdpsnd needs to be enabled (eg --plugin rdpsnd --data alsa --) as well.

## rail (RemoteApp mode)

* `--app --plugin rail --data "<exe_or_file>:<working_dir>:<arguments>" --` - Start RDP in RemoteApp mode, to launch only one application in seamless mode