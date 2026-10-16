# Validation

## Current validation status

The repository contains source code and four retained screenshots from the original Kali/Ubuntu lab. The strongest retained evidence is the network setup and sniffer startup. The ICMP/TCP screenshots should be treated as legacy capture attempts rather than definitive packet-level proof because the visible frames do not clearly expose the expected packet records.

| Check | Evidence | Status |
| --- | --- | --- |
| Python source compiles | `python3 -m py_compile BasicNetworkSniffer/network_sniffer.py` | Reproducible locally |
| Screenshot script shell syntax | `bash -n BasicNetworkSniffer/auto_screenshots.sh` | Reproducible locally |
| Two-VM host-only topology | `screenshots/01-network-setup.png` | Retained evidence |
| Sniffer startup on `eth1` | `screenshots/02-sniffer-running.png` | Retained evidence |
| ICMP packet capture | Intended by `03-icmp-capture.png` | Retest recommended |
| TCP payload capture | Intended by `04-tcp-payload-capture.png` | Retest recommended |

## Reproduction procedure

### 1. Confirm interface

On the Kali/sniffer VM:

```bash
ip -br addr
```

The source currently uses `iface="eth1"`. If your host-only interface has a different name, update the script before testing.

### 2. Install dependency

```bash
cd BasicNetworkSniffer
python3 -m venv .venv
source .venv/bin/activate
python3 -m pip install -r requirements.txt
```

### 3. Start the sniffer

```bash
sudo .venv/bin/python network_sniffer.py
```

### 4. Generate ICMP traffic

From Ubuntu:

```bash
ping -c 4 192.168.56.103
```

Expected observation: IPv4 source/destination information and `Protocol : ICMP` for matching captured packets.

### 5. Generate TCP payload traffic

On Ubuntu:

```bash
nc -lvnp 4444
```

On Kali:

```bash
echo "Hello CodeAlpha Network Sniffer" | nc 192.168.56.102 4444
```

Expected observation: TCP metadata for the connection and, when the relevant segment includes a Scapy `Raw` layer, a bounded representation of the application payload.

## Evidence rule

A successful terminal display should be retained before claiming a specific protocol test as validated. Screenshots should include enough context to show the command, relevant packet record, and expected field(s) without exposing unrelated sensitive data.
