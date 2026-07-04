---
title: JCITechChampSolutions EDA Solutions for Andes from Native AWS
description: Designed and built a fully managed CDK solution that provisions Andes data access infrastructure (Redshift Serverless, Glue ETL, EMR Serverless) into customer AWS accounts via pipeline deployment. 6 teams onboarded, reducing setup from weeks to 1 day.
time: 2026 Q1
type: project
org: Amazon > Japan Consumer Innovation > Retail Science
---

## Summary

I designed and developed JCITechChampSolutions EDA Solutions, a fully managed, pipeline-deployed CDK solution that provisions Andes data access infrastructure into customer AWS accounts. It removed weeks of manual setup per team and brought onboarding down from weeks to 1 day. Eight teams are already live (MCP, Vendor PSI, MOST, Promo Pro, VAMOS-BI, Occam, Claude Code, UX Evaluation), using it for both exploratory analysis and production scheduled data pipelines.

## Context & Problem

Teams needing Andes data access faced weeks of setup: manual AWS console clicks, IAM role configuration, Spark connector integration, and Lake Formation permission grants, all error-prone and team-specific. Each team rebuilt the same infrastructure from scratch. Security posture varied by team and config drifted over time. Spark connector updates required manual work across all accounts.

## What I Did

I designed and built a CDK solution deployed via a centralized pipeline (Pipeline ID: 9247278) that provisions a complete Andes access stack in one onboarding CR:

- **Redshift Serverless (FGAC)**: Fine-Grained Access Control for secure ad-hoc SQL queries
- **AWS Glue ETL (Glue 5.0)**: Interactive Sessions and scheduled jobs with the Andes Spark connector pre-configured
- **EMR Serverless (EMR 7.8.0)**: On-demand Spark compute with a custom image containing the Andes Spark bundle
- **EMR Studio**: Notebook-based exploration for data scientists
- **End-to-end IAM and Lake Formation setup**: Pre-wired roles, policies, and Glue Catalog connections

The pipeline auto-deploys upgrades (Spark versions, security patches, connector updates) to all customer accounts centrally, ensuring consistent infrastructure and security posture without per-team maintenance.

## Impact & Results

- Onboarding time: weeks → 1 day (single CR to first Andes query)
- 8 teams onboarded and live: JP Retail MCP, Vendor PSI/PSL, MOST, Promo Pro, VAMOS-BI, Occam, TEDS Claude Code, UX Evaluation
- Zero infrastructure maintenance for customers: the pipeline auto-deploys all upgrades
- Consistent security: FGAC, Lake Formation, and least-privilege IAM enforced centrally, with no per-team drift
- Cost efficiency: serverless compute means teams pay only for what they query
- Teams like Vendor PSI, Promo Pro, and JP Retail MCP use it for production scheduled data pipelines

## Links

- [Design doc (HLD)](https://quip-amazon.com/qT75AZ2m7z50/HLD-JCI-TEDS-EDA-Solution)
- [Design feedback](https://quip-amazon.com/HMaCA4ueCeGE/Design-Feedback-for-HLD-JCI-TEDS-EDA-Solution)
- [Onboarding wiki](https://w.amazon.com/bin/view/JCI/JCI-TEDS/Products/JCITechChampSolutions)
- [Pipeline (onboarded projects)](https://pipelines.amazon.dev/pipelines-wip/JCITechChampSolutions)
