FreeRDP and WinPR need a new debug system. The current utils are defined as macros in <freerdp/utils/debug.h>. The problem, however, is that it we are including config.h in private header files in order to define debug macros in a semi-automated manner. This should not be the case: debug macros should be easily defined within source files, not header files.

The problem is quite hard to solve: we need a flexible system that can handle various channels and levels of output. Common levels are "error, warning, trace, info". Channels are module-specific debug channels like "disk", "smartcard", "X11", etc. The output should have the ability to be filtered by both channel and level.

Also, we would need a way to redirect the output to the appropriate location. Right now, we are wrapping printf, which is not so great on Windows (we'd like to get rid of the terminal), and not so great when you'd like to collect logs. Other features such as forwarding the debug output over the network would be a bonus but not a requirement.

There are portability issues: format strings are not universal, especially for printing 64-bit values. Right now we are always adding a new line character and prefixing the output with the channel name, which is not very flexible. It turns out to be a problem when it's easier to print something over multiple lines. The degree of verbosity for the output should be easily filtered.

Besides portability of format strings, the debug utils should also handle UNICODE builds just as well as non-UNICODE builds. This means we might want to consider using WinPR's TCHAR macros.

***

## Implemetation Draft


    /* logging.h - Logging "subsystem" */

    #define LL_ERR  1
    #define LL_WARN 2
    #define LL_INFO 3

    #define LL_DEBUG 10 /* anything equal or above this level is debug */

    #define LOGGER(level, channel, msg, ...) log_msg (level, channel, msg, ## __VA_ARGS__)

    #ifdef _DEBUG
    #define LOGDBG(level, channel, msg, ...) log_msg (level, channel, msg, ## __VA_ARGS__)
    #else
    #define LOGDBG(level, channel, msg, ...)
    #endif


Usage:

`LOGGER(LL_ERR, _T("channelname"), _T("Something went wrong in %s"), anydata) ;`

Commandline switches should allow to set the minimum log level and which channels to be logged. The channelname is defined as string, so any module can define it's own channelname, without the need to have a central header file, which contains all channels.

LOGDBG statements will not included in the Release builds.

All log output above the currently set debuglevel will go to a log file. Later on other targets can be added.

LL_ERR will be handled special. Error message will in addition to be loged in the log file saved in a in memory list and outputed in a dialog box when freerdp terminates. This allows to display all errors not only the last one (which might be something not so usefull like "connection terminated") to the user. It also makes sure any thread can log an error, but only the main thread will display the dialog box.

This is similar to the an ealier push request which can be found at

https://github.com/FreeRDP/FreeRDP/commit/819f44fcca86513072032f141acc75b1dbdb0719

