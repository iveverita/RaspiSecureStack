# RaspiSecureStack

RaspiSecureStack is a self-hosted, secure service stack designed to run on a Raspberry Pi.  
It combines **SSH hardening** with a **Dockerized infrastructure** that includes:

- **Portainer** → easy Docker container management  
- **Nginx** → lightweight, secure web server  
- **n8n** → powerful workflow automation  
- **AdGuard Home** → DNS-based ad & tracker blocking  

The goal of this project is to provide a reproducible, security-first setup that can serve as both a personal homelab and a learning project.

---

## Features

- **Hardened SSH**  
  - Key-based login only  
  - Root login disabled  
  - Custom `sshd_config` with stricter security options  

- **Dockerized Services**  
  - **Portainer** for managing containers  
  - **Nginx** for web hosting / reverse proxy  
  - **n8n** for no-code workflow automation  
  - **AdGuard Home** for DNS filtering and privacy  

- **Resource Limits**  
  Each service has defined CPU & memory constraints in `docker-compose.yml` for stability on Raspberry Pi hardware.  

---

## Project Structure

```
RaspiSecureStack/
├── ssh/
│   └── sshd_config             # Hardened SSH configuration
├── docker/
│   ├── docker-compose.yml      # Service stack definition
│   ├── config/
│   │   └── default.conf        # Nginx config
│   ├── html/
│   │   └── index.html          # WebPage source code
│   ├── adguard/
│   │   ├── conf/AdGuardHome.yaml  # AdGuard config
│   │   └── work/ 
│   ├── n8n/
│   │   ├── config/             # Private config
│   │   ├── notes/ 
│   │   └── ssh/ 
│   └── portainer/
│       ├── docker_config/      # chmod 700
│       └── tls/                # chmod 700
└── README.md
```



---

## Getting Started

### Prerequisites
- Raspberry Pi (tested on Pi 5, should work on Pi 3 as well)  
- Raspberry Pi OS (Debian-based) with Docker & Docker Compose installed  
- SSH access with keys configured  

### Deploy
1. Clone this repo:
   ```bash
   git clone https://github.com/<your-username>/RaspiSecureStack.git
   cd RaspiSecureStack/docker```

2. Start the stack:
   ```bash
   docker compose up -d```

3. Access services:
   ```bash
    Portainer → http://<pi-ip>:9000
    Nginx → http://<pi-ip>:8080 (or HTTPS on 8443)
    n8n → http://<pi-ip>:5678
    AdGuard Home → http://<pi-ip>:3000```

