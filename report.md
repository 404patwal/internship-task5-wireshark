# Task 5 — Capture and Analyze Network Traffic Using Wireshark

**Analyst:** Avinash Patwal  
**Date:** 2025-09-26  
**Tools:** Wireshark (version: [your version]), OS: Windows 10

## 1. Objective
Capture ~1 minute of live network traffic and identify basic protocols and traffic types. Produce a `.pcap`/`.pcapng` file and a short report describing at least three protocols observed.

## 2. Capture details
- **Interface:** [Wi-Fi / Ethernet — exact name]
- **Capture start:** [time]
- **Capture stop:** [time]
- **Duration:** ~[60] seconds
- **Capture file:** `task5_capture.pcapng`

## 3. Traffic generation (what I did)
- Opened browser and visited `http://neverssl.com` to generate HTTP traffic.  
- Ran `ping -n 5 8.8.8.8` and `nslookup example.com` to generate ICMP and DNS traffic.

## 4. Protocols identified (at least 3)
1. **DNS**  
   - **How identified:** Display filter `dns` / Protocol Hierarchy shows DNS traffic (~X packets).  
   - **Example packet:**  
     - Packet #: [e.g., 12]  
     - Time: [0.123456 s]  
     - Source → Dest: `[192.168.1.10] → [8.8.8.8]`  
     - Info: `Standard query A www.neverssl.com`  
     - Key fields: Transaction ID = 0xXXXX, Query name = `www.neverssl.com`, Type = A  
   - Screenshot: `screenshots/dns_packet.png`

2. **TCP**  
   - **How identified:** Display filter `tcp` / many TCP handshakes present.  
   - **Example packet:**  
     - Packet #: [e.g., 20]  
     - Time: [0.234567 s]  
     - Info: `192.168.1.10:50432 → 93.184.216.34:80 [SYN]`  
     - Key fields: Flags = SYN, Seq = [x]  
   - Screenshot: `screenshots/tcp_syn.png`

3. **HTTP**  
   - **How identified:** Display filter `http` / HTTP GET request seen.  
   - **Example packet:**  
     - Packet #: [e.g., 25]  
     - Time: [0.245678 s]  
     - Info: `GET / HTTP/1.1` Host: `neverssl.com`  
     - Key fields: Request URI, Host header, User-Agent  
   - Screenshot: `screenshots/http_get.png`

(Optionally also observed **ARP**, **ICMP**, and **TLS** in capture.)

## 5. Statistics & Conversations
- Protocol Hierarchy screenshot: `screenshots/protocol_hierarchy.png`  
- Top endpoints and conversations saved: `screenshots/endpoints.png`, `screenshots/conversations.png`

## 6. Findings / Interpretation
- DNS queries to public resolver show domain resolution for visited sites.  
- TCP SYN/SYN-ACK/ACK sequences indicate successful TCP connections to port 80 for HTTP.  
- HTTP GET/200 OK exchange demonstrates unencrypted HTTP traffic (since site used was HTTP).  
- No obvious suspicious traffic seen in this short capture. (If you find suspicious flows, list here.)

## 7. Limitations
- Encrypted traffic (HTTPS/TLS) cannot be decrypted without server/client keys; so payloads for TLS sessions are not visible.  
- This is a short (~1 min) capture — longer captures give more context.

## 8. Files submitted
- `task5_capture.pcapng` (packet capture)  
- `report.md` (this report)  
- `screenshots/` (evidence images)

---

## Interview Q&A (short answers)
1. **What is Wireshark used for?**  
   Wireshark captures and analyzes network packets to inspect protocols, troubleshoot issues, and perform security analysis.

2. **What is a packet?**  
   A packet is a formatted unit of data carried by a network containing headers (routing/metadata) and payload.

3. **How to filter packets in Wireshark?**  
   Use display filters in the top bar — e.g., `http`, `dns`, `ip.addr == 192.168.1.10`.

4. **Difference between TCP and UDP?**  
   TCP is connection-oriented and reliable (retransmits, ordered). UDP is connectionless and faster but unreliable.

5. **What is a DNS query packet?**  
   A DNS query asks a DNS resolver to translate a domain name into an IP address (type A/AAAA, etc.).

6. **How can packet capture help in troubleshooting?**  
   It shows actual traffic flows, timing, errors, retransmissions, and protocol details so you can identify failure points.

7. **What is a protocol?**  
   A protocol is a set of rules that define how data is formatted and transmitted (e.g., TCP, HTTP, DNS).

8. **Can Wireshark decrypt encrypted traffic?**  
   Only if you have the necessary keys (e.g., TLS session keys or private keys and proper configuration); otherwise encrypted payloads remain unreadable.

