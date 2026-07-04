---
title: Pre-Weblab Evaluation for Customer Review Aspect Lexical Weblab
description: Designed and executed pre-weblab evaluation for the first DU weblab, scaling to hundreds of millions of query-ASINs. Led to +$253MM OPS, -2.83 bps IRR.
time: 2024 Q1-Q2
type: project
org: Amazon > Product Search > Document Understanding
---

## Summary

I designed and executed the pre-weblab evaluation process for the first DU weblab on customer review aspect keyphrase lexical matching, scaling evaluation to hundreds of millions of query-ASINs. The evaluation informed the dial-up decision, leading to a completed QBR goal 4 months early with significant impact (OPS: +$253MM, IRR: -2.83 bps).

## Context & Problem

The team needed a rigorous pre-weblab evaluation process for the customer review aspect keyphrase lexical matching feature. Existing tools (MoE/MetricCalculationStateMachine and Otto Weblab TestDrive) each had strengths and limitations, and there was no established process for combining them effectively for DU weblabs.

## What I Did

I compared and summarized the strengths and limitations of existing offline evaluation tools. I determined that Otto Weblab was well-suited for calculating top result IRR as a weblab relevance guardrail, while MoE excelled at calculating big matchset metrics for recall optimization (SRR, large matchset IRR at 2K+, IRR Ideal).

I developed a plan to leverage both tools during the pre-weblab stage, then carried out the evaluation according to the designed plan. The evaluation results showed that while T2 saw IRR improvement, T1 experienced a decrease. However, T1 in the majority of marketplaces still maintained the IRR guardrail. Both treatments in English marketplaces displayed increasing matchset size and better large matchset IRR and Ideal IRR, indicating improved recall and potential OPS win.

Based on these results, we made the decision to dial up.

## Impact & Results

OPS: +$253MM annualized. IRR: -2.83 bps improvement. Completed QBR goal 4 months ahead of schedule. Established a reusable pre-weblab evaluation methodology for future DU weblabs.

## Links

- [Aspects Lexical Matching Pre-weblab Experiment Results](https://w.amazon.com/bin/view/Search/SST-NLP/DocE/DocumentUnderstanding/AspectsLexicalMatchingPre-weblabexperimentresults)
- [Weblab Design: ASIN Aspects Data Indexing for Lexical Matching](https://w.amazon.com/bin/view/Search/SST-NLP/DocE/DocumentUnderstanding/Weblabdesignasinaspectsdataindexingforlexicalmatching)
- [Searchable Customer Reviews with Aspects](https://w.amazon.com/bin/view/Search/SST-NLP/DocE/SearchableCustomerReviews/)
