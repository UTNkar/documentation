# Domain Name System

UTN governs the following domain names:
- forsranningen.com
- forsranningen.se
- forsränningen.se
- karsamverkan.se
- kårsamverkan.se
- naturvetarbalen.se
- polhacks.se
- recce.se
- tdmottagningen.se
- utn.se
- utnarm.com
- utnarm.se

These domain names are registered at [Loopia](https://customerzone.loopia.com/), but the name servers for `utn.se` are those of [CloudFlare](https://www.cloudflare.com/). (The others are still at Loopia.)

## CloudFlare

CloudFlare is a free service that helps both optimize the access to web server
by caching pages, but also protect the website against threats. It does this by
giving interrupting a client from accessing the actual server if it might be a
threat, it will challenge the user if in doubt of a malicious bot, and then
serve the page from cache if possible.

CloudFlare keeps excessive data on requests, so it's interesting to take a look
once in a while.
