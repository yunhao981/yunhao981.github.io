---
title: FY23Q4-script-improvements
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2023-01-10 14:23:51
---
## Todo List

### STG Deployment

- [ ] Add retry when failed
- [x] less timeout (1000s -> 750s)
- [x] Skip WIP pods on AWS (billing, qahandler)
- [ ] Split message when deploy failure
- [ ] Change message channel to public

### Audit

- [ ] Fix Preference Center
- [x] Filter Out CICD Components

### Audit T3

- [ ] Detect commits into release branch
- [x] Message Channel to Pulic

### Image Scripts

- [x] Catalog liquibase image auto trigger
- [x] Saola Trigger All parameters
- [x] Lockbox sloth, vaquita, cp common base image

### Liquibase job

- [x] Keymaster new config path support
- [x] Fix 'null' prefix in description
- [ ] Message for Liquibase Image
- [ ] Message for Liquibase with Vault Support
