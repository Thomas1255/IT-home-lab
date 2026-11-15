# Troubleshooting Knowledge Base

## VirtualBox VM creation blocked by a non-unique path

- **Symptoms:** The New Virtual Machine wizard initially did not complete when Finish was clicked. A later screenshot showed a red VM Name field and disabled Finish button.
- **Diagnostic evidence:** The lab owner read the tooltip: "virtual machine path is not unique". Read-only inspection confirmed an existing, empty DC01 folder. Hardware and disk settings appeared valid in screenshots.
- **Confirmed blocker:** The intended VM path conflicted with an existing item. The cause of the earlier silent behavior was not separately established.
- **Resolution reported by the lab owner:** Removed the conflicting item and created the VM using the original DC01 name and settings, with the ISO attached. The exact deleted item was not independently verified.
- **Verification:** A subsequent screenshot showed DC01 registered in VirtualBox Manager as Powered Off, with 6144 MB RAM, 2 CPUs, EFI enabled, an 80 GB VDI, and the evaluation ISO attached. VM boot and Windows installation remain untested.
- **Practice:** Check existing folder contents and VM registration before removing an item to resolve a path conflict.
