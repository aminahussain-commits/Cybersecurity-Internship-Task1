# Task 1: Scan Your Local Network for Open Ports

## 🎯 Objective
To learn network reconnaissance fundamentals by discovering active devices and open ports within a local network to understand service exposure and potential security vulnerabilities.

## 🛠️ Tools Used
* **Nmap 7.95** (Network Mapper)
* Windows Command Prompt (Admin)

## 📊 Scan Methodology & Results
1. **Identified Network Range:** `192.168.1.0/24`
2. **Command Executed:** `nmap -sS -oN scan_results.txt 192.168.1.0/24`
3. **Findings Summary:** 
   "The scan completed successfully and discovered X active devices on the network. Common open ports found included 

---

## 🧠 Technical Interview Questions

### 1. What is an open port?
An open port is a network port that actively accepts incoming packets. It indicates that an application or network service is listening on that specific port and is ready to establish a communication channel.

### 2. How does Nmap perform a TCP SYN scan?
Often called a "half-open" scan, Nmap sends a SYN packet (the first step of the TCP three-way handshake) to the target port. If the port responds with a SYN/ACK, the port is open. Nmap then immediately sends a RST (Reset) packet to close the connection before it fully establishes, making the scan fast and less invasive. If the target responds with a RST, the port is closed.

### 3. What risks are associated with open ports?
Open ports themselves aren't dangerous, but the services running behind them can be. If a service is poorly configured, outdated, or contains security vulnerabilities, an attacker can exploit it to gain unauthorized access, execute malicious code, or launch a Denial of Service (DoS) attack.

### 4. Explain the difference between TCP and UDP scanning.
* **TCP Scanning:** Relies on connection-oriented protocols. It involves a reliable handshake process where Nmap expects predictable responses (like SYN/ACK or RST) to determine port status.
* **UDP Scanning:** Relies on connectionless protocols. Nmap sends an empty UDP packet. If no response is received, the port is marked as `open|filtered`. If an ICMP port unreachable error is returned, the port is `closed`. UDP scanning is much slower and less reliable due to how operating systems handle UDP errors.

### 5. How can open ports be secured?
* Close unnecessary ports by disabling or shutting down unused network services.
* Keep all listening software and firmware updated with the latest security patches.
* Implement network firewalls to restrict access to open ports to authorized IP addresses only.
* Implement strong authentication and encryption (e.g., using SSH keys instead of passwords).

### 6. What is a firewall's role regarding ports?
A firewall acts as a security barrier that monitors and filters incoming and outgoing network traffic based on predetermined rules. It can block unauthorized traffic from reaching open ports, stealth ports entirely (making them appear `filtered` to Nmap), and ensure only legitimate connections pass through.

### 7. What is a port scan and why do attackers perform it?
A port scan is a reconnaissance technique used to probe a server or host to discover its open ports. Attackers perform port scans to map out an organization's network perimeter, discover what operating systems and services are running, and identify potential entry points for an attack.

### 8. How does Wireshark complement port scanning?
While Nmap tells you the final status of the ports, Wireshark allows you to capture and analyze the raw network packets being sent and received during the scan. It helps you visualize the TCP flags (SYN, SYN/ACK, RST) in real-time, troubleshoot scanning issues, and understand how intrusion detection systems (IDS) spot scanning activity.
