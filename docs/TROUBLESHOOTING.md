# Troubleshooting Knowledge Base

## VirtualBox VM creation blocked by a non-unique path

- **Symptoms:** The New Virtual Machine wizard initially did not complete when Finish was clicked. A later screenshot showed a red VM Name field and disabled Finish button.
- **Diagnostic evidence:** The lab owner read the tooltip: "virtual machine path is not unique". Read-only inspection confirmed an existing, empty DC01 folder. Hardware and disk settings appeared valid in screenshots.
- **Confirmed blocker:** The intended VM path conflicted with an existing item. The cause of the earlier silent behavior was not separately established.
- **Resolution reported by the lab owner:** Removed the conflicting item and created the VM using the original DC01 name and settings, with the ISO attached. The exact deleted item was not independently verified.
- **Verification at resolution:** A screenshot showed DC01 registered as Powered Off, with 6144 MB RAM, 2 CPUs, EFI enabled, an 80 GB VDI, and ISO attached. Later installation and sign-in were verified separately in SETUP.md.
- **Practice:** Check existing folder contents and VM registration before removing an item to resolve a path conflict.

## DC01 duplicate IPv4 state and failed ping

- **Symptoms:** WIN11-01 could not reach DC01 at 10.10.10.10. DC01's ping to the client failed with General failure.
- **Evidence:** DC01 ipconfig /all showed 10.10.10.10 (Duplicate) plus a 169.254 fallback address. WIN11-01 showed its correct 10.10.10.20/24 address, no gateway, DHCP disabled, and DNS 10.10.10.10. The learner reported configuring the inbound ping rules on both machines; exact rule contents were not independently inspected.
- **Investigation:** Current VirtualBox configuration inspection confirmed both active adapters use Internal Network LabNet and have distinct MAC addresses. Historical snapshot settings were excluded. Global configuration showed host-only DHCP on a separate subnet, with no LabNet DHCP entry. None of this identifies the conflict source.
- **Suggested diagnostic:** Disable and re-enable DC01's Ethernet adapter, then rerun ipconfig /all and both ping directions. If Duplicate persisted, inspect System event 4199 for the conflicting hardware address. The learner's exact recovery action was not explicitly confirmed.
- **Observed recovery:** A subsequent screenshot shows DC01's 10.10.10.10 as Preferred and ping to WIN11-01 at 10.10.10.20 succeeding: 4 sent, 4 received, 0% loss.
- **Remaining verification:** Latest client screenshot pings its own 10.10.10.20 successfully and retains the earlier failed server ping. Obtain a fresh client ping to 10.10.10.10 before marking full connectivity complete.
- **Root cause:** Unconfirmed. Windows reported a conflict; do not assume a second device, firewall problem, or ISO issue without evidence.
- **Evidence:** [Screenshots and verification limits](EVIDENCE.md#troubleshooting-duplicate-address-and-failed-reachability).
