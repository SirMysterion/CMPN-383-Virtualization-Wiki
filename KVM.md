Written by: Calvin C

# What is KVM?
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

* **Hot plug vCPUs**: The ability to add/remove cpu without affecting the virtual Machine state
* **Dynamic Memory management:** KSM(Kernel Samepage Merging) is optimized to improve memory management for the cost of cpu power
* **Live Migration:** Allows the transportation of a VM without losing downtime
* **Over-committing:** Allocating more virtual CPU or memory than the available resource on the system to save money and power
* **Thin Provisioning:** Allocating only the minimal required amount of space
* **Disk I/O throttling:** a method to more efficiently handle memory processing

### Useful Tools
* [Kimchi](https://github.com/kimchi-project/kimchi/) – Web-based Virtualization management tool for KVM
* [Virtual Machine Manager](https://virt-manager.org/) – Supports creating, editing. Starting, and stopping KVM based virtual machines.

# Installation and Management Tools
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

Ensure KVM modules are loaded with
```
lsmod | grep kvm
```
The outputs should be kvm_intel or kvm_amd

![check](https://www.tecmint.com/wp-content/uploads/2015/01/Check-KVM-Kernel-Module.png)


### Management Tools
* **Virt-Manager:** provides a GUI tool

* **Virt-client:** Provides a CL tool

* **Virt-install:** provides the command "virt-install" to create VM from CLI

* **Virt-viewer** Display console for Virtual Machines

* **Libvirt:** provides the server and host side libraries for interacting with hypervisors and host systems

Install KVM package  
```
yum install qemu-kvm
```

Load Libvirtd daemon
```
systemctl enable --now libvirtd
```

### Creating the Virtual Machine
```
# virt-install --name=linuxconfig-vm \
--vcpus=1 \
--memory=1024 \
--cdrom=/tmp/debian-9.0.0-amd64-netinst.iso \
--disk size=5 \
--os-variant=debian8
```

* **name:** Assignment of the name for the Virtual Machine
* **vcpu:** Specifies the amount of CPU assigned
* **memory:** Determine the amount of memory in MiB assigned
* **cdrom:** Location of the OS iso to mount
* **disk:** Determine the amount of storage assigned
* **os-variant:** Configure the VM to a specific Operation System version
* 
### Interaction with Virtual Machine
View all configured Virtual Machine
```
virsh list --all
```
**Start VM on boot**
```
virsh autostart (vm name)
```
**Shut down the VM**
```
virsh shutdown (vm name)
```
**Delete the VM**
```
virsh undefine (vm name)
```
**Edit Machine settings**
```
virsh edit (vm name)
```

# Reference

* [Red Hat: What is KVM?](https://www.redhat.com/en/topics/virtualization/what-is-KVM)
* [Linux Mint: KVM - Kernel Based Virtual Machine](https://community.linuxmint.com/tutorial/view/1727)
* [WikiMili: KVM - Kernel Based Virtual Machine](https://wikimili.com/en/Kernel-based_Virtual_Machine)
* [InternetNews: Avi Kivity, 'Father' of KVM Virtualization](http://www.internetnews.com/infra/video-avi-kivity-father-of-kvm-virtualization.html)
* [Wikipedia: Kernel-based Virtual Machine](https://en.wikipedia.org/wiki/Kernel-based_Virtual_Machine)
* [Comparitech: Create Virtual Machine in Linux with KVM](https://www.comparitech.com/net-admin/create-virtual-machine-in-linux-with-kvm/)
* [Tecmint: Install and Configure KVM in Linux](https://www.tecmint.com/install-and-configure-kvm-in-linux/)
* [TheGeekStuff: How to Install Linux KVM and Create Guest VM](https://www.thegeekstuff.com/2014/10/linux-kvm-create-guest-vm/)
* [Linuxconfig: How to Create and Manage KVM from CLI](https://linuxconfig.org/how-to-create-and-manage-kvm-virtual-machines-from-cli)
