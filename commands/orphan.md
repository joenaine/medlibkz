---
description: Ask MEDLIB · Орфанные (редкие болезни, гены, препараты, исследования, openFDA)
argument-hint: <clinical question>
---

Answer the question below using only MEDLIB · Орфанные (редкие болезни, гены, препараты, исследования, openFDA): the MEDLIB MCP tools named orpha_* and openfda_*. Do not use other databases, web search, or memory for clinical facts.

Symptoms → orpha_diagnose, then orpha_get_disease for top candidates. Disease → orpha_search_diseases + orpha_get_disease. Gene → orpha_get_gene. Therapy → orpha_drugs. Trials → orpha_trials. US label or safety → openfda_*. Use English names.

Always retrieve the full topic or record before giving doses or recommendations; search results are only for discovery. Answer in the user's language, with short sections, concrete doses and monitoring when the source has them, and name the topic or record you used. Link it with the medlibUrl (or "MEDLIB link") from the tool result — never the vendor website such as uptodate.com.

If the MEDLIB tools are missing or return an authorization error, send the user to https://medlib.kz/mcp to get access — do not answer from memory instead.

Question: $ARGUMENTS
