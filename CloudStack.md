## **Authors: Dan K, Brennan W**

## What is CloudStack?
CloudStack can be defined as an open-source cloud computing software for creating, managing, and deploying infastructure cloud services. It is designed to deploy and manage large networks of Virtual Machines, while also being highly available and scalable. The software uses existing popular Hypervisor platforms such as KVM, VMware Vsphere with ESXI and vCentre, and XenServer/XCP. CloudStack is Java based and provides support for it's own API, though also provides support for AWS (Amazon Web Services) and open cloud computing interface via the open grid forum.

## History

* The software was originally developed out of Cupertino, California by a company known as VMops created by its founding members Sheng Liang, Shannon Williams, ALex Huang, Will Chan, and Chiradeep Vittal in 2008. VMops raised approximately $17.6 million in funding from Redpoint Ventures, Nexus Ventures, and Index Ventures and eventually changed it's name from VMops to Cloud.com in 2010 upon announcing its product CloudStack. 

* May 2010 CloudStack was released as a free software under the General Public License (A series of widely used free software licences that guarentee end users the freedom to run, study, share, and modify software), though kept roughly 5% of CloudStack software proprietary.

* In October of 2010, Cloud.com announced a parternship with Microsoft that would then develop integration and support for the software with Windows Server 2008 R2 Hypver-V.
* In July 2011, Cloud.com was purchased by Citrix Systems for approximately $200 million. The following month Citrix relased what proprietary code was remaining under the Apache Software License. CloudStack 3.0 was released in April 2012 and was donated to the Apache Software Foundation where it was then accepted into the Apache Incubator. At this point Citrix ceased development on the software. 
* In November of 2012, CloudStack 4.0 was announced and in March 2013 the software became a Top Level Product (Among the list of projects within the Apache Software Foundation development), with the first stable release of CloudStack being released in 4.0.2.


## How does it work?
CloudStack works by using a Management Server to control many hypervisors from a single management interface. The minimum installation requires 1 machine that must run as the management server, with another machine that acts as the cloud infastructure. First, you must set up the management server, which typically runs on a dedicated physical or virtual machine, then you must specify the resources which are to be managed. This management server then controls the allocation of virtual machines to hosts, and assigns storage and IP addressing as well as other resources to the virtual machines launched within the cloud environment. The management server runs within an Apcache Tomcat container and contains it's own MySQL Database. 

## Management Server resources and CloudStack architecture
The CloudStack environment works by having the management server manage specific resources, these being:
### Regions
A collection of one or more geographically close zones managed by one or more management servers. A Region is the largest available organizational unit (OU) within a CloudStack deployment. Each region is controlled by it's own cluster of management servers (or mangaement server). Regions provide fault tolerance and disaster recovery by segregating resources. Grouping resources into multiple geographic regions provides increased reliability within the cloud. 

