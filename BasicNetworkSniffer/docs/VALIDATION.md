# Basic Network Sniffer Validation

## Source-level checks

From the repository root:

```bash
python3 -m py_compile BasicNetworkSniffer/network_sniffer.py
bash -n BasicNetworkSniffer/auto_screenshots.sh
```

Passing these checks confirms syntax only.

## Live-lab checks

A complete live validation should record:

| Scenario | Expected result | Evidence to retain |
| --- | --- | --- |
| Sniffer startup | Process attaches to intended interface | terminal output |
| ICMP | Correct IPv4 endpoints and ICMP classification | sanitized transcript/screenshot |
| TCP | Correct source/destination ports | sanitized transcript/screenshot |
| TCP payload | Intentional plaintext appears only when `Raw` exists | sanitized transcript/screenshot |
| UDP | Correct UDP source/destination ports | sanitized transcript/screenshot |

## Current retained evidence

- `01-network-setup.png`: useful evidence of the documented lab IP configuration.
- `02-sniffer-running.png`: useful evidence that the sniffer was started on `eth1`.
- `03-icmp-capture.png`: insufficiently clear to substantiate an ICMP detection claim by itself.
- `04-tcp-payload-capture.png`: insufficiently clear to substantiate a payload-capture claim by itself.

Accordingly, documentation describes the last two as tests to rerun rather than completed quantitative validation.
