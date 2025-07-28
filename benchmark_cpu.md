# CPU Benchmark Comparison for MikroTik Devices

| Property | RB5009UG | HAP AX^3 | HAP AX^2 |
|---|---|---|---|
| **Product code** | RB5009UG+S+IN | C53UiG+5HPaxD2HPaxD | C52iG-5HaxD2HaxD-TC |
| **Architecture** | ARM 64bit | ARM 64bit | ARM 64bit |
| **CPU** | 88F7040 | IPQ-6010 | IPQ-6010 |
| **CPU core count** | 4 | 4 | 4 |
| **CPU nominal frequency** | 350-1400 MHz | 864 - 1800 MHz | 864 - 1800 MHz |
| **Size of RAM** | 1 GB | 1 GB | 1 GB |
| **Storage size** | 1 GB | 128 MB | 128 MB |
| **IPsec hardware acceleration** | Yes | Yes | Yes |
| **Suggested price** | $219.00 | $139.00 | $99.00 |
| **Sysbench single thread** | ~1276 | ~841 | ~841 |
| **Sysbench multi thread** | ~5093 | ~3348 | ~3348 |

I will use a container with sysbench:
- --test=cpu --threads=1
- --test=cpu --threads=4

```routeros
/container/add remote-image=mirror.gcr.io/zyclonite/sysbench cmd="--test=cpu --threads=1 run" interface=veth1 logging=yes name=sysbench root-dir=docker/sysbench 
```

### RB5009 - CPU 88F7040

sysbench
```log
threads: 1
sysbench: CPU speed: 1276 events per second
```
```log
threads: 4
sysbench: CPU speed: 5093.27 events per second
```

### HAP AX3 - CPU IPQ-6010

sysbench
```log
threads: 1
sysbench: CPU speed: 841 events per second
```
```log
threads: 4
sysbench: CPU speed: 3347.89 events per second
```

### CHR VPS Red Hat KVM x86_64

I have an old cheap VPS from a cloud provider where CHR was launched a few years ago, it still works without problems or crashes, so I decided to test it as well.

- **CPU:** 1 core (I do not know which CPU is being used)
- **RAM:** 1 GB

```log
threads: 1
sysbench: CPU speed: 2491.79 events per second
```
```log
threads: 4
sysbench: CPU speed: 2483.32 events per second
```

## CPU performance comparison (single thread)

| Device | CPU | Frequency | Events/sec | Relative performance |
|---|---|---|---|---|
| **CHR VPS (KVM)** | x86_64 | - | **2492** | 100% |
| **RB5009UG+S+IN** | 88F7040 | 350-1400 MHz | **1276** | 51% |
| **HAP AX3** | IPQ-6010 | 864-1800 MHz | **841** | 34% |

```
CHR VPS (x86_64)    ████████████████████    2492 events/sec
RB5009 (88F7040)    ██████████▍             1276 events/sec
HAP AX3 (IPQ-6010)  ██████▾                 841 events/sec
```

## CPU performance comparison (multi-threaded mode)

| Device | CPU | Frequency | Events/sec | Relative performance |
|---|---|---|---|---|
| **RB5009UG+S+IN** | 88F7040 | 350-1400 MHz | **5093** | 100% |
| **HAP AX3** | IPQ-6010 | 864-1800 MHz | **3348** | 66% |
| **CHR VPS (KVM)** | x86_64 | - | **2483** | 49% |

```
RB5009 (88F7040)    ████████████████████    5093 events/sec
HAP AX3 (IPQ-6010)  █████████████▎          3348 events/sec
CHR VPS (x86_64)    █████████▾              2483 events/sec
```

## Conclusions

### RB5009 (88F7040)
The leading device with performance 52% higher than the HAP AX3, but also 58% more expensive.

### HAP AX3 (IPQ-6010)
Decent results with a good price-to-performance ratio.

### HAP AX2 (IPQ-6010)
Since the HAP AX2 model has an identical processor, it offers the best price-to-performance ratio. However, keep in mind that there is no USB port, so for container operations you will need to configure separate network storage.

### CHR VPS (x86_64)

Performance here depends on the cloud hosting provider and plan. I have several VPS instances with CHR and usually use the minimal plan (1 core, 1 GB RAM), but performance varies everywhere.

Significant advantage in single-threaded mode, but since my plan only has one core available, it loses to regular hardware in multi-threaded mode.

## Old devices
On earlier devices with 512MB RAM and older ARM versions, I do not recommend running containers, as there may be issues with memory, performance, and builds. I tried using different old routers, there are nuances and not everything works stably and predictably.

## Sysbench
For comparison, other devices in `sysbench` threads=1

```bash
docker run --rm zyclonite/sysbench --test=cpu --threads=1 run
```

```
- Intel N100:            2951.01
- AMD Ryzen 5 5600G:     4711.98
- AMD Ryzen 7 8745H:     5390.37
```

sysbench has many more features and various parameters, and can also compare memory, disk performance, etc. In these tests, I used the simplest option.
