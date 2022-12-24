---
title: test-day-177
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-08-03 11:27:30
---
## Today's Task

- [ ] Build Script User Friendly Changes
  - [x] Extract Common Methods for PCT jobs
  - [x] Remove Audit Tool from old repo
  - [ ] Extract Common methods for T1 image release scripts
    - [x] Catalog
    - [x] Nexus
    - [ ] Nucleus

- [ ] Slack Bot
  - [x] run on AWS
  - [x] Try Demo Full Functions
  - [ ] Basic Function

## Additional Task

- [x] Deploy LBCP on STG from test branch
- [x] Fix LBCP scripts to push image to AWS
- [x] Ask Jen to help creating repositories for LBCP on AWS

## Thought

`mvn clean install` - build the whole multi-module project

`mvn clean install -pl` - build a single or a set modules

`mvn clean install -pl -am` - build a single or a set modules and their dependencies

```bash
declare -A animals=( ["moo"]="cow" ["woof"]="dog")
animals['key']='value'
"${animals[@]}" #expand the values
"${!animals[@]}" #expand the keys
```
