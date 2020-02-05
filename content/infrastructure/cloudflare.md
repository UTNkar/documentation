+++
date = "2016-08-18T12:01:49+02:00"
title = "CloudFlare"
toc = true
weight = 45
+++

The domains **utn.se** and **utnarm.se** is managed at [CloudFlare](https://www.cloudflare.com/).
CloudFlare is a free service that helps both optimize the access to web server
by caching pages, but also protect the website against threats. It does this by
interrupting a client from accessing the actual server if it might be a
threat, it will challenge the user if in doubt of a malicious bot, and then
serve the page from cache if possible.

CloudFlare keeps excessive data on requests, so it's interesting to take a look
once in a while.

### Cloudflare proxy

Next to almost all DNS posts there is a cloud that can be orange or gray. This is the cloudflare proxy. If the cloud is orange the traffic to that domain goes through cloudflare and gets protected. If it is gray, cloudflare wont protect it and will just let traffic through.

### DNS Structure

The DNS records have been organized in a specific structure, making managing the
DNS easier. The structure is as follows:

- Each server (or physical device) has an **A-record** (and a **AAAA-record** if
possible). These records have an alias (e.g., the name of the server), that is
not used as a domain for a website/server.
- For each website or other sort of service a **CNAME-Record** is added for the
domain name that the service uses to the alias of the server. These records
should use the CloudFlare proxy.
- **MX-records** are added for all domains that are used to send emails..
- **TXT-records** are made for various records such as SPF and DKIM.

### SSL/TLS settings

Cloudflare provides some hadny features for dealing with SSL/TLS certificates. One of these features is that Cloudflare can create a and serve a ssl certificate for us. 

*utn.se* and *utnarm.se* has this feature and uses the option **Full(strict)**. This option means that traffic between users and cloudflare and the traffic between cloudflare and our servers will be end-to-end encrypted. One of the requirements for this is that the servers has a trusted CA which we create using [certbot](/server_software/certbot).

{{% notice warning %}}

When using a multi-level domain name (e.g. anmalan.rally.utn.se), the certificate provided by cloudflare is not valid since it only covers one level of subdomains (e.g. rally.utn.se).

{{% /notice %}}

### Page Rules

Cloudflare has a feature called page rules.
With these rules you can apply different rules to different websites.
One of these rules are to redirect a website. 
Redirects should not be deleted since they previous were the main website which were then switched.
During the time before the switch the original URL will exist on many places. 
If someone then goes to the original URL they wont get where they wanted and will become confused.
Currently the following redirects exist on **utn.se**:

- **utnarm.utn.se** goes to **utnarm.se**
- **w.utn.se** goes to **wsektionen.se**

In the free plan, only 3 page rules are included.

### SPF Record

SPF records are essential when dealing with email since they increase the validity of the emails sent from the union.
SPF records tell email services which servers are allowed to send emails on behalf of the domain.
Most SPF records for UTN look like this:
`v=spf1 a:babbage.utn.se a:pay.utn.se a:turing.utn.se include:_spf.google.com ~all`

Make sure you check the SPF entry using a tool like
[MxToolbox](http://mxtoolbox.com/spf.aspx).

### DKIM Record

Alongside SPF records, DKIM records exists as well. They are also essential in when dealing with email.
DKIM signs all emails on a domain with a key.
The same key is also put in the DNS for that domain. 
This way, email providers can validate if the email acctually was sent from that domain.
The DKIM keys are created in GSuite under `apps -> gmail -> authenticate email`.

{{% notice info %}}

When addin a DKIM to a subdomain, the name of the TXT entry must be (optional_prefix)._domainkey.subdomain

{{% /notice %}}

### DMARC Record

DMARC is also important when dealing with email.
DMARC defines a policy for what to do with untrusted email and generates a daily report with the delivered and undelivered mail.
DMARC is added to the DNS as a TXT Record and can be configured in many ways.
DMARC can be added to a subdomain but can also just be added to the primary domain (*utn.se*).

{{% notice info %}}

The current configuration for DMARC is to let suspicious mail be delivered.

{{% /notice %}}
