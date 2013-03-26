Thre are currently two command line interfaces, an old, deprecated one an a new one which was designed to give better interoperability with Windows and is easier to user. Generally speaking, you can now use both --log-option or /long-option. You should use the new interface now the old interface is just kept for compatibility and will be dropped at some point.


# New style options
## Plugins
* \+clipboard : redirect clipboard
* /drive:&lt;sharename&gt;,&lt;path&gt; : Redirect &lt;path&gt; as share &lt;sharename&gt;
* /smartcard:&lt;device&gt; : Redirect smartcard &lt;device&gt;
* /printer:&lt;device&gt;,&lt;driver&gt; : Redirect a specific printer. Redirecting all printers does not currently work.
* /serial:&lt;device&gt; : redirect serial port &lt;device&gt; 
* /parallel:&lt;device&gt;  : redirect parallel port &lt;device&gt; 
* /microphone:sys:alsa : Redirect audio input
* /sound:sys:alsa : Redirect audio output
* /multimedia:sys:alsa : Multimedia redirection
* /usb:id,&lt;usbid&gt; : Redirect usb device &lt;usbid&gt;. Usbid is a string like dev:054c:0268

## Other options
Syntax: /flag enables flag, +toggle or -toggle enables or disables toggle. /toggle and +toggle are the same. Options with values work like this: /option:&lt;value&gt;    
*    /v:&lt;server&gt;&#91;:port&#93;   	Server hostname
*    /port:&lt;number&gt;       	Server port
*    /w:&lt;width&gt;           	Width
*    /h:&lt;height&gt;          	Height
*    /size:&lt;width&gt;x&lt;height&gt;	Screen size
*    /f                   	Fullscreen mode
*    /bpp:&lt;depth&gt;         	Session bpp (color depth)
*    /kbd:0x&lt;layout id&gt; or &lt;layout name&gt;	Keyboard layout
*    /kbd-list            	List keyboard layouts
*    /kbd-type:&lt;type id&gt;  	Keyboard type
*    /kbd-subtype:&lt;subtype id&gt;	Keyboard subtype
*    /kbd-fn-key:&lt;function key count&gt;	Keyboard function key count
*    /admin               	Admin (or console) session
*    /multimon            	Multi-monitor
*    /workarea            	Work area
*    /t:&lt;title&gt;           	Window title
*    +decorations (default:off)	Window decorations
*    /a                   	Addin (additional plugins)
*    /vc                  	Static virtual channel, see plugins section
*    /dvc                 	Dynamic virtual channel, see plugins section
*    /u:&#91;&lt;domain&gt;\&#93;&lt;user&gt; or &lt;user&gt;&#91;@&lt;domain&gt;&#93;	Username
*    /p:&lt;password&gt;        	Password
*    /d:&lt;domain&gt;          	Domain
*    /g:&lt;gateway&gt;&#91;:port&#93;  	Gateway Hostname
*    /gu:&#91;&lt;domain&gt;\&#93;&lt;user&gt; or &lt;user&gt;&#91;@&lt;domain&gt;&#93;	Gateway username
*    /gp:&lt;password&gt;       	Gateway password
*    /gd:&lt;domain&gt;         	Gateway domain
*    /app:||&lt;alias&gt; or &lt;executable path&gt;	Remote application program
*    /app-name:&lt;app name&gt; 	Remote application name for user interface
*    /app-icon:&lt;icon path&gt;	Remote application icon for user interface
*    /app-cmd:&lt;parameters&gt;	Remote application command-line parameters
*    /app-file:&lt;file name&gt;	File to open with remote application
*    /app-guid:&lt;app guid&gt; 	Remote application GUID
*    +compression (default:off)	Compression
*    /shell               	Alternate shell
*    /shell-dir           	Shell working directory
*    /audio-mode          	Audio output mode
*    /mic                 	Audio input (microphone)
*    /network             	Network connection type
*    +clipboard (default:off)	Redirect clipboard
*    +fonts (default:off) 	Smooth fonts (cleartype)
*    +aero (default:off)  	Desktop composition
*    +window-drag (default:off)	Full window drag
*    +menu-anims (default:off)	Menu animations
*    -themes (default:on) 	Themes
*    -wallpaper (default:on)	Wallpaper
*    /gdi:&lt;sw|hw&gt;         	GDI rendering
*    /rfx                 	RemoteFX
*    /rfx-mode:&lt;image|video&gt;	RemoteFX mode
*    /frame-ack:&lt;number&gt;  	Frame acknowledgement
*    /nsc                 	NSCodec
*    /jpeg                	JPEG codec
*    /jpeg-quality:&lt;percentage&gt;	JPEG quality
*    -nego (default:on)   	protocol security negotiation
*    /sec:&lt;rdp|tls|nla|ext&gt;	force specific protocol security
*    -sec-rdp (default:on)	rdp protocol security
*    -sec-tls (default:on)	tls protocol security
*    -sec-nla (default:on)	nla protocol security
*    +sec-ext (default:off)	nla extended protocol security
*    /cert-name:&lt;name&gt;    	certificate name
*    /cert-ignore         	ignore certificate
*    /pcb:&lt;blob&gt;          	Preconnection Blob
*    /pcid:&lt;id&gt;           	Preconnection Id
*    /vmconnect:&lt;vmid&gt;    	Hyper-V console (use port 2179, disable negotiation)
*    -authentication (default:on)	authentication (hack!)
*    -encryption (default:on)	encryption (hack!)
*    -grab-keyboard (default:on)	grab keyboard
*    -mouse-motion (default:on)	mouse-motion
*    /parent-window:&lt;window id&gt;	Parent window id
*    -bitmap-cache (default:on)	bitmap cache
*    -offscreen-cache (default:on)	offscreen bitmap cache
*    -glyph-cache (default:on)	glyph cache
*    /codec-cache:&lt;rfx|nsc|jpeg&gt;	bitmap codec cache
*    -fast-path (default:on)	fast-path input/output
*    /version             	print version
*    /help                	print help

