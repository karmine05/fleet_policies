# CIS Benchmark for macOS Tahoe (macOS 26)

This directory contains policies to audit macOS Tahoe (version 26) devices for compliance with the Center for Internet Security (CIS) Benchmark v1.0.0.

These policies provide a robust framework for securing your macOS. Each policy is meticulously mapped and tagged with its corresponding CIS Safeguard number (e.g., `CIS 5.1`). This direct mapping simplifies compliance auditing, allowing you to precisely track your organization's security posture against the CIS Benchmark. A step forward in your SOC 2 compliance. 

## Files

- **cis-macOSTahoe-policies.yaml** - The main policy file containing all 111 CIS benchmark policies
- **cis-macostahoe-section-map.csv** - CSV mapping of CIS safeguard IDs to policy controls

## Usage

### 1. Download Policies

Clone this repository to your local machine:

```sh
git clone https://github.com/karmine05/fleet_policies.git
cd <your-repo-name>/CIS-8.1/macOS_Tahoe
```

### 2. Apply with fleetctl

Use `fleetctl` to apply the macOS Tahoe security policies to your Fleet instance.

```sh
fleetctl apply -f cis-macOSTahoe-policies.yaml
```

## Policy Categories

The policies cover the following security categories:

| Category | Description |
|----------|-------------|
| updates | Software update configuration |
| malware-protection | XProtect and malware defense |
| cloud-storage | iCloud Drive and document sync |
| credentials | iCloud Keychain settings |
| firewall | macOS firewall configuration |
| sharing | AirDrop, file sharing, Bluetooth sharing |
| time-sync | Time service and NTP settings |
| remote-access | Screen sharing, remote login, remote management |
| network | Internet sharing, Bonjour, HTTP/NFS servers |
| caching | Content caching settings |
| backup | Time Machine configuration |
| ui-awareness | Menu bar status indicators |
| voice-assistant | Siri configuration |
| privacy-location | Location services |
| privacy-advertising | Ad tracking limits |
| privacy-telemetry | Diagnostic data sharing |
| privacy | On-device dictation, Apple Intelligence |
| authz | Authorization and sudo settings |
| screen-lock | Screen saver and password on wake |
| continuity | Universal Control |
| power | Power Nap, sleep, wake settings |
| application-control | Gatekeeper, app permissions |
| encryption | FileVault, volume encryption |
| login | Login window, auto-login, password hints |
| accounts | Guest account, root account, home folders |
| audit | Security auditing, logging |
| authn | Password complexity requirements |
| browser | Safari security settings |
| browser-privacy | Safari privacy settings |
| terminal | Terminal.app security |
| system-protection | SIP, AMFI, SSV |

## Requirements

Different policies have different requirements:

- **standard** - No special requirements
- **fleetd** - Requires Fleet's osquery agent (fleetd)
- **mdm** - Requires MDM profile deployment
- **fda** - Requires Full Disk Access

## Profile Levels

- **Level 1** - Base security recommendations suitable for most environments
- **Level 2** - Enhanced security for environments requiring stricter controls

## Reference

Based on: CIS Apple macOS 26 Tahoe Benchmark v1.0.0 (Released 2025-10-31)

