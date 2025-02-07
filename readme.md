# Nginx Reverse Proxy

This repository contains the configuration for Nginx acting as a Reverse Proxy. It is assumed that when deployed, this web server will be the only application receiving requests from the external network.

## Deployment

Before starting, you need to configure the domain zone that Nginx will serve. The `./configuration/routes.conf` file maps domains to the names of target containers. Technically, this file is an inclusion for the main Nginx configuration.

### Let's Encrypt Certificates

During the container build, domain validation is performed using the DNS-01 Challenge, which makes it possible to obtain a wildcard certificate for all possible subdomains. To pass the validation automatically, a special hook is required.

The Certbot utility provides several hooks for popular DNS providers. You can write custom hooks for your DNS provider if it provides an API for managing your domain zone. This repository uses custom hooks in `./hooks/` directory for Selectel infrastucture.

## Author

Configured by Egor Chumichev.
