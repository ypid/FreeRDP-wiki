
===== RemoteApp =====

RemoteApp is defined in: 
[[http://msdn.microsoft.com/en-us/library/cc242568/|[MS-RDPERP]:   Remote Desktop Protocol: Remote Programs Virtual Channel Extension]] 

==== Packet Captures ====

Windows 7 SP1 to Windows Server 2008 R2 (Firefox 4): {{:mstsc_remoteapp.zip|}}

==== Virtual Channels ====

Even though [MS-RDPERP] mentions a single virtual channel, "rail", the packet capture shows the client registering "rail", "rail_ri" and "rail_wi".

More details about "rail_ri" and "rail_wi" can be found on this page 
http://social.msdn.microsoft.com/Forums/en-US/os_windowsprotocols/thread/d91b20a2-96af-406c-aa56-085058a0af44/ 

==== Remote App usage ====
Now this mode is supported only by development branch of FreeRDP-1.0 version.
You can grab latest sources from here https://github.com/FreeRDP/FreeRDP-1.0 and compile it.

**How to run xfreerdp with RemoteApp support mode?**

./client/X11/xfreerdp -u <UserName> -p <Password> ---app ---plugin channels/rail/rail.so ---data <ExeOfFile>:<WorkingDir>:<Arguments> --- <ServerHost>

where:
<UserName>
user name (login)

<Password>
password credentials

<ExeOfFile>
application identification.
Is can be specified by alias ('||cmd') and by full path to executive file ('c:\windows\system32\cmd.exe')
For creating alias you must add '||' prefix to alias name, which specifies in RemoteApp Manager on TS server.

<WorkingDir>
Working directory for application, which is set on application start.

<Arguments>
Command line arguments for application. They are MUST be allowed on server for each application individually.

<ServerHost>
IP address or DNS name of RDP server.
Examples:
./client/X11/xfreerdp -u test -p testpassword ---app ---plugin channels/rail/rail.so ---data '||wordpad' --- terminal.contoso.com
./client/X11/xfreerdp -u test -p testpassword ---app ---plugin channels/rail/rail.so ---data 'c:\notepad.exe' --- terminal.contoso.com
