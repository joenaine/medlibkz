# MEDLIB для Claude и ChatGPT

Клинические источники [MEDLIB](https://medlib.kz) прямо в вашем ИИ-чате: UpToDate, DynaMed, BMJ Best Practice, ClinicalKey, PubMed, Реестр ЛС РК (NDDA), клинические протоколы МЗ РК, EMA, редкие и орфанные заболевания (Orphanet, гены, препараты, ClinicalTrials.gov) и openFDA.

Для использования нужна подписка MEDLIB: **https://medlib.kz/pricing**.

Адрес MCP-сервера:

```
https://medlib.kz/api/mcp/medlib
```

## Claude Code

```bash
/plugin marketplace add joenaine/medlibkz
```

```bash
/plugin install medlib@medlib
```

При первом запросе Claude откроет браузер для входа в MEDLIB. После этого доступны команды:

| Команда | Источник |
|---|---|
| `/medlib:ask <вопрос>` | MEDLIB сам выберет источник |
| `/medlib:uptodate <вопрос>` | UpToDate |
| `/medlib:dynamed <вопрос>` | DynaMed |
| `/medlib:bmj <вопрос>` | BMJ Best Practice |
| `/medlib:clinicalkey <вопрос>` | ClinicalKey |
| `/medlib:pubmed <вопрос>` | PubMed |
| `/medlib:ndda <вопрос>` | Реестр ЛС РК |
| `/medlib:protocols <вопрос>` | Клинические протоколы МЗ РК |
| `/medlib:ema <вопрос>` | EMA |
| `/medlib:orphan <вопрос>` | Редкие болезни, гены, орфанные препараты, исследования, openFDA |

Пример: `/medlib:protocols внебольничная пневмония у взрослых, стартовая терапия`

## Claude.ai и Claude Desktop

1. **Settings → Connectors → Add custom connector.**
2. Name: `MEDLIB`, URL: `https://medlib.kz/api/mcp/medlib`.
3. Нажмите **Connect** и войдите в аккаунт MEDLIB.
4. В чате нажмите **+** → MEDLIB: там те же команды (UpToDate, Протоколы РК, Орфанные…).

Чтобы Claude сам выбирал источник, загрузите скилл: **Settings → Capabilities → Skills → Upload skill** и выберите папку `skills/medlib` (в zip).

## ChatGPT

1. **Settings → Apps & Connectors → Advanced → Developer mode** (включить).
2. **Create** → Name: `MEDLIB`, MCP Server URL: `https://medlib.kz/api/mcp/medlib`, Authentication: **OAuth**.
3. Войдите в аккаунт MEDLIB.
4. В новом чате выберите MEDLIB в меню **+** и задайте вопрос, например: «Найди в протоколах РК лечение артериальной гипертензии».

## Cursor и другие MCP-клиенты

```json
{
  "mcpServers": {
    "medlib": { "url": "https://medlib.kz/api/mcp/medlib" }
  }
}
```

Если клиент не поддерживает OAuth, создайте токен в [личном кабинете](https://medlib.kz/account) и передайте его заголовком `Authorization: Bearer <токен>`.

## Что внутри

- `.mcp.json` — подключение к MCP-серверу MEDLIB.
- `commands/` — слэш-команды `/medlib:*` для Claude Code.
- `skills/medlib/SKILL.md` — скилл: как выбирать источник и отвечать.

MEDLIB не заменяет клиническое суждение. Проверяйте дозировки по первоисточнику.

---

**English.** MEDLIB connects Claude, ChatGPT and other MCP clients to UpToDate, DynaMed, BMJ Best Practice, ClinicalKey, PubMed, Kazakhstan drug registry and MoH protocols, EMA, rare-disease sources and openFDA. Add `https://medlib.kz/api/mcp/medlib` as a custom connector (OAuth) or install this plugin in Claude Code with `/plugin marketplace add joenaine/medlibkz`.
