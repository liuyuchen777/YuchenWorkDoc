---
title: Video Search Performance Profiling Workflow
description: Designed, implemented, and productionized an automated performance profiling workflow for video search relevance metrics, supporting LKNN HPO and ranker tuning.
time: 2023 Q3-Q4
type: project
org: Amazon > Product Search > Multi-Language Tokenizer
---

## Summary

I designed, implemented, and productionized an automated performance profiling workflow for video search, enabling continuous relevance metric monitoring and supporting LKNN hyperparameter optimization and ranker tuning.

## Context & Problem

Before this workflow, the Lucene team had to manually replay queries and pass the matchset to the DocE team. Applied Scientists would then compute relevance metrics and paste the results into Quip for visibility. This manual process was slow, error-prone, and couldn't support the continuous evaluation needed during the video search development cycle.

## What I Did

I designed and implemented a performance profiling workflow built on top of the DocE team's video search metrics calculation workflow. The core functionality replays a set of queries against the search backend, calculates relevance metrics, and publishes results to a wiki dashboard. I set up periodic triggers to execute the entire process automatically.

The workflow also supports LKNN Hyper-Parameter Optimization (HPO) and ranker tuning processes.

To ensure long-term stability, I productionized both the workflow and DocEVideoSearchExperiment pipeline. I set up a separate production account with limited permission roles to enable external teams (LKNN, VSAR) to leverage the profiling tools independently.

## Impact & Results

Eliminated manual query replay and metric computation. Enabled continuous monitoring of relevance metrics during the video search development cycle. Successfully onboarded external teams (LKNN, VSAR) to use the workflow autonomously.

## Links

- [DU for Video Search](https://w.amazon.com/bin/view/Search/SST-NLP/DocE/DocumentUnderstanding/DUForVideoSearch/)
- [Quality Metrics for Video Search Backend](https://w.amazon.com/bin/view/Search/SST-NLP/DocE/DocumentUnderstanding/QualityMetricsforVideoSearchBackend84)
- [Video Search Architecture Design](https://quip-amazon.com/hTc4AZhwz5i0)
