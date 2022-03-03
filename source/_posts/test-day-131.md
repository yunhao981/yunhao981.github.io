---
title: test-day-131
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-03-03 14:23:20
---
## Today's Task
- [ ] Release Support for Major Release

## Additional Task 

## Thought

## Cassandra FAQ

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

## Simple Strategy

Assign the same replication factor to the entire cluster. For Test and Dev envs only.

## Replication Factor

How many times the data is replicated across the clusters

Need at least 3 nodes if this value is set to 3.

## Durable Writes

Bypass the commit log when writing to the keyspace if set to false.

NEVER disable it when using Simple Strategy.

## Bloom Filter FP Chance

False-positive probability for SSTable bloom filter.

checks if the row exists before executing disk I/O

0 enables with the largest possible bloom filter and uses the most memory.

1.0 disables it.

Default: 0.01

Recommended: 0.1

## Caching



## Compaction

## Compression

## CRC Check Chance

## dclocal_read_repair_chance

## default_time_to_live

## gc_grace_seconds

## max_index-interval

## memtable_flush_period_in_ms

## min_index_interval

## read_repair_chance

## speculative_retry


### Reference

https://docs.datastax.com/en/cql-oss/3.3/cql/cql_reference/cqlCreateTable.html#cqlCreateTable

