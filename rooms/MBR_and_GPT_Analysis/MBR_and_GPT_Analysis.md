# MBR_and_GPT_Analysis

---

Keywords: MBR, GPT, partition schemes, bootkit

## Task 1

Almost quoting:
> "MBR and GPT are different partitioning schemes that act as a map for all of the partitions used in the disk"  

so they retain how all the partitions of the disk are stored.  
These 2 partition schemes are located at the beginning (the first sector) of the disk and contain informations about all the structure.

Because they act on a such low level, attackers can target it with a malware named _bootkit_ .

> A bootkit is an advanced type of stealth malware that infects a computer's low-level startup components-such as the Master Boot Record (MBR), Volume Boot Record (VBR), or UEFI firmware-so that malicious code runs before the operating system and security software ever load.

**MBR** (Master Boot Record)

**GPT** (GUID Partition Table)

```
What are the separate sections on a disk known as?
- partitions
```

```
Which type of malware infects the boot process?
- bootkits
```



## Task 2

Overall boot process 
1. Power-on the system (Hardware Initialization)
2. POST check (Power On Self Test)
3. Locate bootable device
4. Read MBR/GPT (the partition table)
5. Load bootloader  
Here should also have been `Load the Kernel` as a point 6
6. Load OS and User Space


BIOS (Basic Input/Output System) / UEFI (Unified Extensible Firmware Interface) 

Legacy BIOS runs in a 16-bit processor mode. This severely restricts how much memory the firmware can access (only 1 MB) and forces it to initialize hardware components sequentially, one after the other.

UEFI runs in 32-bit or 64-bit mode, allowing it to address significantly more memory. This enables UEFI to initialize hardware components simultaneously in parallel, drastically reducing the time it takes for the system to reach the operating system load screen.

So after pushing the power button, the motherboard initializes the components (the CPU being the first one). Then the CPU fetches and executes the chipset instructions (BIOS/UEFI) that say how the boot process will happen. 



POST (Power on self test)  
After the load of BIOS (or UEFI), it ensures that all system's hardware components are ok.


Locate the Bootable Device.  
The BIOS/UEFI has to locate the bootable devices (SSDs, HDDs, USBs). After locating, there comes the role of the MBR/GPT (in reading)

```
What is the name of the hardware diagnostic check performed during the boot process?
- Power-On-Self-Test
```

```
Which firmware supports a GPT partitioning scheme?
- UEFI
```

```
Which device has the operating system to boot the system?
- bootable device
```

## Task 3


