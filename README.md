# raftkv

A fault-tolerant distributed key-value database built from scratch in Java, using Raft consensus and an LSM-tree storage engine.

## Motivation

raftkv is an opportunity to understand distributed systems at the implementation level. Java builds on my experience with Flink and Kafka, while Raft and the storage engine support my long-term interests in databases and infrastructure.

## Goal

Build a small, understandable three-node database where I understand every major component. My focus is on learning consensus, fault tolerance, and storage-engine design rather than recreating a production database.

## Scope

- **Strong consistency:** coordinate reads and writes through a Raft leader and a majority of nodes.
- **Fault tolerance:** continue operating when one of three nodes fails, and prevent a minority partition from committing writes.
- **Raft consensus:** implement leader election, log replication, persistence, and recovery.
- **LSM-tree storage:** explore write-ahead logging, memtables, sorted files, and compaction.
- **Client interface:** provide simple key-value operations and a way to inspect cluster status.
- **Testing:** exercise node failures, network partitions, recovery, and data consistency.

## Learning and validation

1. Work through [Fly.io's distributed systems challenges](https://fly.io/dist-sys/) as a warm-up for building and testing distributed systems.
2. Study the [Raft paper and resources](https://raft.github.io/) and use [TinyKV](https://github.com/talent-plan/tinykv) as a reference for a distributed key-value store's architecture.
3. Test raftkv with [Maelstrom](https://github.com/jepsen-io/maelstrom), including network partitions and recovery. Integrating with Maelstrom will require adapting raftkv to its testing protocol.

## Benchmarks

Measure and document results for:

- **Throughput:** completed operations per second under defined read and write workloads.
- **p99 latency:** the 99th-percentile response time for reads and writes.
- **Leader failover:** time from leader failure until the cluster can commit a new operation.

Record workload, concurrency, hardware, and cluster configuration alongside results so measurements can be reproduced and compared.

