
### sources

Sources: https://github.com/FreeRDP/FreeRDP/tree/1.0.2-rc1 

Commit: https://github.com/FreeRDP/FreeRDP/commit/af940d2f2486e7af23c436e65cf480c09d8c8a06

### cmake 

cmake -DCMAKE_BUILD_TYPE=Debug -DWITH_SSE2=On -DWITH_PULSEAUDIO=ON -DWITH_PCSC=ON .

cmake log: https://gist.github.com/4031340

make log: https://gist.github.com/4031349

make install log: https://gist.github.com/4031356

install manifest: https://gist.github.com/4031382

### Environment

Client: Ubuntu 12.04 (Atom D425), see cmake log for all needed packages being available.

Testserver (192.168.16.xx): Windows Server 2k8 R2 SP1 Std. (German language), RFX enabled (in local GPO), K-Lite Codec installed, Audio-/Video Payback Redirect enabled.

### Connection string

xfreerdp -u administrator -p password -d 192.168.16.xx  -g 1366x748 --rfx --plugin rdpsnd 
--plugin cliprdr --plugin rdpdr --data disk:A:/mnt/A disk:B:/mnt/B scard:scard -- 
--plugin drdynvc --data tsmf -- 192.168.16.xx

### Results

* `xfreerdp --version` outputs "This is FreeRDP version 1.0.1" (wrong version). 
* `which xfreerdp` outputs "/usr/local/bin/xfreerdp".
* RemoteFX (-rfx) doesn't seem to work as the session isn't logged as "RemoteFx enabled" to Windows Eventlog (Application and Services\Logs\Microsoft\Windows\RemoteDesktopServices-RemoteDesktopSession Manager).
* Clipboard is working.
* Mapping of client drives is working. Bidirectional copy of files, too.
* Smartcard is working.
* Multimedia Redirect (tsmf) has no sound of its own. Sound is only available via rdpsnd (but poor quality and with a great delay of ~5-10 seconds). This is a regression to freerdp 1.0.
* Big Buck Bunny (h264, 480p) is played very choppy and too slow in Windows Media Player. MMR doesn't seem to work.



