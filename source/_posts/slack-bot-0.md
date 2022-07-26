---
title: slack-bot-0
categories: typescript
tags: typescript
description: Slack Bot Dev Notes
show: true
date: 2022-07-26 15:27:39
---

# Features

- Init CM Request

- Approve CM Request

- Show CMs progress

- Trigger CM Cut Build Flow

# Basic Plan

4 weeks without further test and modifications

2 days for regular hotfix CMs in a week -> 3 days to work on the bot

3 days per feature -> only 12 hours per feature

WARNING: the bot is host outside the company network and cannot trigger jenkins jobs host inside, need workaround

## 1. get familiar w/ tutorial bot and general ideas, make it running

2 hours to implement Event Subscription api to talk with slack

### 1.1 cannot call `slack/events` api

只能用 22 端口，call 不通 3000

## 2. implement Init & Approve CM Request Part, with Authorization

## 3. implement Progress Tracking

## 4. implement CM Cut Build Flow with Jenkins Job
