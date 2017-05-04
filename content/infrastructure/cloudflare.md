+++
date = "2016-08-18T12:01:49+02:00"
title = "CloudFlare"
toc = true
weight = 45
+++

The domain *utn.se* is managed at [CloudFlare](https://www.cloudflare.com/).
CloudFlare is a free service that helps both optimize the access to web server
by caching pages, but also protect the website against threats. It does this by
giving interrupting a client from accessing the actual server if it might be a
threat, it will challenge the user if in doubt of a malicious bot, and then
serve the page from cache if possible.

CloudFlare keeps excessive data on requests, so it's interesting to take a look
once in a while.

### DNS Structure

The DNS records have been organized in a specific structure, making managing the
DNS easier. The structure is as follows:

- Each server (or physical device) has an **A-record** (and a **AAAA-record** if
possible). These records have an alias (e.g., the name of the server), that is
not used as a domain for a website/server. (Do not use the CloudFlare proxy for
these.)
- For each website or other sort of service a **CNAME-Record** is added for the
domain name that the service uses to the alias of the server. These records
should use the CloudFlare proxy.
- **MX-records** are added for any sub-domain that has its own mail service.
- **TXT-records** are made for SPF Records (for any domain with a MX-record),
currently no other TXT-records are necessary.

### SPF Record

The SPF record for a domain contains the addresses of any server that can send
e-mails on behalf of people on that domain. The preferred way is to use
structures like `a:turing.utn.se`, however there is a maximum of DNS resolves.
Thus sometimes IP-addresses have to be used instead. A good example of an SPF
record is the one used for the main UTN domain:

`v=spf1 a:babbage.utn.se a:pay.utn.se a:turing.utn.se include:servers.mcsv.net
include:_spf.google.com ~all`

Make sure you check the SPF entry using a tool like
[MxToolbox](http://mxtoolbox.com/spf.aspx).
