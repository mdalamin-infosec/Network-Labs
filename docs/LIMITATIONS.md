# Limitations

The current project is a basic packet-inspection lab and should be evaluated within that scope.

- The capture interface is hard-coded to `eth1`.
- Root/packet-capture privileges are normally required.
- There is no command-line interface for interface or filter selection.
- No BPF capture filter is applied, so the process can receive unrelated traffic visible to the interface.
- Only IPv4-specific fields are parsed explicitly; IPv6 is not handled in the custom output path.
- Raw payload display is not application-protocol decoding.
- Encrypted TLS application contents are not decrypted.
- TCP stream reassembly is not implemented.
- Payload bytes may contain sensitive information if used outside a controlled lab.
- No structured JSON/CSV output or persistent evidence store is implemented.
- No performance benchmark or packet-loss measurement has been recorded.
- The retained ICMP/TCP screenshots do not clearly demonstrate the intended packet records and should be replaced by stronger evidence.
- `auto_screenshots.sh` assumes the original `~/CodeAlpha_BasicNetworkSniffer` path, GUI screenshot tooling, SSH connectivity, and specific lab IP addresses, so it is not portable without editing.
