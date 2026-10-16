# Network Labs

Hands-on networking and packet-analysis portfolio built in an isolated VirtualBox lab. The repository currently contains a Python/Scapy packet sniffer with retained screenshots and reproducible lab instructions.

> **Scope:** Educational and authorized lab use only. The sniffer can expose packet metadata and application payloads, so it should only be used on systems and networks you own or are explicitly permitted to inspect.

## Portfolio Project

| Project | Focus | Current evidence |
| --- | --- | --- |
| [Basic Network Sniffer](BasicNetworkSniffer/) | Live packet capture and protocol inspection with Scapy | Source code, setup instructions, lab topology, retained screenshots, validation notes |

## What the project demonstrates

- Live packet capture on a selected Linux interface.
- IPv4 source/destination inspection.
- TCP, UDP, and ICMP protocol identification.
- TCP/UDP source and destination port extraction.
- Packet length, summary, and bounded payload display.
- Controlled two-VM traffic generation for ICMP and TCP lab testing.
- Clear separation between observed evidence, intended tests, and current limitations.

## Lab topology

```text
VirtualBox host-only network

Kali Linux / sniffer                   Ubuntu Server / traffic peer
192.168.56.103                         192.168.56.102
        |                                      |
        +------------- host-only --------------+
                      network
```

The retained setup screenshot shows the two lab hosts on the `192.168.56.0/24` host-only network. The sniffer source is currently configured for interface `eth1`; verify the interface name before running it on another machine.

## Quick start

```bash
cd BasicNetworkSniffer
python3 -m venv .venv
source .venv/bin/activate
python3 -m pip install -r requirements.txt
sudo .venv/bin/python network_sniffer.py
```

Generate authorized test traffic from the Ubuntu lab VM:

```bash
# ICMP
ping -c 4 192.168.56.103

# TCP listener on Ubuntu
nc -lvnp 4444
```

Then, from Kali:

```bash
echo "Hello CodeAlpha Network Sniffer" | nc 192.168.56.102 4444
```

## Evidence and validation

The repository does **not** claim production IDS capability, encrypted payload visibility, or comprehensive protocol decoding. Current retained evidence is documented in [docs/VALIDATION.md](docs/VALIDATION.md), with screenshot-specific notes in [BasicNetworkSniffer/screenshots/README.md](BasicNetworkSniffer/screenshots/README.md).

## Documentation

- [Architecture](docs/ARCHITECTURE.md)
- [Validation](docs/VALIDATION.md)
- [Testing strategy](docs/TESTING_STRATEGY.md)
- [Limitations](docs/LIMITATIONS.md)
- [Roadmap](docs/ROADMAP.md)
- [Security and responsible use](SECURITY.md)
- [Changelog](CHANGELOG.md)

## Repository structure

```text
Network-Labs/
├── README.md
├── SECURITY.md
├── CHANGELOG.md
├── docs/
│   ├── ARCHITECTURE.md
│   ├── VALIDATION.md
│   ├── TESTING_STRATEGY.md
│   ├── LIMITATIONS.md
│   └── ROADMAP.md
└── BasicNetworkSniffer/
    ├── network_sniffer.py
    ├── requirements.txt
    ├── auto_screenshots.sh
    ├── README.md
    ├── docs/
    │   ├── ARCHITECTURE.md
    │   └── VALIDATION.md
    └── screenshots/
        ├── README.md
        └── *.png
```

## Portfolio-safe summary

> Built a Python/Scapy network packet sniffer in an isolated two-VM lab to inspect IPv4, TCP, UDP, and ICMP traffic, including packet metadata, ports, summaries, and bounded raw payload output. Documented the lab topology, validation procedure, evidence boundaries, and operational limitations.
