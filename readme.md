# Reverse Proxy Server

This repository contains the configuration for Nginx acting as a Reverse Proxy. It is assumed that when deployed, this web server will be the only application receiving requests from the external network.

## Deployment

Application supposed to be run in Docker Container.

Firstly, create `server-certifcates` volume to store SSL certificates:

```bash
sudo docker volume create server-certificates
```

Then obtain Let's Encrypt certificates:

```bash
sudo docker run --rm -v server-certificates:/etc/letsencrypt certonly --standalone --non-interactive \
  --agree-tos --preferred-challenges http \
  -d egorchumichev.dev -d platform.egorchumichev.dev -d registry.egorchumichev.dev \
  --email common@egorchumichev.dev
```

## Author

Configured by Egor Chumichev.
