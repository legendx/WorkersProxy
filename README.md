# WorkersProxy

[![LICENSE](https://img.shields.io/github/license/Siujoeng-Lau/WorkersProxy.svg)](https://github.com/Siujoeng-Lau/WorkersProxy/blob/master/LICENSE)

## Introduction
WorkersProxy is a lightweight Javascript application that retrieves resource as a client from other servers.

Deploying on [Cloudflare Workers](https://www.cloudflare.com/products/cloudflare-workers/), which is an influential platform for building serverless applications, you could build customized reverse proxy without purchasing computing engines and configuring web servers such as Nginx.

Moreover, crucial performance, such as latency and availability, will be optimized, since your application will be distributed through Cloudflare's global network of data centers in more than 90 countries.

By configuring Geolocation and IP address filters, you might directly suspend your reverse proxy service in specific countries or regions according to their regulations. Taking advantage of the mobile redirector, you could distribute various webpages based on users' devices.

## Demo
[Reverse-Proxy Project](https://cdn.reverse-proxy.live) (This demo may not available in specific regions.)

## Getting Started

### Deploy on Cloudflare Workers

1. Navigate to [Cloudflare Workers](https://workers.cloudflare.com), register or sign in your Cloudflare account, and set custom subdomain for workers, and create a new Worker.

2. Customize 'index.js', paste the code into Cloudflare online editor to replace the default one.

3. Change name of your Worker, save and deploy it, and check whether its performance fulfills your demand.

### Bind to Custom Domain

1. Check whether your domain is currently under Cloudflare's protection.

2. Navigate to the dashboard of your domain, select 'Workers' page, and click on 'Add Route'.

3. Type `https://<domain-name>/*` in `Route` and select the Worker you created previously.

4. Add a CNAME DNS record for your custom domain. Concretely, enter the subdomain (or '@' for root) in the 'Name' field, enter the **second level domain** of your workers in the 'Target' field, and set 'Proxy status' to 'Proxied'.

### Customize index.js

Obviously, there's a few constants defined at the top of the main Javascript file.

To customize your own WorkersProxy Service, you should edit them according to your expectations.

```
// List of domains bind to your WorkersProxy.
const domain_list = ['https://cdn.reverse-proxy.live/', 'https://google.xasiimov.workers.dev/']

// Website you intended to retrieve for users.
const upstream = 'https://www.google.com/'

// Website you intended to retrieve for users using mobile devices.
const upstream_mobile = 'https://www.google.com/'

// Countries and regions where you wish to suspend your service.
const blocked_region = ['CN', 'KP', 'SY', 'PK', 'CU']

// IP addresses which you wish to block from using your service.
const blocked_ip_address = ['0.0.0.0', '127.0.0.1']
```
