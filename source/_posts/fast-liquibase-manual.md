---
title: fast-liquibase-manual
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-11-11 12:05:41
---

get artifactory token from `IAD2_Utility` at `/root/token/artifactory.token`

ssh into `IAD2_Jump_Tools_PCI`

ssh into `stgk8smaster-pci-01` or `stgk8smaster-nonpci-01`

```bash
sudo kubectl exec -it -n ${namespace} ${podname} -- bash
```

fetch target file url from artifactory

version is liquibase version on the CM table

url is inside script `test-infra-jenkins/liquibase-deploy/mysql-deploy.sh`

```bash
v="551.0.xxxxx"
t="artifactory_token"
tarfile="liquibase.data-${v}.tar.gz"
urlPrefix="https://artifactory.citools.ea.com/artifactory/releases/com/ea"
urlSuffix="liquibase.data/${v}/${tarfile}"
url="${urlPrefix}/nucleus/${urlSuffix}"

curl -v -H "Authorization: Bearer ${t}" "${url}" -o ${tarfile}
```



```bash
mkdir -p liquibase.data
tar -zxf xxx.tar.gz -C liquibase.data
```

run script inside the tar

```bash
./my-liquibase.py ${component} staging status 551
```
