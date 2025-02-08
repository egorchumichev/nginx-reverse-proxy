# Reverse Proxy Server

This repository contains the configuration for Nginx acting as a Reverse Proxy. It is assumed that when deployed, this web server will be the only application receiving requests from the external network.

## Deployment

The application is intended to run in a Docker container.

### Create Docker Volume

Create a `server-certificates` volume to store SSL certificates:

```bash
sudo docker volume create server-certificates
```

### Obtain SSL Certificates

Obtain Let's Encrypt certificates using the following command:

```bash
sudo docker run --rm -v server-certificates:/etc/letsencrypt certonly --standalone --non-interactive \
  --agree-tos --preferred-challenges http \
  -d egorchumichev.dev -d platform.egorchumichev.dev -d registry.egorchumichev.dev \
  --email common@egorchumichev.dev
```

### Configure Proxying for Docker Containers

The Nginx configuration file is located at `./configuration/nginx.conf`. Modify this file to suit your domain requirements and ensure that it correctly proxies requests to your target Docker containers.

### Start the Server

Start the server using Docker Compose with the following command:

```bash
sudo docker compose -f ./docker/compose.yaml up -d
```

## Author

Configured by Egor Chumichev. Feel free to modify this template.
