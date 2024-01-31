---
title: "The Homelab"
slug: "homelab"
date: "2021-08-14"
author: "kevin"
draft: false
image: ""
---

I'm going to try update this post over time since I get a lot of questions about my home lab. I change things fairly frequently as I test out new technologies and tools, so I'll try to keep the data here updated as best I can so you can see what I'm working on.

### The Cluster
[Proxmox VE](https://www.proxmox.com/en/) builds in [Ceph](https://docs.ceph.com/en/latest/) distributed storage, so I've hyperconverged by having a 1TB NVMe SSD in each machine and running the VMs off the distributed volume. I also run CephFS on top of this volume for Kubernetes shared storage. 

#### prox01-03
* 3x Dell Optiplex 7060 MFF
* i7-8700T hex-core
* 32GB RAM
* 1TB NVMe
* Proxmox VE 8.x

#### Proxmox LXC Containers

##### k\<n\> - Ubuntu 20.04 - Kubernetes Cluster
* Kubernetes 1.26 multi-manager cluster with [RKE2](https://docs.rke2.io/)
* Containerized applications:
  * [Nginx Ingress](https://kubernetes.github.io/ingress-nginx/)
  * [Cert-Manager](https://cert-manager.io/docs/)
  * [Kubernetes Dashboard](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/)
  * [OpenFaaS](https://www.openfaas.com/)
  * [Harbor](https://goharbor.io/)
  * [Gitea](https://gitea.io/en-us/)
  * [OneDev](https://github.com/theonedev/onedev)
  * [Tautulli](https://tautulli.com/)
  * [Calibre Web](https://github.com/janeczku/calibre-web)
  * [Bookstack](https://www.bookstackapp.com/)
  * [InvoiceNinja](https://www.invoiceninja.com/)
  * [Minio](https://min.io/)
  * [Openeats](https://github.com/open-eats/OpenEats)
  * [Palworld](https://github.com/jammsen/docker-palworld-dedicated-server)
  * ...lots more

##### bastion01 - Ubuntu 20.04 - SSH Bastion
* SSH bastion accessible via [Zerotier](https://www.zerotier.com/)

##### lb01 - Ubuntu 20.04 - Load Balancer
* [HAProxy](http://www.haproxy.org/) HTTP/TCP proxy for Kubernetes
* [cloudflared](https://github.com/cloudflare/cloudflared) with Argo Tunnels

##### dns01 - Ubuntu 22.04 - Primary DNS
* [PiHole](https://pi-hole.net/) DNS/Adblock server

##### admin01 - Alpine 3.15 - Admin/Backup/Monitoring
* Runs custom Python monitoring scripts with integrated Slack alerts

##### plex01 - Ubuntu 20.04 - Plex
* [Plex](https://www.plex.tv/) Media Server

##### teleport01 - Ubuntu 20.04 - Teleport
* [Teleport](https://goteleport.com/) Access Server

##### kasm01 - Ubuntu 20.04 - Kasm VDI
* [Kasm](https://kasmweb.com/) VDI

##### mysql01 - Alpine 3.15 - MariaDB
* MariaDB database server

##### pgsql01 - Alpine 3.15 - PostgreSQL
* PostgreSQL database server

### NAS
##### nas01 - Synology DS1819+ NAS
* Media NAS
* 6 x 4TB WD RED HDD (5 active, 1 hot spare)

### Other Endpoints

##### dns02 - Raspbian - Secondary DNS
* Raspberry Pi Model B
* [Adguard](https://adguard.com/) DNS+Adblock

### 3D Printer

Creality Ender 5 Pro
* Embedded Raspberry Pi 4 with [OctoPrint](https://octoprint.org/)

(Updated 1/31/24)