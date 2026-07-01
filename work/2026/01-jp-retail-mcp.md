---
title: JCI Science Model MCP Platform
description: Architected and built the full MCP platform — AI-powered business intelligence enabling vendor managers to query 1P retail data through natural language, covering 115+ metrics.
time: 2026 Q1
type: project
---

## Summary

I designed, built, and operate the JP Retail MCP platform — an AI-powered business intelligence system serving 301 active users (as of May 2026) across 6+ departments. The platform enables vendor managers and brand specialists to query 1P retail data, knowledge, workflow and science model outputs through natural language, replacing manual spreadsheet analysis with self-service analytics.

## Context & Problem

Vendor managers in Japan marketplace needed to analyze complex retail metrics (revenue, traffic, conversion, pricing, inventory, promotions) but relied on manual spreadsheet analysis or waiting for BIE support. There was no self-service tool that could translate business questions into data queries while applying domain-specific business logic. Additionally, multiple teams (Catalyst, ProServe, VAMOS, Jellyfish) each had their own data needs with no unified infrastructure to serve them.

## What I Did

I architected and implemented the full MCP platform end-to-end:

- **Online query path**: Natural language to Athena SQL translation with domain-aware skill warehouse
- **Offline data path**: ETL pipelines for vendor business metrics, ASIN content quality, promotion/deal data, sponsored ads, search keywords, CJA, and more
- **Skill warehouse**: Modular domain skills (vendor business analysis, event performance, MBR generation, metric definitions, proserve, sponsored ads analysis) that guide AI agents through complex multi-step workflows
- **Security model**: 3-layer authentication, SQL injection prevention (migrated from regex to sqlglot AST parsing), team-based ACL, IAM-authenticated MCP Gateway for cross-account agent access
- **Observability**: Dual-dimension CloudWatch metrics, structured logging, caller attribution, user access logging with User-Agent extraction and session tracking
- **Tools**: Explain Metric (Beta) for metric lineage, Context Drift Detector for auto-syncing agent context against table metadata, Daily Feedback Digest

**Evaluation framework**: JCIBusinessAgentEval for systematic testing (see separate entry)

## Impact & Results

**May 2026 metrics (latest monthly flash)**:

- 301 unique active users (+51% MoM), 165 new users acquired in May
- 24K total invocations (+81% MoM), 19K Athena queries, 530 TB data scanned
- 62 power users (100+ calls/month, up from 28)
- 3,000 sessions (+119% MoM)
- Error rate reduced to 9.0% (from 10.2%)
- p50 latency: 6.9s, 75.3% of queries complete within 5s

**Platform coverage**: metrics across vendor business, ASIN content quality, promotion analysis, sponsored ads, search keywords, and CJA funnel data

**Cross-team adoption**: VAMOS, Catalyst, PromoPro, AMEA, and ProServe consuming via IAM gateway; Aki/Kiro 14.2%, QuickSuite 11.8%, Claude Code 4.4% of client mix

**Organizational recognition**: Analyticon 2026 proposal submitted, adopted into JCI TEDS 2026 OP1

## Links

- [Wiki: JP Retail MCP](https://w.amazon.com/bin/view/JCI/JCI-TEDS/Products/JCIScienceModelMCP/)
- [Slack: #jp-retail-mcp-interest](https://amzn-wwc.slack.com/archives/C09UW14JACT) (250 users)
- [May 2026 Monthly Flash (Slack)](https://amzn-wwc.slack.com/archives/C09UW14JACT/p1780459890440139)
- [Requirements Tracker](https://code.amazon.com/packages/JCIScienceModelMCPCDK/blobs/mainline/--/doc/00_product_management/00_requirements_tracker.md)
- [Stakeholder Directory](https://code.amazon.com/packages/JCIScienceModelMCPCDK/blobs/mainline/--/doc/00_product_management/01_stakeholder_directory.md)
