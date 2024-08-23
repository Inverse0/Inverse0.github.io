---
title: "CAVE: Concurrency-Aware Graph Processing on SSDs"
collection: publications
category: conferences
permalink: /publication/2024-02-17-paper-title-number-4
excerpt: # 'This paper is about fixing template issue #693.'
date: 2024-05-30
venue: 'SIGMOD 2024'
paperurl: 'https://dl.acm.org/doi/pdf/10.1145/3654928'
citation: # 'Your Name, You. (2024). &quot;Paper Title Number 3.&quot; <i>GitHub Journal of Bugs</i>. 1(3).'
---

Large-scale graph analytics has become increasingly common in areas like social networks, physical sciences, transportation networks, and recommendation systems. Since many such practical graphs do not fit in main memory, graph analytics performance depends on efficiently utilizing underlying storage devices. These out-of-core graph processing systems employ sharding and sub-graph partitioning to optimize for storage while relying on efficient sequential access of traditional hard disks. However, today's storage is increasingly based on solid-state drives (SSDs) that exhibit high internal parallelism and efficient random accesses. Yet, state-of-the-art graph processing systems do not explicitly exploit those properties, resulting in subpar performance.
In this paper, we develop CAVE, the first graph processing engine that optimally exploits underlying SSD-based storage by harnessing the available storage device parallelism via carefully selecting which I/Os to graph data can be issued concurrently. Thus, CAVE traverses multiple paths and processes multiple nodes and edges concurrently, achieving parallelization at a granular level. We identify two key ways to parallelize graph traversal algorithms based on the graph structure and algorithm: intra-subgraph and inter-subgraph parallelization. The first identifies subgraphs that contain vertices that can be accessed in parallel, while the latter identifies subgraphs that can be processed in their entirety in parallel. To showcase the benefit of our approach, we build within CAVE parallelized versions of five popular graph algorithms (Breadth-First Search, Depth-First Search, Weakly Connected Components, PageRank, Random Walk) that exploit the full bandwidth of the underlying device. CAVE uses a blocked file format based on adjacency lists and employs a concurrent cache pool that is essential to the parallelization of graph algorithms. By experimenting with different types of graphs on three SSD devices, we demonstrate that CAVE utilizes the available parallelism, and scales to diverse real-world graph datasets. CAVE achieves up to one order of magnitude speedup compared to the popular out-of-core systems Mosaic and GridGraph, and up to three orders of magnitude speedup in runtime compared to GraphChi.
