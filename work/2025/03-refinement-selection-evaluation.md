---
title: Refinement Selection Pre-Weblab Evaluation & Quality Monitoring
description: Owned the design and implementation of the refinement selection offline evaluation system. Built the pre-weblab evaluation and automated daily quality monitoring to prevent quality degradation.
time: 2025 Q4 - 2026 Q2
type: project
org: Amazon > Product Search > Document Understanding
---

## Summary

I owned the design and implementation of the Refinement Engine offline evaluation system, which measures refinement selection quality across coverage, utility, duplication, and relevance. Using statistical methods inspired by the weblab metrics deep-dive tool (APT), I built a pre-weblab evaluation pipeline and automated daily quality monitoring that cut experiment feedback loops from months to hours.

## Context & Problem

In 2024, the Search Engine Technologies (SET) org decided to deprecate the legacy refinement selection system (ARPS) and migrate to a search-engine-backed system, Refinement Engine (RE), to improve the search navigation experience. The refinement selection problem is recommending a set of refinements (search result filters) and associated pickers (filter values) based on customer query intent.

During this migration, a critical gap emerged: there was no comprehensive evaluation system to assess the quality impact of changes before launching a weblab. Historically, we relied solely on weblab (A/B testing) results to validate customer impact, which suffered from three limitations:

1. costly: each weblab required weeks to months of SDE effort for integration and instrumentation;
2. slow: search weblab criteria mandated months-long experiments to reach statistical significance;
3. insensitive: results were reported on business-outcome metrics (revenue, clicks) that are noisy and difficult to attribute to refinement quality changes.

This meant scientists and engineers had no rapid signal on whether a refinement algorithm change was an improvement or regression, creating a bottleneck for iteration.

## What I Did

I proposed and built an offline evaluation system that decouples quality measurement from live experimentation. The system uses a traffic-replay mechanism with feature flags to generate paired result sets (control vs. treatment) from the same query sample, then applies comparative statistical analysis to quantify the treatment effect.

Metric design: working with a Senior Applied Scientist, I defined metric families across four dimensions:

1. **Coverage**: the fraction of traffic-weighted queries served with sufficient refinement depth (target: 85%+);
2. **Utility**: value captured through Active Search Refinement Rate and high-value downstream actions (purchases, Add-to-Cart);
3. **Relevance**: refinement-to-query alignment scored with LLM-based relevance labels;
4. **Duplication**: semantically overlapping or redundant refinements within a result set, covering both cross-refinement duplication and picker-level duplication across different refinements.

**Statistical comparative analysis.** For each metric, the system computed per-query differences between control and treatment arms (with mean-imputation for queries present in only one arm), then modeled the distribution of these paired differences with a t-distribution and computed the Probability of Positive Return (PPR). It also computed two-sided paired t-test p-values for hypothesis testing and relative lift (ATE / control mean) for effect size. For set-level overlap analysis, it computed Jaccard similarity and control/treatment-only rates across refinement and picker sets to quantify how much the two arms diverged in their recommendations.

I implemented the evaluation pipeline, which includes traffic sampling, traffic replay, single-arm metrics computation, and comparative metrics analysis.

**Daily quality monitoring.** I then extended the system into a continuous quality assurance framework. The upstream data source for refinement selection is owned by Amazon Selection and Catalog Systems (ASCS) and was previously ingested into the search backend without guardrails. Any upstream data quality regression (for example, a manual deletion of multiple refinements) could silently degrade the customer navigation experience. To catch this, I built an automated daily monitoring pipeline that runs the evaluation framework against a standardized traffic-weighted query set, computes all metric dimensions, and surfaces regressions through alerting and dashboards. This turns the evaluation system from a one-off experiment tool into a production guardrail that catches customer experience degradation from upstream data issues before it compounds.

## Impact & Results

- **Faster iteration**: The feedback loop for refinement algorithm changes dropped from months (weblab-dependent) to hours (offline replay). Scientists could validate new selection algorithms, and engineers could dial up weblabs backed by quantitative evidence from evaluation reports.
- **Pre-weblab sign-off process**: The evaluation system became a standard gating step for the RE US weblab launch (end of 2024) and the 2025 worldwide expansion, giving stakeholders data-backed confidence before committing to a live experiment.
- **Production quality guardrail**: The daily monitoring pipeline catches upstream data regressions that would otherwise silently degrade the customer navigation experience, before they surface in business metrics.

## Links

- [Refinement Selection Evaluation System (design doc)](https://quip-amazon.com/lkwRAcueenbm)
- [Refinement Selection Pre-Weblab Evaluation Vision](https://w.amazon.com/bin/view/Search/SST-NLP/DocE/DocumentUnderstanding/Navigation/RefinementSelectionPre-WeblabEvaluationVision)
- [1-Pager on Refinement Engine Evaluation (MBR)](https://w.amazon.com/bin/view/Search/SST-NLP/DocE/DocumentUnderstanding/Navigation/1-PageronRefinementEngineEvaluation/)
- [Offline Evaluation for Refinement Repository](https://quip-amazon.com/Gb3XA8ieNPbr)
- [Design Improvements for Offline Evaluation Automation](https://quip-amazon.com/G7ZMAES1yb4p)
- [Offline Evaluation Wiki](https://w.amazon.com/bin/view/Search/SST-NLP/DocE/DocumentUnderstanding/Navigation/OfflineEvaluation/)
- [Signing-off RE 1st Weblab Evaluation with Replay](https://w.amazon.com/bin/view/Search/SST-NLP/DocE/DocumentUnderstanding/Navigation/Signing-offRefinementEngine1stweblabevaluationwithreplay)
