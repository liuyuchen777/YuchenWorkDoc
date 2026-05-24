---
title: Document Understanding Platform Development
description: Evolved DU from video-specific pipeline into generalized platform; integrated FTL/BDI, resolved namespace management disagreement, implemented refinement blocklisting.
year: 2024
quarter: Q2-Q4
type: project
---

## Summary

I contributed to evolving the Document Understanding (DU) system from a video-specific enrichment pipeline into a generalized platform for multiple customer review aspect use cases, including FTL integration, BDI namespace resolution, and refinement blocklisting.

## Context & Problem

DU was first developed in 2023 for video document enrichment. In 2024, DocE aimed to evolve DU into a generalized platform for computing and ingesting data into the search index for various use cases. This required integrating with new systems (FTL, BDI) and supporting features like refinement blocklisting.

## What I Did

I worked on integrating DU with the Filtered Text Loader (FTL) and added the first non-iSad track for the aspect lexical feature. I participated in integrating the Bulk Data Ingestion (BDI) system within DU.

During BDI implementation, we encountered a disagreement around namespace management. I advocated for documenting the pros and cons of different solutions. We reached agreement to parse the namespace from the snapshot S3 path, which offloads the operational burden of registering BDI namespaces from DU clients. This simplifies the collaboration model.

I collaborated with James to implement refinement blocklisting within DU. We defined requirements for blocklisting refinements and I supported adding blocklisting rules in the BLT web application, implementing blocklisting at the level of individual refinements.

## Impact & Results

Evolved DU from a single-use video pipeline into a multi-use platform. The BDI namespace decision simplified onboarding for new clients. Refinement blocklisting enabled fine-grained control over refinement quality in production.
