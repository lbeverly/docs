---
title: Linux Repositories
menu:
  main:
    parent: 'reference'
---

ScaleFT distributes client and server packages for Linux via APT and RPM
repositories.

## Ubuntu and Debian

```
# Add the ScaleFT apt repo to your /etc/apt/sources.list system config file:
echo "deb http://pkg.scaleft.com/deb linux main" | sudo tee -a /etc/apt/sources.list

# Trust the repository signing key:
curl -C - https://www.scaleft.com/dl/scaleft_deb_key.asc | sudo apt-key add -

# Retrieve information about new packages
sudo apt-get update
```

## Red Hat, CentOS and Fedora

```
# Add the ScaleFT yum repository
curl -C - https://www.scaleft.com/dl/scaleft_yum.repo | sudo tee /etc/yum.repos.d/scaleft.repo

# Trust the repository signing key
sudo rpm --import https://www.scaleft.com/dl/scaleft_rpm_key.asc
```
