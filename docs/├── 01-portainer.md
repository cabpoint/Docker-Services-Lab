# 01 - Portainer

## Objective

Deploy Portainer Community Edition to simplify Docker container management through a web-based interface.

---

## Environment

| Component | Version |
|----------|---------|
| Operating System | Ubuntu Server 26.04 LTS |
| Docker | Installed |
| Docker Compose | Installed |
| Portainer | Community Edition (LTS) |

---

## Why Portainer?

Managing Docker containers exclusively from the command line is effective, but becomes increasingly difficult as the number of containers grows.

Portainer provides a web interface for managing containers, images, volumes, networks and stacks from a single dashboard.

For this lab, Portainer is used to simplify container administration while continuing to learn the underlying Docker commands.

---

## Deployment

Create a persistent Docker volume.

```bash
docker volume create portainer_data
```

Deploy the Portainer container.

```bash
docker run -d \
  --name portainer \
  --restart unless-stopped \
  -p 8000:8000 \
  -p 9443:9443 \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v portainer_data:/data \
  portainer/portainer-ce:lts
```

---

## Verification

Verify that the container is running.

```bash
docker ps
```

Open the web interface.

```
https://SERVER_IP:9443
```

Create the administrator account.

Connect to the Local Docker environment.

---

## Screenshots

### Container running

> Paste screenshot of:

<img width="1093" height="156" alt="image" src="https://github.com/user-attachments/assets/79eb5fa1-6437-49f9-8a47-9368bf14544e" />


---

### Portainer dashboard

<img width="2559" height="1079" alt="image" src="https://github.com/user-attachments/assets/fb89b826-69bf-48b4-8813-34872fcd9f09" />


---

## Implementation Notes

Portainer stores its configuration inside a Docker volume named `portainer_data`, ensuring that settings persist across container restarts.

The Docker socket is mounted into the container to allow Portainer to communicate with the local Docker Engine.

---

## What I Learned

- Deploy a Docker container using persistent storage.
- Mount the Docker socket into a container.
- Access Docker through a web interface.
- Verify running containers using Docker CLI.

---

## References

- https://docs.portainer.io/
- https://hub.docker.com/r/portainer/portainer-ce

---

## Verification Checklist

- [x] Portainer deployed
- [x] Persistent volume created
- [x] Docker socket mounted
- [x] Web interface accessible
- [x] Local environment connected
