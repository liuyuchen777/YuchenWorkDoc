---
title: Refinement Engine US Launch
description: Contributed to the US launch of Refinement Engine, a Lucene-based search backend replacing ARPS for refinement selection. Delivered +$61MM GCCP, +8MM Paid Units.
time: 2025 Q1
type: project
org: Amazon > Product Search > Document Understanding
---

## Summary

I contributed to the Refinement Engine (RE) US launch, a new Lucene-based search backend architecture for navigational refinement selection that replaced the legacy ARPS system. I was involved in feature building, search metadata configuration, and pre-weblab evaluation that validated the launch-on-flat criteria.

## Context & Problem

The Refinement Engine treats identifying useful refinements as an information retrieval problem: given query context, it selects relevant refinements from its index, which decouples the data source from the selection model. The US launch (weblab SEARCH_SPT_1043600) required validating that the new architecture met launch criteria across latency, business metrics, and relevance guardrails before replacing ARPS on Loom traffic.

## What I Did

I contributed to feature building and feature configuration at the search metadata level. I conducted pre-weblab evaluations for the US launch weblab (SEARCH_SPT_1043600) and related experiments, validating metrics through the development iteration cycle. I owned the weblab MCM and launch MCM for the US launch, managing the operational readiness and change management process. I also supported the non-Loom traffic expansion (SEARCH_SPT_1179751).

## Impact & Results

RE US launched on 2/24/2025 (4 days ahead of target), powering ~72% of US navigation traffic. Weblab delivered +$61MM GCCP (Prob>0=0.78) and +8MM Paid Units (Prob>0=0.89). This completed the first milestone of the 2025 QBR goal to launch Refinement Engine worldwide.

## Links

- [Refinement Engine US Launch Wiki](https://w.amazon.com/bin/view/Search/SST-NLP/DocE/DocumentUnderstanding/Navigation/RefinementEngineLaunchUS/)
- [SEARCH_SPT_1043600 Pre-weblab Evaluation](https://quip-amazon.com/bgINAMSrtOHA)
- [Signing-off RE US Launch with Replay Evaluation](https://quip-amazon.com/qpMLAhQ4bjBg)
- [Configuring the First RE Weblab](https://quip-amazon.com/b8EoAhA7stUw)
- [RE Non-Loom Traffic Launch](https://w.amazon.com/bin/view/Search/SST-NLP/DocE/DocumentUnderstanding/Navigation/RefinementEngineLaunchForNonLoomTraffic/)
- [Weblab Bar Raiser: SEARCH_SPT_1043600](https://w.amazon.com/bin/view/Weblab/BarRaiser/SEARCH_SPT_1043600)
- [Weblab Bar Raiser: SEARCH_SPT_1179751](https://w.amazon.com/bin/view/Weblab/BarRaiser/SEARCH_SPT_1179751)
