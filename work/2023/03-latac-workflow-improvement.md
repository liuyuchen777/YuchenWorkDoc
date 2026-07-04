---
title: LATAC Workflow Improvement & JSON Schema
description: Led plan to address LATAC workflow technical debt; implemented JSON schema for input/output validation, enabling automated testing and better developer experience.
time: 2023 Q3-Q4
type: project
org: Amazon > Product Search > Multi-Language Tokenizer
---

## Summary

I proposed and led an improvement plan for the LATAC workflow, addressing accumulated technical debt. My key contribution was implementing a JSON schema for the workflow's input/output, eliminating invalid inputs and enabling automated validation.

## Context & Problem

The LATAC workflow was initially launched in 2020 as an internal analysis toolkit for evaluating analyzer changes. It had expanded to include document language identification, offline evaluation, matchset analysis, and trivial query identification. This rapid expansion led to accumulated technical debt. Users struggled to compose correct JSON input documents, which caused invalid inputs and failed workflow executions.

## What I Did

I wrote a detailed document outlining the existing problems, then held a meeting with the team to prioritize and assess complexity. We subsequently implemented the actionable items.

I spearheaded the implementation of a JSON schema for the LATAC workflow's input and output. The schema provided a standardized vocabulary to annotate and validate JSON documents, allowing users to identify errors upfront. This also enabled benefits such as automated unit testing of the Step Function definition, programming language binding generation, and workflow documentation.

## Impact & Results

Eliminated a class of runtime errors caused by malformed inputs. Users could validate their inputs before submission, reducing failed workflow executions. The schema enabled downstream benefits: automated testing, code generation, and self-documenting interfaces.
