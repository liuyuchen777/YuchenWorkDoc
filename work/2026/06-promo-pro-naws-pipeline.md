---
title: Native AWS Promo Pro Pipeline
description: Helped build the Native AWS pipeline for Promo Pro, enabling scheduled data processing on NAWS infrastructure.
year: 2026
quarter: Q1
type: project
---

## Summary

I built the pipeline infrastructure for PromoProETL — a Native AWS Step Functions-orchestrated Glue ETL pipeline that processes promotion benchmarking data (Customer Acquisition Cost, conversion, OPS metrics) and publishes results to S3 and Andes. My contributions focused on automation, observability, and developer experience for the CDK infrastructure package.

## Context & Problem

The Promo Pro team needed a production-grade ETL pipeline to process vendor promotion benchmarking data on a scheduled basis. The pipeline required automated triggering when upstream data landed, monitoring with ticketing for production failures, and enforced code quality gates — all on Native AWS infrastructure using Step Functions, Glue, and S3.

## What I Did

I owned the CDK infrastructure (PromoProETLCDK) that orchestrates the pipeline:

- **S3 trigger Lambda**: Built an automated trigger that starts the BenchmarkingETLPipeline Step Functions execution when upstream data lands (detects `_SUCCESS` files, extracts region_id/marketplace_id/dataset_date from S3 key)
- **Monitoring stack**: Added CloudWatch alarms that cut SEV3 SIM tickets to jci-teds-promo-pro on Lambda errors or Step Functions execution failures; fixed error propagation in trigger Lambda (continue → raise)
- **Code review verification**: Added pipeline stage enforcing CR approval before promotion
- **Build enforcement**: Configured git hooks for commit message conventions and enforced hook installation on build
- **Developer tooling**: Authored CLAUDE.md project instructions for the CDK package

## Impact & Results

- Pipeline runs daily in prod (us-east-1, account 943086490430) processing promotion data across 17 Andes tables
- Automated S3 trigger eliminated manual pipeline execution
- Monitoring stack provides immediate alerting on failures with auto-ticketing
- Pipeline is healthy: alpha and prod deployments both succeeding as of June 2026

## Links

- [Pipeline: PromoProETL](https://pipelines.amazon.dev/pipelines-wip/PromoProETL)
- [Code: PromoProETLCDK](https://code.amazon.com/packages/PromoProETLCDK)
- [Code: PromoProETL](https://code.amazon.com/packages/PromoProETL)
