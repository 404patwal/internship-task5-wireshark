# Internship Task — Wireshark Network Traffic Analysis

This repository contains my work for the Wireshark task, where I captured and analyzed network traffic.

## 🔹 Objective
- Use Wireshark to capture live network packets.
- Save the capture in `.pcapng` format.
- Identify and analyze key protocols (DNS, TCP, HTTP, ICMP).
- Document observations about packet flow and potential security insights.

## 🔹 Steps Performed
1. Opened Wireshark and selected the active network interface (Wi-Fi/Ethernet).
2. Started packet capture and generated sample traffic:
   - Opened websites (HTTP/HTTPS).
   - Ran commands like `ping 8.8.8.8` and `nslookup example.com`.
3. Stopped capture after ~1 minute and saved as **`task_capture.pcapng`**.
4. Analyzed packets for:
   - **DNS queries/responses**
   - **TCP handshake (SYN, SYN-ACK, ACK)**
   - **HTTP requests**
   - **ICMP ping packets**
5. Documented findings in `report.md`.

## 🔹 Files Included
- `report.md` — Detailed analysis of the Wireshark capture.
- `task_capture.pcapng` — Saved packet capture file.
- `screenshots/` — Key evidence (packet details, filters applied).

## 🔹 Key Learnings
- Wireshark helps visualize how protocols work at the packet level.
- DNS queries and TCP handshakes show how connections are established.
- HTTP and ICMP traffic can be easily captured and analyzed.
- Network captures are useful for troubleshooting and detecting suspicious traffic.

---
**Note:** The `.pcapng` file only contains test traffic generated during the exercise. No sensitive data was captured.
