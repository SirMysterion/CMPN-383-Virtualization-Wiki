Qubes OS 
Alicia Santarossa
Jose E. Ledesma


# **Brief History**

In 2010, work began on the Qubes OS. The initial release of Qubes 1.0 was September 3, 2012 and is under the Linux OS family whose kernel is based on Xen Hypervisor with minimal Linux-based OS and can be used in Fedora, Debian, Whonix, and Microsoft. Qubes OS is available as a free download, the official website is www.qubes-os.org.
Cybersecurity threats to companies have sky rocketed over the past decade. Operating systems have done very little to meet these threats, thus creating a gap area of vulnerability. Most operating systems still rely on antiquated methods that do little to address the growing number of security concerns, primarily relying on antivirus scanning. This type of approach is reactive, at best they can identify the systems have been compromised after the fact, but are unable to prevent the entire system or networks from being compromised to begin with. 
Qubes OS exists because there was a lack of secure operating systems throughout industry and takes a unique and effective approach to security that simply wasn’t being done in industry. 

# **Description**

Qubes OS is a xen-based virtualized, meant for a single user, desktop operating system which is free and open sourced. Qubes OS’s main feature focuses on security, providing security through isolation. To take a more proactive stance against security threats such as zero-day exploits, Qubes OS has pioneered an approach called Security by Compartmentalization, using domains implemented as lightweight Xen virtual machines to isolate various subsystems. This allows users to compartmentalize different digital activities and data into individual, securely isolated compartments called ‘Qubes’ which operate as a separate hardware level virtual machine. If one Qube becomes compromised, the other Qubes are not affected. 
Qubes OS securely integrates all secure containers into a unified desktop environment. This creates an advantage in user experience and productivity as it is superior to traditional methods of isolation. 


# Who owns it

Joanna Rutkowska is a computer security researcher known for her research on low-level security and stealth malware. Joanna is the founder of the Qubes OS security-focused desktop operating system. In 2007, Joanna founded Invisible Things Labs, a company that focuses on OS and VMM security research and provides various consulting and the developer of Qubes OS. 

# How it’s used

Users can download and install Qubes OS online. Once downloaded, all programs can be run in lightweight virtual machines called Qubes. Each Qube represents a security domain and a template can be selected of either work, personal or untrusted. You can create more templates if you wish. Each Qube shares the root filesystem with its respective TemplateVM. A Qube has read-only access to the file system of the template in which is based, so a Qube cannot modify a TemplateVM in any way. Creating a large number of domains is cheap and only requires as much disk space as necessary. Each Qube is assigned a label, which has pre-defined colours (Useful in identifying if multiple Qubes belong to the same domain). 
Qubes OS lets the user define many security domains, implemented as lightweight VM’s or “AppVMs”. AppVMs can use the applications within those VM’s like they were executing on the local machine. Qubes utilizes virtualization technology to isolate various programs form one another and even sandbox many system-level components, such as networking and storage subsystems as to not affect the integrity of the rest of the system. 
Qubes Core Stack is the glue that connects all other components together, allowing users and admins to interact with and configure the system inclusive of, but not limited to VM-Customization, Qubes GUI virtualization, GUI domain customizations, AdminVM distribution, Xen Hypervisor, multiple Qubes Apps, various ready to use template such as Debian which are used to create actual VM’s, Salt Stack Integration (spin up new laptops to preconfigure end user needs) and Admin API which makes remote administration possible without the risk of a full system compromise (without access to dom0, the administrative domain) while also addressing concerns about admins having unlimited power of users and the legal liability associated with that. 

# Use Cases

Qubes is especially valuable in industries where sensitive data has to be securely segregated, such as Health, Law and Finance sectors. Qubes is well suited for workers who are technically savvy and require access to untrusted resources while creating valuable intellectual property. Networkless ‘Vault’ VM’s are also ideal for storing code signing keys, a password manager and cryptocurrency wallets. 
For a technically savvy end user’s personal use, you can have a Qube for banking online and another for untrusted browsing. If your untrusted browser gets compromised by a malware, your online banking data will not be at risk. Another example is opening attachments on emails where Qubes can open said attachment in its own single-use disposable Qube. This allows the user to do everything on the one physical computer without having to bother about a cyberattacks where a user’s digital life is compromised in one swoop.
Disposable and or Air Gap VM’s reduce the risk of viewing poisoned websites, malware-laced job applications, suspicious email attachments, PDF’s from untrusted sources, Microsoft Office documents, testing software, not updating software quickly enough and installing malware that pretends to be Flash. 

![https://www.qubes-os.org/attachment/site/qubesosdiagram.png](https://www.qubes-os.org/attachment/site/qubesosdiagram.png)


 
*Image used and provided by Qubes OS Official website: https://www.qubes-os.org/intro/



# References:

https://en.wikipedia.org/wiki/Qubes_OS
https://invisiblethingslab.com/
https://en.wikipedia.org/wiki/Joanna_Rutkowska
https://www.qubes-os.org/intro/
https://www.csoonline.com/article/3252765/the-qubes-high-security-operating-system-gains-traction-in-the-enterprise.html




