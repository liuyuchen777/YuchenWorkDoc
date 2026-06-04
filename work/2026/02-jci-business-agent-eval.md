---
title: JCI Business Agent Evaluation Framework
description: Designed and built JCIBusinessAgentEval — a 4-level automated evaluation framework replacing manual testing for the MCP agent, being extended as org-wide AI agent quality infrastructure.
year: 2026
quarter: Q1
type: project
---

## Summary

I designed and built JCIBusinessAgentEval — a TypeScript evaluation framework for systematically testing AI agent performance against the JCI Science Model MCP, replacing manual 2-3 query visual inspection with reproducible multi-level automated evaluation.

## Context & Problem

Manual testing of the MCP agent (2-3 fixed queries with visual inspection) didn't scale. As the platform grew to support 115+ metrics, multiple data sources, and complex multi-step workflows, there was no systematic way to measure agent quality, catch regressions, or validate new features before deployment.

## What I Did

I designed a 4-level evaluation architecture:

- **L0**: Tool call validation (did the agent call the right tools?)
- **L1**: Parameter correctness (are SQL queries well-formed, correct columns?)
- **L2**: Result quality (do outputs match expected patterns/values?)
- **L3**: Analysis quality (LLM-as-judge using Bedrock Claude Sonnet to evaluate business insight quality)

Implemented L0-L2 deterministic graders with 51 unit tests across 4 scenarios. Built CLI interface with JSON output and readable raw_output format. Designed tool parameter capture for grading SQL generation quality.

The framework is being positioned as general-purpose UX evaluation infrastructure (VAMOS team collaboration with omadoka@), extensible beyond SQL/tool-call grading to support UXD rubric evaluation and automated UAT.

## Impact & Results

Replaced ad-hoc manual testing with reproducible automated evaluation. Framework catches SQL errors, incorrect metric formulas, and tool selection regressions before deployment. Being extended as org-wide evaluation infrastructure for AI agent quality.

## Links

- [Demo: Eval Framework](https://jci-science-model-mcp-demo.beta.harmony.a2z.com/hackathon-eval-framework)
- [Design Doc: Evaluation Framework](https://code.amazon.com/packages/JCIScienceModelMCPCDK/trees/mainline/--/doc/05_evaluation_framework)
