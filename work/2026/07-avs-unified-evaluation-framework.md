---
title: User Journey Dataset & UX Evaluation
description: Designing and building a unified evaluation infrastructure connecting all internal tooling applications to a shared user data mart, enabling continuous measurement and a closed-loop product improvement flywheel.
time: 2026 Q2
type: project
---

## Summary

I am designing and building a unified evaluation framework for AVS internal tooling — a 3-layer architecture that connects all user-facing applications (VAMOS, JP Retail MCP, DataQuest MCP, Paid Service, Catalyst, Jellyfish) to a shared User Data Mart, enabling cross-app user journey analysis and a closed-loop product improvement flywheel.

## Context & Problem

Multiple internal tools serve VM/BS and Vendor users, but each application tracks usage in isolation — clickstream logs, MCP invocation logs, and app-specific events live in separate silos. There is no unified view of user behavior across tools, making it impossible to answer questions like "which workflows span multiple tools?" or "where do users drop off across the tooling ecosystem?" Without this, product improvement decisions are made per-app without cross-tool context.

## What I Did

- Authored the 3-layer evaluation architecture design (Layer 1: Applications & Signal Collection → Layer 2: User Data Mart → Layer 3: Downstream Consumers & Insights)
- Created the UXEvaluationCDK package and pipeline (UXEvaluation, pipeline ID 9688303) via BuilderHub
- Defined the signal flow: each L1 app emits structured logs → L2 joins by user identity (VM/BS or Vendor) → L3 consumes purpose-built views for dashboards, UX evaluation, and recommendations

## Impact & Results

Work in progress — architecture defined, infrastructure scaffolded. Target consumers include VAMOS Adoption Dashboard, MCP UX Evaluation, workflow extraction, and user-data-driven recommendations.

## Links

- [Architecture Doc](https://code.amazon.com/packages/UXEvaluationCDK/blobs/mainline/--/doc/00_evaluation_landscape/00_overall_architecture.md)
- [Code: UXEvaluationCDK](https://code.amazon.com/packages/UXEvaluationCDK)
