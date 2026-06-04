---
title: Customer Review Aspect Early Investigation
description: Explored leveraging customer review aspect data for search; identified 3 embedding integration approaches and proposed MoE re-architecture for 2024 evaluation needs.
year: 2024
quarter: Q1
type: research
---

## Summary

I initiated and led an investigation to explore leveraging customer review aspect data to improve the overall search experience, identifying three technical solutions for embedding integration and proposing a re-architecture of the offline evaluation system.

## Context & Problem

The DocE team was expanding beyond video search into customer review aspects as a new data source for search improvement. However, there was no clear technical path for integrating aspect data as embeddings within the product search infrastructure, and the existing offline evaluation (MoE) system had gaps relative to 2024 requirements like HPO and aspect data ingestion evaluation.

## What I Did

For embedding integration, I conducted a thorough review of the Lucene, LKNN, Bi-Encoder, and Baiji codebases to identify three potential technical solutions for integrating aspect data as search embeddings.

For evaluation gaps, I identified shortcomings between the current MoE capabilities and the requirements for evaluating the new data source. I proposed a document outlining potential improvements and a re-architecture of the MoE system.

## Impact & Results

Established the technical foundation for the customer review aspect integration work that followed. The investigation de-risked the embedding approach and informed the evaluation methodology used in subsequent weblabs.

## Links

- [Review Aspects Data Exploration](https://w.amazon.com/bin/view/Search/SST-NLP/DocE/DocumentUnderstanding/Reviewaspectsdataexploration)
- [Customer Review Aspects Lexical Matching Experiment Design Direction](https://w.amazon.com/bin/view/Search/SST-NLP/DocE/DocumentUnderstanding/CustomerReviewAspectsLexicalMatchingExperimentDesignDirection)
- [Searchable Customer Reviews with Aspects](https://w.amazon.com/bin/view/Search/SST-NLP/DocE/SearchableCustomerReviews/)
