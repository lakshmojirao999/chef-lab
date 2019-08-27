# Kubernates Vagrant

[![Licensed under Apache License version 2.0](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0)

> **☞ Notice**
>
> This project will be at maintainance stage and the K8s version support remains on `RELEASE-3.11`. It's been a while that openshift isn't a part of my work life and I have no time to maintain compatibility with the next k8s releases.
>
> Any contributions are warmly welcomed at any time! I hope the project can make your life easy for a cup of coffee.

## Overview

The `Kubernates Vagrant` project aims to make it easy to bring up a real k8s cluster by provisioning pre-configured `Vagrantfile` of several major releases of OKD on your local machine.

## Prerequisites

- Host machine must have at least 8GB memory (16GB for OKD `3.11`)
- Oracle VirtualBox installed on your host machine
- Vagrant (2.0 or above) installed on your host machine
- Vagrant plugin `vagrant-hostmanager` must be installed

## Getting Started

After adjusting your expected version information, now it's time to bring your cluster up and running. 

This Vagrantfile will create 3 VMs in VirtualBox and the network base will be specified by variable `NETWORK_BASE`.

Checkout the table below for more details:

| VM Node | Private IP | Roles |
| --- | --- | --- |
| k8s-master  | #192.168.33.10 | master  |
| k8s-slave-1 | #192.168.33.11 | slave-1 |
| k8s-slave-2 | #192.168.33.12 | slave-2 |

### Bring Vagrant Up

```bash
$ vagrant up
```

### Provisioning Private Keys

```bash
$ vagrant provision --provision-with master-key,node01-key,node02-key
```
### Start Running Kubernates commands
```
kubectl get nodes
```
