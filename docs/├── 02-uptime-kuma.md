# 02 - Uptime Kuma

## Objective

Deploy Uptime Kuma using Docker Compose to monitor the availability and health of services running in the home lab.

---

## Environment

| Component | Version |
|----------|---------|
| Operating System | Ubuntu Server 26.04 LTS |
| Docker | Installed |
| Docker Compose | Installed |
| Uptime Kuma | Latest |

---

## Why Uptime Kuma?

Monitoring is an important part of maintaining any server environment.

For this project, Uptime Kuma is used to continuously monitor the availability of the Nginx web server hosted on `http://192.168.0.150`, providing immediate visibility if the service becomes unavailable.

Additional monitors will be added as new services are deployed throughout this lab.

---

## Docker Compose Configuration

Create a directory for the service.

```bash
mkdir -p ~/docker-services/uptime-kuma
cd ~/docker-services/uptime-kuma
```

Create a `docker-compose.yml` file.

```yaml
services:
  uptime-kuma:
    image: louislam/uptime-kuma:latest
    container_name: uptime-kuma
    restart: unless-stopped

    ports:
      - "3001:3001"

    volumes:
      - uptime-kuma:/app/data

volumes:
  uptime-kuma:
```

Deploy the container.

```bash
docker compose up -d
```

---

## Verification

Verify that the container is running.

```bash
docker ps
```

Open the web interface.

```
http://SERVER_IP:3001
```

Example

```
http://192.168.0.150:3001
```

Create the administrator account.

Create a monitor for one of the deployed services.

---

## Screenshots

### Docker Compose deployment

<img width="620" height="58" alt="image" src="https://github.com/user-attachments/assets/40e81ab0-07f3-4758-99e2-14c3234f4571" />

---

### Running container

<img width="1057" height="178" alt="image" src="https://github.com/user-attachments/assets/f49de898-f9ea-4437-a439-a78adc665e4e" />

---

### Uptime Kuma Dashboard


<img width="1673" height="861" alt="image" src="https://github.com/user-attachments/assets/e16fc6a9-a856-40c6-bbad-6d1dfb778d51" />


---

## Implementation Notes

Persistent storage is provided through a Docker volume to retain monitor configuration and historical uptime data after container restarts.

The service listens on port **3001** by default.

---

## What I Learned

- Deploy a service using Docker Compose.
- Use persistent Docker volumes.
- Monitor service availability.
- Verify container status using Docker CLI.

---

## Future Improvements

- Monitor additional Docker services.
- Configure notifications.
- Add SSL through a reverse proxy.
- Group services into categories.

---

## References

- https://github.com/louislam/uptime-kuma
- https://hub.docker.com/r/louislam/uptime-kuma

---

## Verification Checklist

- [x] Docker Compose file created
- [x] Container deployed
- [x] Volume created
- [x] Dashboard accessible
- [x] Monitor configured
