# Networking Task 02 — Network Devices & IP Addressing

**Author:** Lakshman
**OS used:** Windows 11 (Version 10.0.26200)
**Date:** 08 June 2026

This task covers common network devices, IP address classification, how my own network is structured, and what happens end-to-end when a website is opened.

---

## Summary by Part

**Part A — Network Devices:** Researched Router, Switch, Hub, Access Point, Firewall, and Modem — each with its purpose, how it works, and real-world usage. See `answers.md`.

**Part B — IP Classification:** Classified 6 addresses. Private: `192.168.1.10`, `10.0.0.5`, `172.16.5.20`, `192.168.100.1`. Public: `8.8.8.8` (Google DNS), `1.1.1.1` (Cloudflare DNS). See `answers.md`.

**Part C — My Network:**
| Detail | Value |
|---|---|
| IPv4 Address | `192.168.1.28` |
| Default Gateway | `192.168.1.1` |
| DNS Server | `103.57.86.8` |
| IP Range | `192.168.0.0/16` → **Private** |

The router is the default gateway (DHCP + NAT + routing). If DNS failed, names like `google.com` wouldn't resolve and name-based browsing would break.

**Part D — Communication Flow:** Diagram + explanation of opening `www.google.com`: Device → Router → DNS Server → Google Server → Response. See `network_diagram.md`.

**Part E — Command Exercise:** Ran `ipconfig /all`, `nslookup google.com`, `ping google.com`.
- DNS returned `142.250.146.138` (among several) for Google.
- Ping was successful (0% loss, avg 20 ms).
- DNS is essential because communication is by IP, not name — the name must be resolved first.

See `command_outputs.md`.

---

## Files in This Folder

- `README.md` — this summary
- `answers.md` — Parts A, B, C, E (written answers)
- `network_diagram.md` — Part D communication flow
- `command_outputs.md` — Part E command outputs
- Screenshots: `ipconfig_all.jpg`, `nslookup.jpg`, `ping.jpg`
- `network_diagram.png` — diagram (Part D)
