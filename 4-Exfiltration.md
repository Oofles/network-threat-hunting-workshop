# Module 4: Exfiltration

In this section you are continuing the investigation to determine if any internal hosts exfiltrated sensitive data.

Dashboards used:
- CONN

Searches used:
- `source.ip: 172.32.37.10 AND NOT destination.ip: 20.42.5.0/24`
- `FCqk7B2WM41dP6WtL7`

Filters used:
- `destination.ip: 20.110.212.125`
- `source.ip: 172.32.37.10`

