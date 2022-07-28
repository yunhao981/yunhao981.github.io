---
title: test-day-173
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-07-28 10:52:03
---
## Today's Task
- [ ] Build Script User Friendly Changes
- [ ] Refactor Build Scripts
- [ ] Hadar Groovy Liquibase Job Support

## Additional Task 

## Thought

试着在 Jenkins Job 执行完之前拿到了当前 job 的 console log

需要去 Approve 一些奇怪的权限

```groovy
stage('Result Analysis') {
    steps {
        script {
            def logContent = Jenkins.getInstance().getItemByFullName(env.JOB_NAME).getBuildByNumber(Integer.parseInt(env.BUILD_NUMBER)).logFile.text
            writeFile file: "${env.WORKSPACE}/buildConsolelog.txt", text: logContent
            def consoleOutput = readFile "${env.WORKSPACE}/buildConsolelog.txt"

            def keywords = ["ERROR", "WARNING", "author", "conflict"]

            for(line in consoleOutput.split("\n")) {
                for (keyword in keywords) {
                    if (line.contains(keyword)) {
                        echo line
                    } else if (line.contains("changes")) {
                        changes += line
                        echo line
                    }
                }
            }
        }
    }
}
```
