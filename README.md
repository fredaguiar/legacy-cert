# legacy-cert

## Let's Encrypt / Certbot

Certbot config method: **HTTP-01 Challenge**

Requires Port 80: Your server must be accessible over HTTP (port 80) to complete the challenge.

For most web servers, the HTTP-01 challenge is the most straightforward and popular approach because it is simple to set up and doesn't require access to your DNS provider. However, if you need a wildcard certificate or can't use port 80, the **DNS-01 challenge** is the preferred approach.

## Steps

- Open Portainer: https://{PORTAINER_IP}:9443/#!/2/docker/containers
- stop the nginx container nginx-legacy (to unblock port 80)
- Open putty and connect to the terminal
- go to /opt/legacy-cert
- docker compose build (if needed)
- docker compose up -d
- docker exec -it nginx-certbot /bin/sh
- certbot certonly --nginx (First try: certbot certonly --nginx --dry-run )
- Go back to Portainer
- stop the nginx-certbot container
- start the nginx-legacy container

the certificate is saved on volume legacy-cert_certbot-data

Certificate is saved at: /etc/letsencrypt/live/legacy-backend.xyz/fullchain.pem
Key is saved at: /etc/letsencrypt/live/legacy-backend.xyz/privkey.pem
This certificate expires in a few months.
