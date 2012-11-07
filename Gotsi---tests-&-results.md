
### Connection string

The testserver 192.168.16.3 is a Windows Server 2k8 R2 Std.

xfreerdp -u administrator -p pass -d 192.168.16.3 --ignore-certificate -g 1366x748 --rfx --plugin cliprdr --plugin rdpdr --data disk:A:/mnt/A disk:B:/mnt/B scard:scard -- --plugin drdynvc --data tsmf -- --plugin rdpdbg 192.168.16.3