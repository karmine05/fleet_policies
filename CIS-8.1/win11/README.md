# CIS Benchmark for Win 11

This directory contains policies to audit Win 11 devices for compliance with the Center for Internet Security (CIS) Benchmark v8.1.

These policies provide a robust framework for securing your Windows. Each policy is meticulously mapped and tagged with its corresponding CIS Safeguard number (e.g., `CIS 5.1`). This direct mapping simplifies compliance auditing, allowing you to precisely track your organization's security posture against the CIS Benchmark. A step forward in your SOC 2 compliance. 

## Usage

### 1. Download Policies

Clone this repository to your local machine:

```sh
git clone https://github.com/karmine05/fleet_policies.git
cd <your-repo-name>/win11
```

### 2. Apply with fleetctl

Use `fleetctl` to apply the Win 11 security policies to your Fleet instance.

```sh
fleetctl apply -f cis-win11-policies.yaml
```