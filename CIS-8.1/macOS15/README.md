# CIS Benchmark for macOS 15

This directory contains policies to audit macOS 15 devices for compliance with the Center for Internet Security (CIS) Benchmark v8.1.

These policies provide a robust framework for securing your macOS. Each policy is meticulously mapped and tagged with its corresponding CIS Safeguard number (e.g., `CIS 5.1`). This direct mapping simplifies compliance auditing, allowing you to precisely track your organization's security posture against the CIS Benchmark. A step forward in your SOC 2 compliance. 

## Usage

### 1. Download Policies

Clone this repository to your local machine:

```sh
git clone https://github.com/karmine05/fleet_policies.git
cd <your-repo-name>/macOS15
```

### 2. Apply with fleetctl

Use `fleetctl` to apply the macOS 15 security policies to your Fleet instance.

```sh
fleetctl apply -f cis-macOS15-policies.yaml
```
