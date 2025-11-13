# Room : Networking Concepts
**Platform:** TryHackMe
**Category:** Learn
**Difficulty:** Easy
**Estimated time:** `60 min`
**Objective(s):** Learn about the ISO OSI model and the TCP/IP protocol suite.

---

## TL;DR

This room covers core networking concepts: the OSI and TCP/IP models, how IP addressing and subnets work, the difference between TCP and UDP, encapsulation, and simple service testing with `telnet`. Key practical points: IPv4 uses CIDR (`/n`) to define networks and host ranges; routers forward packets using IP; UDP is connectionless and low-overhead; TCP is connection-oriented and reliable with a three-way handshake and flow/congestion controls. The lab exercises (telnet to echo/daytime/HTTP) demonstrate basic TCP services and why plaintext protocols are insecure.

---

## 1) OSI Model

The **OSI (Open Systems Interconnection)** model, developed by the **International Organization for Standardization (ISO)**, is a conceptual framework describing how communications occur across computer networks.
Although theoretical, understanding the OSI model is crucial to grasp how networking works at different levels.

### The Seven Layers of the OSI Model

| Layer | Name | Description |
|:------:|:------:|:-------------|
| 7 | Application | Provides network services directly to end-user applications. |
| 6 | Presentation | Handles data encoding, compression, and encryption. |
| 5 | Session | Establishes and maintains communication sessions. |
| 4 | Transport | Ensures reliable end-to-end communication between hosts. |
| 3 | Network | Handles logical addressing and routing between networks. |
| 2 | Data Link | Manages data transfer between nodes on the same network. |
| 1 | Physical | Defines the physical means of transmitting data. |

> **Mnemonic:**
> “Please Do Not Throw Spinach Pizza Away”

### Layer 1: Physical Layer
- **Purpose:** Defines the physical connection between devices — cables, signals, and hardware.
- **Transmission:** Electrical, optical, or wireless signals.
- **Examples:** Ethernet cables, optical fiber, Wi-Fi radio bands (2.4 GHz, 5 GHz, 6 GHz).

### Layer 2: Data Link Layer
- **Purpose:** Enables communication between devices on the same network segment.
- **Protocols:** Ethernet (802.3), Wi-Fi (802.11).
- **Identifiers:** Uses **MAC addresses** (6 bytes, hexadecimal format).
- **Example:**
  - A network segment with 10 computers connected to a switch.
  - Each frame contains:
    - Destination MAC address
    - Source MAC address
    - Data payload

### Layer 3: Network Layer
- **Purpose:** Routes packets between different networks.
- **Functions:** Logical addressing (e.g., IP addresses) and routing decisions.
- **Examples:**
  - **Protocols:** IP, ICMP, IPSec, SSL/TLS VPN
  - **Scenario:** Connecting multiple office networks across cities or countries.

### Layer 4: Transport Layer
- **Purpose:** Enables **end-to-end communication** between applications.
- **Functions:** Flow control, segmentation, and error handling.
- **Protocols:** TCP (reliable), UDP (unreliable but faster).

Example: Your web browser connects to the TryHackMe server via the TCP protocol on this layer.

### Layer 5: Session Layer
- **Purpose:** Establishes, maintains, and synchronizes sessions between applications.
- **Functions:** Data synchronization, session recovery after failures.
- **Examples:** NFS (Network File System), RPC (Remote Procedure Call).

### Layer 6: Presentation Layer
- **Purpose:** Prepares data for the application layer — encoding, compression, and encryption.
- **Examples:**
  - Character encoding: ASCII, Unicode
  - File encoding and transmission: MIME for email attachments
  - Image formats: JPEG, GIF, PNG

Example: Sending an image via email involves MIME converting binary data into ASCII text for transfer.

### Layer 7: Application Layer
- **Purpose:** Provides direct network services to end-user applications.
- **Examples:**
  - HTTP — web browsing
  - FTP — file transfer
  - DNS — domain resolution
  - SMTP/POP3/IMAP — email protocols

This is the layer most visible to the user, as applications directly interact with it.

### Summary Table

| Layer Number | Layer Name | Main Function | Example Protocols / Standards |
|:---:|:---|:---|:---|
| 7 | Application | Providing services and interfaces to applications | HTTP, FTP, DNS, POP3, SMTP, IMAP |
| 6 | Presentation | Data encoding, encryption, and compression | Unicode, MIME, JPEG, PNG, MPEG |
| 5 | Session | Establishing, maintaining, and synchronizing sessions | NFS, RPC |
| 4 | Transport | End-to-end communication and data segmentation | TCP, UDP |
| 3 | Network | Logical addressing and routing between networks | IP, ICMP, IPSec |
| 2 | Data Link | Reliable data transfer between adjacent nodes | Ethernet (802.3), Wi-Fi (802.11) |
| 1 | Physical | Physical data transmission media | Electrical, Optical, Wireless |

---

## 2) TCP/IP Model

The **TCP/IP model** is the practical implementation of networking protocols. Developed in the 1970s by the **U.S. Department of Defense (DoD)**, it is designed for resilience: networks remain functional even if some parts fail, using dynamic routing.

Unlike OSI, TCP/IP has **four layers** in its original form. Some references extend it to **five layers** by separating the physical layer.

### Mapping OSI to TCP/IP

