# Initial System Configuration & Security Implementation

## introduction: 
This task focuses on deploying the server and implementing foundational security controls to ensure a secure and manageable environment. The primary objectives include configuring SSH with key-based authentication to establish secure remote access, setting up a firewall to restrict SSH connections to a specific workstation, and managing user accounts with appropriate privilege management, including the creation of a non-root administrative user. Evidence of successful SSH connections, configuration file changes, firewall rules, and remote administration commands will be documented to demonstrate the implementation and effectiveness of these security measures. This process establishes a secure baseline for the server while enabling controlled and auditable remote administration.

## Establishing Administrative Boundaries
My first priority was to move away from the dangerous practice of performing all tasks as the root user. I created a new administrative user, meason, and added them to the sudo group.
Before: My initial access was essentially "unfiltered." Logging in as root meant any typo or command error could be catastrophic.
After: By implementing the meason account, I ensured that any administrative action requires an explicit sudo command. This creates a necessary barrier of intent and an audit trail for system changes. I also tested a secondary account, testuser, to verify how the server handles new connection requests before I locked down the password settings.
## Generating and Deploying Cryptographic Keys
Instead of relying on easily guessable passwords, I decided to implement Ed25519 key-based authentication. This provides a much higher level of security through elliptic-curve cryptography.
Before: The server relied on "knowledge-based" security (passwords), which are vulnerable to brute-force attacks.
After: I generated a key pair on my workstation. I noticed a small hurdle: because I used sudo for key generation, they were stored in /root/.ssh/. My initial attempt to copy the ID failed because the system couldn't find the identities in my local path. I resolved this by running sudo ssh-copy-id, which successfully pushed my public key to the server at 10.0.2.15.

## Hardening the SSH Configuration
With my keys successfully installed and verified, I needed to "lock the door" behind me. I accessed the server and opened the /etc/ssh/sshd_config file to disable insecure access methods.
The Changes I Made:
PermitRootLogin no: I disabled direct root logins to force attackers to guess my specific username first.
PasswordAuthentication no: This was the most critical step. By setting this to "no," I ensured that even if someone has my password, they cannot log in without my physical private key file.
PubkeyAuthentication yes: I confirmed this was active to allow my new keys to function.

## Implementing the Network Perimeter
To add a final layer of defense, I initialized the Uncomplicated Firewall (UFW).
Before: The server was "listening" for anyone on the network. Without a firewall, every service on the machine was potentially exposed.
After: I enabled the firewall to begin blocking all unsolicited traffic. During this phase, I encountered a "Connection refused" error. This was a vital troubleshooting moment; it confirmed that my security settings were active and that I needed to ensure my specific workstation IP was explicitly permitted through the firewall to maintain access.
## Verification of Remote Administration
To conclude the task, I performed a final connection test to prove the implementation was successful.
The Result: As shown in my final evidence, I am now able to SSH into meason@10.0.2.15 without being prompted for a password. The server recognizes my cryptographic key instantly. I confirmed my administrative privileges by successfully running sudo commands within the remote session, proving that I have a fully functional, hardened remote administration environment.
All images are below 
