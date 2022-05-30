# Windows DNS Server

---
## Manage DNS Server via PowerShell

**List available DNS Servers**
```powershell
Get-Module DNSServer -ListAvailable
```

**Show current DNS Records in Zone**
```powershell
Get-DnsServerResourceRecord -ZoneName <your-dns-zone>
```

### Get/Create/Modify DNS Record

**Show DNS Record** 
```powershell
Get-DnsServerResourceRecord -ZoneName <your-dns-zone> -Name <dns-name>
```

**Delete DNS Record**
```powershell
Get-DnsServerResourceRecord -ZoneName <your-dns-zone> -Name <dns-name> | Remove-DnsServerResourceRecord -ZoneName <your-dns-zone>
```

**Add DNS Record**
```
Add-DnsServerResourceRecordA -Name <dns-name> -ZoneName <your-dns-zone> -AllowUpdateAny -IPv4Address <ip-address> -TimeToLive <ttl>
```
