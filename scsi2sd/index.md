# SCSI2SD/400

I have a few older AS/400 machines, however, their SCSI disks are starting to 
go to data-heaven, and it's getting increasingly hard to find the right disks.  
IBM forces you to use the right types of disks for your machine, ruling out 
third party replacement disks. To complicate matters even more, a non-standard 
sector size is being used.

However, there is a neat SCSI-to-SD adapter from [codesrc](
http://www.codesrc.com/mediawiki/index.php?title=SCSI2SD) which is based on a 
Cypress microcontroller, and the firmware is Open Source. Since my machine is 
only a hobbyist machine, I don't expect heavy load, so it should be possible to 
just run it off a couple of SD cards using this. Due to the OSS nature, it 
should also be feasible to add the non-standard IBM gimmicks.

## 2015-12-30

I connected two same-sized IBM-branded disks to a Sun machine with a working 
SCSI controller, and discovered that the following VPD tables are available:

* 0x3
* 0xc0
* 0xc4
* di
* iod
* sn

The 0xc0 table on both disks turned out to be identical:

disk A:
```
  00000000  00 c0 00 14 00 00 00 41  20 20 20 20 20 20 20 20  |.......A        |
  00000010  20 01 00 04 01 0c 00 00                           | .......|
  00000018
```
disk B:
```
  00000000  00 c0 00 14 00 00 00 41  20 20 20 20 20 20 20 20  |.......A        |
  00000010  20 01 00 04 01 0c 00 00                           | .......|
  00000018
```
And the 0xc4 table on both disks contained their serial number information:

disk A:
```
  00000000  00 c4 00 24 20 20 20 20  20 20 20 20 36 38 34 35  |...$        6845|
  00000010  41 42 38 39 56 33 56 44  47 4e 57 41 37 31 50 37  |AB89V3VDGNWA71P7|
  00000020  34 33 30 20 20 20 20 20                           |430     |
  00000028
```

disk B:
```
  00000000  00 c4 00 24 20 20 20 20  20 20 20 20 36 38 34 44  |...$        684D|
  00000010  39 43 34 37 56 33 56 59  59 35 44 41 37 31 50 37  |9C47V3VYY5DA71P7|
  00000020  34 33 30 20 20 20 20 20                           |430     |
  00000028
```

Upon searching my stack of disks, I found an older disk which works in my machine, but it's missing the 0xc0 and 0xc4 tables - it only has the custom 0x3 table. That makes it an ideal candidate for the OS to check if it's a valid IBM disk or not.

The following tables have been observed on my disks:

disk A:
```
00000000  00 03 00 24 00 00 00 00  a1 70 02 ca 00 01 00 46  |...$.....p.....F|
00000010  00 00 00 00 00 00 00 00  20 20 20 20 20 20 20 20  |........        |
00000020  20 20 20 20 00 00 00 00                           |    ....|
00000028
```

disk B:
```
00000000  00 03 00 24 00 00 00 00  a1 70 02 ca 00 01 00 46  |...$.....p.....F|
00000010  00 00 00 00 00 00 00 00  20 20 20 20 20 20 20 20  |........        |
00000020  20 20 20 20 00 00 00 00                           |    ....|
00000028
```

disk C:
```
00000000  00 03 00 24 00 00 00 00  a1 70 02 b1 00 01 00 13  |...$.....p......|
00000010  00 00 00 00 00 00 00 00  20 20 20 20 20 20 20 20  |........        |
00000020  20 20 20 20 00 00 00 00                           |    ....|
00000028
```


## 2015-12-28

I ordered two SCSI2SD cards today, and a bunch of adapters to connect them.  
They should arrive at mine's during the next couple of days, however, it might 
have a bit of a delay due to the holiday season.
