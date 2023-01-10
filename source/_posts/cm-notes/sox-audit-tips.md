---
title: sox-audit-tips
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-03-08 16:45:51
---
# 大概做啥

每个季度会有外部的财务公司审计一下保险费，会根据 CM tools 上规定的每一个 CHG 里包含 commit 的实际完成情况来决定

也就是说，会从 CM tools 上去拉一下这个 CHG 里应该包含些什么，再从 GitLab 上去看一下实际 commit 了什么，审计出来的结果需要发送一封邮件给 Dev

不过现在年久失修，大概有半年以上没发出去过邮件了，两个季度过去好像也没什么事情……

而且如果实际的 commit 完成得比要求的更多，那不是很棒嘛

现在碰到的问题是，原来的 Cassandra 本体包括三台node在内全炸了，重新在 KVM 里搭了一台 master，但没有 node

光杆司令在删除数据的时候需要跑三个小时，而原来的只需要五分钟

目前我只知道 Cassandra 在删数据的时候会先标注上一个小墓碑，然后会给一个 TTL 续命，到期了之后才会真的删掉数据, 默认值是 10 天

# 具体咋做

## 1
Spring Boot + Cassandra

TODO: 把这棵目录树弄得好看一点……

```
src/
    main/G
        java/
            com.soxaudit/
                conf/
                    BeanInit
                db/
                    config/
                        CassandraConfig
                    model/
                        AuditKey
                        RecordDB
                    service/
                        RecordService
                    RecordDAO
                exception/
                    BaseException
                    CMNotFoundException
                    GitSourceNotFoundException
                helper/
                    jira/
                        client/
                            IssueGetter
                        model/
                            JiraRestClientConfig
                    model/
                        DefaultAuthenticator
                    CMToolClient
                    COllectionTool
                    DiffHandler
                    DiffHelper
                    FileHelper
                    GitTools
                    JiraUtils
                    MailReportHelper
                inf/
                    Compare
                model/
                    AuditConstants
                    GitLogBean
                    Merge
                App
                SoxauditApplication
    resources/
        shell/
            testaudit.sh
        sql/
            audit.sql
        application.properties
        log4j2.xml
    test/
        java/
            com.soxaudit/
                SoxauditApplicationTests
```

## 2

入口是 SoxauditApplication.java

里面我不太明白为什么需要创建一个 App 对象，再调一下 getBean，再用 bean.app(args) 把参数传进去

还有 `@ComponentScan("com.soxaudit")` 是在做什么？

```java
@SpringBootApplication
@ComponentScan("com.soxaudit")
public class SoxauditApplication {
    // 1. Marshal xml,rm merges with 006
    // 2. Get cmtool info
    // 3. Diff
    public static void main(String[] args) {
        ConfigurableApplicationContext run = SpringApplication.run(SoxauditApplication.class, args);
        App bean = run.getBean(App.class);
        bean.app(args);

        SpringApplication.exit(run, new ExitCodeGenerator() {
            @Override
            public int getExitCode() {
                return 0;
            }
        });
    }
}
```

## 3. App.java

`@Component`

`@Autowired`


### app(String[] args)

app(String[] args) 会去判断拿到的参数长度是不是正好是 4， 然后去用 auditBranch() 处理

### auditBranch(String source, String branch, String chgBranch, String cr)

先用 GitTools 的 unmarshal() ， 得到 GitLogBean，如果这里面没有 merge 记录就直接 return

#### GitLogBean 

`@XmlRootElement(name = "root")`

`@XmlAccessorType(XmlAccessType.NONE)`

`@XmlElement(name = "merge")`

只有一份 List<Merge>

#### GitTools

大致上是先去 cassandra 里删库，然后跑路（

就是在 service.removeAll(cr) 的时候

卡住了三个小时

然后 start()

### RecordService.removeAll

`@Transactional`

先打一行带 chgNum 的 log

然后用 dao.findAll 去拿到 DB 里所有记录

接着开始遍历每一条记录

如果 CHG 对上了，就去 dao.delete

### start()

### sendReport(List<Merge> opsMerges, List<String> ownerMerges)

### log(String info, Collection o)

会把 o 里每个元素的 size() 打进 log





