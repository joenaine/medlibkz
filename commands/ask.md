---
description: Ask MEDLIB — picks the best source for the question
argument-hint: <clinical question>
---

Answer the question below with the MEDLIB MCP tools. Pick the source that fits:

- Treatment, diagnosis, dosing → UpToDate (uptodate_*), DynaMed (dynamed_*) or BMJ Best Practice (bmj_*)
- Kazakhstan: drug registration → ndda_*; MoH clinical protocols → kzprotocols_*
- EU regulatory and safety → ema_*
- Evidence and studies → pubmed_*
- Rare diseases, symptoms-to-diagnosis, genes, orphan drugs, trials → orpha_*; US labels and FAERS → openfda_*

Use one source unless the question clearly needs two, and say which source each fact came from. Retrieve the full topic before giving doses. If the tools are missing or return an authorization error, send the user to https://medlib.kz/mcp to get access.

Question: $ARGUMENTS
