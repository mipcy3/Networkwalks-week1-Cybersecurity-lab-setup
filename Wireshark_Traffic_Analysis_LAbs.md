# Wireshark Traffic Analysis & Incident Response Lab Portfolio

## 🧑‍💻 Student & Professional Identity
* **Name:** David Ayomipo Gege
* **Role:** Cybersecurity Technical Intern
* **Affiliation:** NetworkWalks Internship Program
* **Documentation Scope:** Comprehensive Traffic Analysis, Forensic Investigation, & Incident Response (Labs 3 - 8)

* This document contains my comprehensive hands-on solutions, deep packet analysis, and technical write-ups for the complete network forensics suite completed on the **NetworkWalks** Wireshark simulator platform. 

The objective of these labs is to act as a SOC Analyst to investigate raw packet captures (`.pcap`), triage active network intrusion vectors, isolate malicious footprints, and document remediation strategies for enterprise infrastructure.

---

## 🛠️ Technical Skills & Tools Demonstrated
* **Analysis Tools:** Wireshark Packet Analyzer (Deep Packet Inspection, TCP Stream Reassembly, Telephony/RTP Diagnostics)
* **Network Protocols:** TCP/IP Suite, HTTP, FTP, SIP, RTP, DNS, ARP, Transport vs. Application Layers
* **Forensic Techniques:** Multi-conditional Display Filtering, Sequence Triage, Status Code Analysis, Port Characterization (Service vs. Ephemeral)
* **Core Concepts:** Network Reconnaissance Mapping, Cleartext Vulnerability Assessment, Brute-Force Anomaly Tracking, Insider Threat Detection

---

## 🔬 Completed Incident Response Portfolio

### 🔍 Lab 3: Threat Identification & Network Reconnaissance Forensic Analysis
* **Scenario:** An active multi-port reconnaissance scanning profile is detected targeting the internal enterprise web infrastructure. 
* **Key Accomplishments & Skills Applied:**
  * Isolated and analyzed multi-port scanning footprints to establish an attack timeline.
  * Extracted malicious actor IP (`192.168.10.66`) and identified target vector IP (`192.168.10.20`).
  * Identified exposed operational entry points across Port 22 (SSH), Port 80 (HTTP), and Port 443 (HTTPS).
  * Isolated standard TCP `[RST, ACK]` response flag packet anomalies, accurately mapping exactly 37 closed network sockets out of 40 global probes.
  * **Final Evaluation Score:** 100 / 100 Marks. 
* <img width="1080" height="1700" alt="Lab 3 Result - David Ayomipo Gege" src="https://github.com/user-attachments/assets/fdc0dbcc-687b-4919-aac2-6921362ebd9d" />

### 📡 Lab 4: Follow TCP Stream (Plain Text Chat Forensics)
* **Scenario:** An organization suspects employees are utilizing unencrypted, non-standard application channels to communicate. The objective was to isolate the rogue chat tool, identify the endpoints involved, and extract the session history.
* **Key Accomplishments & Skills Applied:**
  * Crafted complex multi-conditional display filters (`tcp and !tcp.port == 80 and !tcp.port == 443`) to sweep away normal web background noise.
  * Distinguished between service ports (**Port 5000**) and automatically assigned client ephemeral ports (**Port 49731**).
  * Monitored connection handshakes (`SYN` packets) to pinpoint the exact internal source IP address (`192.168.10.45`) initiating the session.
  * Conducted TCP stream reassembly to extract a plaintext transcript of the live internal chat conversation.
  * **Final Evaluation Score:** 100 / 100 Marks.
<img width="1080" height="1700" alt="Lab 4 Result - David Ayomipo Gege" src="https://github.com/user-attachments/assets/e29edf9a-be66-47c9-a04f-b23c18f992f2" />

### 🌐 Lab 5: Follow TCP Stream Part 2 (Web Server Payload Auditing)
* **Scenario:** An administrator flagged an internal asset interacting unusually with an internal company intranet server, suspecting a configuration secret was exposed within the website source files.
* **Key Accomplishments & Skills Applied:**
  * Filtered web traffic transactions (`http.request.method == "GET"`) to map corporate intranet usage patterns across multiple hosts.
  * Analyzed packet lengths and anomalous traffic signatures to detect data streams mimicking normal server content.
  * Evaluated client-server data propagation direction using Wireshark's directional stream color-coding rules (Inbound Client Requests vs. Outbound Server Payloads).
  * Audited individual stream indices to locate the `/staff.html` page requested by a suspicious secondary IP (`192.168.10.58`).
  * Performed deep packet payload inspection to pull an active infrastructure backup asset location and its sensitive access key (**`Falcon-9921`**) hidden within an unrendered HTML comment tag (`<!-- -->`).
  * **Final Evaluation Score:** 100 / 100 Marks.
