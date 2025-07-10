---
title: "07-memory"
date: "2025-07-08"
author: "KiloCode Bot"
tags: []
type: "always_apply"
description: "Provides guidance on writing memory-efficient Python 3.13 so that AI-generated code scales well in production."
---
<memory-efficiency>
<title>Memory-Efficient Python 3.13</title>
<overview>Provide guidance on writing memory-efficient Python 3.13 so that AI-generated code scales well in production.</overview>
<rules>
    - `Data structures`: Choose the smallest suitable collection (array, deque, bisect) before list.
    - `Streaming`: Process large files/streams lazily (yield from, iter_chunks); avoid loading all into memory.
    - `Slots`: Use data classes with slots=True or regular classes with __slots__ to reduce per-instance overhead.
    - `Immutable over mutable`: Prefer tuples, types.MappingProxyType, and frozen dataclasses for shared data.
    - `Memory profiling`: Use memory-profiler in CI for large modules; fail if regression >5%.
    - `Garbage collection`: Explicitly break reference cycles; use contextlib.ExitStack for many contexts.
    - `Vectorization`: Use numpy or pyarrow for numeric workloads; avoid Python loops.
    - `Cache wisely`: Use functools.cache/lru_cache(maxsize=…) with eviction strategy; document cache lifetime.
    - `Chunked concurrency`: For async generators, limit concurrency via asyncio.Semaphore.
    - `Monitor`: Emit Prometheus metrics for RSS, heap usage; set alerts at 75% of container limit.
</rules>
</memory-efficiency>
