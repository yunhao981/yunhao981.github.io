---
title: test-general-procedures
categories: Test Infra Manual
tags: Test Infra Manual
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-08-09 11:56:48
---
# Useful Links

[Process of Release and Regression](https://developer.ea.com/display/CI/Process+of+Release+and+Regression)

[CHGxxxxxxx-CD-Regression](https://developer.ea.com/display/CI/CHG0150415-CD-Regression)

[cd develop spreadsheel](https://developer.ea.com/pages/viewpage.action?pageId=313443489)

[Fastrun-CN](https://fastrun.china.online.ea.com/regression?page=1)

[Release Runbook](https://developer.ea.com/pages/viewpage.action?spaceKey=CI&title=Release+Runbook)

[Staging deployment jenkins job](https://developer.ea.com/display/CI/Staging+deployment+jenkins+job)

# General Procedures

1. find intersections with my jobs from the process and CHGxxxxxx-CD-Regresssion

    1.1 get table info from both 2 pages

    1.2 calculate which repo is for whom

2. merge those repos using jenkins tools

    is there any way to run build with parameters from console?

    is there any way to check build info without frequently cheking page manually?

3. check parameters: keymaster's release is rel550, and access is 542, others 551.

4. build image of those repos (still using jenkins tools)

5. send merge links & bulid links to slack cm-url-list channel

    check slack apis for auto sending messages

6. deploy staging after image was built

7. update build numbers to chgxxx-cd-regression. lockbox-v2's is in jenkins console log, search tagged for it.

8. initialize regression test with Fastrun