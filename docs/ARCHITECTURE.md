# Architecture

## Objective

The current repository demonstrates basic packet observation in an isolated lab rather than a production monitoring platform.

## Data flow

```text
Ubuntu Server test traffic
        |
        |  ICMP / TCP / UDP
        v
VirtualBox host-only network
        |
        v
Kali Linux interface eth1
        |
        v
Scapy sniff()
        |
        v
analyze_packet(packet)
        |
        +--> IPv4 addresses
        +--> protocol
        +--> TCP/UDP ports
        +--> packet length
        +--> bounded Raw payload (first 150 bytes)
        +--> Scapy packet summary
        |
        v
Terminal output
```

## Components

| Component | Role |
| --- | --- |
| `BasicNetworkSniffer/network_sniffer.py` | Captures and prints packet information. |
| Scapy | Packet-capture and protocol-parsing library. |
| Kali Linux | Current sniffer host in the documented lab. |
| Ubuntu Server | Traffic-generation peer. |
| VirtualBox host-only network | Provides an isolated path between the VMs. |
| `auto_screenshots.sh` | Legacy convenience script for collecting GUI screenshots in the original lab layout. |

## Trust and scope boundaries

The project is intentionally simple. It does not perform stream reassembly, TLS decryption, persistent packet storage, alert correlation, anomaly detection, or response automation. Those capabilities should not be inferred from terminal packet inspection.
