## How to Install Let’s Encrypt on Nginx Ubuntu 20.04

[Let’s Encrypt](https://letsencrypt.org/) is a Certificate Authority (CA) that provides SSL/TLS encryption at no charges and the certificate is valid for 90 days, duing which renewal can take place at any time. In order to get a certificate for your website’s domain from Let’s Encrypt, you have to demonstrate control over the domain. We recommend that to use the [Certbot](https://certbot.eff.org/) client. It can automate certificate issuance and installation with no downtime. It’s easy to use, works on many operating systems.

#### Prerequisites

- A Ubuntu 20.04 and Nginx installed Dedicated Servers or KVM VPS with root or non-root access (for non-root, use “sudo”).
- Registered domain that you wish to get the certificate.
- A DNS A record that points your domain to the public IP address of the server.

#### 1\. Keep server up-to-date

> \# apt update -y

#### 2\. Install certbot’s nginx package

> \# apt install certbot python3-certbot-nginx -y

#### 3\. Obtaining a Certificate

Obtain a certificate using certbot command. The Nginx plugin will take care of reconfiguring Nginx and reloading the config.

> \# certbot –nginx -d yoursite.com -d www.yousite.com

By running certbot first time, you will be prompted to enter an email address and agree to the terms of service. Next, certbot will communicate with Let’s Encrypt server.  
After the successful verification, certbot will ask how you’d like to configure your HTTPS settings:

> Output  
> Please choose whether HTTPS access is required or optional.  
> ——————————————————————————-  
> 1: Easy – Allow both HTTP and HTTPS access to these sites  
> 2: Secure – Make all requests redirect to secure HTTPS access  
> ——————————————————————————-  
> Select the appropriate number \[1-2\] then \[enter\] (press ‘c’ to cancel):

Use any option as per your requirement and hit enter.

That’s it, following message telling you that the process was successfully done and certificate are stored.

> Output  
> IMPORTANT NOTES:  
> – Congratulations! Your certificate and chain have been saved at  
> /etc/letsencrypt/live/example.com/fullchain.pem. Your cert will  
> expire on (Date). To obtain a new or tweaked version of this  
> certificate in the future, simply run certbot again with the  
> “certonly” option. To non-interactively renew \*all\* of your  
> certificates, run “certbot renew”  
> – Your account credentials have been saved in your Certbot  
> configuration directory at /etc/letsencrypt. You should make a  
> secure backup of this folder now. This configuration directory will  
> also contain certificates and private keys obtained by Certbot so  
> making regular backups of this folder is ideal.  
> – If you like Certbot, please consider supporting our work by:
>
> Donating to ISRG / Let’s Encrypt: https://letsencrypt.org/donate  
> Donating to EFF: https://eff.org/donate-le

Try to reload you website using https://

#### 4\. Verify Certbot auto-renewal

Verify that the Certbot’s auto renewal service is active and running. The *certbot* package we installed takes care of this for us by adding a systemd timer that will run twice a day and automatically renew any certificate that’s within thirty days of expiration.

You can query the status of the timer with *systemctl*:

> \# systemctl status certbot.timer

Output:

> ● certbot.timer – Run certbot twice daily  
> Loaded: loaded (/lib/systemd/system/certbot.timer; enabled; vendor preset: enabled)  
> Active: active (waiting) since (Date And Time)
> Trigger: (Date And Timezone)
> Triggers: ● certbot.service
>
> (Date And Time) road systemd\[1\]: Started Run certbot twice daily.
