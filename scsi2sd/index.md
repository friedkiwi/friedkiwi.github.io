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


## 2015-12-28

I ordered two SCSI2SD cards today, and a bunch of adapters to connect them.  
They should arrive at mine's during the next couple of days, however, it might 
have a bit of a delay due to the holiday season.