| Layer Number | OSI Model | TCP/IP Model | Example Protocols |
|---|---|---|---|
| 7 | Application | Application | HTTP, HTTPS, FTP, POP3, SMTP, IMAP, Telnet, SSH |
| 6 | Presentation | Application | HTTP, HTTPS, FTP, POP3, SMTP, IMAP, Telnet, SSH |
| 5 | Session | Application | HTTP, HTTPS, FTP, POP3, SMTP, IMAP, Telnet, SSH |
| 4 | Transport | Transport | TCP, UDP |
| 3 | Network | Internet | IP, ICMP, IPSec |
| 2 | Data Link | Link | Ethernet (802.3), WiFi (802.11) |
| 1 | Physical | — | — |

### Five-Layer Variant
1. Application
2. Transport
3. Network
4. Link
5. Physical

---

## 3) IP Addresses and Subnets

An **IP address** uniquely identifies each network interface. IPv4 addresses are 32-bit numbers written in dotted-decimal notation (e.g., `192.168.1.10`).

### Structure and CIDR
- IPv4 = **4 octets** = 32 bits.
- **CIDR notation:** `192.168.1.10/24` → first 24 bits = network prefix.
- **Subnet mask:** `/24` = `255.255.255.0`.

**Example (bitwise AND):**
- IP: `192.168.1.10` → `11000000.10101000.00000001.00001010`
- Mask: `255.255.255.0` → `11111111.11111111.11111111.00000000`
- Network: `192.168.1.0`

### Usable hosts
- Hosts = `2^(32-n) - 2` (excluding network & broadcast).
- `/24` → 254 hosts, `/30` → 2 hosts.
- `/31` and `/32` are special cases (RFC 3021).

### Network and broadcast
- Network address: lowest address (host bits 0)
- Broadcast address: highest address (host bits 1)

### Private vs Public
- **Private (RFC 1918):**
  - `10.0.0.0/8`
  - `172.16.0.0/12`
  - `192.168.0.0/16`
- Private addresses require NAT to reach the public Internet.

### Routing
- Routers operate at Layer 3.
- Packets traverse multiple routers; each hop strips link-layer headers.

### IPv6
- 128-bit addresses, written in hex (`2001:0db8::1`), solving IPv4 exhaustion.
- `/64` is common LAN prefix.

---

## 4) TCP and UDP

IP delivers packets between hosts; **transport protocols** enable process-to-process communication.

### Port ranges
- Well-known: `0–1023` (HTTP 80, SSH 22)
- Registered: `1024–49151`
- Dynamic/Private: `49152–65535`

### UDP
- Connectionless, minimal overhead.
- No ordering or retransmission.
- Header: source port, destination port, length, checksum.
- Use cases: DNS, streaming, gaming.
- Analogy: standard mail without delivery confirmation.

### TCP
- Connection-oriented and reliable.
- Header: source/dest port, seq/ack numbers, flags, window, checksum, options.
- Three-way handshake:
  1. Client → Server: SYN
  2. Server → Client: SYN+ACK
  3. Client → Server: ACK
- Reliability: retransmission, flow control, ordering.
- Congestion control: slow start, congestion avoidance, fast retransmit/recovery.
- Use cases: HTTP, SSH, FTP, email.

### TCP vs UDP

| Feature | UDP | TCP |
|---|---:|---:|
| Connection | No | Yes |
| Ordering | No | Yes |
| Reliability | No | Yes |
| Overhead | Low | Higher |
| Typical use | DNS, streaming, gaming | Web, email, file transfer |

---

## 5) Encapsulation

**Encapsulation**: each layer adds headers/trailers to pass data to the lower layer.

1. Application layer: user/application data
2. Transport layer: TCP/UDP header → segment/datagram
3. Network layer: IP header → packet
4. Data Link layer: link header/trailer → frame → transmitted

**Packet flow:** browser request → TCP handshake → TCP segment → IP packet → frame → routers → destination → decapsulation to application.

---

## 6) Telnet

Tested TCP services on target VM:

- Echo server (port 7): echoed text.
- Daytime server (port 13): returned date/time.
- HTTP server (port 80): sent manual `GET / HTTP/1.1` request.

**Observations:**
- Echo/daytime are plaintext and insecure.
- Telnet sends data unencrypted.
- Blank line needed to terminate HTTP headers.

**Commands:**
```bash
telnet MACHINE_IP 7
telnet MACHINE_IP 13
telnet MACHINE_IP 80
```

---

## Conclusion

The **Networking Concepts** room provides a practical overview of network communication. Understanding OSI and TCP/IP models helps relate theoretical concepts to real protocols. IP addressing and subnetting are essential for network design and troubleshooting. TCP and UDP choice affects reliability, performance, and latency. Encapsulation enables structured, modular communication. Telnet exercises demonstrate basic TCP services and highlight the importance of secure protocols.

---

## Key Takeaways

- **OSI**: conceptual 7-layer model; **TCP/IP**: practical Internet stack.
- **IPv4**: 32-bit; CIDR (`/n`) defines network prefix; usable hosts = `2^(32-n) - 2`.
- Private IPs require **NAT** for Internet access.
- Routers forward packets at **Layer 3** using IP and routing tables.
- **UDP**: connectionless, low-latency; use when packet loss is tolerable.
- **TCP**: connection-oriented, reliable, flow/congestion control; use for ordered delivery.
- **Encapsulation**: each layer adds headers for end-to-end delivery.
- Telnet exercises are educational; avoid plaintext for sensitive data.
