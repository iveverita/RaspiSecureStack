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
RaspiSecureStack/<br>
├── ssh/<br>
│   └── sshd_config             # Hardened SSH configuration<br>
├── docker/<br>
│   ├── docker-compose.yml      # Service stack definition<br>
│   ├── config/<br>
│   │   └── default.conf        # Nginx config<br>
│   ├── html/<br>
│   │   └── index.html          # WebPage source code<br>
│   ├── adguard/<br>
│   │   ├── conf/AdGuardHome.yaml  # AdGuard config<br>
│   │   └── work/ <br>
│   ├── n8n/<br>
│   │   ├── config/             # Private config<br>
│   │   ├── notes/ <br>
│   │   └── ssh/ <br>
│   └── portainer/<br>
│       ├── docker_config/      # chmod 700<br>
│       └── tls/                # chmod 700<br>
└── README.md<br>
```

