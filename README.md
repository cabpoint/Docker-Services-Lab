# Docker Services Lab

A highly documented Docker Compose lab built on Ubuntu Server.

This project demonstrates how to deploy, manage and expose self-hosted services using Docker Compose and Nginx Proxy Manager while documenting every step of the process.

---

## Objective

The objective of this project is to learn how Docker Compose simplifies multi-container deployments and how self-hosted services can be managed through a centralized environment.

Topics covered include:

- Docker Compose
- Portainer
- Homepage
- Uptime Kuma
- File Browser
- Nginx Proxy Manager
- Reverse Proxy configuration
- Local DNS using the hosts file

---

## Environment

| Component | Value |
|-----------|-------|
| Operating System | Ubuntu Server 26.04 LTS |
| Docker | 29.6.2 |
| Docker Compose | v5.3.1 |
| Host IP | 192.168.0.150 |
| Documentation | Markdown |

---

## Project Structure

```
docker-services/
├── 00-installation.md
├── 01-portainer.md
├── 02-uptime-kuma.md
├── 03-homepage.md
├── 04-filebrowser.md
├── 05-reverse-proxy.md
└── images/
```

---

## Services

| Service | Purpose |
|----------|---------|
| Docker Compose | Multi-container orchestration |
| Portainer | Container management |
| Homepage | Central dashboard |
| Uptime Kuma | Service monitoring |
| File Browser | Web-based file management |
| Nginx Proxy Manager | Reverse proxy & custom domains |

---

## Documentation

| Guide |
|-------|
| [00 - Installation]([00-installation.md](https://github.com/cabpoint/Docker-Services-Lab/blob/main/docs/%E2%94%9C%E2%94%80%E2%94%80%2000-installation.md)) |
| [01 - Portainer]([01-portainer.md](https://github.com/cabpoint/Docker-Services-Lab/blob/main/docs/%E2%94%9C%E2%94%80%E2%94%80%2001-portainer.md)) |
| [02 - Uptime Kuma]([02-uptime-kuma.md](https://github.com/cabpoint/Docker-Services-Lab/blob/main/docs/%E2%94%9C%E2%94%80%E2%94%80%2002-uptime-kuma.md)) |
| [03 - Homepage]([03-homepage.md](https://github.com/cabpoint/Docker-Services-Lab/blob/main/docs/%E2%94%9C%E2%94%80%E2%94%80%2003-homepage.md)) |
| [04 - File Browser]([04-filebrowser.md](https://github.com/cabpoint/Docker-Services-Lab/blob/main/docs/%E2%94%9C%E2%94%80%E2%94%80%2004-filebrowser.md)) |
| [05 - Reverse Proxy]([05-reverse-proxy.md](https://github.com/cabpoint/Docker-Services-Lab/blob/main/docs/%E2%94%9C%E2%94%80%E2%94%80%2005-reverse-proxy.md)) |

---

## Final Architecture

> *(Insert your architecture diagram here.)*

---

## Result

The final environment provides access to all services through custom local domains.

| Service | URL |
|----------|-----|
| Homepage | http://ubuntu.home.lab |
| Portainer | https://portainer.ubuntu.home.lab |
| Uptime Kuma | http://status.ubuntu.home.lab |
| File Browser | http://files.ubuntu.home.lab |

---

## Skills Demonstrated

- Linux Administration
- Docker
- Docker Compose
- Container Networking
- Reverse Proxies
- Service Monitoring
- Self-hosting
- Web-based Infrastructure Management
- Markdown Documentation

---

## References

- https://docs.docker.com/
- https://docs.docker.com/compose/
- https://docs.portainer.io/
- https://gethomepage.dev/
- https://github.com/louislam/uptime-kuma
- https://filebrowser.org/
- https://nginxproxymanager.com/

---
