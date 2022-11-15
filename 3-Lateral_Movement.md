# Module 3: Lateral Movement

## Part 1: RDP

For part 1, the goal is to investigate the RDP connections and determine if any successful connections came from an IP you don't expect.

Dashboards used:
- RDP
- CONN

Searches used:
- `destination.port: 3389`
- `destination.port: 3389 AND NOT source.ip: 172.32.0.0/16`
- `NOT source.ip: 172.32.37.0/24`

Filters used:
- `zeek.rdp.result: encrypted`

## Part 2: SSH

In combination with the analysis you performed in part 1, your goal in this section is to investigate the timeline associated with the RDP and SSH connections.

Dashboards used:
- CONN

Searches used:
- `destination.port: 22`
