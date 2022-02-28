---
title: cassandra-cql-tips
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-02-25 10:46:40
---
## Cassandra CQL

```sql
CREATE KEYSPACE sox WITH replication = {'class': 'SimpleStrategy', 'replication_factor': '3'}  AND durable_writes = true;

CREATE TABLE sox.audit_history (
    hash_code text,
    cm_num text,
    message text,
    tag text,
    PRIMARY KEY (hash_code, cm_num)
) WITH CLUSTERING ORDER BY (cm_num ASC)
    AND bloom_filter_fp_chance = 0.01
    AND caching = {'keys': 'ALL', 'rows_per_partition': 'NONE'}
    AND comment = ''
    AND compaction = {'class': 'org.apache.cassandra.db.compaction.SizeTieredCompactionStrategy', 'max_threshold': '32', 'min_threshold': '4'}
    AND compression = {'chunk_length_in_kb': '64', 'class': 'org.apache.cassandra.io.compress.LZ4Compressor'}
    AND crc_check_chance = 1.0
    AND dclocal_read_repair_chance = 0.1
    AND default_time_to_live = 0
    AND gc_grace_seconds = 864000
    AND max_index_interval = 2048
    AND memtable_flush_period_in_ms = 0
    AND min_index_interval = 128
    AND read_repair_chance = 0.0
    AND speculative_retry = '99PERCENTILE';
```

`Keyspace` namespace that defineds data replication on nodes

`Replication Factor`

`Durable Writes`

`Clustering`

`bloom filter fp chance`

`caching`

`comment`

`compaction`

`compression`

`crc check chance`

`dclocal read repair chance`

to be continued...
