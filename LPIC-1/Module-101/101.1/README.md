# Determine and configure hardware

## sysfs

Shows what happens in kernel mind about hardware.

```bash
ubuntu@dms-test:/sys/bus/cpu/devices$ ls /sys/
block  bus  class  dev  devices  firmware  fs  hypervisor  kernel  module  power
```

Here are some hardware related commands

**USB Devices Info**

```bash
ubuntu@dms-test:/sys/bus/cpu/devices$ lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse   
Bus 001 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

**PCI Devices Info**

```
ubuntu@dms-test:/sys/bus/cpu/devices$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:07.7 System peripheral: VMware Virtual Machine Communication Interface (rev 10)
00:0f.0 VGA compatible controller: VMware SVGA II Adapter
00:10.0 SCSI storage controller: Broadcom / LSI 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01)
00:11.0 PCI bridge: VMware PCI bridge (rev 02)
00:15.0 PCI bridge: VMware PCI Express Root Port (rev 01)
...
```

**Block Devices Info**

```bash
ubuntu@dms-test:/sys/bus/cpu/devices$ lsblk
NAME                      MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
sda                         8:0    0   50G  0 disk
├─sda1                      8:1    0    1M  0 part
├─sda2                      8:2    0    2G  0 part /boot      
└─sda3                      8:3    0   48G  0 part
  └─ubuntu--vg-ubuntu--lv 252:0    0   47G  0 lvm  /
sr0                        11:0    1  2.6G  0 rom
```

**Hardware Overview**

```bash
ubuntu@dms-test:/sys/bus/cpu/devices$ sudo lshw | tail -n 10
...
       logical name: /dev/input/event3
       logical name: /dev/input/mouse1
       capabilities: i8042
  *-input:3
       product: VirtualPS/2 VMware VMMouse
       physical id: 5
       logical name: input4
       logical name: /dev/input/event2
       logical name: /dev/input/mouse0
       capabilities: i8042
```

**Kenel Modules (Drivers)**

```bash
# module information
$ modinfo tls

# remove a module
$ rmmod tls

# load a module
$ modprobe tls
```

