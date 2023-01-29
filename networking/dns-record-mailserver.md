# Mail Server DNS Records Cheat-Sheet
If you want to run a mail server on the public internet, you need to set up your DNS records correctly. While some [DNS Records](dns-record-types.md) are necessary to send and receive emails, others are recommended to build a good reputation.

## Required Mail Server DNS Records
### A Record
DNS A Record that will resolve to the public IP address of your mail server. This is also needed when your web server has a different IP address than your mail server.

**Recommended Settings Example:**

Type | Host | Points to | TTL
---|---|---|---
`A`|`mail`|`your-mail-servers-ipv4`|`1 hour`

### MX Record
The MX record is important when you want to receive emails. This tells everyone which IP address to contact.

If you have multiple Mail Servers that need to be load-balanced use the same **priority**. Lower numbers are prioritized. Higher numbers can be used as backup servers.

**Recommended Settings:**

Type | Host | Points to | Priority | TTL
---|---|---|---|---
`MX`|`@`|`mail.your-domain`|`0`|`1 hour`

### RDNS or PTR Record
The reverse DNS record or also called PTR (Pointer Resource Record) is important when you want to send mails. Almost all mail servers check the RDNS record to perform simple anti-spam checks. RDNS is just like a DNS query, just backward.

>Your RDNS record is not configured on your DNS server, instead, it’s configured on your hosting provider where you got your public IP address from.

## (Optional but recommended) DNS Records

### SPF Record
The SPF (Sender Policy Framework) is a TXT record on your DNS server that specifies which hosts are allowed to send mails for a given domain. When a mail server receives a mail that seems to come from your domain it can check if it’s a valid message. Some mail servers reject mails if they can’t validate that the message comes from an authorized mail server.

**Recommended Settings:**

Type | Host | TXT Value | TTL
---|---|---|---
`TXT`|`@`|`v=spf1 ip4:your-mail-servers-ipv4 -all`|`1 hour`

### DKIM Record
DKIM (Domain Keys Identified Mail) allows the receiving mail server to check that an email was indeed sent by the owner of that domain. The sending mail server adds a digital signature to every mail that is sent. This signature is added as a header and secured with encryption. These signatures are not visible to the end-user.

>If you want to add DKIM to your mail server you first need to create a [private and public keypair](create-dkim-keypair.md)
 
**Recommended Settings:**

Type | Host | TXT Value | TTL
---|---|---|---
`TXT`|`dkim._domainkey`|`v=DKIM1;k=rsa;p=public-dkim-key`|`1 hour`

### DMARC Record
DMARC (Domain-based Message Authentication, Reporting, and Conformance) extends your existing SPF and DKIM records. It makes sure that the sender's emails are protected by SPF and DKIM and tells the receiving mail server what to do if these checks fail.
 
**Recommended Settings:**

Type | Host | TXT Value | TTL
---|---|---|---
`TXT`|`_dmarc`|`v=DMARC1;p=quarantine`|`1 hour`

## (Optional) DNS Records
### Autoconfiguration DNS Records
If you’re using mail clients like Outlook, Thunderbird on your Computer, or Mobile devices they offer the ability to do an “autoconfiguration” also called “Autodiscover”. That means you just need to enter your email address and password and the mail client tries to resolve the mail server IP addresses, used ports, and encryption settings for IMAP and SMTP. You can achieve this by adding SRV DNS records that are defined in the [RFC 6186 standard](https://tools.ietf.org/html/rfc6186) and some specific records that are used in Outlook clients.
