# Setup Record

Status: DC01 and WIN11-01 are installed, graphical sign-in and Active activation states are verified in screenshots, and both Windows computer names match their VM names. Baseline snapshots exist for both VMs. Server update completion is reported by the lab owner; client updates are deferred at the lab owner's request. Both adapters are now verified on isolated LabNet, and static addresses are verified. Ping tests in both directions are verified with 0% loss; Active Directory and DNS services remain pending.

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

Oracle VirtualBox is the hypervisor. The following DC01 lab settings were verified in the lab owner's screenshots; network settings have now been restored after temporary internet maintenance:

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

The ISO was downloaded and used from its existing location outside the Git checkout. The VM files are also outside the checkout. A pre-installation screenshot shows only adapter 1 in the network summary, attached to Internal Network named LabNet. A later guest ipconfig /all screenshot verifies the static IPv4 address, mask, DNS, DHCP disabled, and no gateway. DC01-to-client ping is now verified with four replies and 0% loss; client-to-server ping is verified too; DNS service operation remains unverified.

## Recovery checkpoint

The lab owner's screenshot verifies a VirtualBox snapshot named `01-Clean-Server-Install`, with Current State beneath it, after Windows installation and edition verification. Snapshot restoration has not been tested.

A later screenshot verifies the client snapshot `01-Clean-Client-Install` with Current State beneath it. Both DC01 and WIN11-01 are shown Powered Off in that screenshot. The client baseline includes completed sign-in, verified hostname and activation, with Windows updates deferred. Neither snapshot has been restore-tested.

## Windows 11 workstation

The learner downloaded the client ISO. A VirtualBox Manager screenshot verifies the new VM's configuration:

| Setting | Observed value |
| --- | --- |
| VirtualBox VM name / Windows computer name | WIN11-01 / WIN11-01, verified in VM title and guest Settings |
| OS profile | Windows 11 (64-bit) |
| Installed operating system | Windows 11 Enterprise Evaluation, identified by desktop watermark |
| Installed version / build | 26H2 / 26300.9457, verified in About Windows |
| Signed-in account | labadmin, Local Account, verified in Settings |
| Activation | Active, verified in Settings > System > Activation |
| Memory / virtual processors | 8192 MB / 2 |
| Disk | WIN11-01.vdi, 80 GB |
| Firmware / security | EFI enabled, TPM 2.0, Secure Boot enabled |
| Optical drive | Client Enterprise Evaluation x64 English ISO, filename includes CLIENTENTERPRISEEVAL_OEMRET_x64FRE_en-us |
| Network adapter 1 | Internal Network LabNet, confirmed by current VirtualBox configuration inspection |
| Static IPv4 / mask / DNS | 10.10.10.20 / 255.255.255.0 / 10.10.10.10; DHCP No, gateway blank |

The WIN11-01 screenshots verify successful graphical sign-in and About Windows identifies Windows 11 Enterprise Evaluation, version 26H2, OS build 26300.9457. Settings verifies labadmin as a Local Account, Activation state Active, and device name WIN11-01. The client baseline snapshot exists; DC01-to-client connectivity is verified; the fresh reverse ping is verified with 0% loss. Client updates are deferred at the lab owner's request; no patch-completion claim is made. The client is now on isolated LabNet.

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
- Client identity/activation: guest Settings screenshots show labadmin Local Account, Windows 11 Enterprise Evaluation Activation state Active, and device name WIN11-01. No AD domain membership is claimed.
- Client recovery checkpoint: snapshot tree shows `01-Clean-Client-Install` with Current State beneath it, and both lab VMs Powered Off. Restoration is untested.

## Outstanding initial setup

A Settings screenshot verifies DC01's Windows Server 2025 Standard Evaluation activation state is Active. The lab owner subsequently reported that DC01 finished updating; a final Windows Update page, pending-restart status, and post-update build were not independently inspected. Temporary NAT/automatic-address maintenance was instructed, and the learner supplied a Microsoft website screenshot as a connectivity check; exact temporary server adapter settings were not captured. Client activation and both baseline snapshots are now verified. LabNet attachments and both static configurations have now been verified; client-to-server ping is now verified with 4/4 replies and 0% loss. Client updates are deferred at the lab owner's request. Keep Windows Firewall enabled and port-forwarding rules empty.

Completed configurations and their verification results will be documented here. Passwords and product keys are excluded.

## Restored lab addressing and connectivity evidence

Current VirtualBox XML inspection verifies both active adapter 1 attachments use Internal Network LabNet and distinct MAC addresses. Guest screenshots verify both static addresses and DNS settings. The server address was temporarily marked Duplicate, but a later screenshot shows Preferred and DC01 pinging WIN11-01 successfully (4/4 replies, 0% loss). Client firewall rules were configured by learner report; exact contents are not independently inspected. New screenshots verify both DC01 pinging 10.10.10.20 and WIN11-01 pinging 10.10.10.10, each with 4/4 replies and 0% loss. The earlier self-ping was not counted as remote verification. See [screenshot evidence](EVIDENCE.md) and [troubleshooting record](TROUBLESHOOTING.md).
