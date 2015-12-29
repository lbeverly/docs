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
echo "deb https://scaleft.bintray.com/scaleft-apt ubuntu main" | sudo tee -a /etc/apt/sources.list

# Trust the repository signing key:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 379CE192D401AB61
```

## Red Hat, CentOS and Fedora

```
# Add the ScaleFT yum repository
curl https://bintray.com/scaleft/scaleft-rpm/rpm > scaleft.repo
sudo mv scaleft.repo /etc/yum.repos.d/
```
