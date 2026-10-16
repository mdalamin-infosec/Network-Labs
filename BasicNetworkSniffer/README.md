# Basic Network Sniffer

A small Python/Scapy packet-inspection project for an isolated two-VM lab. It captures traffic from a configured Linux interface and prints selected packet metadata to the terminal.

Originally developed as part of a CodeAlpha cybersecurity internship exercise.

## Capabilities

For captured IPv4 packets, the script reports:

- packet sequence number and local observation time;
- packet length;
- source and destination IPv4 addresses;
- TCP, UDP, or ICMP classification;
- TCP/UDP source and destination ports;
- up to the first 150 bytes of a Scapy `Raw` payload when present;
- Scapy's packet summary.

## Lab environment

```text
Kali Linux       192.168.56.103   sniffer host
Ubuntu Server    192.168.56.102   traffic peer
Network          VirtualBox host-only
Capture iface    eth1             current source configuration
```

Verify interface names with:

```bash
ip -br addr
```

## Installation

```bash
python3 -m venv .venv
source .venv/bin/activate
python3 -m pip install -r requirements.txt
```

Scapy packet capture normally requires elevated privileges. Run the interpreter from the virtual environment explicitly:

```bash
sudo .venv/bin/python network_sniffer.py
```

## Controlled validation

### ICMP

From Ubuntu Server:

```bash
ping -c 4 192.168.56.103
```

The sniffer should classify relevant IPv4 echo traffic as ICMP.

### TCP with intentional plaintext payload

On Ubuntu Server:

```bash
nc -lvnp 4444
```

From Kali Linux:

```bash
echo "Hello CodeAlpha Network Sniffer" | nc 192.168.56.102 4444
```

The sniffer should show TCP metadata. If the application data is present in a captured segment as a Scapy `Raw` layer, the script prints a bounded representation of that payload.

### UDP

UDP parsing is implemented in the source, but no clear retained UDP validation artifact is currently included. Treat UDP as implemented-but-not-retained-evidence until a controlled test is recorded.

## Screenshots

See [`screenshots/README.md`](screenshots/README.md) before using the images as portfolio evidence. The network setup and sniffer startup are visible; the existing ICMP/TCP screenshots are weaker and should be replaced after a clean rerun.

## Architecture and validation

- [Project architecture](docs/ARCHITECTURE.md)
- [Project validation](docs/VALIDATION.md)
- [Repository-wide testing strategy](../docs/TESTING_STRATEGY.md)
- [Known limitations](../docs/LIMITATIONS.md)

## Ethical use

Capture only traffic you are authorized to inspect. Packet metadata and plaintext payloads can be sensitive. Use synthetic or intentionally generated traffic for public portfolio evidence.
