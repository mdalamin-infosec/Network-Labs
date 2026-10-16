# Basic Network Sniffer Architecture

## Execution path

```text
Scapy sniff(iface="eth1", store=False)
              |
              v
      analyze_packet(packet)
              |
      +-------+--------+----------------+
      |                |                |
      v                v                v
     IPv4             TCP/UDP/ICMP     Raw
 addresses             metadata       payload
      |                |                |
      +----------------+----------------+
                       |
                       v
                 terminal output
```

`store=False` prevents Scapy from keeping the captured packet list in memory. The application still prints observed metadata and payload bytes to the terminal, so terminal output must be treated as potentially sensitive.

## Current design choices

- Single-process terminal application.
- Callback-based packet handling through Scapy.
- No persistent packet storage.
- No explicit capture filter.
- Hard-coded capture interface.
- Bounded raw-payload display (`[:150]`).

The implementation is intentionally small and is suitable for demonstrating packet parsing fundamentals rather than production monitoring architecture.
