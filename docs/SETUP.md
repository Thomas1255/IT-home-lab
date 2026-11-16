# Setup Record

Status: DC01 VM created and its adapter set to Internal Network LabNet, as verified in the lab owner's screenshots. Windows Server installation and guest network addressing are pending.

## Host inventory

Initial inventory reported by the lab owner; not independently inspected:

| Component | Reported value |
| --- | --- |
| Host operating system | Windows 11 Home, 64-bit; version/build pending |
| Memory | 32 GB |
| Processor | AMD Ryzen 9 7900X; 12 cores reported |
| Physical storage | Two SSDs and one HDD |
| Hardware virtualization | Enabled, as observed in Task Manager |

Oracle VirtualBox is installed, as confirmed by the lab owner. Read-only inspection of the installed executable reports version 7.2.22.175245. A successful VM startup has not yet been verified. The intended lab SSD and its available space remain unspecified.

## Lab design

Oracle VirtualBox is the hypervisor. The following DC01 settings were verified in the lab owner's screenshots:

| Setting | Observed value |
| --- | --- |
| VM name and state | DC01, Powered Off |
| Memory | 6144 MB |
| Virtual processors | 2 |
| Firmware | EFI enabled |
| Virtual disk | DC01.vdi, 80 GB; full preallocation unchecked in the creation wizard |
| Optical drive | Windows Server 2025 evaluation x64 ISO attached |
| VirtualBox OS profile | Windows Server 2022 (64-bit); this profile does not identify an installed OS |
| Network adapter 1 | Intel PRO/1000 MT Desktop, Internal Network named LabNet |

The ISO was downloaded and used from its existing location outside the Git checkout. The VM files are also outside the checkout. The latest screenshot shows only adapter 1 in the network summary, attached to Internal Network named LabNet. Guest IP addressing, connectivity, and Windows Server installation remain unverified.

## Verified setup steps

- Oracle VirtualBox installation: lab owner reported installation complete; executable version inspected separately.
- Windows Server evaluation ISO download: confirmed by the lab owner and attached image visible in the DC01 storage summary.
- DC01 creation: screenshots show the registered, powered-off VM with the resources listed above. No Windows installation or boot success is claimed.
- DC01 network attachment: screenshot verifies adapter 1 uses Internal Network LabNet. No guest IP configuration or connectivity is claimed.

Completed configurations and their verification results will be documented here. Passwords and product keys are excluded.
