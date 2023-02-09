---
title: test-day-280
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2023-01-12 14:24:51
---
## Today's Task

- [x] Try Calling Jenkins API
- [x] Code Merge Trigger

## Additional Task

## Thought

`Error: undable to verify the first certificate`

```typescript
import * as https from "https";
import axios from "axios";

const response = await axios.post(url, {}, {
    httpsAgent: new https.Agent({
        rejectUnauthorized: false
    })
})

```
