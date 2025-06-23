# TASK-1
NMAP &amp; WIRESHARK
Cybersecurity Internship – Task 1: Nmap-Based Network Scanning
1) Objective
Conduct local network reconnaissance using Nmap, identify active hosts, perform port and service scans on a target machine, and optionally inspect packet captures with Wireshark.
2) Tools Used
- [Nmap 7.94SVN](https://nmap.org/)
- Wireshark (for `.pcapng` analysis)
- OS: Kali Linux (Virtual Machine)
3) Target Environment
- **Network Range Scanned:** `192.168.0.0/24`
- **Scanned Host IP:** `192.168.0.107`
- **MAC Address:** `FC:B0:DE:01:30:A1`
- **Operating System Detected:** Microsoft Windows (via service info)
4) Nmap Commands Executed
1. Ping Sweep (Host Discovery)  
   ```bash
   sudo nmap -sn 192.168.0.1/24
➤ Identified 24 active hosts on the local subnet.
2. Fast Scan with Service Version Detection
    ```bash
    sudo nmap -sV 192.168.0.107 -F
➤ Found services: RPC, NetBIOS, SMB, MySQL.
3. TCP SYN Scan (Stealth)
   bash
   sudo nmap -sS 192.168.0.107
➤ Detected same TCP services as above.
4. TCP Connect Scan (Full TCP Handshake)
   bash
   sudo nmap -sT -v 192.168.0.107
➤ Confirmed ports 135, 139, 445, and 3306 open.
5. UDP Scan
   bash
   sudo nmap -sU -v 192.168.0.107
➤ Detected UDP port 137 open (NetBIOS Name Service).
6. Targeted Port Scan with Version Info
   bash
   sudo nmap -sV -p 135,139 192.168.0.107
➤ Detailed service info on RPC and NetBIOS
5) Key Findings

| Port | Protocol | Service         | Description                        |
|------|----------|------------------|------------------------------------|
| 135  | TCP      | msrpc            | Microsoft RPC                      |
| 139  | TCP      | netbios-ssn      | NetBIOS Session Service            |
| 445  | TCP      | microsoft-ds     | Windows File/Printer Sharing       |
| 3306 | TCP      | mysql            | MySQL Server (unauthorized)        |
| 137  | UDP      | netbios-ns       | NetBIOS Name Service               |

 6) Risk Insight

- **SMB/NetBIOS (Ports 139/445):** Known vectors for malware like WannaCry.
- **MySQL (3306):** Unauthorized access possible if not secured.
- **NetBIOS-NS (UDP 137):** Can leak system names and be abused in spoofing.

7) Supporting Files

- `task 1.txt` – All command outputs and scan logs
- `task 1.pcapng` – Wireshark capture of scanning traffic
- `a.jpg` to `g.jpg` – Screenshots of scan commands/results

8) screenshots
   
![d](https://github.com/user-attachments/assets/04297db6-ee60-402a-ae68-1e75eaddb2c8)
![f](https://github.com/user-attachments/assets/9be6eea2-25ea-4210-a17e-dae7ff14dd65)
![e](https://github.com/user-attachments/assets/d41690de-1ccc-428f-9d32-71e106109209)
![c](https://github.com/user-attachments/assets/b1358054-d0fe-4abb-bfde-e2dec2db453d)
![b](https://github.com/user-attachments/assets/ed4ed6c6-629e-436e-a22c-0060f95cdf8a)
![a](https://github.com/user-attachments/assets/ae75c1cc-49c2-4ef0-af0b-55ab784df7cb)
![g](https://github.com/user-attachments/assets/76ee073b-085f-4a6f-825c-724760e58479)

9) Summary

This task demonstrated practical usage of Nmap for network reconnaissance and service enumeration. It covered essential scanning techniques (Ping, SYN, Connect, UDP, and Targeted Scans) and helped identify vulnerable services running on a local host. Wireshark logs and screenshots further validated the activity.

