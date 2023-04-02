---
title: Homelab Stand 03-2023
tags:
- Technik
---

## NAS
- Mainboard: Asus P9D-I
- RAM: 16GB ECC Kingston
- Case: Fractal Node 304
- CPU: Intel i3-4130T
- Speicher: 2x4TB Ironwolf Pro (ZFS Mirror)
- Boot Drive: 128GB SSD Kingston
- OS: Ubuntu mit ZFS
- Docker:
	- Syncthing
	- Vaultwarden
	- Jellyfin


## Virtualisierungsumgebung
- Minisforum HM90
- 32GB RAM Crucial
- 1TB Samsung NVMe SSD
- OS: Proxmox
- Umgebung:
    - Container
        - normales Ubuntu
        - Gitea
        - PiHole
        - Grafana (samt Datenbanken)
        - Docker
            - Traefik
        - Docker Testumgebung
    - VMs
        - Windows 
