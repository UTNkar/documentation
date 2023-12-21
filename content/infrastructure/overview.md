---
title: "Overview"
weight: 2
---

In summary, when a user attempts to access a UTN domain, the request first goes to Loopia, which redirects configured domains to Cloudflare. Cloudflare then manages traffic, security, and DNS records, directing website requests to the appropriate servers at Digital Ocean and routing email traffic to Google Workspace via MX records. This infrastructure ensures that UTN's digital services are secure, reliable, and efficiently managed.

### Domain Registry and Initial Request Handling

- **Loopia**: UTN's domain names, such as utn.se, are registered with Loopia, a domain name registrar. When a user makes a request to a UTN domain, the request is first directed to Loopia's DNS servers.

### Cloudflare and Traffic Management

- **Cloudflare**: After the initial request reaches Loopia, if the domain is configured to use Cloudflare, the request is then passed on to Cloudflare's network. Only domains configured to point to Cloudflare will be redirected there. This configuration is achieved by updating the domain's nameservers at Loopia to those provided by Cloudflare.
- **Redirection and Security**: Cloudflare acts as a reverse proxy, providing benefits such as DDoS protection, traffic acceleration, and SSL/TLS encryption. All incoming traffic to UTN's domains filters through Cloudflare before reaching the actual servers.
- **DNS Records**: Cloudflare manages the DNS records for domains under its control. A DNS record tells the internet where to send traffic for a particular domain or subdomain. For example, a request to utn.se would be directed to Cloudflare, which in turn would consult its DNS records to determine where to route the request next.

### Email Handling with Google Workspace and MX Records

- **Google Workspace Email**: All emails sent to UTN's domains are managed via Google Workspace (formerly G Suite). This service provides email hosting and additional productivity tools.
- **MX Records**: Mail Exchange (MX) records in Cloudflare's DNS settings dictate where email traffic should be directed. These records point to Google's mail servers, ensuring that emails sent to UTN addresses are received and managed by Google Workspace.

### Website Redirection to Digital Ocean Servers

- **Digital Ocean**: UTN's websites are hosted on several servers provided by Digital Ocean, such as Moore, Babbage, and Turing. Each server hosts different applications and services.
- **DNS Redirection**: When Cloudflare receives a request for a UTN website, it redirects the request to the appropriate Digital Ocean server based on A (Address) or CNAME (Canonical Name) DNS records. An A record maps a domain to the server's IP address, while a CNAME record maps a domain to another domain name (often used for subdomains).
- **Server Response**: Once the request reaches the correct Digital Ocean server, the server processes the request and serves the requested website or web application to the user.
