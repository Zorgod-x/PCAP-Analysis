# PCAP-Analysis

Project Description:

In this project, we will perform a security log analysis of a Packet Capture (PCAP) file to uncover network-related security incidents and anomalies. PCAP files contain raw network traffic data, and analyzing them can reveal insights into network activities, potential threats, and vulnerabilities. You will use various tools and techniques to extract meaningful information from the PCAP and generate actionable insights for improving network security.


# Phase 1: Data Collection
PCAP Acquisition: Obtain a PCAP file from a network capture tool or a publicly available dataset.
# How to capture the data :
- Endpoint download of wireshark
- SPAN - mirror ( send all data to virtual port)
- Network tap device

# Before capturing
Who is impacted?
All the time?
What applications?
What servers are they interacting with?
What network path?

# Phase 2: Initial Analysis

PCAP Inspection: Use Wireshark to open the PCAP file and perform initial inspections. Look for unusual patterns, high volumes of traffic, or known attack signatures.

Packet Filtering: Apply filters in Wireshark to focus on specific traffic of interest, such as HTTP, DNS, or suspicious IP addresses.

1. Filtering packets based on IP address
  ip.addr==    
  ipv6.addr==
2. Subnet filtering allows for filtering a range of addresses within a specific subnet.
  ip.addr== x./0-32    
3. Setting a range of ports using the membership operator.
  tcp.port ==
  tcp.port in {80,443,8000..8005}
5. Filters in Wireshark for TCP analysis.
  tcp.analysys.flags
6. Slow protocol response time
  dns.time>
  http.time>
  smb.time>
7. Analyzing TCP reset flags is important for investigating connection issues.
  tcp.flags.reset==1

# Phase 3: Deep Analysis
-Protocol Analysis: Analyze different network protocols (e.g., HTTP, DNS, SMB) to identify potential security issues, anomalies, or unauthorized activities.
-Traffic Flow Analysis: Study the flow of network traffic, looking for unusual communication patterns, large data transfers, or unexpected connections.
-Payload Inspection: Examine packet payloads for signs of malware, command and control traffic, or data exfiltration attempts.

# Troubleshooting:
1. First thing to look for : slow application response time could be http, dns, smb   # http.time>2 = slow web server
2. Large network latency
3. packet loss: time to figure out if something is missing and then retransmit       #tcp.analysis.lost_segment
Usually means network problem : congestion or link level errors (bad cable / transceiver)
4. TCP layer, tcp window problem
5. connectivity problems : Reset    #tcp.flags.reset==1












