# Limit Order Book (C++)

A limit order book implementation in C++, built as an iterative study of exchange data structures and the latency characteristics that matter when feeding one.

## Iteration Plan

This project is explicitly versioned. Each stage is a measurement baseline for the next.

**v1 — In progress.** `std::map<Price, Level>` for the price ladder. Goal: correctness and clarity. Establishes the order/event spec, the replay harness, and the regression test suite that v2 and v3 inherit.

**v2 — Planned.** Contiguous price-level array for O(1) best bid/ask and cache-friendly iteration across the top-of-book. Benchmarks against v1 on replayed market data — report mean and tail latencies, not just throughput.

**v3 — Planned.** Lock-free single-producer single-consumer (SPSC) ingestion queue separating the parse/network thread from the book-update thread. Measures end-to-end latency distribution from wire to book mutation under contended load.

## Why this structure

The v1 `std::map` implementation is the baseline, not the product. Publishing the iteration plan up front prevents the naive read ("it's just a wrapper around std::map") and makes the real intent — measured progression across three data-structure / concurrency regimes — visible from the README.

## Status

v1 scaffolding in progress. README published ahead of code to lock the design intent and the evaluation plan.
