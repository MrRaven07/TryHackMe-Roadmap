# More_on_MBR

---

Introduced in the 1980s, MBR is the legacy standard. It is tightly coupled with the older BIOS (Basic Input/Output System) firmware.

## MBR structure

Summary:
- Introduced: 1983
- Max capacity: 2TB
- Max partitions: 4 Primary (or 3 + 1 Extended)
- Firmware match: (Legacy BIOS)
- Data redundency: none, Single point of failure (SPOF)
- Error Checking: none

MBR occupies exactly the first 512 bytes (Sector 0) of the disk. This controls the entire drive and is divided into three parts:

1. Master Boot Code (446 bytes): A small program that identifies the active (bootable) partition and loads the operating system into memory.
2. Partition Table (64 bytes): The actual map of the drive. Since each partition entry requires 16 bytes, MBR can only natively support a maximum of four primary partitions (64 / 16 = 4).
3. Boot Signature (2 bytes): A "Magic Number" (`55 AA` in hexadecimal) that tells the BIOS this sector contains a valid bootloader.


## MBR Limitations

Capacity Limit: MBR uses 32-bit logical block addressing ([LBA](https://en.wikipedia.org/wiki/Logical_block_addressing) , this wikipedia article lead me to some interesting rabbit holes, like ). This caps the maximum addressable space at 2 Terabytes (TB). Any space beyond 2 TB on a modern drive is invisible to an MBR layout and wasted.

Partition Limit: The user is restricted to 4 primary partitions. To get more, they must convert one into an "extended partition," which can hold multiple "logical partitions", a complex and easily corrupted workaround.

Single Point of Failure: All partition and boot data lives in Sector 0. If a virus or physical bad sector corrupts this specific area, the entire drive becomes unreadable and the system will not boot.


