# SYSTEM PLANNING AND DISTRIBUTION SELECTION

## Introduction:
In this document shown the explanation and planning for a virtual operating system deployment that I have designed. My main objective here is to select and deploy two OS -operating systems within a networked environment, which will form the foundation for week 2 and week 3 of the coursework. In this document I present the proposed system architecture, the explanation for my decision in choosing an operating system for both the server and the workstation, as well as the virtual network connection used.

## SYSTEM ARCHITECTURE DESIGN
In the image below you can see the flow of traffic from a private NAT Network to the Internet, beginning with two virtual machines: an Ubuntu Server (IP: 10.0.2.15/24) and an Ubuntu Desktop: (IP: 10.0.2.4/24). These are capable of direct inter-VM communication. These machines connect through a virtual Gateway (IP: 10.0.2.255) to the Windows 11 host machine, which acts as the bridge between the virtualized environment and the physical hardware. Finally, the connection passes through a firewall and out to the broader Internet, completing the path from the internal virtual subnet to external web resources.
![](/week1_image/designimg.png)

## SERVERS OVERVIEW
### Ubuntu server overview:
Ubuntu Server is widely used in both academic and enterprise environments due to its reliability, performance, and long-term support releases. The LTS (Long Term Support) versions provide security updates and maintenance for several years, making it ideal for servers that require stability. Ubuntu also has extensive documentation and a large community, which makes troubleshooting and learning much easier. It runs efficiently on low-spec hardware and supports a wide range of server applications.
### Fedora Server – Overview
Fedora Server focuses on delivering the latest technologies and features, making it suitable for testing and development environments. However, it has a much shorter support lifecycle compared to Ubuntu, meaning frequent upgrades are required. While Fedora is secure and modern, its cutting-edge nature can introduce instability, which makes it less suitable for production servers where reliability is critical
### Windows Server – Overview
Windows Server is a proprietary operating system developed by Microsoft and is commonly used in enterprise environments. It offers strong integration with Microsoft services such as Active Directory and Azure. However, it requires a paid licence, consumes more system resources, and is less flexible compared to Linux-based servers. It is also more vulnerable to malware due to its popularity and closed-source nature.



![](/week1_image/NAT_DESKTOP.png)

![](/week1_image/NAT_SERVER.png)

![](/week1_image/ubuntu_desktop_commands.png)

![](/week1_imageubuntuserver_commands.png)

![](/week1_image/ubuntu_desktop_ipa.png)

![](/week1_image/ubuntu_server_ipa.png)
