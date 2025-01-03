# Lab: Network Analysis Web Shell
##### Skills: Wireshark, TCPDump, TShark
## Scenario
The SOC received an alert in their SIEM for "Local to Local Port Scanning" where an internal private IP began scanning another internal system. Can you investigate and determine if this activity is malicious or not? You have been given a PCAP to investigate using any tools you'd like. 

## Introduction
In this lab, I investigated PCAPs from the perspective of a SOC analyst. I conducted the lab using a Kali Linux virtual machine.

## Walkthrough
To begin, I'll be using a Kali machine to download and investigate the PCAP. We can start by looking at the PCAP's properties. This might seem useless at first but in a real-world scenario, we might be able to reach out to the client and ask if the machines ran a vulnerability scan. If it was them who started the scan, then the local to local port scanning might be benign. We should also ask the client if the PCAP provided is correct. That way, we won't risk wasting our time on investigating a useless PCAP.

