mount microsoft formatted exfat drive:

```
sudo apt-get install exfat-fuse exfat-utils
sudo mkdir /media/SSD
sudo mount -t auto /dev/sda2 /media/SSD

```

persist after boot method:
```
vi /etc/fstab
```
add the following:
(note: nofail will keep the os from locking you out if the drive fails to mount!
nonemtpy option will allow drive to be mounted even if their are files in the diretory)

```
/dev/sda2 /media/SSD auto defaults,nofail,nonempty  0   0
```
to keep binary backups of sd card trim and not bloated with deleted files:
(can be run periodically as cron on mounted file system)
(note: caution, experimental)
```
sudo fstrim -v /
```

if pi loses wifi connectivity, can try restarting the interface:
```
sudo systemctl daemon-reload
sudo systemctl restart dhcpcd
```
