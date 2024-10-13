# Mikrotik containers

MikroTik's implementation of Linux containers [RouterOS](https://help.mikrotik.com/docs/display/ROS/Container)

Requirements
Container package is compatible with arm arm64 and x86 architectures.

There is a device for tests **Mikrotik hap ax3**:
- Architecture: ARM 64bit
- CPU: IPQ-6010, 4 core, (864 - 1800) MHz
- Size of RAM: 1 GB
- Storage size: 128 MB

RAM total, 1Gb (of which about 650Mb is free)


## Collection of containers for RouterOS

A collection of projects that might be interesting to run on a router

### Proxy:
- [Nginx](https://github.com/nginx/nginx)
- [Nginx Proxy Manager](https://github.com/NginxProxyManager/nginx-proxy-manager)
- [Traefik](https://github.com/traefik/traefik)
- [Caddy](https://github.com/caddyserver/caddy)

### Network:
- [cloudflared](https://github.com/cloudflare/cloudflared)
- [freeradius-server](https://github.com/FreeRADIUS/freeradius-server)

### DNS: 
- [Pi-hole](https://github.com/pi-hole/docker-pi-hole)
- [AdGuardHome](https://github.com/AdguardTeam/AdGuardHome)
- [blocky](https://github.com/0xERR0R/blocky)

### Misc:
- [openspeedtest](https://github.com/openspeedtest/Speed-Test)



## INFO

> [!NOTE]  
> External disk is highly recommended (formatting USB on ext4)


> [!WARNING]  
> **Security risks:**
> 
> Running an obscure container image on your router can open a security breach
> 
> If the router is hacked, the containers can be used to easily install malicious software on your router and over the network