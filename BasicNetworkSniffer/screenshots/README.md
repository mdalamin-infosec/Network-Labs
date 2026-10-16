# Screenshot Evidence

These screenshots are retained from the original Kali/Ubuntu lab. They should be interpreted according to what is visibly demonstrated, not according to their filenames alone.

| File | What is visibly useful | Evidence strength |
| --- | --- | --- |
| `01-network-setup.png` | Kali and Ubuntu interface/address information in the two-VM lab | Strong for topology/setup |
| `02-sniffer-running.png` | Basic Network Sniffer startup banner and `eth1` interface | Strong for startup |
| `03-icmp-capture.png` | Terminal window from the ICMP capture workflow | Weak; expected ICMP record is not clearly visible |
| `04-tcp-payload-capture.png` | Terminal activity from the TCP capture workflow | Weak; expected payload record is not clearly visible |

## Replacement standard

When recapturing evidence:

1. Show the test command or label the traffic source.
2. Show the matching packet record with the relevant protocol/port/payload field.
3. Avoid unrelated terminal history and secrets.
4. Keep IP addresses limited to the isolated lab.
5. Prefer a small text transcript or synthetic PCAP-derived test fixture when it provides clearer evidence than a GUI screenshot.
