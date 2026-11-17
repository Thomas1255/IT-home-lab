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
