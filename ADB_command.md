
adb shell screencap /storage/emulated/0/DCIM/screen_17.png && adb pull /storage/emulated/0/DCIM/screen_17.png /Users/Work_2/Android/screen_17.png

**делаем скриншот с тел. И сохраняем на комп.**

----------

adb logcat | grep -rnw "com.android. prilogenie " > /Users/Work_2/Android/crash_17.log

**Сохраняем лог накомп**

----------

adb logcat | grep -rnw "com.android.prilogenie"

**выводим лог приложения**

----------

adb devices
   
**выводим  список или один подкл девайс**

----------

adb reboot 
  
 **перезагрузка тел.**

----------

adb install /Users/todolist_1.apk     

**установка АРК в тел.**

----------

adb uninstall com.android.todolist      удаление АРК из тел.





#**Подключаем тел. По WIFI**#

**вводим по очередно эти команды**

adb start-server

adb devices

adb shell setprop service.adb.tcp.port 4444

adb tcpip 4444

    отключаем телефон от компа

adb connect ***IP телефона в сети WiFi***:4444

----------

----------




1. Android Debug Bridge version 1.0.32
1. 
1.  -a                            - directs adb to listen on all interfaces for a connection
1.  -d                            - directs command to the only connected USB device
1.                                  returns an error if more than one USB device is present.
1.  -e                            - directs command to the only running emulator.
1.                                  returns an error if more than one emulator is running.
1.  -s <specific device>          - directs command to the device or emulator with the given
1.                                  serial number or qualifier. Overrides ANDROID_SERIAL
1.                                  environment variable.
1.  -p <product name or path>     - simple product name like 'sooner', or
1.                                  a relative/absolute path to a product
1.                                  out directory like 'out/target/product/sooner'.
1.                                  If -p is not specified, the ANDROID_PRODUCT_OUT
1.                                  environment variable is used, which must
1.                                  be an absolute path.
1.  -H                            - Name of adb server host (default: localhost)
1.  -P                            - Port of adb server (default: 5037)
1.  devices [-l]                  - list all connected devices
1.                                  ('-l' will also list device qualifiers)
1.  connect <host>[:<port>]       - connect to a device via TCP/IP
1.                                  Port 5555 is used by default if no port number is specified.
1.  disconnect [<host>[:<port>]]  - disconnect from a TCP/IP device.
1.                                  Port 5555 is used by default if no port number is specified.
1.                                  Using this command with no additional arguments
1.                                  will disconnect from all connected TCP/IP devices.
1. 
1. device commands:
1.   adb push [-p] <local> <remote>
1.                                - copy file/dir to device
1.                                  ('-p' to display the transfer progress)
1.   adb pull [-p] [-a] <remote> [<local>]
1.                                - copy file/dir from device
1.                                  ('-p' to display the transfer progress)
1.                                  ('-a' means copy timestamp and mode)
1.   adb sync [ <directory> ]     - copy host->device only if changed
1.                                  (-l means list but don't copy)
1.                                  (see 'adb help all')
1.   adb shell                    - run remote shell interactively
1.   adb shell <command>          - run remote shell command
1.   adb emu <command>            - run emulator console command
1.   adb logcat [ <filter-spec> ] - View device log
1.   adb forward --list           - list all forward socket connections.
1.                                  the format is a list of lines with the following format:
1.                                     <serial> " " <local> " " <remote> "\n"
1.   adb forward <local> <remote> - forward socket connections
1.                                  forward specs are one of:
1.                                    tcp:<port>
1.                                    localabstract:<unix domain socket name>
1.                                    localreserved:<unix domain socket name>
1.                                    localfilesystem:<unix domain socket name>
1.                                    dev:<character device name>
1.                                    jdwp:<process pid> (remote only)
1.   adb forward --no-rebind <local> <remote>
1.                                - same as 'adb forward <local> <remote>' but fails
1.                                  if <local> is already forwarded
1.   adb forward --remove <local> - remove a specific forward socket connection
1.   adb forward --remove-all     - remove all forward socket connections
1.   adb reverse --list           - list all reverse socket connections from device
1.   adb reverse <remote> <local> - reverse socket connections
1.                                  reverse specs are one of:
1.                                    tcp:<port>
1.                                    localabstract:<unix domain socket name>
1.                                    localreserved:<unix domain socket name>
1.                                    localfilesystem:<unix domain socket name>
1.   adb reverse --norebind <remote> <local>
1.                                - same as 'adb reverse <remote> <local>' but fails
1.                                  if <remote> is already reversed.
1.   adb reverse --remove <remote>
1.                                - remove a specific reversed socket connection
1.   adb reverse --remove-all     - remove all reversed socket connections from device
1.   adb jdwp                     - list PIDs of processes hosting a JDWP transport
1.   adb install [-lrtsd] <file>
1.   adb install-multiple [-lrtsdp] <file...>
1.                                - push this package file to the device and install it
1.                                  (-l: forward lock application)
1.                                  (-r: replace existing application)
1.                                  (-t: allow test packages)
1.                                  (-s: install application on sdcard)
1.                                  (-d: allow version code downgrade)
1.                                  (-p: partial application install)
1.   adb uninstall [-k] <package> - remove this app package from the device
1.                                  ('-k' means keep the data and cache directories)
1.   adb bugreport                - return all information from the device
1.                                  that should be included in a bug report.
1. 
1.   adb backup [-f <file>] [-apk|-noapk] [-obb|-noobb] [-shared|-noshared] [-all] [-system|-nosystem] [<packages...>]
1.                                - write an archive of the device's data to <file>.
1.                                  If no -f option is supplied then the data is written
1.                                  to "backup.ab" in the current directory.
1.                                  (-apk|-noapk enable/disable backup of the .apks themselves
1.                                     in the archive; the default is noapk.)
1.                                  (-obb|-noobb enable/disable backup of any installed apk expansion
1. 
1.                                     (aka .obb) files associated with each application; the default
1. 
1.                                     is noobb.)
1.                                  (-shared|-noshared enable/disable backup of the device's
1.                                     shared storage / SD card contents; the default is noshared.)
1.                                  (-all means to back up all installed applications)
1.                                  (-system|-nosystem toggles whether -all automatically includes
1.                                     system applications; the default is to include system apps)
1.                                  (<packages...> is the list of applications to be backed up.  If
1.                                     the -all or -shared flags are passed, then the package
1.                                     list is optional.  Applications explicitly given on the
1.                                     command line will be included even if -nosystem would
1.                                     ordinarily cause them to be omitted.)
1. 
1.   adb restore <file>           - restore device contents from the <file> backup archive
1. 
1.   adb help                     - show this help message
1.   adb version                  - show version num
1. 
1. scripting:
1.   adb wait-for-device          - block until device is online
1.   adb start-server             - ensure that there is a server running
1.   adb kill-server              - kill the server if it is running
1.   adb get-state                - prints: offline | bootloader | device
1.   adb get-serialno             - prints: <serial-number>
1.   adb get-devpath              - prints: <device-path>
1.   adb status-window            - continuously print device status for a specified device
1.   adb remount                  - remounts the /system and /vendor (if present) partitions on the device read-write
1.   adb reboot [bootloader|recovery] - reboots the device, optionally into the bootloader or recovery program
1.   adb reboot-bootloader        - reboots the device into the bootloader
1.   adb root                     - restarts the adbd daemon with root permissions
1.   adb usb                      - restarts the adbd daemon listening on USB
1.   adb tcpip <port>             - restarts the adbd daemon listening on TCP on the specified port
1. networking:
1.   adb ppp <tty> [parameters]   - Run PPP over USB.
1.  Note: you should not automatically start a PPP connection.
1.  <tty> refers to the tty for PPP stream. Eg. dev:/dev/omap_csmi_tty1
1.  [parameters] - Eg. defaultroute debug dump local notty usepeerdns
1. 
1. adb sync notes: adb sync [ <directory> ]
1.   <localdir> can be interpreted in several ways:
1. 
1.   - If <directory> is not specified, /system, /vendor (if present), and /data partitions will be updated.
1. 
1.   - If it is "system", "vendor" or "data", only the corresponding partition
1.     is updated.
1. 
1. environmental variables:
1.   ADB_TRACE                    - Print debug information. A comma separated list of the following values
1.                                  1 or all, adb, sockets, packets, rwx, usb, sync, sysdeps, transport, jdwp
1.   ANDROID_SERIAL               - The serial number to connect to. -s takes priority over this if given.
1.   ANDROID_LOG_TAGS             - When used with the logcat option, only these debug tags are printed.
1. 
