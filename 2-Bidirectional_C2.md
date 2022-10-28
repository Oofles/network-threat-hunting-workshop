# Module 2: Bidirectional C2

## Part 1: Hunting through Certificates

For Part 1 the goal is to investigate whether any internal hosts are browsing to pastebin.com. 

Dashboards used:
- TLS
- DNS
- CONN (Connection)

Searches used:
- `pastebin`
- `zeek.dns.query: *pastebin*`
- `destination.ip: (104.23.98.190 OR 104.23.99.190)`

Filters used:
- `source.ip: 172.32.24.201`
- `destination.ip: 104.23.99.190`

---

## Part 2: There's More to the Story!

In Part 2, the goal is to investigate the Source host further to see what other traffic it's involved in.

Dashboards:
- CONN
- TLS
- HTTP

Filters:
- `source.ip: 172.32.24.201`
- `tls.version: 1.0`
- `tls.established: false`
- `destination.ip: 23.211.109.200`
- `url.domain: 121.43.68.40`
- `user_agent.original: Go-http-client/1.1`

Search:
- `destination.ip: (20.110.25.96 OR 104.23.99.190)`

## Part 3: HTTP Payloads

In Part 3, the goal is to analyze the filtered HTTP PCAP to investigate what information was sent or received from meowmix.ironcatfood.com.

Wireshark Filters:
- 
