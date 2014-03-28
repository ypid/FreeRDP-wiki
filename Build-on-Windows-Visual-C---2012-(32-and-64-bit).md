==Prerequisites==

* MS Visual C++ Express 2012 http://www.microsoft.com/express
Microsoft Visual C++ Express (Namely Visual Studio Express For Desktop (SDK Included)
* OpenSSL Library http://slproweb.com/products/Win32OpenSSL.html
* cmake http://www.cmake.org/cmake/resources/software.html
* git http://code.google.com/p/tortoisegit/
* Windows Vista or newer. It does neither build nor run on XP.

There are reports that you need 32 bit OpenSSL even on a 64 bit System, otherwise the build fails.

If you like working in a shell, get cygwin. You can also use cygwins git, but NOT the cmake that comes with cygwin

==Obtaining the source==
<pre>git clone git://github.com/FreeRDP/FreeRDP.git</pre>

==Preparing the build==
From the command line, go to the directory where you pulled the sources and type
<pre>cmake .</pre>  If you wish to build for 64 bit systems an edit is required.  Edit winpr/sysinfo.c and change the line
<pre>#if "&#40;!defined&#40;_WIN32&#41;&#41; || &#40;defined&#40;_WIN32&#41; && &#40;_WIN32_WINNT < 0x0600&#41;&#41;"</pre> back to the original
<pre>#if &#40;!defined&#40_WIN32&#41;&#41; || &#40;defined&#40;_WIN32&#41; && &#40;_WIN32_WINNT < 0x0501&#41;&#41;</pre> and type
<pre>cmake . -G"Visual Studio 11 Win64"</pre>.  I will look for a way around this in the future as the compiler complains that GetTickCount64 is already defined.

If you have a multi targeting environment that targets Win32 and Win64, you'll note that OpenSSL is not in your path.  To add it at the cmake at the
<pre> -DOPENSSL_ROOT_DIR=c:/Openssl/Whatever</pre>

Of course, you can also run cmake-gui that comes with the windows cmake install and point it to your sources.
See [[Build options]] for a list of options you can specify.
== Building ==
In Visual Studio, open the FreeRDP project map and build it. It should build clean.

If you wish to build from the command line call the appropriate environment x64 -- x86_amd64 or x86 and call
<pre>msbuild FreeRDP.sln /p:Configuration=Debug or Release</pre>

and it does actually run.
== Plugin status ==
* rdpdr disk, printer and smartcard plugin are actively developed and should be available soon (Sept. 2012)
* cliprdr plugin lacks ~1000 lines of source and does not yet work, though it builds clean
* Status of all other plugins is unknown
* Command line has changed, see [[CommandLineInterface]]

== Dev Snapshot ==
* offical place is http://pub.freerdp.com/snapshots/
* Alternative Binaries from Huihong Luo are available here: [http://www.vmlite.com/VMLiteRemote.zip] This binary supports audio, RemoteFX and clipboard, but not the printer. Merging is in progress, please be patient