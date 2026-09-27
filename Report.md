# Task 2 - Defensive Analysis Report
**Analyst:** Ragavendra Viswa | **Tool:** Wireshark

### 1. Affected Component
Lab Wi-Fi, file: lab_traffic.pcapng (Own lab + wiki.wireshark.org sample)

### 2. Protocols Observed
DNS:53, HTTP:80, TCP, UDP, ARP, ICMP

### 3. Risks Identified
- RISK 1: Unencrypted HTTP (Packet 3,11) - Data exposure
- RISK 2: Repeated DNS suspicious-tracker.xyz (4,5,6) - DNS tunneling
- RISK 3: Suspicious DNS data-exfil.evil.com (10) - Exfiltration attempt
- RISK 4: High ARP broadcast (7,8) - ARP spoofing recon

### 4. Evidence
Filter: dns || http || arp
Proof: wireshark_proof.png (attached)
Repeated 3 queries in 1 sec, cleartext HTTP GET, broadcast ARP

### 5. Mitigation (Defensive)
1. Enforce HTTPS + HSTS
2. Secure DNS (DoH)
3. IDS rule for DNS frequency
4. Dynamic ARP Inspection
5. Continuous monitoring

### 6. Conclusion
Defensive analysis helps detect early threats. Performed in authorized lab only.
