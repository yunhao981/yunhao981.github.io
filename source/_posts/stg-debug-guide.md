---
title: stg-debug-guide
categories: Test Infra Manual
tags: Test Infra Manual
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-11-01 11:57:24
---

# Ready Precontact

https://se-pm.iad2.infery.com

password is RSA passcode on mobile phone, after entering the 8-digit pin for the code

LDAP, Ephemeral Hosts

check slack bot message for login info

novassh, choose PCI jumpbox

login with the password set inside iad2, not the passcode

```bash
ssh stgk8smaster-pci-01
```

```bash
ssh stgk8smaster-nonpci-01
```

They are the two master nodes

PCI is for components related with credit card money


get all pods
```bash
sudo kubectl get pod -A
```

get pods inside specific namespace
```bash
sudo kbuectl get pod -n stg-nucleus
```

`0/1` service down, need redeploy

ipgeo and Completed jobs can be ignored


## Reboot pod

```bash
sudo kubectl delete pod -n stg-xxx stgxxx-1
```

```bash
sudo kubectl exec -it -n stg-xxx stgxxx-1 bash
```

kubectl describe pod

`~/xxx.app/serv`

`alert.log` 内有详细信息

`vim -R` 可以让 vim 只读


## Manually Deploy image to STG

```bash
kubectl edit sts -n stg-xxx
kubectl delete pod -n stg-xxx stgxxx-0

```
edit `sts` ！！
delete `pod` ！！