# MEDLIB GPT (ChatGPT Actions)

Настройка GPT в редакторе ChatGPT (**Explore GPTs → Create → Configure**).

1. **Name:** MEDLIB. **Description:** UpToDate, протоколы РК, реестр ЛС, PubMed и другие источники MEDLIB.
2. **Instructions:** вставьте текст из [GPT_INSTRUCTIONS.md](GPT_INSTRUCTIONS.md).
3. **Actions → Create new action → Import from URL:**
   ```
   https://medlib.kz/api/gpt/openapi.json
   ```
4. **Authentication → OAuth:**
   - Client ID и Client Secret: значения `MEDLIB_GPT_CLIENT_ID` и `MEDLIB_GPT_CLIENT_SECRET` с сервера MEDLIB
   - Authorization URL: `https://medlib.kz/api/mcp/oauth/authorize`
   - Token URL: `https://medlib.kz/api/mcp/oauth/token`
   - Scope: `mcp:tools`
   - Token Exchange Method: Default (POST request)
5. **Privacy policy:** `https://medlib.kz/privacy-policy`
6. Сохраните GPT, откройте **Share → Anyone with the link** (или GPT Store) и пропишите ссылку в `NEXT_PUBLIC_MEDLIB_GPT_URL` на сервере, чтобы она появилась на medlib.kz/mcp.
