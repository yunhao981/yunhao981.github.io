---
title: test-day-245
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-11-17 15:18:27
---
## Today's Task
- [x] PCT message format change
- [ ] Add exception and retry for PCT when FR down
- [x] Fix Sox Audit Message

## Additional Task 

## Thought

在 Java 8 的历史项目里接了个 slack-api-client 去发消息

得到了某个 Kotlin 的 Exception ...

手动在 pom 里面指定了 kotlin-stdlib 和 okhttp 的版本

```
<dependency>
    <groupId>com.slack.api</groupId>
    <artifactId>slack-api-client</artifactId>
    <version>1.27.0</version>
</dependency>
<dependency>
    <groupId>org.jetbrains.kotlin</groupId>
    <artifactId>kotlin-stdlib</artifactId>
    <version>1.3.70</version>
</dependency>
<dependency>
    <groupId>com.squareup.okhttp3</groupId>
    <artifactId>okhttp</artifactId>
    <version>4.10.0</version>
</dependency>
```

```
Exception in thread "main" java.lang.reflect.InvocationTargetException
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.springframework.boot.loader.MainMethodRunner.run(MainMethodRunner.java:48)
	at org.springframework.boot.loader.Launcher.launch(Launcher.java:87)
	at org.springframework.boot.loader.Launcher.launch(Launcher.java:50)
	at org.springframework.boot.loader.JarLauncher.main(JarLauncher.java:51)
Caused by: java.lang.NoSuchMethodError: kotlin.collections.ArraysKt.copyInto([B[BIII)[B
	at okio.Segment.writeTo(Segment.kt:169)
	at okio.Segment.compact(Segment.kt:152)
	at okio.Buffer.write(Buffer.kt:1491)
	at okio.Buffer.read(Buffer.kt:1503)
	at okio.Buffer.writeAll(Buffer.kt:1290)
	at okio.Options$Companion.buildTrieRecursive(Options.kt:189)
	at okio.Options$Companion.buildTrieRecursive(Options.kt:175)
	at okio.Options$Companion.buildTrieRecursive$default(Options.kt:107)
	at okio.Options$Companion.of(Options.kt:72)
	at okhttp3.internal.Util.<clinit>(Util.kt:70)
	at okhttp3.internal.concurrent.TaskRunner.<clinit>(TaskRunner.kt:309)
	at okhttp3.ConnectionPool.<init>(ConnectionPool.kt:41)
	at okhttp3.ConnectionPool.<init>(ConnectionPool.kt:47)
	at okhttp3.OkHttpClient$Builder.<init>(OkHttpClient.kt:471)
	at com.slack.api.util.http.SlackHttpClient.buildOkHttpClient(SlackHttpClient.java:45)
	at com.slack.api.util.http.SlackHttpClient.<init>(SlackHttpClient.java:94)
	at com.slack.api.util.http.SlackHttpClient.<init>(SlackHttpClient.java:90)
	at com.slack.api.util.http.SlackHttpClient.<init>(SlackHttpClient.java:86)
	at com.slack.api.Slack.<clinit>(Slack.java:68)
	at com.soxaudit.helper.slack.SlackMessageHelper.sendFileMessage(SlackMessageHelper.java:42)
	at com.soxaudit.App.sendReport(App.java:108)
	at com.soxaudit.App.start(App.java:93)
	at com.soxaudit.App.auditBranch(App.java:62)
	at com.soxaudit.App.app(App.java:44)
	at com.soxaudit.SoxauditApplication.main(SoxauditApplication.java:18)
	... 8 more
```