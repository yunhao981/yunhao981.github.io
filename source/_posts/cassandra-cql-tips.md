---
title: cassandra-cql-tips
categories: test
tags: test
description: life as Test Contractor at EADP-C&I Test-Infra Team
show: true
date: 2022-02-25 10:46:40
---
# Cassandra CQL Sample

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

# Cassandra FAQ

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

Optimize the memory usage of tables.

will be weighted by size and frequency.

work with cassandra.yml

## Compaction

## Compression

## CRC Check Chance

## dclocal_read_repair_chance

Probability that a successful read operation triggers a read repair

limited to replicas in the same DC as the coordinator

## default_time_to_live

max: 20 years in second

disabled: 0

a new TTL timestamp is calculated when the data is updated and the row is removed after all the data expires

## gc_grace_seconds

GC: Garbage Collection

Tombstone: Deletion marker

data is marked with a Tombstone -> wait some time -> eligible for gc !

this config is about how long it should wait

Default: 10 days in second

## memtable_flush_period_in_ms

Memtables:

Milliseconds before memtables associated with the table are flushed

## max_index-interval

## min_index_interval

## read_repair_chance

similar to dclocal_read_repair_chance, but this repair is not limited to replicas in the same DC as the coordinator

## speculative_retry


# not configured variables

dclocal_read_repair_chance

read_repair_chance

memtable_flush_period_in_ms

# Reference

https://docs.datastax.com/en/cql-oss/3.3/cql/cql_reference/cqlCreateTable.html#cqlCreateTable
