---
date: 2022-04-09 14:45:01
layout: post
title: "VSC-docker-Error"
subtitle: "How to fix vsc docker connection failure"
description: "If you install the Docker plugin in Linux without setting anything, the connection will fail.
"
image: >+
    https://miro.medium.com/max/719/1*gc54u-dwEz70EadqtJ8LEw.png
optimized_image: >+
    https://miro.medium.com/max/719/1*gc54u-dwEz70EadqtJ8LEw.png
category: VSC
tags:
    - VSC
    - docker
    - error
    - linux
author: Bakuturtle
paginate: 1
---

**How to fix vsc docker connection failure?**

***

# Error 

>Failed to connect. Is Docker running?
    Error: connect EACCES /var/run/docker.sock




---

*Useally, if /var/run/docker.sock is not touched, the permissions are as follows.*

```bash
srw-rw---- 1 root docker 0  4월  9 15:31 /var/run/docker.sock
```
*It's just a problem that VSC cannot access docker.sock, which you just need to change the access rights as follows.*



```bash
sudo chmod a+x /var/run/docker.sock
```
![Error_image_2](https://camo.githubusercontent.com/d435d7e9319e6bb37daebdf61cc7a8ed16acb820f63d1da9eafbdca3a54a7ea2/68747470733a2f2f692e6962622e636f2f317157665150502f323032322d30342d30392d32302d32352d30312e706e67)

---



*As aside as, if you run the code below on another site and it doesn't work, check it out.*

```bash
    sudo usermod -a -G docker $USER
```
*Check group docker.sock access right*

*Since the access permission is set to rw-------(600), there is a high probability that it will not work.*

---


>keyword

* check ur docker.sock aceess right