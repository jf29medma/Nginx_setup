# Nginx_setup

This docker-compose.yml sets up an nginx-proxy with automatic SSL certificate renewal via Let's Encrypt.

## What it does

- **Automatic reverse proxy**: Any Docker service connected to the `proxy-net` network will be automatically reverse proxied
- **Automatic certificate renewal**: SSL certificates are automatically obtained and renewed via Let's Encrypt

## Usage

To enable automatic reverse proxying for a service, add it to the `proxy-net` network and include these environment variables:

```yaml
environment:
  - VIRTUAL_HOST=${EXPRESS_HOSTNAME}
  - LETSENCRYPT_HOST=${EXPRESS_HOSTNAME}
  - VIRTUAL_PORT=${EXPRESS_INTERNAL_PORT}
```

## Notes

- `ENABLE_IPV6: "true"` is not necessary if you only use IPv4