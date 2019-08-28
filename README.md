# chef Lab Vagrant

[![Licensed under Apache License version 2.0](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0)

> **☞ Notice**
>
> This project will be at maintainance stage and the chef version support remains on `RELEASE-2.4.17`. It's been a while that openshift isn't a part of my work life and I have no time to maintain compatibility with the next k8s releases.
>
> Any contributions are warmly welcomed at any time! I hope the project can make your life easy for a cup of coffee.

## Overview

The `chef-lab Vagrant` project aims to make it easy to bring up a real chef-lab cluster by provisioning pre-configured `Vagrantfile` on your local machine.

## Prerequisites

- Host machine must have at least 8GB memory 
- Oracle VirtualBox installed on your host machine
- Vagrant (2.0 or above) installed on your host machine
- Vagrant plugin `vagrant-hostmanager` must be installed

## Getting Started

After adjusting your expected version information, now it's time to bring your cluster up and running. 

This Vagrantfile will create 3 VMs in VirtualBox and the network base will be specified by variable `NETWORK_BASE`.

Checkout the table below for more details:

| VM Node | Private IP | Roles |
| --- | --- | --- |
| chef-workstation  | #192.168.105.10 | workstation  |
| chef-node-1       | #192.168.105.11 | node-1 |
| chef-node-2       | #192.168.105.12 | node-2 |

### Bring Vagrant Up

```bash
$ vagrant up
```
```
vagrant ssh chef-workstation
```
### Chef-dk installation on chef-workstation(centos)
```
    sudo wget https://packages.chef.io/files/stable/chefdk/2.4.17/el/7/chefdk-2.4.17-1.el7.x86_64.rpm
    sudo rpm -ivh chefdk-2.4.17-1.el7.x86_64.rpm
    echo 'eval "$(chef shell-init bash)"' >> ~/.bash_profile
    source ~/.bash_profile
```
### Chef-dk installation on chef-workstation(ubuntu)
```
	VER="2.4.17"
	wget https://packages.chef.io/files/stable/chefdk/${VER}/ubuntu/16.04/chefdk_${VER}-1_amd64.deb
	sudo dpkg -i chefdk_${VER}-1_amd64.deb
	echo 'eval "$(chef shell-init bash)"' >> ~/.bash_profile
	source ~/.bash_profile
```			
### chef validation
chef --version

### Sing up and app.chef.io
https://manage.chef.io/login

Raise request for saplinghr chef organization and get stater-kit

Extrat stater-kit under chef-workstation and name it as chef-repo

chef-repo consist of knife.rb and user.pem files/stable/chefdk/$

### knife bootstrape node
```
knife bootstrap chef-node1 -x vagrant -i ~/.ssh/id_rsa --sudo --node-name chef-node1
knife node list
```