<img width="1080" height="1700" alt="Lab 5 Result - David Ayomipo Gege" src="https://github.com/user-attachments/assets/cf6a1654-5ade-4da1-8db4-3423efc61192" />

### 🔐 Lab 6: HTTP Plain Text Credentials (Cleartext Exposure Auditing)
* **Scenario:** A legacy corporate authentication portal running over unencrypted HTTP (Port 80) is audited to prove how cleartext credentials can be sniffed and extracted from network transport payloads.
* **Key Accomplishments & Skills Applied:**
  * Isolated credential transmission activity across the network by deploying targeted display filters: `http.request.method == "POST"`.
  * Conducted focused deep packet inspection on `HTML Form URL Encoded: application/x-www-form-urlencoded` data segments inside HTTP streams.
  * Pinpointed the central target web application host server sitting at IP address `192.168.10.20`.
  * Extracted exposed plaintext user credentials (`username: farhan.k` / `password: Mango2025`) directly out of transport payloads.
  * Recommended implementation of secure **HTTPS (TLS/SSL)** alongside **HSTS** execution policies to neutralize plain-text data sniffing.
  * **Final Evaluation Score:** 100 / 100 Marks.
<img width="1080" height="1700" alt="Lab 6 Result - David Ayomipo Gege" src="https://github.com/user-attachments/assets/8e18ea5e-a0d8-4d35-916a-2c965bd1b336" />

### 🛡️ Lab 7: Catch the Brute Force Attacker (FTP Triage & Verification)
* **Scenario:** An enterprise FTP storage asset reports a massive influx of connection failures, indicating an ongoing automated password-guessing attempt.
* **Key Accomplishments & Skills Applied:**
  * Evaluated operational connection anomalies using Wireshark **Conversations Matrix** and **Protocol Hierarchy Statistics** to identify target host `192.168.10.20`.
  * Audited brute-force scripts cycling through common administrative usernames, locating a high-intensity focus on the `admin` profile.
  * Leveraged specific error-code verification parameters (`ftp.response.code == 530`) to establish the exact frequency boundary and failed attempt count.
  * Monitored the complete authentication timeline to trap the precise payload where the server accepted an entry vector (`ftp.response.code == 230`), exposing the compromised operational password (**`Mango#2026`**).
  * **Final Evaluation Score:** 100 / 100 Marks.
<img width="1080" height="1700" alt="Lab 7 Result - David Ayomipo Gege" src="https://github.com/user-attachments/assets/c2c0dd20-6abc-4040-9e4a-6d78e491771a" />

### 📞 Lab 8: Catch the Call Scammer (VoIP Interception & Media Forensics)
* **Scenario:** An employee phone call was made through the company VoIP system. Captured the traffic, mapped the handshake protocols, and reconstructed the actual audio stream to detect data leaks.
* **Key Accomplishments & Skills Applied:**
  * Analyzed text-based call setups by filtering for Session Initiation Protocol (**SIP**) session flags (`sip.Method == "INVITE"`) to isolate internal calling extensions (`101` and `202`).
  * Verified live telephony voice channel encoding frameworks running uniquely over **RTP (Real-time Transport Protocol)** blocks.
  * Determined the active communication compression algorithm by parsing payload signatures to confirm **G.711 PCMU (mu-law)** stream processing.
  * Utilized Wireshark's built-in **VoIP Player Diagnostics Tool** to stitch raw media stream blocks together and play back the recorded call file directly.
  * Discovered an insider threat data leak, extracting exposed accounting card numbers and account metrics spoken plainly over the unencrypted connection.
  * Drafted defensive recommendations favoring transitioning open media lanes to **SRTP (Secure RTP)** to mandate end-to-end payload obfuscation.
  * **Final Evaluation Score:** 90 / 100 Marks.
 <img width="1080" height="1700" alt="Lab 8 Result - David Ayomipo Gege" src="https://github.com/user-attachments/assets/e7d402a1-ba97-4ed0-adf2-d3380e8e059d" />
