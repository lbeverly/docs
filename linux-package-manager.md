---
title: Linux Package Repos
category: Reference
weight: 5
---

## Add ScaleFT to Your Package Manager

### Deb (Aptitude)

1. Add the ScaleFT apt repo to your /etc/apt/sources.list system config file:

  ```echo "deb https://scaleft.bintray.com/scaleft-apt ubuntu main" | sudo tee -a /etc/apt/sources.list```

2. Trust Bintray:

  ```sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 379CE192D401AB61``` 

3. `sudo apt-get update`


### RPM (Yum, DNF)

1. Run the following to get a generated .repo file:

  ```wget https://bintray.com/scaleft/scaleft-rpm/rpm -O bintray-scaleft-scaleft-rpm.repo```

  or - Copy this text into a 'bintray-scaleft-scaleft-rpm.repo' file on your Linux machine:

   ```
   #bintraybintray-scaleft-scaleft-rpm - packages by scaleft from Bintray
   [bintraybintray-scaleft-scaleft-rpm]
   name=bintray-scaleft-scaleft-rpm
   baseurl=https://scaleft.bintray.com/scaleft-rpm
   gpgcheck=0
   enabled=1 
   ```

2. `sudo mv  bintray-scaleft-scaleft-rpm.repo /etc/yum.repos.d/`