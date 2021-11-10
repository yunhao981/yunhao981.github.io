---
title: transfer-lockbox-jobs-tips
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-11-10 17:59:50
---

# 6天里面在迁移 Jenkins Job 上碰到的坑

## 1. Build Lockbox.Birdwing 的时候 没有找到 LB.api 和 LB.qa
```
[ERROR] Failed to execute goal on project Lockbox.Birdwing: Could not resolve dependencies for project com.ea.eadp.lb.test:Lockbox.Birdwing:jar:490.0-SNAPSHOT: The following artifacts could not be resolved: com.ea.lb:lb.api:jar:5.0.0-SNAPSHOT, com.ea.lb:lb.qa:jar:5.0.0-SNAPSHOT: Failure to find com.ea.lb:lb.api:jar:5.0.0-SNAPSHOT in https://artifactory.citools.ea.com/artifactory/ea-snapshots was cached in the local repository, resolution will not be reattempted until the update interval of nucleus.snapshots has elapsed or updates are forced -> [Help 1]
```

需要 build lockbox-sloth 和 build lockbox-qa

于是迁移了这两个 job 到 Testinfra Master 上

同时，root 和 shdev 两个用户的 maven repository 目录不同

## 2. RL-Customer-Portal-BVT Compilation error

```
[ERROR] COMPILATION ERROR : 
[INFO] -------------------------------------------------------------
[ERROR] /home/shdev/local/lockbox-cp/cp-integration/src/test/java/com/ea/eadp/test/ui/customerportal/dataProvider/dataProviders/TestDataProviderHelper.java:[1213,38] error: cannot find symbol
  symbol:   method setSteamNameDiscoverable(String)
  location: variable pidPrivacySettingsType of type PidPrivacySettingsType
```

## 3. Build Sloth 找不到 POM

```
[ERROR] The goal you specified requires a project to execute but there is no POM in this directory (/home/shdev/pct/jenkins/workspace/Build_Sloth). Please verify you invoked Maven from the correct directory. -> [Help 1]
```

通过 `-f` 手动指定 pom

## 4. RL-Customer-Portal-BVT NullPointerException

```
INFO  2021-11-03 02:57:15 - db.mysql.password.encrypted: *****
java.lang.NullPointerException
	at com.ea.nova.test.client.SystemPropertiesHelper.loadTestProperties(SystemPropertiesHelper.java:173)
	at com.ea.nova.test.client.SystemPropertiesHelper.init(SystemPropertiesHelper.java:90)
```

需要在 `/usr/bin/config.key` 里写个密钥

## 5. BVT test 会用 Win 下的 ChromeDriver

`-Dwebdriver.chrome.driver=\${path}`

手动指定 chrome driver 的目录

## 6. linux 下 ChromeDriver 不能用 root 执行

```
org.openqa.selenium.WebDriverException: unknown error: Chrome failed to start: exited abnormally.
  (unknown error: DevToolsActivePort file doesn't exist)
  (The process started from chrome location /usr/bin/google-chrome is no longer running, so ChromeDriver is assuming that Chrome has crashed.)
Build info: version: '3.141.59', revision: 'e82be7d358', time: '2018-11-14T08:17:03'
System info: host: 'jenkinsmaster', ip: 'Unknown', os.name: 'Linux', os.arch: 'amd64', os.version: '3.10.0-1062.1.2.el7.x86_64', java.version: '1.8.0_252'
Driver info: driver.version: ChromeDriver
```

导致了 139 个 case 执行两次，每个 case 各失败一次，跳过一次

需要用普通用户执行，而不是 root

因此需要从 master 搬到 slave1 上，那里的 Jenkins 用的不是 root

## 7. chmod 权限问题

```
[ERROR] Failed to execute goal org.apache.maven.plugins:maven-assembly-plugin:2.3:single (default) on project lb.app: Failed to create assembly: Error creating assembly archive assembly-copy: chmod exit code was: 1 -> [Help 1]
```
```
[WARNING] chmod: changing permissions of '/home/shdev/local/lockbox-sloth/lb.app/target/lb.app/conf/lb.configuration.data-5.0.0-SNAPSHOT.jar': Operation not permitted
```

Master 上 git clone 用的是 root 用户，所以对应的目录用户组也是 root

需要 `chown -R` 

## 8. Chrome 无法启动

```
INFO  2021-11-04 04:59:19 - ***Test Skipped*** [CaseName:com.ea.eadp.lb.test.cases.lockbox5.origin.ui.checkout.payments.creditCard.BasicTest#newCreditCardCheckout] [Priority:BVT] [Duration:10] [Status:Enable] [BugNumber:] [Release:Default] [Features:(Origin X) checkout - origin x ui toolkit integration and UX updates] [FailedMessage:]
Tests run: 2, Failures: 1, Errors: 0, Skipped: 1, Time elapsed: 11.652 sec <<< FAILURE!
beforeMethod(com.ea.eadp.lb.test.cases.lockbox5.origin.ui.checkout.payments.creditCard.BasicTest)  Time elapsed: 10.372 sec  <<< FAILURE!
org.openqa.selenium.WebDriverException: unknown error: Chrome failed to start: exited abnormally
  (unknown error: DevToolsActivePort file doesn't exist)
  (The process started from chrome location /usr/bin/google-chrome is no longer running, so ChromeDriver is assuming that Chrome has crashed.)
```

ssh 上去是不行的，没有 GUI 的环境

需要 vnc 上去作为 shdev 手动执行命令

## 9. LB.pin and LB.api compilation error

```
[ERROR] COMPILATION ERROR : 
[INFO] -------------------------------------------------------------
[ERROR] /home/shdev/local/lockbox-sloth/lb.pin/src/main/java/com/ea/eadp/lb/pin/dal/ConfigurablePinClientApi.java:[3,35] package com.ea.eadp.dodo.client.pin does not exist
[ERROR] /home/shdev/local/lockbox-sloth/lb.pin/src/main/java/com/ea/eadp/lb/pin/dal/ConfigurablePinClientApi.java:[8,47] cannot find symbol
  symbol: class PinClientApi
```

```
[ERROR] Error resolving version for plugin 'com.ea.eadp.lb:dodo.swagger.util' from the repositories [local (/home/shdev/.m2/repository), central (https://artifactory.citools.ea.com/artifactory/ea-releases), snapshots (https://artifactory.citools.ea.com/artifactory/ea-snapshots)]: Plugin not found in any plugin repository -> [Help 1]
```

需要确认 maven settings.xml 的 repository 配置

直接用了 master 上的 settings.xml

并且通过 `-s` 指定这个 xml