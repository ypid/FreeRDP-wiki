** This page is not completed **

# Plugins list
* cliprdr - synchronize buffers between host and local machines
* drdynvc - ???
* rdpdr - disk redirection
* tsmf - ???

# Plugins usage

All plugins can be used by adding parameter `--plugin <plugin name>` in command line. But some plugins has extra parameters.

## cliprdr

## rdpsnd

* `--data alsa --` - use ALSA system
* `--data pulse --` - use PulseAudio

## rdpdr

* `--data disk:<Name>:<Path> --` - redirect system **\<Path\>** as disk with name **\<Name\>**
