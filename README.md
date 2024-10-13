# Mikrotik containers

MikroTik's implementation of Linux containers [RouterOS](https://help.mikrotik.com/docs/display/ROS/Container)

> Container package is compatible with arm arm64 and x86 architectures.

There is a device for tests **Mikrotik hap ax3**:
- Architecture: ARM 64bit
- CPU: IPQ-6010, 4 core, (864 - 1800) MHz
- Size of RAM: 1 GB
- Storage size: 128 MB

RAM total, 1Gb (of which about 650Mb is free)


## Collection of containers for RouterOS

A collection of projects that might be interesting to run on a router

### Nginx
Is a web server that can also be used as a reverse proxy, load balancer, mail proxy and HTTP cache.
- **Github:** https://github.com/nginx/nginx 
- **Docker Hub:** https://hub.docker.com/_/nginx
- **RAM:** 

### Nginx Proxy Manager
Docker container and built in Web Application for managing Nginx proxy hosts with a simple, powerful interface, providing free SSL support via Let's Encrypt.
- **Github:** https://github.com/NginxProxyManager/nginx-proxy-manager
- **Docker Hub:** https://hub.docker.com/r/jc21/nginx-proxy-manager
- **RAM:** 

### Traefik
Modern HTTP reverse proxy and load balancer that makes deploying microservices easy.
- **Github:** https://github.com/traefik/traefik
- **Docker Hub:** https://hub.docker.com/_/traefik
- **RAM:** 

### Caddy
Powerful, enterprise-ready, open source web server with automatic HTTPS written in Go.
- **Github:** https://github.com/caddyserver/caddy
- **Docker Hub:** https://hub.docker.com/_/traefik
- **RAM:** 

### Mikrotik Proxy Manager
container in RouterOS for managing proxy hosts via winbox
- **Github:** https://github.com/akmalovaa/mikrotik-proxy-manager
- **Docker Hub:** https://hub.docker.com/r/akmalovaa/mikrotik-proxy-manager
- **RAM:** 120


### Network:
- [Cloudflared](https://github.com/cloudflare/cloudflared)
- [Freeradius-server](https://github.com/FreeRADIUS/freeradius-server)

### DNS: 
- [Pi-hole](https://github.com/pi-hole/docker-pi-hole)
- [AdGuardHome](https://github.com/AdguardTeam/AdGuardHome)
- [Blocky](https://github.com/0xERR0R/blocky)

### Misc:
- [Openspeedtest](https://github.com/openspeedtest/Speed-Test)


## Guide

Registry URL
```shell
/container/config/set registry-url=https://registry-1.docker.io tmpdir=/usb1/tmp
```

### Example commands:
Start blank nginx
```shell
/container/add remote-image=nginx:latest interface=veth1 root-dir=usb1/docker/nginx logging=yes
```


## Info

> [!NOTE]  
> External disk is highly recommended (formatting USB on ext4)


> [!WARNING]  
> **Security risks:**
> 
> Running an obscure container image on your router can open a security breach
> 
> If the router is hacked, the containers can be used to easily install malicious software on your router and over the network