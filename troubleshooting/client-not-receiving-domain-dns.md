# Client Not Receiving Domain DNS (UTM / Windows Lab)

## Problem
After moving the lab to a new subnet in UTM, the Windows 11 client (WS01) could not
discover the domain. `ipconfig /all` showed:

- IP from 192.168.64.0/24
- DHCP Server: UTM (192.168.64.1)
- DNS Server: 192.168.100.10 (old DC address)

Because DNS did not point to the Domain Controller, the client could not resolve
`corp.local` or find a DC.

## Root Cause
- The Domain Controller (DC01) was moved from `192.168.100.10` to `192.168.64.10`
  to match UTM’s Shared Network.
- The DHCP scope options were updated, but the client still had:
  - Cached DNS entries
  - A manual IPv4 configuration from earlier testing

UTM also runs its own DHCP service, which can answer before the Windows DHCP role.
What matters for Active Directory is that **DNS points to the DC**.

## Fix

### On DC01
1. Verified static IP:
   - IP: `192.168.64.10`
   - DNS: `192.168.64.10`
2. Updated DHCP Scope Options:
   - `006 DNS Servers` → `192.168.64.10`
   - `015 DNS Domain Name` → `corp.local`

### On WS01
1. Set IPv4 to:
   - Obtain IP automatically
   - Obtain DNS automatically
2. Ran:
   ```bat
   ipconfig /flushdns
   ipconfig /release
   ipconfig /renew

