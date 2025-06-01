Task 1 26.05.2025 
Network Reconnaissance Using Nmap & Wireshark

This project keenly focuses on performing basic network reconnaissance within a local network using Nmap and optionally analyzing traffic using Wireshark. The process is structured into 8 key steps which guide the user from installation to interpreting findings.

Installation and Setup:
The first step involves installing Nmap from its official website. This tool is essential for scanning networks to detect active hosts and open ports. The local IP range, typically something like 192.168.141.0/24, is identified using commands such as ip a or ipconfig.

Scanning the Network:
Using the command nmap -sS 192.168.141.0/24, a TCP SYN scan is performed. This type of scan is efficient and stealthy, identifying open ports without completing the full TCP handshake. It’s ideal for reconnaissance without alerting firewalls.

 Findings from the Scan:
Several hosts were found to be live, such as 192.168.141.1, 192.168.141.2, and 192.168.141.3. The scan revealed open ports such as:

Port 53: Running the DNS service, which could be at risk if zone transfers are misconfigured.

Port 7070: Typically associated with RTSP or proxy services, often used for streaming or admin panels. These findings suggest the presence of key network services, some of which may be unnecessary or vulnerable.

Packet Analysis (Optional):
Wireshark can be used to capture traffic during scans. Filters such as
tcp.flags.syn == 1 || tcp.flags.syn == 1 && tcp.flags.ack == 1 || tcp.flags.ack == 1
help trace the TCP 3-way handshake (SYN → SYN-ACK → ACK), making it easier to confirm open ports and connection attempts.

Service and Risk Analysis:
A deeper look into ports showed known services, like DNS on port 53. Tools like nmap -sV help in identifying specific software and versions. Open ports pose risks like:

1. Unauthorized access

2. Exploitable vulnerabilities

3. Information leakage

4. Brute-force login attempts

5. Malware backdoors and communications

Saving Results:
The scan results were saved using:

nmap -sS 192.168.141.0/24 -oN scan_results.txt

for a text file, or for an HTML version:

nmap -sS 192.168.141.0/24 -oX scan.xml
xsltproc scan.xml -o scan.html
