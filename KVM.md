Calvin C

# What is KVM
KVM, Kernal-based Virtual Machine, is one of the foremost open-source virtualization technologies that are utilized nowadays. IBM and Red Hat, multinational technology companies, use KVM as the premise for their Linux virtualization technologies, and it is most popularly used in the OpenStack cloud as well.

KVM, a virtualization module, found within the Linux kernel and it allows the kernel to act and function as a hypervisor. It provides hardware-assisted virtualization for a wide assortment of guest operating systems including Linux, Solaris, BSD, Windows, Haiku, macOS, and ReactOS. In addition, Android 2.2, GNU/Hurd, and many more other operating systems that are known to work, but with certain impediments. KVM furthermore provides paravirtualization support for Linux, OpenBSD, FreeBSD, NetBSD, and Windows guests using the VirtIO API. This incorporates a paravirtual ethernet card, disk I/O controller, balloon device, and a VGA graphics interface using SPICE or VMware drivers. To utilize KVM, it requires a CPU processor with hardware virtualization extensions, such as Intel’s Virtualization Technology or AMD Virtualization. 

# History

* KVM was originally written and developed by Avi Kivity, an Israeli software developer, in Mid-2006 while working at Qumranet, an enterprise software company that was acquired by Red Hat in 2008.

* KVM emerged in 2006 and merged into the Linux kernel mainline in kernel version 2.6.20 on February 5, 2007.

# How it works
Hypervisors require operating system-level components such as a memory manager, process scheduler, I/O stack, device drivers, security manager, and more to run VMs. KVM converts Linux into a bare-metal hypervisor as it has the ability to access all the components due to being part of the Linux Kernel. 

KVM adds a driver (/dev/kvm) that allows Intel and AMD’s hardware virtualization extensions to communicate with the x86 architecture and exposes the virtualization capabilities to the user. By utilizing the driver, it loads a host kernel module and a processor-specific module, and an emulator to run a virtual machine in its own virtual environment that contains its virtual hard disk, network adapters, and display.

![Linux Module](https://i.imgur.com/3XyFTun.png)

## Features

* Hot plug vCPUs
* Dynamic Memory management
* Live Migration
* Over-committing
* Thin Provisioning
* Disk I/O throttling
* Automatic NUMA balancing
* Virtual CPU hot add capability
* 

### Tools
Tools
* Kimchi – Web-based Virtualization management tool for KVM
* Virtual Machine Manager – Supports creating, editing. Starting, and stopping KVM based virtual machines.
* OpenORM – Management platform for managing heterogeneous data center

# example of use
The prerequisites for KVM requires you to verify that you have the hardware virtualization extension.

for Intel extension [vmx]
```
grep -e 'vmx' /proc/cpuinfo
```
![Intel](https://www.tecmint.com/wp-content/uploads/2015/01/Check-Virtualization-Support.png)
for AMD extension [svm]
```
grep -e 'svm' /proc/cpuinfo
```
![AMD](https://www.tecmint.com/wp-content/uploads/2015/01/Check-CPU-Virtualization-Support.png)

## How to create a new Virtual Machine

