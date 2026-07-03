---
title: End-to-End Causal Inference Framework for Vendor Sales Impact Estimation
description: Designed and built a DML-based causal inference framework using EconML, spanning feature store construction off raw business tables, estimator experimentation, and SageMaker training. Increased vendor coverage by +1960 bps (NA) and +1570 bps (JP).
time: 2025 Q3-Q4
type: project
---

## Summary

I designed and built an end-to-end causal inference framework for estimating heterogeneous treatment effects on vendor sales impact (PSI/PSL). The framework spans feature store construction from raw business tables, training/validation set preparation, and a modular Double Machine Learning (DML) estimation module built on EconML. Scientists can run different estimators locally for fast experimentation and deploy the same code to SageMaker training pipelines. This cut model iteration from weeks to hours and expanded vendor coverage by +1,960 bps (NA) and +1,570 bps (JP).

## Context & Problem

The vendor Predicted Sales Impact (PSI) / Predicted Sales Lift (PSL) system estimates the causal effect of vendor programs on sales outcomes, guiding retail 1P business role toward high-impact actions. The legacy system (launched 2022) relied on CBA's DML pipeline on EMR through the SPIE team 3P PSI pipeline, creating three limitations:

1. Limited estimator experimentation: The CBA DML pipeline was a black box with fixed model choices. Scientists could not easily swap estimators (LinearDML, CausalForestDML, SparseLinearDML) or tune nuisance model specifications to test how sensitive the treatment effect estimates were.
2. No local iteration loop: Without a way to run estimators locally, the hypothesis-to-result cycle took weeks per experiment. That made it hard to validate identification assumptions or diagnose issues in treatment effect heterogeneity.
3. Stale feature inputs: The architecture could not integrate updated feature stores, so models trained on outdated covariates. This weakened the conditional independence assumption that valid causal identification requires.

## What I Did

### Feature Store Construction & Data Pipeline

I built the feature engineering pipeline from raw business tables, constructing treatment, outcome, and covariate features. I designed the training/validation set preparation pipeline with proper sample splitting to support cross-fitting in the DML framework.

### DML Estimator Module Design

I built a modular estimator framework on the EconML library that:

- **Abstracts the DML workflow**: a common interface for fitting nuisance models (propensity/outcome), estimating CATE, and computing confidence intervals
- **Supports estimator comparison**: scientists can switch between LinearDML, CausalForestDML, SparseLinearDML, and other EconML estimators through configuration, then compare treatment effect estimates under different modeling assumptions
- **Enables local-first experimentation**: the same estimator code runs locally on sample data for quick hypothesis testing, then runs at scale on SageMaker training jobs without changes

### Infrastructure choices for faster science

I chose Native AWS components (SageMaker Processing, Training, batch transform) over the legacy EMR architecture to give science a fast iteration loop: a new estimator hypothesis can be tested locally in minutes and promoted to full-scale training in hours instead of weeks.

## Impact & Results

Launched 6th October 2025 for both JP and NA vendors.

- **Model iteration cycle**: weeks → hours (about 10x more experiments per quarter)
- **NA vendor coverage**: 72.5% → 92.1% (+1,960 bps, +27.0% relative)
- **JP vendor coverage**: 68.6% → 84.3% (+1,570 bps, +22.9% relative)
- **NA GMS coverage**: 50.3% → 84.8% (+3,450 bps, +68.6% relative)
- **JP GMS coverage**: 37.1% → 76.3% (+3,920 bps, +105.7% relative)

The coverage gains came from resolving stale covariates (better conditional independence) and the ability to select more appropriate estimators per program through rapid experimentation.
