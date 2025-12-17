# SYSTEM PLANNING AND DISTRIBUTION SELECTION

## Introduction:
In this document shown the explanation and planning for a virtual operating system deployment that I have designed. My main objective here is to select and deploy two OS -operating systems within a networked environment, which will form the foundation for week 2 and week 3 of the coursework. In this document I present the proposed system architecture, the explanation for my decision in choosing an operating system for both the server and the workstation, as well as the virtual network connection used.

## SYSTEM ARCHITECTURE DESIGN
In the image below you can see the flow of traffic from a private NAT Network to the Internet, beginning with two virtual machines: an Ubuntu Server (IP: 10.0.2.15/24) and an Ubuntu Desktop: (IP: 10.0.2.4/24). These are capable of direct inter-VM communication. These machines connect through a virtual Gateway (IP: 10.0.2.255) to the Windows 11 host machine, which acts as the bridge between the virtualized environment and the physical hardware. Finally, the connection passes through a firewall and out to the broader Internet, completing the path from the internal virtual subnet to external web resources.
![](/week1_image/designimg.png)


![](/week1_image/NAT_DESKTOP.png)

![](/week1_image/NAT_SERVER.png)

![](/week1_image/ubuntu_desktop_commands.png)

![](/week1_imageubuntuserver_commands.png)

![](/week1_image/ubuntu_desktop_ipa.png)

![](/week1_image/ubuntu_server_ipa.png)
