# CIS Benchmark Policies for Fleet

This repository provides a collection of security policies designed for use with [FleetDM](https://fleetdm.com/). These policies help you audit devices for compliance with the Center for Internet Security (CIS) Benchmarks.

Each policy is mapped to its corresponding CIS Safeguard number (e.g., `CIS 5.1`), simplifying compliance auditing and helping you track your organization's security posture. This is a step forward in achieving SOC 2 compliance.

## Supported Platforms

This repository currently includes CIS Benchmark v8.1 policies for the following operating systems:

*   [macOS 15](macOS15/README.md)
*   [Windows 11](win11/README.md)

## Usage

To use these policies, follow the steps below:

1.  **Clone the repository:**
    ```sh
    git clone https://github.com/karmine05/fleet_policies.git
    cd fleet_policies
    ```

2.  **Apply Policies:**
    Navigate to the directory for your target operating system (e.g., `macOS15/`) and follow the instructions in its `README.md` file to apply the policies using `fleetctl`.

    For example, for macOS 15:
    ```sh
    cd macOS15
    fleetctl apply -f cis-macOS15-policies.yaml
    ```

## Directory Structure

```
.
├── CIS Control CIS Safeguard Asset Type Sec.csv
├── LICENSE
├── macOS15
│   ├── cis-macOS15-policies.yaml
│   ├── cis-macos15-section-map.csv
│   └── README.md
└── win11
    ├── cis-win11-policies.yaml
    ├── cis-win11-section-map.csv
    └── README.md
```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.