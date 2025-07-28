# RouterOS Containers

Main wiki - https://help.mikrotik.com/docs/display/ROS/Container

The ability to run containers on MikroTik routers opens up many possibilities—now, the only limits are your imagination and the device's resources.

If you decide to experiment with containers at homelab, it is recommended to choose devices with:

- ARM64
- RAM > 1 GB

or use a **CHR VM**

At the moment, the most interesting models for homelab are:

- hap ax2 (There is no USB port, you need to use a network drive)
- hap ax3
- RB5009

Useful links:
- [Guide](https://github.com/akmalovaa/mikrotik-containers/blob/main/guide.md)
- [Mikrotik CPU comparison](https://github.com/akmalovaa/mikrotik-containers/blob/main/benchmark_cpu.md)


## Collection of useful containers for RouterOS

> [!NOTE]  
> Only the minimum resources requests to run the container are listed here, without taking into account the load.

**CPU Load:**
- 🟢 **Low** - Minimal CPU consumption, can be run on devices
- 🟡 **Medium** - Moderate CPU consumption, doubtful but ok
- 🔴 **High** - High CPU consumption, not recommended to use
- ⚪ **Unknown** - No information available

**RAM** - Approximate memory consumption in megabytes during downtime and required for container startup



### Proxy

| Name | Description | Repository | CPU Load | RAM (MB) |
|------|-------------|------------|----------|----------|
| **Nginx** | High-performance web server and reverse proxy | [nginx/nginx](https://github.com/nginx/nginx) | 🟢 | ~15 |
| **Nginx Proxy Manager** | User-friendly web interface for managing Nginx proxy with SSL | [NginxProxyManager/nginx-proxy-manager](https://github.com/NginxProxyManager/nginx-proxy-manager) | 🟡 | ~ |
| **Traefik** | Modern reverse proxy with automatic service discovery | [traefik/traefik](https://github.com/traefik/traefik) | 🟢 | ~125 |
| **Caddy** | Web server with automatic HTTPS certificates | [caddyserver/caddy](https://github.com/caddyserver/caddy) | 🟢 | ~20 |
| **Mikrotik Proxy Manager** | Specialized proxy manager for MikroTik | [akmalovaa/mikrotik-proxy-manager](https://github.com/akmalovaa/mikrotik-proxy-manager) | 🟢 | ~120 |

### Network

| Name | Description | Repository | CPU Load | RAM (MB) |
|------|-------------|------------|----------|----------|
| **Cloudflared** | Cloudflare tunnel for secure access to local services | [cloudflare/cloudflared](https://github.com/cloudflare/cloudflared) | 🟢 | ~ |
| **Freeradius-server** | RADIUS server for network device authentication | [FreeRADIUS/freeradius-server](https://github.com/FreeRADIUS/freeradius-server) | 🟢 | ~ |

### DNS

| Name | Description | Repository | CPU Load | RAM (MB) |
|------|-------------|------------|----------|----------|
| **Pi-hole** | DNS-level ad blocker with web interface | [pi-hole/docker-pi-hole](https://github.com/pi-hole/docker-pi-hole) | 🟢 | ~ |
| **AdGuardHome** | Modern Pi-hole alternative with advanced features | [AdguardTeam/AdGuardHome](https://github.com/AdguardTeam/AdGuardHome) | 🟢 | ~80 |
| **Blocky** | Fast DNS proxy with ad blocking and caching | [0xERR0R/blocky](https://github.com/0xERR0R/blocky) | 🟢 | ~ |

### Observability

| Name | Description | Repository | CPU Load | RAM (MB) |
|------|-------------|------------|----------|----------|
| **MKTXP Prometheus Exporter** | MikroTik metrics exporter for Prometheus monitoring | [akpw/mktxp](https://github.com/akpw/mktxp) | ⚪ | ~ |
| **SNMP Prometheus Exporter** | Universal SNMP exporter for metrics collection | [prometheus/snmp_exporter](https://github.com/prometheus/snmp_exporter) | ⚪ | ~ |

### Misc

| Name | Description | Repository | CPU Load | RAM (MB) |
|------|-------------|------------|----------|----------|
| **Librespeed** | Self-hosted speed test server | [librespeed/speedtest-rust](https://github.com/librespeed/speedtest-rust) | 🟡 | ~10 |


Write me your containers in Telegram that you found interesting, I'll try to launch them and add them to this list too.

