---
title: "ddclient and Cloudflare"
slug: "ddclient-cloudflare"
date: "2019-09-02"
author: "kevin"
draft: true
image: ""
---

I use a ddclient container in my Kubernetes cluster to maintain my IP with Cloudflare's free DNS hosting. I recently noticed issues with my configuration of ddclient for use with DNS hosted in Cloudflare. For anyone that finds this and sees this error, this is what resolved it for me:

Error:
```WARNING:  file /var/cache/ddclient/ddclient.cache, line 3: Invalid Value for keyword 'ip' = ''```

It appears this is due to the Cloudflare API URL changing, so ddclient can't get the current IP.

New config file:
```
daemon=300
syslog=yes
ssl=yes
use=web,web=ipinfo.io/ip
protocol=cloudflare
# **This is the important change**
server=api.cloudflare.com/client/v4
login=<email>
password=<password>
zone=<zone>
<record>
```

Hope this helps you out!