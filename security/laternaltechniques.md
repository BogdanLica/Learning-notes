### Basic Idea
* gain access to a lower protected, lower priviledged asset
* escalate priviledges
* find interesting targets


### Common techniques
* Psexec
    * part of the pstools which let administrators to remotely control Windows systems from the terminal
    * offer the ability to uplad, execute and interact with an executable on a remote host
    * not blacklisted or deteted by AVs as it is a legitimate system administration tools by Microsoft

* File shares
    * with enough priviledges, an attacker can find almost anything in a Windows fileshare from customer databases to details of aditional systems
    * FIND MORE

* Remote desktop
    * a GUI with full control through a legitimate channel built into Windows
    * once the attacker has the valid credentals, RPD is commonly used
    * RDP connections are encrypted and opaque to monitoring solutions

* Powershell
    * since sandboxing was an effective way to catch malware without signature, hackers started to use the built in capabilities of the operating system to replicate malware functionality
    * again, PowerShell is a genuine program from MS, which means that it will avoid detection

* Port-scans
    * used to quickly identify services running
    * low and slow scans can get past practically any network monitoring system
    * when using Nmap, do not use features(like OS detection,script scanning etc) if you do not need them, only TCP connects to find possible targets and not get caught

* WMI(Windows Management Instrumentation framework)
    * used to manage the configuration of Windows systems
        * start remote processes
        * query system information
        * store persistent data(malware in this case)
        * enumerate system information of classify targets

* Scheduled tasks
    * ! scheduled tasks run as the SYSTEM user, allowing an attacker to escalate priviledges for complete control over the host 
    * good for scheduling batch jobs that require a lot of CPU and bandwith like zipping up folders and transferring them over then network

* Token stealing
    * i.e: mimikatz and Windows Credential Editor
    * find service account in memory, create Kerberos tickets and elevate priviledges from a normal user to a domain admin

* Pass-the-hash
    * based on the NTLM protocol
    * attackers use the ecrypted hash of a password instead of the actual password to log in( even though the attacker does not know the plain password)
    * 
* Active directory
    * a 'phone book' of the network
    * the starting point for an attacker is to list the AD computers
    * quick search for databases, backup systems, SCADA controllers

* Remote registry
    * can be used to 
        * disable protection mechanism
        * remove auto-start programs and services
        * install persistance mechanism

* Admin shares
    * built in shares like ADMIN$,C$
    * give complete access to the %SYSTEMROOT% folder
    * the attacker has read-write access to the entire hard disk of the remote machine

* Stolen credentials
    * almost all the attacks have a stage where they make use of legitimate credentials to move ahead
* Breached host analysis
    * once an attacker breaches into a host, he starts to gather as much information(passwords in text files,details of other systems etc) as possible to move further

* Central admin consoles
    * concentrate on breaking in to the system that controls all the hosts, instead of breaking into each individual host

* Network sniffer
    * useful to get credentials and other information
    * man in the middle attacks like : ARP spoofing
        *  generate face ARP requests

* Email pillage
    * more than 35% of all the informaton a company has sits in the e-mail
    * useful for information gathering, spear phising attacks

* Software deployment
    * there are system that are allowed to execute arbitrary code on thousands of hosts

* VNC / Teamviewer
    * usually used for remote technical support
    * some offer file transfers and persistance features
  