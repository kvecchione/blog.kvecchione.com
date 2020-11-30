---
title: "The Homelab"
slug: "homelab"
date: "2020-11-21"
author: "kevin"
draft: false
image: ""
---

I'm going to try update this post over time since I get a lot of questions about my home lab. I change things fairly frequently as I test out new technologies and tools, so I'll try to keep the data here updated as best I can so you can see what I'm working on.

## Physical
#### The Cluster
Proxmox VE builds in Ceph distributed storage, so I've hyperconverged by having a 256GB SSD in each machine and running the VMs off the distributed volume. I also run CephFS on top of this volume for Kubernetes shared storage. 

##### pve01
* Dell PowerEdge T20 Server
* Xeon E3-1225 (4c)
* 16GB RAM
* Proxmox VE 6.2

##### pve02/pve03
* Dell Optiplex 7020 SFF i5-4590 (4c)
* 256GB SSD
* 16GB RAM
* Proxmox VE 6.2

### NAS
##### nas01 - Synology DS1819+ NAS
* Media NAS
* 6 x 4TB WD RED HDD (4 active, 2 hot spares)
* Docker for Homebridge
* Plex (backup)

### Endpoints
##### einstein - Windows 10 - Gaming Desktop
* Intel i5 2500 (Sandy Bridge still going strong since 2012!)
* 16G RAM
* Gigabyte GTX 960 Video Card

##### ironman - MacBook Pro 16 (2019)
* Daily Driver

## Virtual
##### k[ms][nn] - Ubuntu 18.04 - Kubernetes Nodes
* 3-node Kubernetes 1.18 cluster with RKE2
* Containerized applications:
  * Nginx Ingress (internal and external)
  * Certificate Manager
  * MetalLB
  * Kubernetes Dashboard
  * OpenFaaS
  * Harbor
  * ArgoCD
  * Gitea
  * Tautulli
  * Calibre Web
  * Wekan
  * Bookstack
  * Invoice Ninja
  * MySQL (shared)
  * Postgres (shared)
  * MongoDB (shared)
  * Ombi
  * Minio
  * Openeats
  * ddclient
  * ...lots more

##### lb01 - Alpine 3.11 - HAProxy
* HTTP/TCP proxy for Kubernetes

##### dns01 - Debian 10 - PiHole DNS
* PiHole DNS/Adblock server

##### plex01 - Ubuntu 18.04 - Plex
* Plex Media Server

##### backup01 - Ubuntu 18.04 - Backups
* Runs various backup jobs

## 3D Printer

Creality Ender 5 Pro
* Embedded Raspberry Pi 4 with OctoPrint
