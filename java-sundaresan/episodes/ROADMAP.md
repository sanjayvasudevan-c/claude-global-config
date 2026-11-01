# Episode chain

Dr. Sparks is building **H.E.LIOS** in the forest. Each episode he adds one
part — and that part breaks in a way that forces the next part.

The chain is the point. Episode N ends on the failure Episode N+1 solves, so
anyone who finishes one video has a concrete reason to start the next.

| # | Machine | Concept | Ends broken by |
|---|---|---|---|
| 1 | **The Splitter** — a log splitter fed by a chute | Queues, service time, throughput vs latency | The pile grows forever; he gates the chute — where do refused logs go? |
| 2 | **The Gate** | Backpressure, shedding load | Everything he turns away comes straight back |
| 3 | **The Stampede** | Retry storms, backoff, jitter | He adds more splitters |
| 4 | **The Second Splitter** | Parallelism, horizontal scaling | They both reach for the same sharpening stone |
| 5 | **The Sharpening Stone** | Contention, shared resources, locks | Both wait on each other — nothing moves |
| 6 | **The Deadlock** | Deadlock, ordering, timeouts | He starts keeping split logs in a bin to avoid re-splitting |
| 7 | **The Bin** | Caching | The bin holds logs that rotted weeks ago |
| 8 | **The Rot** | Cache invalidation, TTL, write-through | Every log in the bin expires at the same moment |
| 9 | **The Empty Bin** | Thundering herd, stampede protection | One bin can't hold the whole forest |
| 10 | **The Split Yard** | Sharding, partitioning | Every log is oak — one shard takes all the load |

Episode 11 onward: hot partitions → replication → replication lag →
consistency. Each still one machine, still one break.

## Choosing later episodes
A topic earns a slot only if it has a **physical failure you can draw**. If the
failure can't be shown as an object breaking, it isn't an episode yet — find a
better machine or drop it.
