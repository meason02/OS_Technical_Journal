# Advanced Security and Monitoring Infrastructure

## introduction:
This task focuses on executing detailed performance testing and analysing operating system behaviour under a range of different workload conditions. The objective is to evaluate how the system responds to varying levels of demand by measuring key performance metrics, including CPU usage, memory consumption, disk I/O performance, network performance, system latency, and service response times. By monitoring and comparing these metrics across selected applications and services, this task provides insight into system efficiency, stability, and scalability. The results of this analysis are used to identify performance trends, potential bottlenecks, and overall system suitability for sustained operation under load.

## Establishing the Performance Baseline (CPU & Memory)
To begin my analysis, I needed to understand the "idle" state of my hardened server. I utilized the system information provided upon login to capture a snapshot of resource distribution.
My Observations:
CPU Usage: My initial system load was recorded at a very low 0.07 to 0.09. This indicates that my background security services, like AppArmor and UFW, are highly efficient and do not place a significant tax on the processor during standard operations.
Memory Usage: I observed a consistent memory footprint of 4% of available RAM. Even with the fail2ban-server active, the memory usage remained stable, demonstrating that the intrusion prevention system is well-optimized for this environment.
## Analysing Disk I/O and Storage Health
Monitoring disk performance is critical, especially when automated services like unattended-upgrades are writing logs or downloading patches.
My Observations:
Disk Utilization: Currently, my root filesystem usage sits at 8.4% of 31.32GB.
The Impact of Security: Through my monitoring, I verified that while services like Fail2Ban frequently write to log files to track failed attempts, the overall Disk I/O impact remains negligible. I used my monitoring-server.sh logic to ensure that these write operations aren't causing bottlenecks that would affect service response times.

## Network Performance and Connection Latency
Since this server is managed entirely via SSH, network performance and latency directly impact my administrative efficiency.
My Observations:
Network Stability: By monitoring the enp0s3 interface at IP 10.0.2.15, I tracked the network handshake during key-based authentication.
Latency: I noticed that disabling password authentication and moving to Ed25519 keys reduced the time the server spent processing login requests. By eliminating the "Password:" prompt delay, the system responds almost instantly to authorized users.

## Service Response Times and Workload Analysis
I used my custom scripts to measure how quickly the system can verify its own security posture under load.
My Observations:
Baseline Verification Speed: I timed the execution of my security-baseline2.sh script. The OS was able to parse the sshd_config, check UFW status, and audit AppArmor profiles in seconds.
Inference: The fact that the script returns "Secure" results for all categories without a spike in system load confirms that the OS can maintain high security and high performance simultaneously.

## OS Behaviour Under Security Workloads
The final part of my analysis focused on how the OS manages background tasks like unattended-upgrades.
My Observations:
Automated Task Impact: My monitoring showed that the unattended-upgrades.service has been active for over 2 hours without causing a rise in CPU temperature or memory swap.
The Thinking: This proves that the Ubuntu 24.04 kernel effectively prioritizes these security tasks as background processes, ensuring they do not interfere with the primary "Service Response Times" of the administrative shell.
