## Freerdp shipped with my distribution is rather old - is there a recent version?
For ubuntu there is a [remmina](http://remmina.sourceforge.net/)/freerdp personal package archive available at https://launchpad.net/~freerdp-team/+archive/freerdp which provides daily builds.
For other distributions are currently no daily packages available so you will need to build from source.

## I am experiencing severe audio lag when viewing multimedia content.
Use the ``--data latency:X --`` argument to specify the audio latency.  X is in milliseconds.

Example command line:

``xfreerdp -u user --no-nla -f --plugin rdpsnd --data latency:50 -- 192.168.x.x``

Further reading:
* http://comments.gmane.org/gmane.network.freerdp.devel/1469
* https://github.com/FreeRDP/FreeRDP/issues/352