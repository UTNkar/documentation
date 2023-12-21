---
title: "CloudFlare"
toc: true
weight: 45
---

Cloudflare is a service that optimizes and secures web servers by caching pages and protecting websites from threats. It intercepts potentially harmful client requests, challenges dubious bots, and serves cached pages when possible.

Cloudflare provides extensive data on requests, making it worthwhile to review periodically. It also conceals server IP addresses, adding an extra layer of attack protection.

{{% notice warning %}}
Do not publicly disclose server IP addresses. Share them only with trusted individuals.
{{% /notice %}}

### Cloudflare Proxy

Next to most DNS records in Cloudflare, there is a cloud icon that can be orange or gray. This represents the Cloudflare proxy. An orange cloud indicates that traffic is routed through Cloudflare and is protected; a gray cloud means Cloudflare will not protect the traffic.

Set all records to be proxied through Cloudflare (orange) for protection.

{{% notice info %}}
Multi-level domains should not be proxied due to SSL certificate limitations.
{{% /notice %}}

{{% notice warning %}}
When a record is proxied through Cloudflare, SSH cannot be used on that domain (e.g., `ssh moore.utn.se`). Instead, SSH directly to the IP (`ssh XXX.XXX.XXX.XXX`).
{{% /notice %}}

### DNS Structure

The DNS records are structured to facilitate easier management:

- **A records** (and **AAAA records** when possible) are created for each server or device. These records have an alias not used as a domain for a website or server.
- **CNAME records** point the domain name used by a service to the alias of the server and should be proxied through Cloudflare.
- **MX records** are added for domains used for sending emails.
- **TXT records** are created for various purposes, including SPF and DKIM.

### SSL/TLS Settings

Cloudflare offers SSL/TLS certificate management features. Use the [**Full (strict)**](https://developers.cloudflare.com/ssl/origin-configuration/ssl-modes/full-strict/) setting for all domains which ensures end-to-end encryption for traffic. Servers require a trusted certificate, which can be an [origin certificate](https://support.cloudflare.com/hc/en-us/articles/115000479507-Managing-Cloudflare-Origin-CA-certificates) provided by Cloudflare.

{{% notice info %}}
The current origin certificates expire on June 18, 2035.
{{% /notice %}}
{{% notice info %}}
Multi-level domain names (e.g., *anmalan.rally.utn.se*) are not covered by Cloudflare's certificate. Use a one-level domain (e.g., *anmalan-rally.utn.se*) to avoid errors.
{{% /notice %}}
{{% notice warning %}}
Keep the certificate and private key in `/etc/ssl/certs` and `/etc/ssl/private` secret.
{{% /notice %}}

### Page Rules

Cloudflare's page rules can apply specific rules to different websites, such as redirects. Do not delete redirects as they may have been primary websites before being switched.

### SPF Record

SPF records specify which servers are authorized to send email on behalf of a domain. A typical SPF record for UTN is `v=spf1 a:babbage.utn.se a:pay.utn.se a:turing.utn.se include:_spf.google.com ~all`. Verify SPF records using tools like [MxToolbox](http://mxtoolbox.com/spf.aspx).

### DKIM Record

DKIM records are used in email verification by signing emails with a key that matches one in the DNS. DKIM keys are configured in GSuite.

{{% notice info %}}

When adding a DKIM record for a subdomain, the TXT entry name should be (optional_prefix)._domainkey.subdomain.

{{% /notice %}}

### DMARC Record

DMARC policies manage the handling of untrusted emails and provide reports on email delivery. DMARC is added as a TXT Record in the DNS.

{{% notice info %}}

The current DMARC policy allows the delivery of suspicious mail.

{{% /notice %}}
