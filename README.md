# legacy-cert

## Let's Encrypt / Certbot

Certbot config method: **HTTP-01 Challenge**

Requires Port 80: Your server must be accessible over HTTP (port 80) to complete the challenge.

For most web servers, the HTTP-01 challenge is the most straightforward and popular approach because it is simple to set up and doesn't require access to your DNS provider. However, if you need a wildcard certificate or can't use port 80, the **DNS-01 challenge** is the preferred approach.

## Steps

- stop the nginx server on port 80
- docker-compose build
- docker-compose up -d
- certbot --nginx (First try: certbot --nginx --dry-run )
