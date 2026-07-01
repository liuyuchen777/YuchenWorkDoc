---
title: AI Agent Evaluation Framework for Business Analysis Agent
description: Designed a multi-level agent evaluation framework adopting Anthropic's eval methodology — combining deterministic graders with LLM-as-judge to systematically measure agent quality, catch regressions, and validate new capabilities for JP Retail MCP.
time: 2026Q1 -
type: project
---

## Summary

I designed and built an automated evaluation framework for systematically measuring AI agent performance on business analysis tasks. Adopting methodology from Anthropic's agent evaluation research, the framework combines deterministic code-based graders (tool call validation, parameter correctness, result verification) with model-based LLM-as-judge assessment for open-ended analysis quality. The project won "Most Innovative Use of AI" and "Most Feasible and Production Ready" at Japan Store Hackathon, and now serves as the quality guardrail enabling rapid, regression-free iteration on JP Retail MCP capabilities.

## Context & Problem

As the JP Retail MCP platform grew to support 115+ metrics, multiple data sources, and complex multi-step agentic workflows, quality assurance relied on manual inspection of 2-3 fixed queries — a methodology that fundamentally cannot scale to validate non-deterministic agent behavior. Key scientific challenges:

1. **Non-determinism**: Agents take different valid paths to the same answer; evaluating correctness requires grading *outcomes*, not rigid step sequences
2. **Multi-dimensional quality**: A single query exercises tool selection, SQL generation, data interpretation, and business insight synthesis — each requiring a different grading methodology
3. **Capability vs. regression tension**: The system needed to simultaneously measure what the agent *can't yet do* (capability frontier) and protect what it *already does well* (regression detection)

## What I Did

### Evaluation Methodology Design

Drawing on Anthropic's framework for demystifying agent evals, I designed a layered evaluation architecture that applies the right grading methodology at each level of abstraction:

- **L0 — Tool Call Validation** (code-based deterministic grader): Verifies the agent invokes correct tools in valid sequences. Grades *outcome* (correct tool was called) rather than *process* (exact ordering), following the principle that agents frequently find valid unanticipated approaches.
- **L1 — Parameter Correctness** (code-based deterministic grader): Validates SQL well-formedness, correct column/table references, and metric formula accuracy. Uses static analysis patterns — fast, cheap, and catches clear regressions with zero ambiguity.
- **L2 — Result Quality** (code-based with partial credit): Assesses whether outputs match expected patterns and value ranges. Implements partial credit scoring — an agent that retrieves 3 of 4 required data points scores higher than one that fails entirely, providing gradient signal for improvement.
- **L3 — Analysis Quality** (model-based LLM-as-judge): Uses Bedrock Claude Sonnet with isolated rubric dimensions to evaluate business insight quality, relevance, and actionability. Each dimension is judged independently to avoid correlated scoring errors.

### Eval-Driven Development Process

I structured the framework around the capability-to-regression lifecycle: new use cases start as capability evals (expected low pass rate, representing the improvement frontier), and graduate into the regression suite once they consistently pass. This gives the team a clear signal — when regression evals drop, something broke; when capability evals plateau, we need new approaches.

Each test case is designed so two domain experts would independently reach the same pass/fail verdict, with reference solutions and unambiguous success criteria.

### Guardrail for Rapid Iteration

The framework now runs as part of JP Retail MCP's development cycle: before any new capability ships, it must pass existing regression evals (protecting old use cases) and demonstrate improvement on capability evals (validating the new feature works). This enables the team to iterate quickly with confidence — new MCP tools and metrics can be added without fear of silent quality degradation.

## Impact & Results

- **Japan Store Hackathon**: Won "Most Innovative Use of AI" and "Most Feasible and Production Ready" awards
- **Adopted as development guardrail**: Now the standard quality gate for all JP Retail MCP feature releases
- **Regression detection**: Catches SQL errors, incorrect metric formulas, tool selection regressions, and analysis quality degradation before deployment
- **Iteration velocity**: Enables rapid addition of new use cases with automated validation that old capabilities are preserved
- **Platform growth with quality maintained**: The eval framework enabled confident scaling — May 2026 saw 300 unique users (+58% MoM from 190 in April), 2,992 sessions (+134% MoM), and 23,681 tool invocations (+93% MoM), with weekly active users growing from 65 to 186 through the month. This growth was only possible because the eval guardrails ensured each new capability shipped without degrading existing ones

## Links

- [Demo: Eval Framework](https://jci-science-model-mcp-demo.beta.harmony.a2z.com/hackathon-eval-framework)
- [Design Doc: Evaluation Framework](https://code.amazon.com/packages/JCIScienceModelMCPCDK/trees/mainline/--/doc/05_evaluation_framework)
- [Reference: Anthropic — Demystifying Evals for AI Agents](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents)
