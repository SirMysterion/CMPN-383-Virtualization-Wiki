By: Thomas Peters

# Description
LXC (Linux Containers) is a method of of running multiple isolated Linux based containers with their own user spaces and allocated resources while still sharing the host Linux kernel. The Linux kernel provides support for cgroups and namespace isolation that allow limited CPU, memory, block I/O, and networking without staring dedicated virtual machines. This method of cgroups and namespaces allow for complete isolation between host and neighbour containers.

# Brief History
Although Container technology is the hot new buzz word the technology has been evolving for some time. While FreeBSD was one of the first to add container technology in the form of “jails” in 2000, 2001 brought about the VServer project to allowed “running several general purpose Linux server on a single box with a high degree of Independence and security.” The project ultimately failed it was one of the first attempts at containerizing processes. In 2006, Paul Menage adapted mainline kernel mechanisms to create Generic Process Containers later to be renamed "control groups" (or "cgroups") which became an important part of LXC. These cgroups allowed for processes to be grouped together with an allocation of cpu and disk I/O. Engineers from IBM around 2008 created the Linux Containers Project (LXC) that added userspace tooling on top of the aforementioned cgroups and namespaces. LXC 1.0 was released early 2014 and added improved security features with support with SELinux and Seccomp. Following on all prior developments, Docker originally wrapped all of the LXC userspace tools aimed for developers to create simple application packages. Docker has since dropped support for LXC as of v1.10

# Who owns it
While Developed originality by engineers from IBM, LXC is licensed under the GNU LGPLv2.1+ and as such is free software that allows for developers and companies to use and integrate LXC as the wish. The only requirement is that the newly created/modified work is also published and licensed under the same licence. See [GNU Lesser General Public License](https://en.wikipedia.org/wiki/GNU_Lesser_General_Public_License)


# How it is used
LXC containers fall in a category that is in between a Linux chroot environment and a fully virtualized VM with it’s own kernel. Being in this space allows for the creation of customized Linux application servers with their own assigned resources but without the overhead of a full Linux virtual machine with it’s own kernel. The downside of this implementation is that applications that require specific kernel modules to be loaded must also be loaded in the host’s kernel to be utilized.

# Examples of use
Proxmox ships with support for containers and uses LXC as it’s underlying container technology. LXC containers can be used anywhere a Linux environment is needed but without the additional Full VM overhead. This wiki is currently hosted in an LXC container that was deployed from an Ubuntu 20.04 LTS template and had Nginx and [Gollum](https://github.com/gollum/gollum) installed.

On Debian based systems LXC can bee installed with:
`sudo apt-get install lxc`
or
`sudo snap install lxd`

To get started with LXC, Create your first container with:
```
lxc-create -t download -n my-container
```

You can list running containers with 
```
lxc-ls -f
```

To access the running shell within the container:
```
lxc-attach -n my-container
```

Stopping containers can be done with:
```
lxc-stop -n my-container
```

And removing/deleting a container is done with:
```
lxc-destroy -n my-container
```

# Sources:

<https://en.wikipedia.org/wiki/LXC>  
<https://linuxcontainers.org>  
<https://www.redhat.com/en/blog/history-containers>  
