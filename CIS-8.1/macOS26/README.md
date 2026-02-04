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
fleetctl apply --policies-team "workstations" -f cis-macOSTahoe-policies.yaml
```

---

## Context: CIS Recommendation Splits

> **Why do some CIS Recommendations map to multiple Fleet policies?**
>
> This occurs when a single recommendation covers multiple technical controls, hardware types, or granular sub-settings.

### 📋 The 11 Major Splits

| CIS ID | Topic | Why It Was Split | # of Policies |
| ------ | ----- | ---------------- | :-----------: |
| 2.5.2.2 | Siri Settings | Split to cover individual toggles for Lock Screen access, Voice Triggers ("Hey Siri"), Status Menu visibility, and Type-to-Siri. | 8 |
| 5.2.3 | Password Complexity | Broken down into separate checks for Numeric, Alphabetic, and Special Character requirements to allow granular enforcement. | 3 |
| 3.4 | Audit Retention | Split into checks for retention time (days), the existence of a max-size limit, and the auditd process state. | 3 |
| 5.3.1 | Storage Encryption | Separated to handle modern APFS volumes vs. legacy CoreStorage logical volumes. | 2 |
| 6.3.5 | Safari IP Hiding | Provides both "Enabled" and "Disabled" variants, allowing organizations to choose their privacy posture (visibility vs. proxy). | 2 |
| 2.1.1.1/2 | iCloud Sync | Split to differentiate between Passwords vs. Keychain syncing and iCloud Drive vs. Desktop/Documents syncing. | 2 each |
| 5.1.2 | SIP (System Integrity) | Splits the general requirement from a specific technical audit of the SIP state to ensure no "partially disabled" mode. | 2 |
| 2.4.1 | Menu Bar Icons | General audit of icons vs. a specific focal check for the Bluetooth status menu. | 2 |
| 2.12.2 | Touch ID | Split to audit generic Touch ID state and a specific sub-check for its usage in secure prompts. | 2 |
| 2.6.1.1 | Location Services | Implementation split to verify the global toggle vs. a specific "Enabled" state expected by auditing tools. | 2 |
| 6.3.10 | Safari UI | Shared ID for "Show Status Bar" and a separate probe for "Popup Windows" auditing logic. | 2 |

### 📊 Summary of Trade-offs

| ✅ Pros of Splitting | ❌ Cons of Splitting |
| ------------------- | ------------------- |
| **Granular Reporting** — See exactly which part of Siri or Password policy failed. | **Dashboard Noise** — Increases the total policy count (136 vs 125). |
| **Cross-Architecture Support** — Correctly identifies compliance on both Intel and Apple Silicon Macs. | **Mapping Complexity** — Requires cross-referencing multiple Fleet IDs back to one CIS Recommendation. |
| **Flexibility** — Allows overriding one part of a complex block (e.g., requiring special chars but not mixed case). | |

---

## Policy Categories

The policies cover the following security categories:

| Category | Description |
| -------- | ----------- |
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
