# SYSTEM PLANNING AND DISTRIBUTION SELECTION

## Introduction:
In this document shown the explanation and planning for a virtual operating system deployment that I have designed. My main objective here is to select and deploy two OS -operating systems within a networked environment, which will form the foundation for week 2 and week 3 of the coursework. In this document I present the proposed system architecture, the explanation for my decision in choosing an operating system for both the server and the workstation, as well as the virtual network connection used.

## SYSTEM ARCHITECTURE DESIGN
In the image below you can see the flow of traffic from a private NAT Network to the Internet, beginning with two virtual machines: an Ubuntu Server (IP: 10.0.2.15/24) and an Ubuntu Desktop: (IP: 10.0.2.4/24). These are capable of direct inter-VM communication. These machines connect through a virtual Gateway (IP: 10.0.2.255) to the Windows 11 host machine, which acts as the bridge between the virtualized environment and the physical hardware. Finally, the connection passes through a firewall and out to the broader Internet, completing the path from the internal virtual subnet to external web resources.
![](/week1_image/designimg.png)

## SERVERS OVERVIEW
### Ubuntu server:
Ubuntu Server is widely used in both academic and enterprise environments due to its reliability, performance, and long-term support releases. The LTS (Long Term Support) versions provide security updates and maintenance for several years, making it ideal for servers that require stability. Ubuntu also has extensive documentation and a large community, which makes troubleshooting and learning much easier. It runs efficiently on low-spec hardware and supports a wide range of server applications:
### Fedora Server
Fedora Server focuses on delivering the latest technologies and features, making it suitable for testing and development environments. However, it has a much shorter support lifecycle compared to Ubuntu, meaning frequent upgrades are required. While Fedora is secure and modern, its cutting-edge nature can introduce instability, which makes it less suitable for production servers where reliability is critical
### Windows Server:
Windows Server is a proprietary operating system developed by Microsoft and is commonly used in enterprise environments. It offers strong integration with Microsoft services such as Active Directory and Azure. However, it requires a paid licence, consumes more system resources, and is less flexible compared to Linux-based servers. It is also more vulnerable to malware due to its popularity and closed-source nature.

## WORKSTATION OVERVIEW
### Ubuntu Desktop (Workstation)
Ubuntu Desktop is a stable and widely used workstation operating system suitable for both academic and professional environments. It provides a user-friendly interface, strong security features, and regular updates supported by long-term support (LTS) releases. Ubuntu Desktop is lightweight, performs efficiently in virtual machines, and offers access to a large software repository, making it ideal for everyday workstation tasks such as system administration, development, and documentation.
### Fedora Workstation 
Fedora Workstation focuses on delivering the latest software and development tools, making it well suited for advanced users and testing environments. However, it has a shorter release and support cycle, requiring frequent updates. While Fedora is secure and modern, its cutting-edge approach can reduce stability, which makes it less suitable for a workstation intended for long-term use in a production or learning environment.
### Windows 11 
Windows 11 is a proprietary workstation operating system widely used in enterprise and home environments. It provides strong compatibility with commercial software and a familiar graphical interface. However, it requires licensing, consumes more system resources, and is less efficient in virtualised environments compared to Linux-based systems. Its closed-source nature also limits flexibility and customisation.

## WHY I CHOOSE UBUNTU (server & workstation)
I selected Ubuntu for both the server and workstation environments after comparing it with Fedora and Windows-based operating systems. Ubuntu was chosen primarily due to its long-term support (LTS) releases, which provide extended security updates and long-term stability: an essential requirement for both server reliability and workstation consistency. In contrast, Fedora focuses on cutting-edge features with a shorter support lifecycle, making it less suitable for long-term deployment, while Windows Server and Windows 11 require paid licences and higher system resources.
Ubuntu’s lightweight performance makes it particularly well suited for virtualised environments, allowing efficient use of system resources on both the server and workstation. Additionally, Ubuntu offers strong security, extensive documentation, and a large support community, which simplifies deployment, management, and troubleshooting. Using Ubuntu across both systems also ensures compatibility and consistency, reducing configuration issues and improving overall system integration. For these reasons, Ubuntu provides the most balanced, cost-effective, and reliable solution for the networked virtual environment.


## NETWORK CONFIGURATION
Desktop Network Settings:
![](/week1_image/NAT_DESKTOP.png)
In the images above and below you can see that both the server and the workstation(desktop) are on the same network named: NAT

Server Network Settings:
![](/week1_image/NAT_SERVER.png)

## IP ADDRESSING
### Desktop IP address
![](/week1_image/ubuntu_desktop_ipa.png)

Desktop server IP address: 10.0.2.4/24

### Server IP address
![](/week1_image/ubuntu_server_ipa.png)

Server IP address: 10.0.2.15/24

## CLI USED TO DOCUMENT THE SYSTEM
### Desktop Commands:

![](/week1_image/ubuntu_desktop_commands.png)

#### uname:
Used to verify the operating system and kernel version for user compatibility and development or administrative tasks.

#### free:
Used to check RAM usage during user tasks and confirm the system can handle applications smoothly.

#### df -h:
Used to check available storage for user files, applications, and system updates.

#### ip addr:
Used to confirm network connectivity and correct IP assignment within the virtual network.

#### lsb_release:
Used to confirm the Ubuntu Desktop version installed for compatibility with applications and updates.

### Server Commands:
![](/week1_image/ubuntuserver_commands.png) 

#### uname
Used to confirm the kernel version and system architecture to ensure server compatibility, stability, and security patching.

#### free:
sed to monitor memory availability to ensure server services can run continuously without performance issues.

#### df -h
Used to monitor disk usage to prevent storage-related service failures and ensure sufficient space for logs and services.

#### ip addr:
Used to verify static IP configuration and network connectivity required for consistent access to server services.

#### lsb_release: 
Used to confirm the exact Ubuntu Server version installed for stability and long-term support planning.

