---
title: User Journey Dataset & UX Evaluation
description: Designing and building a unified evaluation infrastructure connecting all internal tooling applications to a shared user data mart, enabling continuous measurement and a closed-loop product improvement flywheel.
time: 2026 Q2
type: project
org: Amazon > Japan Consumer Innovation > Retail Science
---

## Summary

I partnered with UX team designed and built a unified user experience evaluation framework for Amazon Vendor Service (AVS) internal and external tooling. It enables cross-app user journey analysis and a closed-loop product improvement flywheel.

## Context & Problem

There're multiple internal tools serve Vendor Manager (VM) / Brand Specialist (BS) in internal and Vendor users from external, but each application tracks usage in isolation manner. Clickstream logs, MCP invocation logs, and app-specific events live in silos. There is no unified view of user behavior across tools, so we cannot answer questions like "which workflows span multiple tools?" or "where do users drop off across the tooling ecosystem?" Without it, product improvement decisions get made per-app with no cross-tool context.

## What I Did

- Authored the 3-layer evaluation architecture design (Layer 1: Applications & Signal Collection → Layer 2: User Data Mart → Layer 3: Downstream Consumers & Insights)
- Created the UXEvaluationCDK package and pipeline (UXEvaluation, pipeline ID 9688303) via BuilderHub
- Defined the signal flow: each L1 app emits structured logs → L2 joins by user identity (VM/BS or Vendor) → L3 consumes purpose-built views for dashboards, UX evaluation, and recommendations

## Impact & Results

Work in progress. The architecture is defined and the infrastructure is scaffolded. Target consumers include the VAMOS Adoption Dashboard, MCP UX Evaluation, workflow extraction, and user-data-driven recommendations.

## Links

- [Architecture Doc](https://code.amazon.com/packages/UXEvaluationCDK/blobs/mainline/--/doc/00_evaluation_landscape/00_overall_architecture.md)
- [Code: UXEvaluationCDK](https://code.amazon.com/packages/UXEvaluationCDK)
