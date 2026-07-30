# 00 - Docker Compose Installation

## Objective

Verify that Docker Compose is installed and ready for deploying multi-container applications.

---

## Environment

| Component | Version |
|----------|---------|
| Operating System | Ubuntu Server 26.04 LTS |
| Docker | Installed |
| Docker Compose | v5.3.1 |

---

## Why Docker Compose?

Managing multiple Docker containers using individual `docker run` commands quickly becomes difficult.

Docker Compose allows an entire application stack to be defined in a single YAML configuration file, making deployments reproducible and easier to maintain.

Benefits include:

- Centralized configuration
- Multi-container deployments
- Simplified updates
- Easier maintenance
- Reproducible environments

---

## Verify Installation

Run:

```bash
docker compose version
```

Example output:

```text
Docker Compose version v5.3.1
```

---

## Screenshot

<img width="336" height="41" alt="image" src="https://github.com/user-attachments/assets/49618980-3d9b-4dbd-acdb-eac6fc7dd8d3" />

>
> `docker compose version`

---

## Implementation Notes

Docker Compose was already available after installing Docker.

No additional installation steps were required.

---

## What I Learned

- Docker Compose extends Docker for multi-container deployments.
- A single configuration file can define an entire application stack.
- Docker Compose simplifies deployment, updates and maintenance.

---

## References

- https://docs.docker.com/compose/
- https://docs.docker.com/compose/intro/compose-application-model/

---

## Verification Checklist

- [x] Docker installed
- [x] Docker Compose installed
- [x] Version verified
- [x] Ready to deploy Compose applications
