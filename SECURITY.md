# Security and Responsible Use

## Authorized use only

This repository contains packet-capture tooling. Use it only on hosts and networks that you own or where you have explicit authorization to capture traffic.

Packet capture can reveal sensitive information, including addresses, ports, host activity, and unencrypted application payloads. Do not deploy this project for covert monitoring, credential collection, or interception of third-party traffic.

## Lab boundary

The documented workflow uses an isolated VirtualBox host-only network between Kali Linux and Ubuntu Server. IP addresses in the documentation are lab addresses and should not be treated as production configuration.

## Data handling

- Do not commit packet captures containing real credentials, tokens, personal data, or confidential traffic.
- Review screenshots before publishing them.
- Treat payload output as potentially sensitive.
- Prefer synthetic or intentionally generated test traffic for portfolio evidence.

## Reporting a security issue

If this repository is used as a public portfolio, report security issues privately to the repository owner rather than placing sensitive details in a public issue.
