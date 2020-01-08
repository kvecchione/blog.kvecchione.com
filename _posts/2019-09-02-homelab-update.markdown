---
layout: post
title:  "The Homelab (updated)"
date:   2019-09-02 00:01:00 -0400
categories: computing
author: Kevin Vecchione
---

(last updated: 1/7/20)

## Physical
### skynet - Google WiFi Mesh
* 3x Google WiFi AP, wired backbone

### ironman - MacBook Pro 16 (2019)
* Daily driver
* Thank you Apple for finally listening

### maxwell - MacBook Pro 13 (2010) (offline)
* Drobo Gen1 (USB) Network Gateway
* OSX Remote Desktop

### tesla - Dell T20 server
* Quad core Xeon E3-1225
* 16GB RAM
* XCP-NG 7.6.0

### edison and volta
* 2 x Dell Optiplex 7020 SFF i5-4590 (4c)
* 256GB SSD
* 16GB RAM
* XCP-NG 7.6.0

### galileo - Drobo 5N NAS
* Media NAS
* 4 x 4TB WD RED HDD

### einstein - Windows 10 - Gaming Desktop
* Intel i5 2500 (still going strong!)
* 16G RAM
* Gigabyte GTX 960 Video Card

## Virtual
### xoa - Xen Orchestra Appliance
* XOA Web Management Interface for XCP-NG

### lb01 - Ubuntu 18.04 - RP/LB
* HAProxy service for reverse proxying traffic internal and external and routing into Kubernetes

### dns01 - Ubuntu 18.04 - PowerDNS
* PowerDNS server

### plex01 - Ubuntu 18.04 - Plex
* Plex Media Server

### vpn01 - Ubuntu 18.04 - OpenVPN
* OpenVPN-AS Server
  * Have tried containerizing OpenVPN-AS, but it was more of a pain than it was worth due to the certificate renewal process with LetsEncrypt.

### kube[ms]01-03[ab] - Ubuntu 18.04 - Kubernetes Nodes
* docker-ce
* Kubernetes 1.14 (kubeadm)
* Containerized applications:
  * Traefik (routing)
  * Kubernetes Dashboard
  * Gitea
  * Tautulli
  * Calibre Web
  * Wekan
  * Bookstack
  * Invoice Ninja
  * Shinobi
  * Organizr
  * MySQL (shared)
  * The Lounge (IRC)
  * Ombi
  * ddclient
  * ...lots

### gluster01-03 - Ubuntu 18.04 - GlusterFS
* GlusterFS Cluster

### backup01 - Ubuntu 18.04 - Backups
* Runs various backup jobs