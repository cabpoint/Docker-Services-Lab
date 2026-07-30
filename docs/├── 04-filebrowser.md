# 04 - File Browser

## Objective

Deploy File Browser using Docker Compose to provide secure web-based access to files stored on the Ubuntu server.

---

## Environment

| Component | Version |
|----------|---------|
| Operating System | Ubuntu Server 26.04 LTS |
| Docker | Installed |
| Docker Compose | Installed |
| File Browser | Latest |

---

## Why File Browser?

Managing files exclusively through SSH is effective, but it can become inconvenient for routine tasks such as uploading, downloading or organizing files.

File Browser provides a lightweight web interface for managing files directly from a browser while continuing to use the server's existing file system.

For this project, it is used to simplify file management within the Docker Services Lab.

---

## Service Configuration

| Setting | Value |
|----------|-------|
| Image | filebrowser/filebrowser |
| Port | 8080 |
| Restart Policy | unless-stopped |
| Database | filebrowser.db |

---

## Docker Compose Configuration

Create a project directory.

```bash
mkdir -p ~/docker-services/filebrowser
cd ~/docker-services/filebrowser
```

Create a `docker-compose.yml` file.

```yaml
services:
  filebrowser:
    image: filebrowser/filebrowser:latest
    container_name: filebrowser
    restart: unless-stopped

    ports:
      - "8080:80"

    volumes:
      - /home/kali:/srv
      - ./database:/database
      - ./config:/config

    environment:
      PUID: 1000
      PGID: 1000
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

Open the web interface.

```
http://SERVER_IP:8080
```

Example

```
http://192.168.0.150:8080
```

Log in using the default credentials.

Change the administrator password after the first login.

---

## Operational Use

File Browser provides browser-based access to files stored on the Ubuntu server.

For this lab it is used to:

- Browse project directories
- Upload files
- Download files
- Organize documentation
- Verify Docker project files

---

## Screenshots

### Deployment

<img width="619" height="59" alt="image" src="https://github.com/user-attachments/assets/4870b036-6d33-4b6c-b4b2-f80632bb3c1f" />


---

### Running Container


<img width="1084" height="97" alt="image" src="https://github.com/user-attachments/assets/3adb6e33-0dad-407d-bcd5-cc962c717c38" />



---

### File Browser Dashboard

<img width="2559" height="1079" alt="image" src="https://github.com/user-attachments/assets/bd1b2cab-8135-4f51-a07b-d03c3cada4c8" />


---

## Implementation Notes

The host home directory is mounted into the container, allowing File Browser to manage existing server files without duplicating data.

Configuration and database files are stored outside the container to preserve settings after updates or recreation.

---

## What I Learned

- Deploy services using Docker Compose.
- Mount host directories into containers.
- Use bind mounts for persistent file access.
- Provide secure browser-based administration.

---

## Future Improvements

- Configure HTTPS using Nginx Proxy Manager.
- Restrict access to specific directories.
- Create additional user accounts.
- Enable file previews for supported formats.

---

## References

- https://filebrowser.org/
- https://github.com/filebrowser/filebrowser

---

## Verification Checklist

- [x] Docker Compose file created
- [x] Container deployed
- [x] Web interface accessible
- [x] Home directory mounted
- [x] Administrator password changed
