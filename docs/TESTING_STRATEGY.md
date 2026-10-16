# Testing Strategy

## Purpose

Validation should distinguish source-code correctness from actual packet-capture behavior.

## Layers

### 1. Static checks

```bash
python3 -m py_compile BasicNetworkSniffer/network_sniffer.py
bash -n BasicNetworkSniffer/auto_screenshots.sh
```

These checks detect syntax problems but do not prove live packet capture.

### 2. Controlled protocol tests

Use intentionally generated traffic in the isolated VM network:

| Test | Generator | Expected observation |
| --- | --- | --- |
| ICMP echo | `ping` | IPv4 addresses and ICMP classification |
| TCP connection | `nc` | TCP ports and packet summary |
| TCP plaintext payload | `echo ... | nc` | Raw payload when present in captured segment |
| UDP datagram | `nc -u` or equivalent | UDP source/destination ports |

### 3. Negative/edge tests

Future validation should also cover:

- packets without an IPv4 layer;
- IPv4 packets without a `Raw` payload;
- different interface names;
- invalid/nonexistent interfaces;
- high packet rates;
- graceful interruption with `Ctrl+C`;
- payloads containing non-printable bytes.

## Evidence quality

Prefer a short terminal transcript or sanitized PCAP-derived test fixture over screenshots alone. If packet captures are retained, use synthetic traffic and review them before committing.
