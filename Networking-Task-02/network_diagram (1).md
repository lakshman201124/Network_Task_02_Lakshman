# Network Diagram — Communication Flow (Part D)

What happens when I open **www.google.com**:

```
   +-------------+
   | Your Device |   1. Type www.google.com → device needs Google's IP
   | 192.168.1.28|
   +-------------+
          |
          v
   +-------------+
   |   Router    |   2. Forwards the DNS request out to the internet
   | 192.168.1.1 |      (acts as gateway + NAT)
   +-------------+
          |
          v
   +-------------+
   | DNS Server  |   3. Looks up www.google.com,
   | 103.57.86.8 |      returns Google's IP (142.250.146.138)
   +-------------+
          |
          v
   +-------------+
   |Google Server|   4. Device opens a connection to that IP
   |142.250.146.138|    and sends an HTTP request for the page
   +-------------+
          |
          v
   +-------------+
   | Response    |   5. Google sends the page data back along the
   | back to you |      same path; the browser renders the website
   +-------------+
```

### Step-by-step explanation

1. **Your Device** — You type `www.google.com`. The device first checks its DNS cache; if the name isn't known, it sends a DNS query toward the configured DNS server.

2. **Router** — The query leaves your network through the router (the default gateway). The router uses NAT so your private device can communicate over the internet using the public IP.

3. **DNS Server** — The DNS server (`103.57.86.8`) resolves `www.google.com` and replies with Google's IP address, e.g. `142.250.146.138`.

4. **Google Server** — Now knowing the IP, your device opens a TCP/TLS connection to Google's server and sends an HTTP request asking for the web page.

5. **Response Back to Device** — Google's server returns the page data, which travels back through the router to your device, and the browser renders the page on screen.

*Diagram file:* `network_diagram.png`
