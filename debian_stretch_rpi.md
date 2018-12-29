mount microsoft formatted ext4 drive:

```
sudo apt-get install exfat-fuse exfat-utils
sudo mkdir /media/SSD
sudo mount -t auto /dev/sda2 /media/SSD

```

persist after boot method:
```
vi /etc/fstab
```
add:

```
/dev/sda2 /media/SSD auto defaults,nofail,nonempty  0   0
```
