> **Note**,
> this information/guide is compiled information from sources listed at the bottom.  
> This is for IT firmware(HBA), IR firmware(RAID) is also included just change the file name in the command to ```2108ir.bin```  
> It is only for the LSI SAS 9210-8i card but can be used for other cards by downloading and replacing the firmware file from link at the bottom.  


## How to:
* Download attached zip or find files in resources.
* Format a USB drive to FAT/FAT32 and unzip all files to it.
* Plug drive into pc and preferably disconnect all other drives (Some SSDs can have controllers that you may accidentally flash)
* Figure out if your motherboard is UEFI or BIOS and go to that part

----

### UEFI Motherboard:
* Get into BIOS and figure out how to boot an EFI shell and do it. Usually in Exit, mine is labeled "Launch EFI Shell from USB drives"
* Once in shell type ```map``` to display what drives are detected, then type ```mount <yourdrive>``` to mount the drive. ie, I typed ```mount fs0```
* Type ```ls``` or ```dir``` to see and verify files

##### Flashing:
* ```sas2flash.efi -listall``` to show the controller and verify the current version.
* ```sas2flash.efi -o -e 6``` to erase the firmware, do not reboot after this command.
* ```sas2flash.efi -o -f 2108it.bin -b mptsas2.rom``` to write the new firmware and BIOS.
* ```sas2flash.efi –listall``` once more to verify the updated card.
Done!

----
  
### BIOS Motherboard:
* Get into BIOS and boot freeDOS from the drive.

##### Flashing:
* ```sas2flsh.exe -listall``` to show the controller and verify the current version.
* ```sas2flsh.exe -o -e 6``` to erase the firmware, do not reboot after this command.
* ```sas2flsh.exe -o -f 2108it.bin -b mptsas2.rom``` to write the new firmware and BIOS.
* ```sas2flsh.exe –listall``` once more to verify the updated card.
Done!

----
  
### Links and resources:
##### Firmware: 
* https://www.broadcom.com/support/download-search

##### Guides: 
* https://www.truenas.com/community/resources/detailed-newcomers-guide-to-crossflashing-lsi-9211-9300-9305-9311-9400-94xx-hba-and-variants.54/
* https://digitalcardboard.com/blog/2014/07/09/flashing-it-firmware-to-the-lsi-sas-9211-8i-hba-2014-efi-recipe/
* https://nguvu.org/freenas/Convert-LSI-HBA-card-to-IT-mode/
