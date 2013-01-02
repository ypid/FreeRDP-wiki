# (Longterm) Tasks and Todos
* Create test code for schannel (deeply linked with the certificate validation API)
* Create required subset of bcrypt api (http://msdn.microsoft.com/en-us/library/windows/desktop/aa376210/)
 * write stubs and tests
 * warp openssl (maybe other ssl libraries in future)
* Create more and in depth documentation
* Replacement for current debug system/macros - https://github.com/FreeRDP/FreeRDP/wiki/Debug-System
 * easy to use
 * option to output to a file
 * create a wrapper printf function in winpr, probably the one from the strsafe api, which provides us with a consistent format string format
* create a test plan for new releases - in progress (bm)
* add plug and play device redirection

## Tasks Corey is thinking of doing
* Windows Server
 * fix sound latency
 * send sound with parallel clients
 * handle when screen resizes/rotates/magic happens
 * refuse to run inside a remote desktop session
* C# GUI / Bindings
 * password auth
 * per client force disconnect
 * set max clients
 * simple IP filter
 * tray iconification
 * enumerate monitors and select screen to capture
* Mac Server
 * Keyboard support
 * Mouse support
 * Basic RemoteFX
 * Optimized RemoteFX
* Linux server
 * Lots of things