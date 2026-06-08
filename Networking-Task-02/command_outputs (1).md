# Command Outputs — Practical Command Exercise (Part E)

Commands run on Windows: `ipconfig /all`, `nslookup google.com`, `ping google.com`.

---

## ipconfig /all
Key values from the active **Wireless LAN adapter WiFi** (Realtek RTL8188EU 802.11n USB):

- Host Name: `LakshmanPC`
- IPv4 Address: `192.168.1.28`
- Subnet Mask: `255.255.255.0`
- Default Gateway: `192.168.1.1`
- Physical (MAC) Address: `7C-C2-C6-20-CB-FB`
- DHCP Enabled: Yes

*Screenshot:* `ipconfig_all.jpg`

---

## nslookup google.com
- Resolver (Server): `blr-tdc-bngs-13` → `103.57.86.8`
- Returned for `google.com` (non-authoritative): multiple addresses
  - IPv6: `2404:6800:4000:1006::64` and others
  - IPv4: `142.250.146.100`, `142.250.146.101`, `142.250.134.113`, `142.250.146.102`, `142.250.146.139`, `142.251.220.78`, `142.250.146.138`, `142.250.134.102`

Google returns many IPs so traffic can be load-balanced across servers.

*Screenshot:* `nslookup.jpg`

---

## ping google.com
- Resolved to: `142.250.146.138`
- Packets: Sent = 4, Received = 4, **Lost = 0 (0% loss)**
- Round-trip times: Min = 17 ms, Max = 26 ms, Avg = 20 ms, TTL = 114

*Screenshot:* `ping.jpg`
