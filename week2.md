# Security Planning and Testing Methodology

## Introduction:
This task focuses on establishing a security baseline and defining a structured performance testing methodology for the deployed systems. The objective is to design and document a remote monitoring and performance testing approach that ensures the system operates reliably under expected conditions. In addition, this task aims to implement and verify core security configurations, including access control, network protection, and system hardening measures. Finally, a threat model is developed to identify potential security risks and outline appropriate mitigation strategies, ensuring the system remains secure, resilient, and aligned with best practice standards.

## Plan For Testing Perfomance
### Tools for monitoring:
Monitoring tools are used to observe system performance and resource usage in real time to ensure that both server and workstation systems operate efficiently and securely. These tools provide visibility into CPU usage, memory consumption, disk activity, and running processes. Continuous monitoring helps identify performance bottlenecks, detect abnormal behaviour, and support proactive system management, which is essential for maintaining system reliability and supporting performance testing.
#### Htop:
Htop is an interactive, terminal-based process monitoring tool that provides a real-time view of system resource usage. It displays CPU, memory, and swap usage, along with a list of running processes that can be sorted and managed directly from the interface. Htop improves on the traditional top command by offering a more user-friendly layout and colour-coded output, making it easier to identify high-resource processes.
#### Btop:
Btop is a modern system monitoring tool designed to provide detailed and visually enhanced performance metrics. It displays CPU, memory, disk, and network usage in a clean and highly customisable interface. Btop is particularly useful for visualising system behaviour over time and is lightweight enough to be used on both servers and workstations without significant performance impact.
#### Nmon:
Nmon (Nigel’s Monitor) is a performance monitoring tool primarily used for in-depth system analysis. It collects detailed statistics on CPU, memory, disk I/O, and network usage, making it suitable for performance testing and troubleshooting. Nmon is often used in server environments due to its ability to generate performance data for later analysis.
### Differences Between Htop, Btop, and Nmon
While all three tools monitor system performance, they serve different purposes. Htop focuses on process management and real-time system interaction, making it ideal for quick troubleshooting. Btop provides a visually rich and comprehensive overview of system performance, which is useful for continuous monitoring. Nmon is more analytical and is best suited for performance testing and data collection, particularly in server environments. Together, these tools provide a balanced approach to system monitoring by covering real-time interaction, visual insight, and detailed performance analysis.

## btop: desktop
  ![](/wee2images/btop_desktop.png)
## btop: server
  ![](/wee2images/server_btop.png)

## htop:
  ![](/wee2images/htop_desktop.png)

## nmon install:
  ![](/wee2images/nmon_isntall.png)

Here you can see that I did not have nmon installed and therefore I went ahead and installed it using the command sudo apt install nmon and then the server asked for my password and after the password was successfully entered it continued the download. 

## nmon: nmon menu
  ![](/wee2images/Menu_for_nmon.png)
  
## nmon CPU:
  ![](/wee2images/nmon_cpu.png)

## nmon Memory:
  ![](/wee2images/nmon_memory.png)
