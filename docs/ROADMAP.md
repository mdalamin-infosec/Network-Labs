# Roadmap

## Priority 1 — reproducible capture configuration

- Add CLI arguments for interface selection.
- Add optional BPF filters.
- Validate the selected interface and provide a clear error message.

## Priority 2 — stronger evidence

- Re-run ICMP, TCP payload, and UDP tests.
- Retain sanitized terminal transcripts or synthetic PCAP fixtures.
- Replace ambiguous legacy screenshots with clear evidence.

## Priority 3 — engineering quality

- Add unit tests for packet formatting using synthetic Scapy packets.
- Add structured JSON output.
- Add graceful shutdown statistics.
- Record packet counts by protocol.

## Priority 4 — deeper network analysis

- Add IPv6 support.
- Add basic DNS/HTTP metadata parsing for intentionally generated lab traffic.
- Add optional PCAP input for offline analysis.

These items are roadmap goals, not current capabilities.
