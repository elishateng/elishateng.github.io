---
layout: post
title: Linux Partition Table Repair
categories: Blog
description: Linux Partition Table Repair
keywords: partition, linux, repair
---

## TestDisk Usage
```sh
sudo apt-get install testdisk

#testdisk /dev/sdb
```
```
TestDisk 7.1, Data Recovery Utility, July 2019
Christophe GRENIER <grenier@cgsecurity.org>
https://www.cgsecurity.org

  TestDisk is free software, and
comes with ABSOLUTELY NO WARRANTY.

Select a media (use Arrow keys, then press Enter):
>Disk /dev/sdb - 500 GB / 465 GiB - WDC WD5000AAKX-75U6AA0








>[Proceed ]  [  Quit  ]

Note: Disk capacity must be correctly detected for a successful recovery.
If a disk listed above has an incorrect size, check HD jumper settings and BIOS
detection, and install the latest OS patches and disk drivers.
```
```
TestDisk 7.1, Data Recovery Utility, July 2019
Christophe GRENIER <grenier@cgsecurity.org>
https://www.cgsecurity.org


Disk /dev/sdb - 500 GB / 465 GiB - WDC WD5000AAKX-75U6AA0

Please select the partition table type, press Enter when done.
>[Intel  ] Intel/PC partition
 [EFI GPT] EFI GPT partition map (Mac i386, some x86_64...)
 [Humax  ] Humax partition table
 [Mac    ] Apple partition map (legacy)
 [None   ] Non partitioned media
 [Sun    ] Sun Solaris partition
 [XBox   ] XBox partition
 [Return ] Return to disk selection



Hint: Intel partition table type has been detected.
Note: Do NOT select 'None' for media with only a single partition. It's very
rare for a disk to be 'Non-partitioned'.
```
*如果不确定，可以选择Intel
```
TestDisk 7.1, Data Recovery Utility, July 2019
Christophe GRENIER <grenier@cgsecurity.org>
https://www.cgsecurity.org


Disk /dev/sdb - 500 GB / 465 GiB - WDC WD5000AAKX-75U6AA0
     CHS 60801 255 63 - sector size=512

>[ Analyse  ] Analyse current partition structure and search for lost partitions
 [ Advanced ] Filesystem Utils
 [ Geometry ] Change disk geometry
 [ Options  ] Modify options
 [ MBR Code ] Write TestDisk MBR code to first sector
 [ Delete   ] Delete all data in the partition table
 [ Quit     ] Return to disk selection





Note: Correct disk geometry is required for a successful recovery. 'Analyse'
process may give some warnings if it thinks the logical geometry is mismatched.
```
```
TestDisk 7.1, Data Recovery Utility, July 2019
Christophe GRENIER <grenier@cgsecurity.org>
https://www.cgsecurity.org

Disk /dev/sdb - 500 GB / 465 GiB - CHS 60801 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * Linux                    0  32 33 54840  96 40  881008640
 2 P Linux                54840  96 41 60801  47 46   95760384








*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
>[Quick Search]  [ Backup ]
                            Try to locate partition
```
```
TestDisk 7.1, Data Recovery Utility, July 2019
Christophe GRENIER <grenier@cgsecurity.org>
https://www.cgsecurity.org

Disk /dev/sdb - 500 GB / 465 GiB - CHS 60801 255 63
     Partition               Start        End    Size in sectors
>* Linux                    0  32 33 54840  96 40  881008640
 P Linux                54840  96 41 60801  47 46   95760384











Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
ext4 blocksize=4096 Large_file Sparse_SB Recover, 451 GB / 420 GiB
```
```
TestDisk 7.1, Data Recovery Utility, July 2019
Christophe GRENIER <grenier@cgsecurity.org>
https://www.cgsecurity.org

Disk /dev/sdb - 500 GB / 465 GiB - CHS 60801 255 63

     Partition                  Start        End    Size in sectors

 1 * Linux                    0  32 33 54840  96 40  881008640
 2 P Linux                54840  96 41 60801  47 46   95760384











 [  Quit  ]  [ Return ]  [Deeper Search] >[ Write  ]
                       Write partition structure to disk
```

Return and Reboot

Solved!
