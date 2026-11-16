# Setup Record

Status: DC01 and WIN11-01 are installed and graphical sign-in is verified in screenshots. DC01 activation is verified Active; server update completion is reported by the lab owner. Client Windows updates are deferred at the lab owner's request. Client activation, restored lab isolation, Active Directory, and inter-VM connectivity remain pending.

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

Oracle VirtualBox is the hypervisor. The following DC01 lab settings were verified in the lab owner's screenshots; network settings are to be restored after temporary internet maintenance:

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
| Guest IPv4 / subnet mask | 10.10.10.10 / 255.255.255.0 |
| DHCP enabled | No |
| Default gateway | None |
| Preferred DNS | 10.10.10.10; local DNS service not yet installed |

The ISO was downloaded and used from its existing location outside the Git checkout. The VM files are also outside the checkout. A pre-installation screenshot shows only adapter 1 in the network summary, attached to Internal Network named LabNet. A later guest ipconfig /all screenshot verifies the static IPv4 address, mask, DNS, DHCP disabled, and no gateway. Inter-VM connectivity and DNS service operation remain unverified.

## Recovery checkpoint

The lab owner's screenshot verifies a VirtualBox snapshot named `01-Clean-Server-Install`, with Current State beneath it, after Windows installation and edition verification. Snapshot restoration has not been tested.

## Windows 11 workstation

The learner downloaded the client ISO. A VirtualBox Manager screenshot verifies the new VM's configuration:

| Setting | Observed value |
| --- | --- |
| VirtualBox VM name | WIN11-01; installed Windows computer name not yet established |
| OS profile | Windows 11 (64-bit) |
| Installed operating system | Windows 11 Enterprise Evaluation, identified by desktop watermark |
| Installed version / build | 26H2 / 26300.9457, verified in About Windows |
| First sign-in | Graphical desktop visible in WIN11-01 VM window; exact account name not separately inspected |
| Memory / virtual processors | 8192 MB / 2 |
| Disk | WIN11-01.vdi, 80 GB |
| Firmware / security | EFI enabled, TPM 2.0, Secure Boot enabled |
| Optical drive | Client Enterprise Evaluation x64 English ISO, filename includes CLIENTENTERPRISEEVAL_OEMRET_x64FRE_en-us |
| Network adapter 1 | Intel PRO/1000 MT Desktop, NAT for initial setup/activation/updates |

The WIN11-01 screenshots verify successful graphical sign-in and About Windows identifies Windows 11 Enterprise Evaluation, version 26H2, OS build 26300.9457. About Windows displays labadmin as the registered user; the actual signed-in account and Windows guest computer name have not been separately inspected. Client activation and LabNet connectivity remain unverified. Client updates are deferred at the lab owner's request; no patch-completion claim is made. The client will be moved to the isolated lab network after initial activation/setup.

## Verified setup steps

- Oracle VirtualBox installation: lab owner reported installation complete; executable version inspected separately.
- Windows Server evaluation ISO download: confirmed by the lab owner and attached image visible in the DC01 storage summary.
- DC01 creation: screenshots show the registered VM with the resources listed above.
- DC01 network attachment: screenshot verifies adapter 1 uses Internal Network LabNet. No guest IP configuration or connectivity is claimed.
- Windows installation: screenshots show the empty 80 GB virtual installation target, initial Administrator password setup, and successful sign-in to the graphical desktop with Server Manager.
- Edition verification: About Windows identifies Windows Server 2025 Standard Evaluation, version 24H2, OS build 26100.32230. The graphical desktop confirms Desktop Experience. Passwords were not collected or recorded.
- Recovery checkpoint: `01-Clean-Server-Install` exists in the VirtualBox snapshot tree, verified by screenshot. Restore testing is not claimed.
- Windows computer name: Server Manager > Local Server screenshot shows Computer name DC01 and Workgroup WORKGROUP. This verifies the hostname; it does not establish an Active Directory domain or domain controller.
- Static IPv4: guest ipconfig /all shows hostname DC01, IPv4 10.10.10.10 (Preferred), subnet mask 255.255.255.0, DHCP Enabled No, DNS Servers 10.10.10.10, and an empty Default Gateway. IPv6 remains enabled with a link-local address. This verifies local configuration, not network reachability.
- Client installation/sign-in: screenshot with title WIN11-01 [Running] shows the graphical desktop and Windows 11 Enterprise Evaluation watermark. This verifies installation of an eligible client edition; no domain join is claimed.

## Outstanding initial setup

A Settings screenshot verifies DC01's Windows Server 2025 Standard Evaluation activation state is Active. The lab owner subsequently reported that DC01 finished updating; a final Windows Update page, pending-restart status, and post-update build were not independently inspected. Temporary NAT/automatic-address maintenance was instructed, and the learner supplied a Microsoft website screenshot as a connectivity check; exact temporary server adapter settings were not captured. Verify client activation, then restore and verify Internal Network LabNet and DC01's static settings above. Client updates are deferred at the lab owner's request. Keep Windows Firewall enabled and port-forwarding rules empty.

Completed configurations and their verification results will be documented here. Passwords and product keys are excluded.
