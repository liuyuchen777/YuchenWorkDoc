---
title: Persona-Enhanced Action Prediction Research
description: Led a 4-week research sprint investigating persona inference from behavioral traces for next-action prediction, demonstrating inferred personas outperform self-reported ones with increasing benefit for longer sequences.
year: 2026
quarter: Q1
type: research
---

## Summary

I led a research project (PersonaEnhancedActionPrediction) investigating whether personas inferred from behavioral traces can outperform self-reported personas for next-action prediction in e-commerce. Working with two researchers (Meihong Jia, Xi Chen), we developed a hierarchical temporal modeling approach that separates stable user traits from dynamic states, and validated our hypothesis on the OPeRA dataset using Qwen2.5-7B.

## Context & Problem

Traditional user modeling approaches either ignore persona information or rely on self-reported survey data, which is expensive to collect and often inaccurate for behavioral prediction. The question was: can we infer action-relevant personas purely from behavioral traces, and would these inferred personas be more predictive than ground-truth self-reported ones?

## What I Did

I designed the research direction and led the 4-week sprint. Key innovations:

- **Persona inference without surveys** — discovering user traits directly from action sequences using Claude (AWS Bedrock) for hierarchical inference
- **Hierarchical temporal modeling** — separating stable persona traits from dynamic session states to minimize persona variance
- **Action + rationale prediction** — predicting both WHAT users do and WHY (novel evaluation dimension)
- **4-condition experimental design** — Baseline, Self-reported persona, Refined persona, and Inferred persona

I built the evaluation pipeline (zero-shot + SFT with Bedrock batch inference), managed the multi-researcher workflow, and coordinated the experimental matrix across 100K+ sessions.

## Impact & Results

Validated the core hypothesis: inferred personas from behavioral traces outperform self-reported personas for action prediction, with increasing advantage for longer sequences. Paper and slides available in the package reference docs.
