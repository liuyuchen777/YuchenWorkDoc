---
title: JCI Science Model MCP Platform
description: Architected and built the full MCP platform — AI-powered business intelligence enabling vendor managers to query 1P retail data through natural language, covering 115+ metrics.
year: 2026
quarter: Q1
type: project
---

## Summary

I designed and built the JCI Science Model MCP platform — an AI-powered business intelligence system that enables vendor managers to query 1P retail business data and science model outputs through natural language interaction via Model Context Protocol (MCP) tools.

## Context & Problem

Vendor managers in JCI Japan marketplace needed to analyze complex retail metrics (revenue, traffic, conversion, pricing, inventory, promotions) but relied on manual spreadsheet analysis or waiting for BIE support. There was no self-service tool that could translate business questions into data queries while applying domain-specific business logic.

## What I Did

I architected and implemented the full MCP platform including:

- **Online query path**: Natural language to Athena SQL translation with domain-aware skill warehouse
- **Offline data path**: ETL pipelines for vendor business metrics, ASIN content quality, promotion/deal data
- **Skill warehouse**: Modular domain skills (vendor business analysis, event performance, MBR generation, metric definitions) that guide AI agents through complex multi-step workflows
- **Security model**: 3-layer authentication, SQL injection prevention, team-based ACL
- **Observability**: Dual-dimension CloudWatch metrics, structured logging, caller attribution
- **Query optimization**: Inline subquery patterns for Athena constraints (no CTE support)
- **Evaluation framework**: JCIBusinessAgentEval for systematic testing (see separate entry)

I also built interactive React-based demo presentations for both product leadership (April 2) and engineering audiences (April 13 SWE deep-dive), covering MCP architecture, scaffolding engineering philosophy, and open problems.

Supported what-if modeling tool development with Vendor Growth Team (bilguunn@) and planned future data sources (COOP agreements, po_items_beta).

## Impact & Results

Platform serves JCI Japan marketplace (Marketplace ID 6) vendor managers with self-service analytics covering 115+ metrics across vendor business, ASIN content quality, and promotion analysis. Enables on-demand Monthly Business Reviews, event performance analysis (MDE, Prime Day, BFW), and actionable PSL recommendations with predicted GMS uplift.

## Links

- [Wiki: JCI Science Model MCP](https://w.amazon.com/bin/view/JCI/JCI-TEDS/Products/JCIScienceModelMCP/)
- [Slack: #jp-retail-mcp-interest](https://amzn-wwc.slack.com/archives/C09UW14JACT) (250 users)
- [Exract 2026 May status update](https://amzn-wwc.slack.com/archives/C09UW14JACT/p1780459890440139)
