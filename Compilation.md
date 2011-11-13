Install the suggested base dependencies:

_debian based_

    sudo apt-get install build-essential git cmake libssl-dev libx11-dev libxext-dev libxinerama-dev libxcursor-dev libxdamage-dev libxv-dev libxkbfile-dev libasound2-dev libcups2-dev

_rhel based_

    sudo yum install gcc cmake openssl-devel libX11-devel libXext-devel libXinerama-devel libXcursor-devel libXdamage-devel libXv-devel libxkbfile-devel alsa-lib-devel cups-devel

Optionally, you can install the following dependencies:

 _debian based_

    sudo apt-get install libcunit1-dev libdirectfb-dev xmlto doxygen

where cunit is for the unit tests, directfb is for dfreerdp, xmlto is for man pages, and doxygen for API documentation.

Generate makefiles:

    cmake -DCMAKE_BUILD_TYPE=Debug -DWITH_SSE2=ON .

If you are using Eclipse, you can also generate Eclipse project files:

    cmake -G "Eclipse CDT4 - Unix Makefiles" -DCMAKE_BUILD_TYPE=Debug -DWITH_SSE2=ON .

Build:

    make

Install:

    sudo make install

Now create /etc/ld.so.conf.d/freerdp.conf and add the following line to it:

    /usr/local/lib/freerdp

and then run ldconfig. You should now have xfreerdp installed in /usr/local/bin:

    awake@envy:~$ which xfreerdp
    /usr/local/bin/xfreerdp

Plugins are installed in /usr/local/lib/freerdp:

    awake@envy:/usr/local/lib/freerdp$ ls
    cliprdr.so  disk.so  drdynvc.so  printer.so  rail.so  rdpdbg.so  rdpdr.so  rdpsnd_alsa.so  rdpsnd.so

keymaps are installed in /usr/local/share/freerdp:

    awake@envy:/usr/local/share/freerdp$ ls keymaps/
    aliases  ataritt       empty  fujitsu  ibm        macosx    sony  xfree86  xkb.pl
    amiga    digital_vndr  evdev  hp       macintosh  sgi_vndr  sun   xfree98

After launching FreeRDP at least once, ~/.freerdp will be created to store known hosts:

    awake@envy:~/.freerdp$ ls
    cacert  known_hosts

CA certificates can be added to ~/.freerdp/cacert for additional trusted CAs.
