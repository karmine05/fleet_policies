# CIS Benchmark for Ubuntu 24 (Desktop & Server)

This directory contains policies to audit Ubuntu 24 (Desktop and Server) hosts for compliance with the Center for Internet Security (CIS) Benchmark v8.1.

Both variants share many safeguards. Where they differ, separate policy bundles are provided so you can apply only what is relevant to each asset type.

Each policy is mapped and tagged with its corresponding CIS Safeguard number (e.g., `CIS 5.1`). This direct mapping simplifies compliance auditing, allowing you to track your security posture against the CIS Benchmark and progress toward frameworks like SOC 2.

## Contents

| File | Purpose |
|------|---------|
| `cis-ubuntu24-desktop-policies.yaml` | Fleet policy definitions for Ubuntu 24 Desktop |
| `cis-ubuntu24-server-policies.yaml` | Fleet policy definitions for Ubuntu 24 Server |
| `cis-ubuntu24-desktop-section-map.csv` | Mapping of Desktop policies to CIS sections |
| `cis-ubuntu24-server-section-map.csv` | Mapping of Server policies to CIS sections |

## Usage

### 1. Clone Repository

```sh
git clone https://github.com/karmine05/fleet_policies.git
cd fleet_policies/CIS-8.1/ubuntu24
```

### 2. Apply Policies with fleetctl

Apply Desktop policies:
 
```sh
fleetctl apply -f cis-ubuntu24-desktop-policies.yaml
```

Apply Server policies:
 
```sh
fleetctl apply -f cis-ubuntu24-server-policies.yaml
```

(You can apply one or both depending on your managed host types.)

### 3. Validation & Reporting

After applying, use Fleet's policy reporting to verify compliance and surface failing hosts. Policies are labeled with their CIS safeguard for straightforward filtering and dashboarding.

## Notes

* Review each policy before broad rollout—some hardening items may impact legacy workloads.
* Consider phasing enforcement: start in "monitor" mode (observe failures) before remediating.
* Keep both policy sets updated as CIS guidance evolves.

## License

This project is licensed under the MIT License. See the root `LICENSE` file for details.
