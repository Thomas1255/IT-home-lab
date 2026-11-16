# Setup Record

Status: Windows Server 2025 Standard Evaluation with Desktop Experience installed and first sign-in verified in screenshots. DC01 uses Internal Network LabNet. Guest addressing, Active Directory, and client deployment remain pending.

## Host inventory

Initial inventory reported by the lab owner; not independently inspected:

| Component | Reported value |
| --- | --- |
| Host operating system | Windows 11 Home, 64-bit; version/build pending |
| Memory | 32 GB |
| Processor | AMD Ryzen 9 7900X; 12 cores reported |
| Physical storage | Two SSDs and one HDD |
| Hardware virtualization | Enabled, as observed in Task Manager |

Oracle VirtualBox is installed, as confirmed by the lab owner. Read-only inspection of the installed executable reports version 7.2.22.175245. Screenshots verify successful DC01 boot and graphical Windows sign-in. The intended lab SSD and its available space remain unspecified.

## Lab design

Oracle VirtualBox is the hypervisor. The following DC01 settings were verified in the lab owner's screenshots:

| Setting | Observed value |
| --- | --- |
| VirtualBox VM name | DC01 |
| Windows computer name / membership | DC01 / WORKGROUP, verified in Server Manager |
| Installed operating system | Windows Server 2025 Standard Evaluation with Desktop Experience |
| Installed version/build | 24H2, OS build 26100.32230, verified using winver |
| Memory | 6144 MB |
| Virtual processors | 2 |
| Firmware | EFI enabled |
| Virtual disk | DC01.vdi, 80 GB; full preallocation unchecked in the creation wizard |
| Optical drive | Windows Server 2025 evaluation x64 ISO attached |
| VirtualBox OS profile | Windows Server 2022 (64-bit); this profile does not identify an installed OS |
| Network adapter 1 | Intel PRO/1000 MT Desktop, Internal Network named LabNet |

The ISO was downloaded and used from its existing location outside the Git checkout. The VM files are also outside the checkout. A pre-installation screenshot shows only adapter 1 in the network summary, attached to Internal Network named LabNet. Guest IP addressing and connectivity remain unverified.

## Recovery checkpoint

The lab owner's screenshot verifies a VirtualBox snapshot named `01-Clean-Server-Install`, with Current State beneath it, after Windows installation and edition verification. Snapshot restoration has not been tested.

## Verified setup steps

- Oracle VirtualBox installation: lab owner reported installation complete; executable version inspected separately.
- Windows Server evaluation ISO download: confirmed by the lab owner and attached image visible in the DC01 storage summary.
- DC01 creation: screenshots show the registered VM with the resources listed above.
- DC01 network attachment: screenshot verifies adapter 1 uses Internal Network LabNet. No guest IP configuration or connectivity is claimed.
- Windows installation: screenshots show the empty 80 GB virtual installation target, initial Administrator password setup, and successful sign-in to the graphical desktop with Server Manager.
- Edition verification: About Windows identifies Windows Server 2025 Standard Evaluation, version 24H2, OS build 26100.32230. The graphical desktop confirms Desktop Experience. Passwords were not collected or recorded.
- Recovery checkpoint: `01-Clean-Server-Install` exists in the VirtualBox snapshot tree, verified by screenshot. Restore testing is not claimed.
- Windows computer name: Server Manager > Local Server screenshot shows Computer name DC01 and Workgroup WORKGROUP. This verifies the hostname; it does not establish an Active Directory domain or domain controller.

## Outstanding initial setup

The latest Server Manager screenshot shows DHCP-enabled IPv4 configuration, Windows not activated, and no recorded update checks or installed updates in that view. Exact IP configuration, successful activation, and servicing remain to be verified before Active Directory setup.

Completed configurations and their verification results will be documented here. Passwords and product keys are excluded.
