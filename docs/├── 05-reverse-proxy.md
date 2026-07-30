# 05 - Reverse Proxy (Nginx Proxy Manager)

## Objective

Deploy Nginx Proxy Manager using Docker Compose to centralize access to self-hosted services through a reverse proxy.

---

## Environment

| Component | Version |
|----------|---------|
| Operating System | Ubuntu Server 26.04 LTS |
| Docker | Installed |
| Docker Compose | Installed |
| Nginx Proxy Manager | Latest |

---

## Why Nginx Proxy Manager?

As additional services are deployed, accessing each application through a different port becomes increasingly difficult to manage.

A reverse proxy provides a single entry point and forwards incoming requests to the appropriate service.

For this project, Nginx Proxy Manager is used to simplify access to self-hosted services and prepare the environment for HTTPS and custom domain names.

---

## Diagram

The following diagram illustrates how Nginx Proxy Manager routes incoming requests to the self-hosted services deployed throughout this lab.

<img width="300" height="140" alt="Nginx Proxy Manager drawio" src="https://github.com/user-attachments/assets/a5e79237-8768-4204-9a31-57a6512d603c" />


---

## Service Configuration

| Setting | Value |
|----------|-------|
| Image | jc21/nginx-proxy-manager |
| HTTP | 80 |
| HTTPS | 443 |
| Admin Interface | 81 |
| Restart Policy | unless-stopped |

---

## Docker Compose Configuration

Create the project directory.

```bash
mkdir -p ~/docker-services/nginx-proxy-manager
cd ~/docker-services/nginx-proxy-manager
```

Create `docker-compose.yml`

```yaml
services:
  npm:
    image: jc21/nginx-proxy-manager:latest
    container_name: nginx-proxy-manager
    restart: unless-stopped

    ports:
      - "80:80"
      - "81:81"
      - "443:443"

    volumes:
      - ./data:/data
      - ./letsencrypt:/etc/letsencrypt
```

Deploy.

```bash
docker compose up -d
```

---

## Verification

Verify the container.

```bash
docker compose ps
```

Open the administration interface.

```
http://SERVER_IP:81
```

Example

```
http://192.168.0.150:81
```

Log in using the default administrator account.

Create the first Proxy Host.

Verify that Homepage is accessible through the reverse proxy.

---

## Operational Use

Nginx Proxy Manager acts as the entry point for all services running in the Docker Services Lab.

Current proxy hosts include:

- Homepage

---

## Screenshots

### Deployment

<img width="691" height="60" alt="image" src="https://github.com/user-attachments/assets/181cd89b-d67e-45e6-8255-6b462b97b32d" />


---

### Running Container

<img width="1085" height="77" alt="image" src="https://github.com/user-attachments/assets/0da250e6-7add-4c56-b11d-a501bacd26f1" />

---

### Dashboard

<img width="2559" height="1079" alt="image" src="https://github.com/user-attachments/assets/e638ebe0-0647-4f65-9946-11f40bdbf836" />


---

### Proxy Hosts

<img width="2559" height="1079" alt="image" src="https://github.com/user-attachments/assets/1d359507-d862-43d6-93b5-42fdb0a51e4c" />


---

## Implementation Notes

Each application remains on its original Docker port while Nginx Proxy Manager forwards incoming requests based on hostname.

This approach avoids exposing multiple ports directly to users and simplifies future HTTPS configuration.

---

## What I Learned

- Deploy a reverse proxy using Docker Compose.
- Configure host-based routing.
- Forward traffic to internal services.
- Centralize access to self-hosted applications.

---

## Future Improvements

- Configure Let's Encrypt certificates.
- Enable automatic HTTPS redirection.
- Restrict administrative access.
- Publish selected services externally.

---

## References

- https://nginxproxymanager.com/
- https://github.com/NginxProxyManager/nginx-proxy-manager

---

## Verification Checklist

- [x] Container deployed
- [x] Dashboard accessible
- [x] Proxy Host created
- [x] Homepage reachable through reverse proxy
