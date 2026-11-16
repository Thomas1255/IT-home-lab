# Enterprise Active Directory & IT Help Desk Home Lab

A hands-on IT support lab for a fictional company of approximately 25 employees.

## Current status

DC01 runs Windows Server 2025 Standard Evaluation with Desktop Experience, and WIN11-01 runs Windows 11 Enterprise Evaluation. Both graphical sign-ins, Windows computer names, Active activation states, and baseline snapshots were verified in screenshots. DC01 updates are complete by the lab owner's report; client updates are deferred. Restoration of isolated LabNet networking remains pending. Active Directory and inter-VM connectivity are not configured or verified yet. Technologies listed below describe the planned full environment.

## Planned technologies

- Windows Server 2025, Active Directory Domain Services, and DNS
- A domain-joined Windows 11 workstation
- Organizational units, accounts, security groups, and Group Policy
- File shares and access permissions
- Windows troubleshooting tools and PowerShell
- GLPI and realistic Tier 1 support incidents

## Documentation

- [Setup record](docs/SETUP.md)
- [Troubleshooting knowledge base](docs/TROUBLESHOOTING.md)

## Lab practices

Use fictional employee data and an isolated lab network. Avoid exposing lab services to the internet and take VM snapshots before risky changes. Documentation will record completed work and verification results. Portfolio material must exclude credentials, license keys, and personal information.
