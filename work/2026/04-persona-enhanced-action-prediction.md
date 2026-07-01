---
title: Persona-Enhanced Action Prediction Research
description: Participated in a research project for persona inference from behavioral traces for next-action prediction, demonstrating inferred personas outperform self-reported ones with increasing benefit for longer sequences.
time: 2026 Q1
type: research
---

## Summary

I participated in the research project PersonaEnhancedActionPrediction with two Applied Scientists (Meihong Jia, Xi Chen), investigating whether personas inferred from behavioral traces can outperform self-reported personas for next-action prediction in e-commerce. We developed a hierarchical temporal modeling approach that separates stable user traits from dynamic states, and validated our hypothesis on the OPeRA dataset using few-shot prompting with Claude (AWS Bedrock).

## Context & Problem

Traditional user modeling approaches either ignore persona information or rely on self-reported survey data, which is expensive to collect and often inaccurate for behavioral prediction. The question was: can we infer action-relevant personas purely from behavioral traces, and would these inferred personas be more predictive than ground-truth self-reported ones?

## What I Did

I contributed to the research direction and participated in the 4-week sprint. Key innovations:

- **Persona inference without surveys** — discovering user traits directly from action sequences using Claude (AWS Bedrock) for hierarchical inference
- **Hierarchical temporal modeling** — separating stable persona traits from dynamic session states to minimize persona variance
- **Action + rationale prediction** — predicting both WHAT users do and WHY (novel evaluation dimension)
- **4-condition experimental design** — Baseline, Self-reported persona, Refined persona, and Inferred persona

I built the evaluation pipeline (few-shot prompting with Bedrock batch inference), contributed to the multi-researcher workflow, and helped coordinate the experimental matrix across 100K+ sessions.

## Impact & Results

Validated the core hypothesis: inferred personas from behavioral traces outperform self-reported personas for action prediction, with increasing advantage for longer sequences. Paper and slides available in the package reference docs.
