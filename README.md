# Mikrotik containers

Main RouterOS wiki - https://help.mikrotik.com/docs/display/ROS/Container

The ability to run containers on MikroTik routers opens up many possibilities—now, the only limits are your imagination and the device's resources.

If you decide to experiment with containers at homelab, it is recommended to choose devices with:

- ARM64
- RAM > 1 GB

or use a **CHR VM**

At the moment, the most interesting models for homelab are:

- hap ax2 (There is no USB port, you need to use a network drive)
- hap ax3
- RB5009

[mikrotik cpu comparison](https://github.com/akmalovaa/mikrotik-containers/blob/main/benchmark_cpu.md)

## Collection of containers for RouterOS

A collection of projects that might be interesting to run on a router

### Proxy:
- [Nginx](https://github.com/nginx/nginx )
- [Nginx Proxy Manager](https://github.com/NginxProxyManager/nginx-proxy-manager)
- [Traefik](https://github.com/traefik/traefik)
- [Caddy](https://github.com/caddyserver/caddy)
- [Mikrotik Proxy Manager](https://github.com/akmalovaa/mikrotik-proxy-manager) | 120

### Network:
- [Cloudflared](https://github.com/cloudflare/cloudflared)
- [Freeradius-server](https://github.com/FreeRADIUS/freeradius-server)

### DNS: 
- [Pi-hole](https://github.com/pi-hole/docker-pi-hole)
- [AdGuardHome](https://github.com/AdguardTeam/AdGuardHome)
- [Blocky](https://github.com/0xERR0R/blocky)

### Observability:
- [MKTXP Prometheus Exporter](https://github.com/akpw/mktxp)
- [SNMP Prometheus Exporter](https://github.com/prometheus/snmp_exporter)

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