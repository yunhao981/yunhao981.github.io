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

- [x] Add retry when failed
- [x] less timeout (1000s -> 750s)
- [x] Skip WIP pods on AWS (billing, qahandler)
- [ ] Split message when deploy failure
- [ ] Fix Retry (gen parameters from failed pod log)
- [x] Change message channel to public

### Audit

- [ ] Fix Preference Center
- [x] Filter out Billing_tools
- [x] Filter Out CICD Components
- [x] Fix Message parametes

### Audit T3

- [ ] Detect commits into release branch
- [x] Message Channel to Pulic
- [x] Add Lockbox Legacy

### Image Scripts

- [x] Catalog liquibase image auto trigger
- [x] Saola Trigger All parameters
- [x] Lockbox sloth, vaquita, cp common base image
- [x] Parameter Check to avoid image from retro branch merged to release (retro/xxx_MERGED)

### Liquibase job

- [x] Keymaster new config path support
- [x] Fix 'null' prefix in description
- [x] Message for Liquibase Image
- [ ] Message for Liquibase with Vault Support

### Code Merge

- [x] Block Merge-cut and recut for retro branch

### Data-Consistency Tool

- [x] Fix Message when jenkins git plugin error

