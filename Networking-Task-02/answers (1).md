# Answers — Networking Task 02

**Author:** Lakshman · **OS:** Windows 11 · **Date:** 08 June 2026

---

## Part A — Network Devices Research

### Router
- **Purpose:** Connects different networks together — most commonly your local home/office network to the internet — and decides the best path for data to travel between them.
- **How it works:** It reads the destination IP address of each packet, checks its routing table, and forwards the packet toward its destination. It also runs DHCP (handing out local IPs like `192.168.1.28`) and NAT (letting many private devices share one public IP).
- **Real-world usage:** The WiFi router at home that connects all your phones, laptops, and TVs to the internet through your ISP.

### Switch
- **Purpose:** Connects multiple devices *within the same local network* (LAN) and delivers data only to the specific device it's meant for.
- **How it works:** It learns the MAC address of every device plugged into each port, builds a MAC address table, and forwards each frame only to the correct port (Layer 2). This avoids the wasted traffic a hub creates.
- **Real-world usage:** Office and data-centre wired networks connecting many PCs, printers, and servers.

### Hub
- **Purpose:** An older, basic device that connects several devices in a LAN.
- **How it works:** It has no intelligence — any data arriving on one port is broadcast to *all* other ports (Layer 1), so every device receives everything. This causes collisions and wastes bandwidth.
- **Real-world usage:** Largely obsolete and replaced by switches; occasionally seen in very old or tiny legacy setups.

### Access Point (AP)
- **Purpose:** Provides wireless (WiFi) access to a wired network.
- **How it works:** It bridges wireless devices to the wired LAN, converting between WiFi radio signals and Ethernet so wireless clients can reach the rest of the network.
- **Real-world usage:** Extending WiFi coverage across offices, campuses, and large homes; it's also the "WiFi half" built into a home router.

### Firewall
- **Purpose:** A security device or software that monitors and filters incoming and outgoing traffic to protect a network.
- **How it works:** It checks each packet against a set of rules (allow or block based on IP, port, or protocol). A stateful firewall also tracks active connections to make smarter decisions.
- **Real-world usage:** Blocking unauthorised access and attacks — e.g. Windows Defender Firewall on a PC, or a dedicated hardware firewall guarding a company network.

### Modem
- **Purpose:** Connects your home network to your ISP by converting signals between your network and the ISP's transmission medium (cable / DSL / fibre).
- **How it works:** It *mo*dulates and *dem*odulates signals (hence "modem") — turning your network's digital data into a form that travels over the ISP's line, and back again.
- **Real-world usage:** The broadband box from your ISP; in many homes the modem and router are combined into a single unit.

---

## Part B — IP Address Classification

| IP Address | Category | Why |
|---|---|---|
| `192.168.1.10`  | **Private** | Falls in the `192.168.0.0 – 192.168.255.255` private block (Class C private range), used inside local networks. |
| `10.0.0.5`      | **Private** | Falls in the `10.0.0.0 – 10.255.255.255` private block (Class A private range), common in large internal networks. |
| `172.16.5.20`   | **Private** | Falls in the `172.16.0.0 – 172.31.255.255` private block (Class B private range). |
| `8.8.8.8`       | **Public**  | A globally routable address — it's Google's Public DNS server, reachable from anywhere on the internet. |
| `1.1.1.1`       | **Public**  | A globally routable address — Cloudflare's Public DNS server. |
| `192.168.100.1` | **Private** | Falls in the `192.168.0.0/16` private block; typically a router/gateway address on a local network. |

**Key idea:** Private IPs (`10.x`, `172.16–31.x`, `192.168.x`) are reserved for use inside local networks and are *not* routed on the public internet. Public IPs are unique, globally routable, and assigned by ISPs/registries.

---

## Part C — Understanding Your Network

**Found on my device:**
- IPv4 Address: `192.168.1.28`
- Default Gateway: `192.168.1.1`
- DNS Server: `103.57.86.8`

**Answers:**

1. **Which IP range does your device belong to?**
   `192.168.0.0 – 192.168.255.255` (the `192.168.0.0/16` block).

2. **Is it Public or Private?**
   **Private** — `192.168.x.x` is a reserved private range, so my device isn't directly reachable from the internet; it goes out through the router's NAT.

3. **What role does your router play in your network?**
   It's the **default gateway** for all my devices. It assigns local IPs via DHCP, performs NAT so the whole network shares one public IP, and routes all traffic between my local network and the internet. It's the single point through which everything enters and leaves my network.

4. **What would happen if the DNS server stopped working?**
   Domain names could no longer be translated into IP addresses. Websites typed by name (like `google.com`) would fail with "can't reach" errors, even though the internet connection itself is fine. Connecting directly by raw IP would still work, but normal name-based browsing would effectively break.

*Screenshot:* `ipconfig_all.jpg`

---

## Part E — Practical Command Exercise (Answers)

1. **What IP address did DNS return for Google?**
   `nslookup` returned several addresses for `google.com` — IPv6 (e.g. `2404:6800:4000:1006::64`) and IPv4 (`142.250.146.100`, `142.250.146.101`, `142.250.134.113`, and more). The `ping` then used **`142.250.146.138`**. (Google returns many IPs for load balancing.)

2. **Was the ping successful?**
   Yes — 4 packets sent, 4 received, **0% loss**, average 20 ms.

3. **Why is DNS important before communication begins?**
   Computers route data using IP addresses, not human-friendly names. Before any connection can start, the name (`google.com`) must first be resolved into an IP via DNS. Without that translation step, the device has no destination to send the request to, so communication can't even begin.

*Screenshots:* `nslookup.jpg`, `ping.jpg`
