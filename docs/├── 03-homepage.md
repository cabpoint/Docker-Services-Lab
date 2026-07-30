# 03 - Homepage Dashboard

## Objective

Deploy Homepage using Docker Compose to provide a centralized dashboard for accessing services running in the Docker Services Lab.

---

## Environment

| Component | Version |
|----------|---------|
| Operating System | Ubuntu Server 26.04 LTS |
| Docker | Installed |
| Docker Compose | Installed |
| Homepage | Latest |

---

## Why Homepage?

As additional services are deployed, remembering multiple ports and URLs becomes increasingly difficult.

Homepage provides a single dashboard where all self-hosted services can be organized and accessed from one location.

For this project, Homepage serves as the central entry point for the Docker Services Lab.

---

## Service Configuration

| Setting | Value |
|----------|-------|
| Image | ghcr.io/gethomepage/homepage |
| Port | 3000 |
| Restart Policy | unless-stopped |
| Volume | homepage-config |

---

## Docker Compose Configuration

Create a project directory.

```bash
mkdir -p ~/docker-services/homepage
cd ~/docker-services/homepage
```

Create the `docker-compose.yml` file.

```yaml
services:
  homepage:
    image: ghcr.io/gethomepage/homepage:latest
    container_name: homepage
    restart: unless-stopped

    ports:
      - "3000:3000"

    volumes:
      - ./config:/app/config
      - /var/run/docker.sock:/var/run/docker.sock:ro
```

Deploy the service.

```bash
docker compose up -d
```

---

## Verification

Verify the container is running.

```bash
docker compose ps
```

Open the dashboard.

```
http://SERVER_IP:3000
```

Example

```
http://192.168.0.150:3000
```

Confirm the Homepage dashboard loads successfully.

---

## Operational Use

Homepage acts as the central dashboard for this lab.

Currently it provides quick access to:

- Ubuntu Home Server
- Portainer
- Uptime Kuma

Additional services will be added as the environment grows.

---

## Screenshots

### Deployment


<img width="590" height="62" alt="image" src="https://github.com/user-attachments/assets/11bdf22b-1a8f-4d7d-ae6f-a09af3bd8964" />


---

### Running Container

<img width="1089" height="101" alt="image" src="https://github.com/user-attachments/assets/d83e7304-ddc9-40d1-982c-61d6e2a73a2d" />


---

### Homepage Dashboard

<img width="2559" height="1079" alt="image" src="https://github.com/user-attachments/assets/a6de2a0d-92ec-4225-8205-8dc88fb6a8b3" />


---

## Implementation Notes

Homepage stores its configuration inside the mounted configuration directory, allowing dashboards to persist across container restarts.

The Docker socket is mounted as read-only, enabling Homepage widgets to retrieve Docker information without allowing modifications to the Docker Engine.

---

## What I Learned

- Deploy applications using Docker Compose.
- Mount persistent configuration directories.
- Use bind mounts and read-only Docker socket access.
- Build a centralized dashboard for self-hosted services.

---

## Future Improvements

- Add File Browser
- Add Nginx Proxy Manager
- Organize services into categories
- Add custom icons
- Configure widgets for Docker containers

---

## References

- https://gethomepage.dev/
- https://github.com/gethomepage/homepage

---

## Verification Checklist

- [x] Docker Compose file created
- [x] Homepage deployed
- [x] Dashboard accessible
- [x] Services added
- [x] Configuration persisted
