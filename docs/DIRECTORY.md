# Northstar directory design

Northstar is a fictional company targeting approximately 25 employees across five departments. OUs organize objects for administration and future Group Policy. Security groups will grant access separately.

Verified structure:

```text
ad.northstar.example
  Northstar
    Groups
    Users
      IT
      HR
      Finance
      Sales
      Operations
    Workstations
```

Accounts will go in department OUs, security groups in Groups, and the client in Workstations after domain join. DC01 stays in Domain Controllers. Accounts, groups, client placement, and policies remain planned.

![Verified department OU tree](images/department-ous.png)

DNS remains unresolved: automatic and manual domain-zone creation fail with Win32 error 123. Promotion logs show DNS installed but configuration failed. Local AD queries succeed and both DNS partitions report DNS_DP_OKAY. The underlying cause is unknown; client domain join is deferred.

## Employee account checkpoint

The learner supplied Get-ADUser output scoped to OU=Users,OU=Northstar,DC=ad,DC=northstar,DC=example showing 25 unique employee accounts, all Enabled=True. This verifies the count, account names, and enabled state within that subtree. The displayed output does not independently verify individual department placement, password settings, or successful sign-in.

One display name is Isabelle Ross with logon isabella.ross; this is a naming difference from the proposed Isabella Ross, not a demonstrated authentication failure. Security groups and memberships remain pending. DNS remains unresolved.

Follow-up screenshot evidence verifies five user objects in each of IT, HR, Finance, Sales, and Operations. Department placement is now verified in the [evidence gallery](EVIDENCE.md#employee-department-placement). Security-group creation and membership remain unverified.

Security-group creation checkpoint: five security groups are visible in Northstar/Groups. Scope and the truncated Operations name await command verification. Membership assignment and access grants remain pending. See the [group screenshot](images/department-security-groups.png).

Membership verification is complete: GG_IT, GG_HR, GG_Finance, GG_Sales, and GG_Operations are Global Security groups, each with the correct five department accounts. The full Operations name is confirmed. See [membership evidence](images/department-memberships.png). Resource permissions and client domain sign-in remain unverified; DNS is unresolved.
