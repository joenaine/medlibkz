---
name: medlib
description: Answer clinical questions from MEDLIB sources — UpToDate, DynaMed, BMJ Best Practice, ClinicalKey, PubMed, the Kazakhstan drug registry (NDDA) and MoH clinical protocols, EMA, rare/orphan diseases (Orphanet, genes, orphan drugs, ClinicalTrials.gov) and openFDA. Use when a physician asks about diagnosis, treatment, dosing, drug registration in Kazakhstan, national protocols, EU drug safety, rare diseases or literature, or names one of these sources. Requires the MEDLIB connector.
---

# MEDLIB clinical sources

MEDLIB (https://medlib.kz) gives access to clinical databases through one MCP connector, `https://medlib.kz/api/mcp/medlib`. This skill tells you how to use it well.

## Before anything else

1. Check that MEDLIB tools are available (names such as `uptodate_search`, `pubmed_search`, `orpha_diagnose`, usually prefixed by the connector name).
2. If they are not available, or a call returns 401/403, stop and send the user to https://medlib.kz/mcp to get access and connect MEDLIB, then ask again.
   Do not answer the clinical question from memory instead.

## Pick the source

| Question | Source | Tools |
|---|---|---|
| Treatment, diagnosis, dosing, monitoring | UpToDate · DynaMed · BMJ Best Practice | `uptodate_*`, `dynamed_*`, `bmj_*` |
| Guidelines, textbooks | ClinicalKey | `clinicalkey_*` |
| Studies, evidence, reviews | PubMed | `pubmed_*` |
| Is a drug registered in Kazakhstan, ATC, manufacturer | Реестр ЛС (NDDA) | `ndda_*` |
| Kazakhstan MoH clinical protocol | Протоколы РК | `kzprotocols_*` |
| EU authorisation, referrals, PSUSA, DHPC | EMA | `ema_*` |
| Rare disease, symptoms → differential, gene, orphan drug, trials | Орфанные | `orpha_*` |
| US label, FAERS adverse events, recalls | openFDA | `openfda_*` |

If the user names a source (or runs a `/medlib:<source>` command), use only that source.

## How to query

- Search first, then retrieve the full topic or record (`*_get_topic`, `*_get_content`, `*_get_article`, `*_get_drug`, `kzprotocols_get`, `orpha_get_disease`). Search results are for discovery only; never give doses from a search snippet.
- Query language: English for UpToDate, DynaMed, BMJ, ClinicalKey, PubMed, EMA, openFDA and Orphanet; Russian МНН / trade names / ATC for NDDA; Russian or ICD-10 for Протоколы РК.
- NDDA is a registry, not an indication database: search drug names or ATC codes, never a disease name.
- `orpha_diagnose` ranks diseases by phenotype overlap. It is a differential to consider, not a diagnosis.
- FAERS counts are reporting frequency, never incidence or causality. Open Targets has no doses.

## Answer

- Answer in the user's language.
- Start with the main clinical action in one or two sentences, then short sections.
- Copy concrete doses, routes, frequencies, durations and monitoring targets from the retrieved text. Do not invent what was not retrieved; say what is missing.
- Name the topic, protocol, PMID or record each fact came from, and link it with the `medlibUrl` (or the "MEDLIB link" line) from the tool result. These pages open inside MEDLIB; never link to uptodate.com, dynamed.com, bestpractice.bmj.com or clinicalkey.com.
