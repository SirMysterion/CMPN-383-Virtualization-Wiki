### **Authors: Dan K, Brennan W**

## What is CloudStack?
CloudStack can be defined as an open-source cloud computing software for creating, managing, and deploying infastructure cloud services. It is designed to deploy and manage large networks of Virtual Machines, while also being highly available and scalable. The software uses existing popular Hypervisor platforms such as KVM, VMware Vsphere with ESXI and vCentre, and XenServer/XCP. CloudStack is Java based and provides support for it's own API, though also provides support for AWS (Amazon Web Services) and open cloud computing interface via the open grid forum. [1]

## History

* The software was originally developed out of Cupertino, California by a company known as VMops created by its founding members Sheng Liang, Shannon Williams, ALex Huang, Will Chan, and Chiradeep Vittal in 2008. VMops raised approximately $17.6 million in funding from Redpoint Ventures, Nexus Ventures, and Index Ventures and eventually changed it's name from VMops to Cloud.com in 2010 upon announcing its product CloudStack.[1]

* May 2010 CloudStack was released as a free software under the General Public License (A series of widely used free software licences that guarentee end users the freedom to run, study, share, and modify software), though kept roughly 5% of CloudStack software proprietary.[1]

* In October of 2010, Cloud.com announced a parternship with Microsoft that would then develop integration and support for the software with Windows Server 2008 R2 Hypver-V.[1]

* In July 2011, Cloud.com was purchased by Citrix Systems for approximately $200 million. The following month Citrix relased what proprietary code was remaining under the Apache Software License. CloudStack 3.0 was released in April 2012 and was donated to the Apache Software Foundation where it was then accepted into the Apache Incubator. At this point Citrix ceased development on the software. 
* In November of 2012, CloudStack 4.0 was announced and in March 2013 the software became a Top Level Product (Among the list of projects within the Apache Software Foundation development), with the first stable release of CloudStack being released in 4.0.2.[1]


## How does it work?
CloudStack works by using a Management Server to control many hypervisors from a single management interface. The minimum installation requires 1 machine that must run as the management server, with another machine that acts as the cloud infastructure. First, you must set up the management server, which typically runs on a dedicated physical or virtual machine, then you must specify the resources which are to be managed. This management server then controls the allocation of virtual machines to hosts, and assigns storage and IP addressing as well as other resources to the virtual machines launched within the cloud environment. The management server runs within an Apcache Tomcat container and contains it's own MySQL Database.[2],[3] 

## CloudStack Architecture
The CloudStack environment works by having the management server manage specific resources, these being:
### Regions
A collection of one or more geographically close zones managed by one or more management servers, a Region is the largest available organizational unit (OU) within a CloudStack deployment. Each region is controlled by it's own cluster of management servers (or mangaement server). Regions provide fault tolerance and disaster recovery by segregating resources. Grouping resources into multiple geographic regions provides increased reliability within the cloud.[3],[4]

