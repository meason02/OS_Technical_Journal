# Application Selection for Performance Testing

## Introduction:

This journal documents the selection, deployment, and evaluation of applications representing different workload types for performance testing. The objective of this task is to identify suitable applications that generate CPU-intensive, memory-intensive, disk I/O-intensive, network-intensive, and server-based workloads, and to justify their use through an application selection matrix. In addition, this journal records the SSH-based installation process, outlines the expected resource usage for each application, and defines a monitoring strategy to measure system behaviour and performance under each workload scenario.

## Application Selection for Performance Evaluation
For performance evaluation, applications were selected to generate CPU-intensive, memory-intensive, and I/O-intensive workloads, as these represent core system resource demands. CPU-intensive applications are used to assess processor utilisation and system responsiveness under heavy computational load. Memory-intensive applications evaluate how efficiently the system manages RAM usage and handles memory allocation under stress. I/O-intensive applications are used to measure disk read and write performance, which is critical for understanding storage behaviour and identifying potential bottlenecks. Testing these workload types provides a clear insight into overall system performance and stability.

## Workload Types and Selected Applications

The selected workload types focus on CPU, memory, and disk I/O stress, as these directly reflect how system resources behave under load. Each workload type was mapped to an appropriate application capable of generating controlled and measurable stress on the target resource. This approach ensures that performance testing is structured and that each application serves a specific evaluation purpose, allowing clear observation of system behaviour without overlap between workload categories.

## Application Selection Matrix and Justification
For performance evaluation, I selected applications to represent different workload types, including CPU-intensive, memory-intensive, I/O-intensive, and network-intensive tasks. For CPU-intensive workloads, I used stress-ng in CPU mode, which generates sustained computational load to test processor performance and responsiveness. Memory-intensive workloads were simulated using stress-ng in VM/memory mode, which allocates large amounts of memory to evaluate RAM management and system stability under pressure. For I/O-intensive workloads, stress-ng in HDD mode was chosen to generate heavy disk read and write operations, allowing assessment of storage performance and potential bottlenecks. Finally, for network-intensive workloads, I used iperf3, which creates controlled network traffic to measure bandwidth, latency, and throughput between systems. Together, these applications provide a comprehensive evaluation of system behaviour across different types of resource usage.

## SSH-Based Installation Process
For all selected applications, the installation was carried out remotely using SSH access to the server and workstation environments. SSH provides a secure and encrypted connection, allowing commands to be executed safely over the network. Using SSH, I was able to install, configure, and verify the required software without physical access to the machines, ensuring consistency and repeatability in the setup process.

## Installation Commands and Configuration
Each application was installed using precise command-line instructions. For stress-ng, the installation was performed with sudo apt install stress-ng, while iperf3 was installed using sudo apt install iperf3. After installation, basic configuration was applied to ensure the applications could run with the required workload parameters. This approach allows automated deployment and ensures that each tool operates correctly for subsequent performance testing.

## Expected Resource Usage Profiles
Before running the applications, I outlined the anticipated resource usage for each workload type. CPU-intensive workloads are expected to utilise high CPU percentages while consuming minimal memory. Memory-intensive workloads are expected to allocate large amounts of RAM, with moderate CPU use. I/O-intensive workloads will primarily stress disk read/write operations, and network-intensive workloads are expected to generate significant bandwidth usage while having minimal impact on CPU and memory. Establishing these profiles provides a benchmark for evaluating actual system performance.

## Performance Monitoring Strategy
The performance of each application is monitored continuously during execution to capture real-time data on resource utilisation. Tools such as htop, btop, nmon, and system CLI commands (free, df -h, ip addr) are used to track CPU, memory, disk, and network performance. Monitoring is performed at regular intervals to identify peak loads, resource bottlenecks, and any system instability. This strategy ensures that both the server and workstation are evaluated comprehensively under each workload.

## Measurement Tools and Metrics
Metrics such as CPU utilisation, memory usage, disk I/O throughput, and network bandwidth are recorded to assess system behaviour. Htop provides real-time process and CPU monitoring, btop offers a visually enhanced overview of system performance, and nmon captures detailed historical performance data. Network performance is measured using iperf3, which reports bandwidth, latency, and packet loss. These tools collectively provide both quantitative and qualitative insights into system performance under each workload.

## Summary of Performance Evaluation Approach
The performance evaluation approach involves executing each selected application according to its workload type, monitoring system behaviour in real time, and comparing observed resource usage against the expected profiles. This structured methodology enables identification of strengths and limitations in the system configuration, highlights potential bottlenecks, and verifies that the environment can handle the intended workloads. By combining workload generation with systematic monitoring, I can produce a comprehensive assessment of system stability, responsiveness, and efficiency.

### Images and refrences are in week 2. 
