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

## rdpsnd

* `--data alsa --` - use ALSA system
* `--data pulse --` - use PulseAudio

## rdpdr

* `--data disk:<Name>:<Path> --` - redirect system **\<Path\>** as disk with name **\<Name\>**
