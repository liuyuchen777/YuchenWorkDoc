---
title: Refinement Selection Pre-Weblab Evaluation & Quality Monitoring
description: Owned the design and implementation of the refinement selection offline evaluation system. Built the pre-weblab evaluation and automated daily quality monitoring to prevent quality degradation.
time: 2025 Q4 - 2026 Q2
type: project
---

## Summary

I owned the design and implementation of the Refinement Engine offline evaluation system — a comprehensive framework for measuring refinement selection quality across coverage, utility, duplication, and relevance dimensions. By applying statistical methods inspired by weblab metrics deep-dive tool (APT), I built a pre-weblab evaluation pipeline and automated daily quality monitoring that reduced experiment feedback loops from months to hours.

## Context & Problem

In 2024, the Search Engine Technologies (SET) org decided to deprecate the legacy refinement selection system (ARPS) and migrate to a search-engine-backed system, Refinement Engine (RE), to improve the search navigation experience. The refinement selection problem is recommending a set of refinements (search result filters) and associated pickers (filter values) based on customer query intent.

During this migration, a critical gap emerged: there was no comprehensive evaluation system to assess the quality impact of changes before launching a weblab. Historically, we relied solely on weblab (A/B testing) results to validate customer impact, which suffered from three limitations:

1. costly: each weblab required weeks to months of SDE effort for integration and instrumentation;
2. slow: search weblab criteria mandated months-long experiments to reach statistical significance;
3. insensitive: results were reported on business-outcome metrics (revenue, clicks) that are noisy and difficult to attribute to refinement quality changes.

This meant scientists and engineers had no rapid signal on whether a refinement algorithm change was an improvement or regression, creating a bottleneck for iteration.

## What I Did

I proposed and built an offline evaluation system that decouples quality measurement from live experimentation. The system uses a traffic-replay mechanism with feature flags to generate paired result sets (control v.s. treatment) from the same query sample, then applies comparative statistical analysis to quantify the treatment effect.

Metric Design: Collaborating with Senior Applied Scientist, I defined metric families across four dimensions:

1. **Coverage**: measuring the fraction of traffic-weighted queries served with sufficient refinement depth (target: 85%+);
2. **Utility**: capturing value through Active Search Refinement Rate and high-value downstream actions (purchases, Add-to-Cart);
3. **Relevance**: scoring refinement-to-query alignment using LLM-based relevance labels;
4. **Duplication**: detecting semantically overlapping or redundant refinements within a result set, both cross-refinement duplication and picker-level duplication across different refinements.

**Statistical Comparative Analysis.** For each metric, the system computed per-query differences between control and treatment arms (with mean-imputation for queries present in only one arm). Then modeled the distribution of these paired differences using a t-distribution and computed the Probability of Positive Return (PPR). Additionally, the system computed two-sided paired t-test p-values for hypothesis testing and relative lift (ATE / control mean) for effect size. For set-level overlap analysis, the system computed Jaccard similarity and control/treatment-only rates across refinement and picker sets to quantify how much the two arms diverged in their recommendations.

I implemented the evaluation pipeline, includes traffic sampling, traffic replay, single arm metrics computation and comparative metrics analysis components.

**Daily Quality Monitoring.** Beyond pre-weblab evaluation, I extended the system into a continuous quality assurance framework. The upstream data source for refinement selection is owned by Amazon Selection and Catalog Systems (ASCS), and ingested into the search backend without guardrails before. Any upstream data quality regression (e.g. manually delete of multiple refinements) could silently degrade the customer navigation experience. To address this, I built an automated daily monitoring pipeline that runs the evaluation framework against a standardized traffic-weighted query set, computes all metric dimensions, and surfaces regressions through alerting and visualization dashboards. This transforms the evaluation system from a one-off experiment tool into a production guardrail that catches customer experience degradation caused by upstream data issues before they compound.

## Impact & Results

- **Accelerated iteration velocity**: Reduced the feedback loop for refinement algorithm changes from months (weblab-dependent) to hours (offline replay), enabling scientists to validate new selection algorithms and engineers to confidently dial up weblabs with quantitative evidence from evaluation reports.
- **Established pre-weblab sign-off process**: The evaluation system became a standard gating step for the RE US weblab launch (end of 2024) and the 2025 worldwide expansion, providing stakeholders with data-driven confidence before committing to live experimentation.
- **Production quality guardrail**: Daily monitoring pipeline catches upstream data regressions that would otherwise silently degrade customer navigation experience, preventing compounding issues before they surface in business metrics.

## Links

- [Refinement Selection Evaluation System (design doc)](https://quip-amazon.com/lkwRAcueenbm)
- [Refinement Selection Pre-Weblab Evaluation Vision](https://w.amazon.com/bin/view/Search/SST-NLP/DocE/DocumentUnderstanding/Navigation/RefinementSelectionPre-WeblabEvaluationVision)
- [1-Pager on Refinement Engine Evaluation (MBR)](https://w.amazon.com/bin/view/Search/SST-NLP/DocE/DocumentUnderstanding/Navigation/1-PageronRefinementEngineEvaluation/)
- [Offline Evaluation for Refinement Repository](https://quip-amazon.com/Gb3XA8ieNPbr)
- [Design Improvements for Offline Evaluation Automation](https://quip-amazon.com/G7ZMAES1yb4p)
- [Offline Evaluation Wiki](https://w.amazon.com/bin/view/Search/SST-NLP/DocE/DocumentUnderstanding/Navigation/OfflineEvaluation/)
- [Signing-off RE 1st Weblab Evaluation with Replay](https://w.amazon.com/bin/view/Search/SST-NLP/DocE/DocumentUnderstanding/Navigation/Signing-offRefinementEngine1stweblabevaluationwithreplay)
