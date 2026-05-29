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

##### k\<n\> / kw\<n\> - Ubuntu 20.04 - Kubernetes Cluster
* Kubernetes 1.35 multi-manager cluster with [RKE2](https://docs.rke2.io/)
* 3 Managers, 3 Workers
* Containerized applications:
  * [Nginx Ingress](https://kubernetes.github.io/ingress-nginx/)
  * [Cert-Manager](https://cert-manager.io/docs/)
  * [Kubernetes Dashboard](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/)
  * [Gitea](https://gitea.io/en-us/)
  * [Tautulli](https://tautulli.com/)
  * [Calibre Web](https://github.com/janeczku/calibre-web)
  * [Bookstack](https://www.bookstackapp.com/)
  * [InvoiceNinja](https://www.invoiceninja.com/)
  * [Minio](https://min.io/)
  * [Openeats](https://github.com/open-eats/OpenEats)
  * ...lots more

##### bastion01 - Ubuntu 24.04 - SSH Bastion
* SSH bastion accessible via [Zerotier](https://www.zerotier.com/)

##### lb01 - Ubuntu 24.04 - Load Balancer
* [HAProxy](http://www.haproxy.org/) HTTP/TCP proxy for Kubernetes
* [cloudflared](https://github.com/cloudflare/cloudflared) with Argo Tunnels

##### dns0X - Ubuntu 24.04 - DNS (3)
* [Technitium DNS](https://technitium.com/dns/)

##### admin01 - Ubuntu 24.04  - Admin/Backup/Monitoring
* Runs custom Python monitoring scripts with integrated Slack alerts

##### plex01 - Ubuntu 24.04 - Plex
* [Plex](https://www.plex.tv/) Media Server

##### homebridge01 - Ubuntu 24.04 - Homebridge
* [Homebridge](https://homebridge.io/)

##### mysql01 - Alpine 3.15 - MariaDB
* MariaDB database server

##### pgsql01 - Alpine 3.15 - PostgreSQL
* PostgreSQL database server

##### smtp01 - Alpine 3.15 - SMTP Relay
* Private SMTP relay server

### NAS
##### nas01 - Synology DS1819+ NAS
* Media NAS
* 6 x 4TB WD RED HDD (5 active, 1 hot spare)

### 3D Printer
BambuLab P1S

(Updated 5/29/26)