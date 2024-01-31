---
title: "Static Website Migration"
slug: "static-migration"
date: "2018-06-03"
author: "kevin"
draft: true
image: ""
---

I've been hosting my websites at home for some time now, mostly with Wordpress, and I've been pretty happy with it. I recently migrated my Wordpress sites from Apache to nginx then to Docker, each an improvement along the way, but then I had an idea to put one of my sites (www.vecchione.us) on Amazon   S3/Google Cloud Storage to help speed it up and help secure it better, but since my site is Wordpress, I didn't think I could - well I was wrong.

I found a Wordpress plugin, Simply Static, which allows you to convert your Wordpress website to static html files which worked great for me since my site is static anyway. I ran the converter on relative mode and it dumped out 10MB of data. Success! It's actually extremely efficient and appears to just crawl the site and gather the output, then gives you a link to download a ZIP - pretty cool.

I then looked into where to put the data, knowing that S3 and GCS both allow for static website hosting from within their storage repositories for a _very_ low price. As I was copying the data to Google, I found out about GitHub Pages and their new features custom DNS and enforced HTTPS. Being _completely_ free, I figured I'd have to try this out first.

Turns out it's awesome! My static files are now hosted on GitHub, and my DNS resolves to their servers directly. I enabled HTTPS which triggers the system to retrieve a custom LetsEncrypt SSL cert for my domain and use it. For services like comments and forms, you can't use normal Wordpress built-ins or plugins, but you can use third party services like Disqus or Google Forms.

So then I needed to figure out how to make updates to the site if needed, since I really don't feel like digging into the generated HTML if I could help it, so I updated my site URLs on my Docker hosted website to use it as a staging environment. I make the change, run the static output generator, copy it over to my git repo, commit, push, done!

My next project will be to use some sort of CI pipeline to attempt to automate this process a bit, so we'll see where that goes. In the meantime I migrated my dad's site using the same mechanism in about 30 minutes.

I then moved onto this site which was previously hosted on Ghost on Docker. Looking at GitHub pages led me to Jekyll which is where this site is hosted now. I'm still a newbie to the technology, but the site looks pretty sweet after only a day. I love that it generates a static site (secure and fast!) but still maintains so many great blogging features. So far so good! 