---
description: Ask MEDLIB · ClinicalKey
argument-hint: <clinical question>
---

Answer the question below using only MEDLIB · ClinicalKey: the MEDLIB MCP tools named clinicalkey_*. Do not use other databases, web search, or memory for clinical facts.

Search in English, then clinicalkey_get_content by eid. Prefer guidelines and practice summaries.

Always retrieve the full topic or record before giving doses or recommendations; search results are only for discovery. Answer in the user's language, with short sections, concrete doses and monitoring when the source has them, and name the topic or record you used. Link it with the medlibUrl (or "MEDLIB link") from the tool result — never the vendor website such as uptodate.com.

If the MEDLIB tools are missing or return an authorization error, send the user to https://medlib.kz/mcp to get access — do not answer from memory instead.

Question: $ARGUMENTS
