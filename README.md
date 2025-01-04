# Lab: Network Analysis Web Shell
##### Skills: Wireshark, TCPDump, TShark
## Scenario
The SOC received an alert in their SIEM for "Local to Local Port Scanning" where an internal private IP began scanning another internal system. Can you investigate and determine if this activity is malicious or not? You have been given a PCAP to investigate using any tools you'd like. 

## Introduction
In this lab, I investigated PCAPs from the perspective of a SOC analyst. I conducted the lab using a Kali Linux virtual machine.

## Walkthrough
To begin, I'll use a Kali machine to download and investigate the PCAP. We can start by looking at the PCAP's properties. This might seem useless at first but in a real-world scenario, we might be able to reach out to the client and ask if the machines ran a vulnerability scan. If they started the scan, then the local-to-local port scanning might be benign. We should also ask the client if the PCAP provided is correct. That way, we won't risk wasting our time on investigating a useless PCAP.

Going into `Conversations`, we can identify IPv4 and TCP connections. Going under the TCP tab, we can notice that `10.251.96.4` is hitting a lot of ports on `10.251.96.5`. The IP address `10.251.96.4` generates multiple TCP connections originating from a single port to numerous destinations, a strong indicator of port scanning activity.

Looking at the byte sizes of each connection, we can notice that port 22 and port 80 are anomalies. The other byte sizes of the conversations are 118 bytes while the TCP connections of ports 22 and 80 are 184. This signifies that the three-way TCP handshake was completed; the SYN/ACK packet was dropped by the other connections since those ports were closed.
