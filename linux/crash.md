# Ways to Get Out of a Linux Crash

## Go to virtual console
Press Ctrl + Alt + F3.
In Ubuntu base systems F1 response for login screen F3 for ghnome-shell, and F3-F7 response for virtual terminals .

After that, enter command below to the virtual terminal:
```bash
sudo systemctl restart gdm3
```
For KDE write sddm, as for DE/WM -> lightdm

## Kill DE process
```bash
ps aux | grep X
```
Like in first example, Ubuntu base system will have virtual position vt2(vt1 for login).
Then kill the process.
```bash
sudo kill -9 "process number"
```

## Use shut down
```bash
sudo shutdown -r now 
sudo kill -9 1203
```

##  REISUB
Press and hold key combination Alt + SysRq(Print Screen) after that enter one by one letters R.E.I.S.U.B 
It will implement followed actions:
-   R: Switch the keyboard from raw mode to XLATE mode
-   E: Send the SIGTERM signal to all processes except init
-   I: Send the SIGKILL signal to all processes except init
-   S: Sync all mounted filesystems
-   U: Remount all mounted filesystems in read-only mode
-   B: Immediately reboot the system, without unmounting partitions or syncing
