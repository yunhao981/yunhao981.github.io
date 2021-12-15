---
title: stg-liquibase-deploy-steps
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2021-12-15 17:03:36
---
Steps:  
1. release liquibase deploy image:
  - mysql:
    - nucleus: https://reports.citools.ea.com/jenkins/job/ReleaseProductInNucleusRepo, Product: liquibase.data
    - more to come...
  - cassandra:
    - nucleus: https://reports.citools.ea.com/jenkins/job/ReleaseProductInNucleusRepo, Product: liquibase.cassandra
    - more to come...
2. Log on to `stgk8smaster-pci-01`
3. `cd` into /opt/iad2_kubernetes_for_liquibase/stg/application/liquibase
4. Git checkout latest version, currently tianyitao-liquibase, future master
5. `sudo bash apply.sh [job_type] [image_version] [action]` or `sudo bash apply.sh` for help message
6. Log folder and other information will be printed. Example below:
```
    replacing {IMAGE_VERSION} with 551.0.20211214.799.9f6a920.nocm.1639467754, outputting to liquibase-job-nucleus.liquibase.cassandra.deploy.yaml.211214075413
    job exists, will delete using
    kubectl delete job -n stg-liquibase stgliquibase-nucleus-liquibase-cassandra-deploy
    job.batch "stgliquibase-nucleus-liquibase-cassandra-deploy" deleted
    applying job using
    kubectl apply -n stg-liquibase -f liquibase-job-nucleus.liquibase.cassandra.deploy.yaml.211214075413
    job.batch/stgliquibase-nucleus-liquibase-cassandra-deploy created
    Job running, scanning for log folder
    Checking new serv dir...
    New folder not found, sleep for 5 seconds
    Checking new serv dir...
    New folder not found, sleep for 5 seconds
    Checking new serv dir...
    New folder is 211214075420
    Job is running
    check log file: /central_log_stg/app_logs/stgliquibase/nucleus.liquibase.cassandra.deploy/serv/211214075420/status.log
    or
    check pod: kubectl logs -n stg-liquibase stgliquibase-nucleus-liquibase-cassandra-deploy-qn6fs
```