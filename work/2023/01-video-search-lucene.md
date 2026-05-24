---
title: Video Search Lucene Ranking & Matching Features
description: Developed QU-driven ranking features (q2pt, adult filtering, query specificity) and established workflow management for the cross-team Lucene video search work group.
year: 2023
quarter: Q2-Q4
type: project
---

## Summary

I developed query understanding (QU)-driven ranking and matching features for video search in Lucene, and advocated for establishing a structured workflow management process for the cross-team Lucene work group.

## Context & Problem

When the Lucene work group began working on video search, we only had high-level milestones and roadmap defined but lacked concrete progress tracking and breakdown work. Project members were joined from multiple teams, making it difficult to split up tasks, monitor progress, and communicate effectively with stakeholders.

## What I Did

I advocated for the video search Lucene work group to establish a workflow management process. With this cooperation model, we accomplished 8 subtasks in M1, 11 subtasks in M2, and 39 subtasks in M3, demonstrating increasing productivity through improved organization and tracking. I also ran twice-weekly Lucene video search sync meetings to regularly share updates on task progress and ensure alignment.

I implemented the first QU feature, Query to Product Type (q2pt), in video search. The goal was to identify potential blockers for incorporating QU features into the ranking model. Prior to data ingestion, I conducted proof-of-concept testing in Lucene unit test and metadata functional test to validate feasibility. After consulting with PE Mike Sokolov, we determined it best to utilize the newly developed virtual function `querydoc-score` instead of the existing `query-score` used in product search. I found that `querydoc-score` did not support the required float data type, and worked with Egor from the Dublin Lucene team to create a change request that would add float number support. Once ingested, I validated the q2pt signal functionality on the dev silo before handing off to others working on the full ranking implementation.

In addition to q2pt, I also developed ranking features for adult filtering, browse node related features, and query specificity.

## Impact & Results

The structured process enabled the team to scale from 8 subtasks (M1) to 39 subtasks (M3) in successive milestones. The QU features I developed (q2pt, adult filtering, query specificity) became foundational ranking signals for the video search view.
