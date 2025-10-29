https://chatgpt.com/c/6900a146-fc50-8332-9e41-f8827758e13d
https://chatgpt.com/s/t_6900b847eba08191b2271acb8ac7b97e

# Important Todo

1. Host-based Certbot + Mount into Docker (simpler for single container)

- Install **Certbot** on your host server.

```bash
sudo apt update
sudo apt install -y certbot python3-certbot-nginx
certbot --version
```

- Request certificates for your domains:

```bash
sudo certbot certonly --nginx -d example.com -d www.example.com
sudo certbot certonly --nginx -d api.example.com
```

- Certificates live in `/etc/letsencrypt/live/`.
- Mount them into your Nginx container:

```yaml
volumes:
  - /etc/letsencrypt:/etc/letsencrypt:ro
```

- Create a **cron job** or systemd timer to renew:

```bash
sudo crontab -e
# Add:
0 3 * * * certbot renew --post-hook "docker exec nginx-proxy nginx -s reload"
```

# To install Docker Compose on Ubuntu

Docker Compose V1 (sudo docker-compose)

```bash
sudo apt install docker-compose -y
```

Docker Compose V2 (sudo docker compose)

```bash
sudo apt install docker-compose-plugin -y
```