# Old style options
## Plugins
Option handling was very counter intuitive. The general syntax was --plugin &lt;pluginname&gt;  &#91; --data &lt;plugindata&gt; -- &#93;

* -- plugin cliprdr : Synchronize client and server clipboard data. Plain text, Unicode text, HTML content and images are supported on UX platforms. For xfreerdp on Mac, only text works due to the interaction between X Server and the Mac. For windows, cliprdr does not work.

* --plugin rdpdr --data &lt;subplugin&gt; &#91;&lt;subplugin&gt; ...&#93; -- : Redirects file system devices on your client to the server. &lt;subplugin&gt; can be one of more of the following:

    + disk:&lt;sharename&gt;:&lt;path&gt; Redirect &lt;path&gt; to the server as shared folder \\tsclient\&lt;sharename&gt;.

    + printer&#91;:&lt;printername&gt;&#91:&lt;driver&gt;&#93;&#93; Redirect printers to the server. Redirecting all printers does not work right now.

    + serial:&lt;sharename&gt;:&lt;device&gt; Redirect serial &lt;device&gt; to the server. It will be referenced by &lt;sharedname&gt;.

    + parallel:&lt;sharedname&gt;:&lt;lptdevice&gt; Redirects parallel device &lt;lptdevice&gt; on your client to the server, where it will be referenced by <sharedname>. Bidirectional/Read support requires Windows XP or newer. 

* --plugin drdynvc --data &lt;subplugin&gt; &#91;&lt;subplugin&gt; ...&#93; -- : Load the Dynamic Virtual Channel. &lt;ubplugin&gt; can be the DVC sub-plugin name, or a path specifying the sub-plugin module. If the DVC sub-plugin name was passed, xfreerdp will try to locate the sub-plugin in its plugin path. Allowed subplugins:

    + audin Redirect audio recording device to the server. This is an RDP 7.0 feature available in Windows 7, Windows 2008 and Windows 2008 R2. Note that Windows 7 Enterprise edition and Windows 2008 Server has audio redirection disabled by default.

## Other options

*  -0: connect to console session
*  -a: set color depth in bit, default is 16
*  -c: initial working directory
*  -D: hide window decorations
*  -T: window title
*  -d: domain
*  -f: fullscreen mode
*  -g: set geometry, using format WxH or X% or 'workarea', default is 1024x768
*  -h: print this help
*  -k: set keyboard layout ID
*  -K: do not interfere with window manager bindings
*  -n: hostname
*  -o: console audio
*  -p: password
*  -s: set startup-shell
*  -t: alternative port number, default is 3389
*  -u: username
*  -x: performance flags (m[odem], b[roadband] or l[an])
*  -X: embed into another window with a given XID.
*  -z: enable compression
*  --app: RemoteApp connection. This implies -g workarea
*  --ext: load an extension
*  --no-auth: disable authentication
*  --authonly: authentication only, no UI
*  --from-stdin: unspecified username, password, domain and hostname params are prompted
*  --no-fastpath: disable fast-path
*  --no-motion: don't send mouse motion events
*  --gdi: graphics rendering (hw, sw)
*  --no-osb: disable offscreen bitmaps
*  --no-bmp-cache: disable bitmap cache
*  --bcv3: codec for bitmap cache v3 (rfx, nsc, jpeg)
*  --rfx: enable RemoteFX
*  --rfx-mode: RemoteFX operational flags (v[ideo], i[mage]), default is video
*  --frame-ack: number of frames pending to be acknowledged, default is 2 (disable with 0)
*  --nsc: enable NSCodec (experimental)
*  --disable-wallpaper: disables wallpaper
*  --composition: enable desktop composition
*  --disable-full-window-drag: disables full window drag
*  --disable-menu-animations: disables menu animations
*  --disable-theming: disables theming
*  --no-nego: disable negotiation of security layer and enforce highest enabled security protocol
*  --no-rdp: disable Standard RDP encryption
*  --no-tls: disable TLS encryption
*  --no-nla: disable network level authentication
*  --ntlm: force NTLM authentication protocol version (1 or 2)
*  --ignore-certificate: ignore verification of logon certificate
*  --certificate-name: use this name for the logon certificate, instead of the server name
*  --sec: force protocol security (rdp, tls or nla)
*  --tsg: Terminal Server Gateway (<username> <password> <hostname>)
*  --kbd-list: list all keyboard layout ids used by -k
*  --no-salted-checksum: disable salted checksums with Standard RDP encryption
*  --pcid: preconnection id
*  --pcb: preconnection blob
*  --version: print version information

# Source
Command line options are derived from a datastructure. You can dump this using _xfreerdp --help_ or _xfreerdp /help_