# sd-fuse_s5p6818
Create bootable SD card for NanoPi M3/NanoPC T3


## Build android bootable SD card
```
# git clone https://github.com/friendlyarm/sd-fuse_s5p6818.git
# cd sd-fuse_s5p6818
# sudo ./fusing.sh /dev/sde android
```

## Build an sd card image
```
# git clone https://github.com/friendlyarm/sd-fuse_s5p6818.git
# cd sd-fuse_s5p6818
# wget http://112.124.9.243/dvdfiles/S5P6818/images-for-eflasher/android-lollipop-images.tgz
# tar xvzf android-lollipop-images.tgz
```
Now,  Change something under the android directory, 
for example, replace the file you compiled, then build android bootable SD card: 
```
# sudo ./fusing.sh /dev/sde android
```
or build an sd card image:
```
# sudo ./mkimage.sh android
```

## Build a package similar to S5P6818-eflasher-sd8g-yyyymmdd-full.img:
```
# git clone https://github.com/friendlyarm/sd-fuse_s5p6818.git
# cd sd-fuse_s5p6818
# sudo ./mkimage.sh eflasher
# DEV=`losetup -f`
# losetup ${DEV} S5P6818-eflasher-sd8g-20170819.img
# partprobe ${DEV}
# sudo mkfs.vfat ${DEV}p1 -n FRIENDLYARM
# mkdir -p /mnt/fat
# mount -t vfat ${DEV}p1 /mnt/fat
# sudo wget -qO- http://112.124.9.243/dvdfiles/S5P6818/images-for-eflasher/core-qte-images.tgz | tar xvz -C /mnt/fat --strip-components=1
# umount /mnt/fat
# losetup -d ${DEV}
```

