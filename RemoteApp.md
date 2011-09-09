RemoteApp is defined in 
[[MS-RDPERP]:   Remote Desktop Protocol: Remote Programs Virtual Channel Extension](http://msdn.microsoft.com/en-us/library/cc242568/)

# Packet Captures

Windows 7 SP1 to Windows Server 2008 R2 (Firefox 4): mstsc_remoteapp.zip

# Virtual Channels

Even though [MS-RDPERP] mentions a single virtual channel, "rail", the packet capture shows the client registering "rail", "rail_ri" and "rail_wi".

More details about "rail_ri" and "rail_wi" can be found on this [page](http://social.msdn.microsoft.com/Forums/en-US/os_windowsprotocols/thread/d91b20a2-96af-406c-aa56-085058a0af44/).

# Usage

RemoteApp support was introduced in FreeRDP 1.0, so you should get the latest sources from git.

    ./client/X11/xfreerdp -u <username> -p <password> --app --plugin channels/rail/rail.so --data "<app>:<working_dir>:<arguments>" -- <hostname>

    ./client/X11/xfreerdp -u Administrator -p Password --app --plugin channels/rail/rail.so --data "||cmd" -- 192.168.1.200
