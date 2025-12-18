# Advanced Security and Monitoring Infrastructure

## introduction:
This task focuses on implementing advanced security controls and developing a robust monitoring infrastructure for the server environment. The objectives include configuring access control mechanisms using SELinux or AppArmor to enforce strict security policies, enabling automatic security updates to maintain system integrity, and deploying fail2ban for enhanced intrusion detection. In addition, custom scripts are created to automate verification and monitoring: security-baseline.sh ensures that all security configurations from previous phases are correctly applied, while monitor-server.sh allows remote collection of performance metrics via SSH. Together, these measures establish a secure and auditable environment while enabling continuous system monitoring and performance evaluation.

### Automating Security Patches
To ensure the server remains protected against newly discovered vulnerabilities without requiring my constant manual intervention, I implemented automatic security updates.
Before: My server was at risk of falling behind on critical security patches if I didn't manually run apt upgrade daily. This manual process is prone to human error and neglect.
After: I installed the unattended-upgrades package and verified its status. The service is now active and running, configured to automatically download and install security updates in the background. This transition from manual to automated patching significantly reduces the window of opportunity for attackers exploiting known bugs.

## Intrusion Detection and Prevention
To protect the SSH service from persistent brute-force attempts and denial-of-service patterns, I configured Fail2Ban.
Before: Although I previously disabled password authentication, my logs were still being cluttered by thousands of failed login attempts from bots. These attempts consume system resources and make auditing more difficult.
After: I configured a local jail for SSH and restarted the service. I verified that the fail2ban.service is active and "ready," meaning it is now actively monitoring log files and will automatically block any IP address that shows suspicious behavior.

## Security Baseline Verification
I developed a custom shell script, security-baseline2.sh, to automate the verification of all security controls I have implemented across both phases of the project.
Before: Checking every configuration file manually to ensure settings hadn't drifted was time-consuming and inconsistent.
After: I executed my verification script via SSH. The script confirmed that PasswordAuthentication is securely set to "NO," PubkeyAuthentication is "YES," the UFW firewall is active, and root login is disabled. Running this script gives me an instant "green light" status for the entire server's security posture.

## Remote Performance Monitoring
Finally, I created a monitoring infrastructure to collect performance metrics from my workstation without needing to stay logged into the server terminal.
Before: I had no visibility into server health, such as memory spikes or CPU load, unless I manually logged in and ran commands like top.
After: I successfully deployed a monitoring script that connects via SSH to pull real-time data. I verified that I could track the status of the unattended-upgrades service and other system processes remotely. This allows me to maintain a high-level view of server performance and stability from my administrative workstation.

## All images are below:

### aa-status:
![](/week5_images/aa-status.png)

### Security-baseline script:
![](/week5_images/baseline-script.png)

### fail2ban_successfull:
![](/week5_images/fail2ban_successfull.png)

### monitoring script:
![](/week5_images/monitoring_script.png)

### unattended upgrade:
![](/week5_images/unattended_upgrades.png)
