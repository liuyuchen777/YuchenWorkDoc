---
title: Vendor PSI/PSL Native AWS Pipeline & Updated Feature Store
description: Built Native AWS pipelines and integrated updated feature store for PSI/PSL recommendations, increasing vendor coverage by +1960 bps (NA) and +1570 bps (JP), and reducing model training iteration from ~2 days to ~1 hour.
year: 2025
quarter: Q2-Q4
type: project
---

## Summary

I implemented Native AWS (NAWS) pipelines and integrated an updated feature store for the vendor PSI/PSL recommendation system. This reduced model training iteration cycles from ~2 days to ~1 hour, enabled faster program onboarding, and resolved a long-standing feature store integration issue that had limited vendor coverage since the system's 2022 launch. Vendor coverage increased by +1960 bps (NA) and +1570 bps (JP).

## Context & Problem

The vendor PSI/PSL recommendation system, originally launched in 2022, had three key issues: (1) slow iteration cycles (~2 days per training run) made new program onboarding painful — recent programs like SnS Discount required 100+ training cycles and AB Discount ~70 cycles; (2) the pipeline was hard to operate and onboard new team members to; (3) a long-standing feature store integration bug meant models were not using up-to-date input features, resulting in low vendor coverage for both NA and JP.

## What I Did

I built the new pipeline using Native AWS components, replacing the legacy infrastructure. This made pipelines easier to operate and faster for newcomers to onboard. The NAWS architecture also improved extensibility — for example, a long-requested PSL coverage reporting feature could be implemented in just 2 SDE days.

I integrated the updated feature store, resolving the data freshness issue that had persisted since 2022. Newly onboarded models now use up-to-date input features for the first time.

The simplified pipeline architecture also enabled faster onboarding of new programs through a more hands-off-the-wheel (HOTW) process, reducing the total lead time for scientists to onboard new PSI/PSL programs.

## Impact & Results

Launched 6th October 2025 for both JP and NA vendors.

- Model training iteration: ~2 days → ~1 hour
- NA vendor coverage: 72.5% → 92.1% (+1,960 bps, +27.0% relative)
- JP vendor coverage: 68.6% → 84.3% (+1,570 bps, +22.9% relative)
- NA GMS coverage: 50.3% → 84.8% (+3,450 bps, +68.6% relative)
- JP GMS coverage: 37.1% → 76.3% (+3,920 bps, +105.7% relative)
- PSL coverage reporting: implemented in 2 SDE days (previously infeasible)