![RegImage](http://docs.cloudstack.apache.org/projects/archived-cloudstack-getting-started/en/latest/_images/region-overview.png)
Image Source: [3] [https://docs.cloudstack.apache.org/projects/archived-cloudstack-getting-started/en/latest/concepts.html](https://docs.cloudstack.apache.org/projects/archived-cloudstack-getting-started/en/latest/concepts.html)

### Zones
A zone is the second largest OU within CloudStack. A zone typically can be compared to a single datacentre, although it is possible to be running multiple datacentres within a single zone. Each seperate zone contains its own power, network, and is capable of being seperated geographically in order to provide both physical isolation and added redundancy. A zone contains one or more pods as well as one or more pirmary storage servers which are then shared by all the pods within the same zone. A zone also contains secondary storage which is also shared by all pods in the respective zone.

Zones are capable of being public, or private. Public zones are visible to all users, meaning that any user may create a guest within that zone. Private zones however are reserved for a specific domain and only users within that domain or its subdomains may create guests in that zone. Hosts within the same zone are direclty accessible to one another without having to bypass any barriers such as firewalls, hosts in different zones are capable of accessing one another via a VPN tunnel. 

When a new zone is created, the admin will be prompted to configure the zones physical network, create the first pod, cluster, host, primary, and secondary storage. At the created of a zone a VMware datacentre must be specified, and in order to support live migration of hosts within that zone ONLY one VMware datacentre should be used.[3],[4]

![zoneimage](http://docs.cloudstack.apache.org/projects/archived-cloudstack-getting-started/en/latest/_images/zone-overview.png)

Image Source: [3] [https://docs.cloudstack.apache.org/projects/archived-cloudstack-getting-started/en/latest/concepts.html](https://docs.cloudstack.apache.org/projects/archived-cloudstack-getting-started/en/latest/concepts.html)

### Pods
A pod is the third largest OU within CloudStack and often relates to a single rack found within a datacentre (Zone). Hosts found within the same pod are also found within the same subnet. Pods are contained within Zones, with each zone being capable of containing multiple different pods, similar to how multiple subnets can be found within a given network. 

Pods consist of one or more clusters of hosts as well as one or more primary servers. Pods are NOT visible to the end user, therefore they are not aware of which pod location they can be found.[3],[4]

![podimage](http://docs.cloudstack.apache.org/projects/archived-cloudstack-getting-started/en/latest/_images/pod-overview.png)

Image Source: [3] [https://docs.cloudstack.apache.org/projects/archived-cloudstack-getting-started/en/latest/concepts.html](https://docs.cloudstack.apache.org/projects/archived-cloudstack-getting-started/en/latest/concepts.html)

### Clusters
Clusters consist of one or more hosts as well as one or more primary storage servers and are next in terms of size when analyzing a CloudStack environment. Clusters provide a means of easily grouping hosts, with a Cluster commonly being associated with being a KVM Server, Xenserver Server Pool, or VMware Cluster.

Hosts within a given cluster all have identical hardware, run the same hypervisor, use the same primary storage, and are found within the same subnet (since a Pod is one given subnet). By accessing the same storage device, this means that VM instances can be migrated from one host to another within the same cluster without any interuption to services or to that user. Multiple clusters can be deployed into a single pod environment, and even when using 1 singluar host, a cluster is still a mandatory OU.[3],[4]

![clusterimage](http://docs.cloudstack.apache.org/projects/archived-cloudstack-getting-started/en/latest/_images/cluster-overview.png)

Image Source: [3] [https://docs.cloudstack.apache.org/projects/archived-cloudstack-getting-started/en/latest/concepts.html](https://docs.cloudstack.apache.org/projects/archived-cloudstack-getting-started/en/latest/concepts.html)

### Hosts
Hosts are the smallest OU found within CloudStack and signify a single computer capabale of providing resources that can then run guest Virtual Machines in the CloudStack environment. Each host has it's own hypervisor software installed which is then used to manage whichever guest VM's are created. 

Hosts provide the CPU, memory, storage, and network resources needed to host VM's. Different hosts may have different capacities of these resources, though hosts found within the same cluster MUST be the same. Additional hosts can be added at any given time, with CloudStack being capable of detecting the amount of CPU and Memory provided by the hosts upon creation. Hosts are NOT visible to the end user, therefore the user cannot detect which host their guest VM was created under.[3],[4] 


### Primary Storage
Primary Storage is commonly associated with a cluster and is known to store the virtual disks for all the VM's that are currently running on hosts within that cluster. Although only 1 primary storage is required, multiple can be configured with any of this storage usually being configured as close to it's hosts as possible to increase performance. 

Although Primary Storage is often placed within the cluster, this cluser-wide storage also means that the data is only directly available to the VM's found within that cluster. If the data is requested from VM's of a different cluster, the data must first be copied to the target zones secondary storage, then to the requesting clusters primary storage. A solution to this means placing the Primary Storage within the zone to create zone-wide storage, thus avoiding extra data copy operations. This zone-wide storage is not available when using hyper-v however.[3],[4]

### Secondary Storage
Secondary storage is used to store Templates of OS images taht can then be used to boot VM's as well as additional configurations for installed applications on VM's. It also contains the ISO images, as well as disk volume snapshots for recovery or creation of new templates. Secondary Storage is available to all hosts within the scope of that storage, and can be used either zone-wide or region-wide.

CloudStack provides plugins that enable both Openstack Object Storage (Swift) as well as Amazon Simple Storage Service (S3). When using either of these plugins, you can then configure that storage for the entire CloudStack environment while using an NFS secondary staging store for each zone. This NFS storage acts as a staging area for which all templates and secondary storage data pass before eventually being handed off to either the Swift or S3 storage. 

Keep in mind that Secondary Storage within a region must be alike. You cannot set up both an S3 server and a Swift server even if they are found within different zones.[3],[4]

## Uses
CloudStack’s toolset is utilized through a single portal and can be used to produce scalable hosted private clouds, hosted public clouds, and on-prem private clouds. The software facilitates the creation of virtual infrastructure into a cloud-based IaaS platform. This is due to the automation of server and infrastructure creation. Instead of having to manually configure the servers, the process becomes much more streamlined. Because of these benefits, CloudStack may be used to reduce time/money spent on server maintenance and upgrades and also offer the ability to pay as you go and scale the infrastructure up or down as needed. Short-term use is also a valid solution and can be implemented in cases such as marketing campaigns or promotions. Once the promotion has ended the service can be terminated or scaled back.[5],[6]

While CloudStack can be granular in its settings if you want it to be, the dashboard breaks down the functions of the software cleanly into a few core tabs: dashboard, instances, affinity groups, storage, network, templates, and more. 

### Example

The dashboard is the main tab of the web portal and lists your cloud’s virtual machines, events, private networks, and consumed public IP addresses. 
![dashboard](https://i.imgur.com/6x0bRXM.png)

Image Source: [7] [https://www.youtube.com/watch?v=WbBTDUMk0w0](https://www.youtube.com/watch?v=WbBTDUMk0w0)


One of the most common tasks that anyone will be doing while managing the infrastructure is creating and managing instances. To begin the process of creating the instance, you simply click on the “Instances” tab on the left, and then click on “Add Instance” on the top right corner of the “Instances” page.
![instances](https://i.imgur.com/6fdMuMq.png)

Image Source: [7] [https://www.youtube.com/watch?v=WbBTDUMk0w0](https://www.youtube.com/watch?v=WbBTDUMk0w0)


A window will pop up to guide you through the instance creation process. Begin by first selecting  a zone, and then how you want to create the instance. This can be done either through a template or an ISO. 
![createinstance1](https://i.imgur.com/cTSIZUa.png)

Image Source: [7] [https://www.youtube.com/watch?v=WbBTDUMk0w0](https://www.youtube.com/watch?v=WbBTDUMk0w0)


On the second page a template is selected. A template is essentially a saved and reusable configuration for a virtual machine. This is a great time saver when you are deploying many machines.
![createinstance2](https://i.imgur.com/B2hlGii.png)

Image Source: [7] [https://www.youtube.com/watch?v=WbBTDUMk0w0](https://www.youtube.com/watch?v=WbBTDUMk0w0)


On the “compute offering” page you will select the necessary specifications and hardware for your purpose. Having an underpowered machine for the desired task will impact performance while an overpowered machine will be a waste of resources. 
![createinstance3](https://i.imgur.com/Yxm5cen.png)

Image Source: [7] [https://www.youtube.com/watch?v=WbBTDUMk0w0](https://www.youtube.com/watch?v=WbBTDUMk0w0)


Under “disk offerings” you can optionally add another storage device to the virtual machine. When using a template to create the VM a 50 GB drive is automatically installed. 
![createinstance4](https://i.imgur.com/LNyuczy.png)

Image Source: [7] [https://www.youtube.com/watch?v=WbBTDUMk0w0](https://www.youtube.com/watch?v=WbBTDUMk0w0)


Next, an affinity group can be assigned optionally. An affinity group influences which virtual machines can run on which hosts. This is useful for offering redundancy. If a host fails, a machine running the same services on another host will still be running on an operational host.
![createinstance5](https://i.imgur.com/IoJW7uk.png)

Image Source: [7] [https://www.youtube.com/watch?v=WbBTDUMk0w0](https://www.youtube.com/watch?v=WbBTDUMk0w0)


When adding the machine to a network you can choose to either add it to a private (isolated) or public (shared) network. The private network will have the added benefit of being behind a firewall.
![createinstance6](https://i.imgur.com/U3tKrzC.png)

Image Source: [7] [https://www.youtube.com/watch?v=WbBTDUMk0w0](https://www.youtube.com/watch?v=WbBTDUMk0w0)


The final step will allow you to name the VM and add it to a group, as well as review and edit the configured settings. Finalize the VMs creation by clicking on the “launch machine” option in the bottom right corner.
![createinstance7](https://i.imgur.com/yRs5nfo.png)

Image Source: [7] [https://www.youtube.com/watch?v=WbBTDUMk0w0](https://www.youtube.com/watch?v=WbBTDUMk0w0)


The machine will be created, and a password will be generated. This password will allow you to log into the machine later. Make sure to save this to a safe location.
![instancepassword](https://i.imgur.com/rqmJ3DY.png)

Image Source: [7] [https://www.youtube.com/watch?v=WbBTDUMk0w0](https://www.youtube.com/watch?v=WbBTDUMk0w0)


The machine has machine has been created successfully if you see a “running” status under “State”.
![instancecreated](https://i.imgur.com/1DZ5Y6s.png)

Image Source: [7] [https://www.youtube.com/watch?v=WbBTDUMk0w0](https://www.youtube.com/watch?v=WbBTDUMk0w0)


Clicking on the VM name will bring you to the details page of the VM. Here you have options for managing your virtual machine.
From left to right the options are stop machine, restart machine, take a VM snapshot, destroy instance, attach ISO, reset password, change service offering (to adjust your machine’s CPU and memory), and console access to the machine.
More obviously, you also have the options to view volumes, snapshots, affinity groups, and reset the VM. Resetting the machine bring the machine back to its original state when it was first deployed.
![instancemanagement](https://i.imgur.com/wctuStE.png)

Image Source: [7] [https://www.youtube.com/watch?v=WbBTDUMk0w0](https://www.youtube.com/watch?v=WbBTDUMk0w0)


## References

* [1] [https://en.wikipedia.org/wiki/Apache_CloudStack](https://en.wikipedia.org/wiki/Apache_CloudStack)

* [2] [https://www.8bitmen.com/what-is-apache-cloudstack-everything-you-should-know/](https://www.8bitmen.com/what-is-apache-cloudstack-everything-you-should-know/)

* [3] [http://docs.cloudstack.apache.org/projects/archived-cloudstack-getting-started/en/latest/concepts.html](http://docs.cloudstack.apache.org/projects/archived-cloudstack-getting-started/en/latest/concepts.html)

* [4] [http://docs.cloudstack.apache.org/projects/cloudstack-administration/en/4.8/virtual_machines.html](http://docs.cloudstack.apache.org/projects/cloudstack-administration/en/4.8/virtual_machines.html)

* [5] [https://www.shapeblue.com/about/](https://www.shapeblue.com/about/)

* [6] [https://www.mulesoft.com/resources/cloudhub/iaas-infrastructure-as-a-service#:~:text=IaaS%3A%20Benefits%20and%20use%20cases&text=IaaS%20allows%20cloud%20adopters%20to,drastically%20reducing%20time%20to%20market.](https://www.mulesoft.com/resources/cloudhub/iaas-infrastructure-as-a-service#:~:text=IaaS%3A%20Benefits%20and%20use%20cases&text=IaaS%20allows%20cloud%20adopters%20to,drastically%20reducing%20time%20to%20market.)

* [7] [https://www.youtube.com/watch?v=WbBTDUMk0w0](https://www.youtube.com/watch?v=WbBTDUMk0w0)




