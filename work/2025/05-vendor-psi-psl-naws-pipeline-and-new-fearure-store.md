---
title: End-to-End Causal Inference Framework for Vendor Sales Impact Estimation
description: Designed and built a DML-based causal inference framework using EconML — from feature store construction off raw business tables through estimator experimentation to SageMaker training — increasing vendor coverage by +1960 bps (NA) and +1570 bps (JP).
time: 2025 Q3-Q4
type: project
---

## Summary

I designed and built an end-to-end causal inference framework for estimating heterogeneous treatment effects on vendor sales impact (PSI/PSL). The framework spans feature store construction from raw business tables, training/validation set preparation, and a modular Double Machine Learning (DML) estimation module built on EconML that enables rapid local experimentation with different estimators and seamless deployment to SageMaker training pipelines. This reduced model iteration from weeks to hours and expanded vendor coverage by +1,960 bps (NA) and +1,570 bps (JP).

## Context & Problem

The vendor Predicted Sales Impact (PSI) / Predicted Sales Lift (PSL) system estimates the causal effect of vendor programs on sales outcomes, guiding retail 1P business role toward high-impact actions. The legacy system (launched 2022) relied on CBA's DML pipeline on EMR through the SPIE team 3P PSI pipeline, creating three limitations:

1. Limited estimator experimentation: The CBA DML pipeline was a black-box with fixed model choices; scientists could not easily swap estimators (e.g., LinearDML vs. CausalForestDML vs. SparseLinearDML) or tune nuisance model specifications to test sensitivity of treatment effect estimates
2. No local iteration loop: Without the ability to run estimators locally, the hypothesis-to-result cycle took weeks per experiment, severely limiting our ability to validate identification assumptions or diagnose issues in treatment effect heterogeneity
3. Stale feature inputs: The architecture could not integrate updated feature stores, meaning models trained on outdated covariates, weakening the conditional independence assumption required for valid causal identification

## What I Did

### Feature Store Construction & Data Pipeline

I built the feature engineering pipeline from raw business tables, constructing treatment, outcome, and covariate features. I designed the training/validation set preparation pipeline with proper sample splitting to support cross-fitting in the DML framework.

### DML Estimator Module Design

I built a modular estimator framework using EconML library that:

- **Abstracts the DML workflow** — common interface for fitting nuisance models (propensity/outcome), estimating CATE, and computing confidence intervals
- **Supports estimator comparison** — scientists can swap between LinearDML, CausalForestDML, SparseLinearDML, and other EconML estimators through configuration, enabling systematic comparison of treatment effect estimates under different modeling assumptions
- **Enables local-first experimentation** — identical estimator code runs locally on sample data for rapid hypothesis testing, then executes at scale on SageMaker training jobs without modification

### Infrastructure Choices in Service of Science

I chose Native AWS components (SageMaker Processing → Training → batch transform) over the legacy EMR architecture specifically to enable the fast iteration loop science need: a new estimator hypothesis can be tested locally in minutes and promoted to full-scale training in hours, not weeks.

## Impact & Results

Launched 6th October 2025 for both JP and NA vendors.

- **Model iteration cycle**: weeks → hours (enabling 10x more experiments per quarter)
- **NA vendor coverage**: 72.5% → 92.1% (+1,960 bps, +27.0% relative)
- **JP vendor coverage**: 68.6% → 84.3% (+1,570 bps, +22.9% relative)
- **NA GMS coverage**: 50.3% → 84.8% (+3,450 bps, +68.6% relative)
- **JP GMS coverage**: 37.1% → 76.3% (+3,920 bps, +105.7% relative)

The coverage gains came from resolving stale covariates (better conditional independence) and the ability to select more appropriate estimators per program through rapid experimentation.
