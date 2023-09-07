# Microsoft365 EMail Protection

Email authentication (also known as email validation) is a group of standards that tries to stop email messages from forged senders (also known as spoofing). Microsoft 365 uses the following standards to verify inbound email:

- SPF (Sender Policy Framework)
- DKIM (DomainKeys Identified Mail)
- DMARC (Domain-based Message Authentication, Reporting, and Conformance)

## Prerequisites

WIP

## Set up SPF to help prevent spoofing

WIP

## Use DKIM to validate outbound email sent from your custom domain

### Publish two CNAME records for your custom domain in DNS

For each domain for which you want to add a DKIM signature in DNS, you need to publish two CNAME records.

```txt
Name:   selector1._domainkey
Target: selector1-yourdomain-com._domainkey.yourdomaincom.onmicrosoft.com
TTL:    3600

Name:   selector2._domainkey
Target: selector2-yourdomain-com._domainkey.yourdomaincom.onmicrosoft.com
TTL:    3600
```

### To enable DKIM signing for your custom domain in the Microsoft 365 Defender portal

Once you have published the CNAME records in DNS, you are ready to enable DKIM signing through Microsoft 365. You can do this either through the Microsoft 365 admin center or by using PowerShell.

1. In the Microsoft 365 Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to Email & Collaboration > Policies & Rules > Threat policies > Email Authentication Settings in the Rules section >DKIM. To go directly to the DKIM page, use [https://security.microsoft.com/dkimv2](https://security.microsoft.com/dkimv2).
2. On the DKIM page, select the domain by clicking on the name.
3. In the details flyout that appears, change the Sign messages for this domain with DKIM signatures setting to Enabled (Toggle on.)
When you're finished, click Rotate DKIM keys.
4. Repeat these step for each custom domain.
5. If you are configuring DKIM for the first time and see the error 'No DKIM keys saved for this domain' you will have to use Windows PowerShell to enable DKIM signing as explained in the next step.

#### (Optional) To enable DKIM signing for your custom domain by using PowerShell

1. Connect to Exchange Online PowerShell.
2. Use the following syntax:
`Set-DkimSigningConfig -Identity your-domain -Enabled $true`
your-domain is the name of the custom domain that you want to enable DKIM signing for.
This example enables DKIM signing for the domain contoso.com:
`Set-DkimSigningConfig -Identity contoso.com -Enabled $true`

### To Confirm DKIM signing is configured properly for Microsoft 365

WIP

