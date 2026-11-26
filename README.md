# MEDLIB для Claude и ChatGPT

Клинические источники [MEDLIB](https://medlib.kz) прямо в вашем ИИ-чате: UpToDate, DynaMed, BMJ Best Practice, ClinicalKey, PubMed, Реестр ЛС РК (NDDA), клинические протоколы МЗ РК, EMA, редкие и орфанные заболевания (Orphanet, гены, препараты, ClinicalTrials.gov) и openFDA.

Для использования нужна подписка MEDLIB: **https://medlib.kz/pricing**.

Адрес MCP-сервера:

```
https://medlib.kz/api/mcp/medlib
```

## Что в репозитории

MCP и скилл устанавливаются отдельно.

| Часть | Папка | Что даёт |
|---|---|---|
| **MCP-коннектор** | `mcp/` | Доступ к источникам MEDLIB и слэш-команды `/medlib:*` |
| **Скилл** | `skill/`, архив `medlib-skill.zip` | Объясняет Claude, как подключить MEDLIB, какой источник выбрать и как отвечать |

Скилл без коннектора только подскажет, как подключиться. Коннектор работает и без скилла.

## Claude Code

Добавьте маркетплейс:

```bash
/plugin marketplace add joenaine/medlibkz
```

MCP-коннектор и команды:

```bash
/plugin install medlib@medlib
```

Скилл:

```bash
/plugin install medlib-skill@medlib
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

1. **Customize → Connectors → «+» → Add custom connector.**
2. Name: `MEDLIB`, URL: `https://medlib.kz/api/mcp/medlib`.
3. Нажмите **Connect** и войдите в аккаунт MEDLIB.
4. В чате нажмите **+** → MEDLIB: там те же команды (UpToDate, Протоколы РК, Орфанные…).

Скилл ставится отдельно: скачайте [medlib-skill.zip](medlib-skill.zip), затем **Customize → Skills → Upload skill**.

## ChatGPT

**MEDLIB GPT.** Откройте MEDLIB GPT в ChatGPT, нажмите «Sign in with medlib.kz» и задайте вопрос. Работает на любом тарифе ChatGPT, где доступны GPTs.

**Коннектор.**

1. Откройте [chatgpt.com/plugins](https://chatgpt.com/plugins) в браузере (нужна веб-версия).
2. Нажмите «+» и **Add custom MCP server**. Если кнопки нет, на вашем тарифе или в рабочем пространстве свои MCP-серверы недоступны. Используйте Claude.
3. Name: `MEDLIB`, Connection: `https://medlib.kz/api/mcp/medlib`, Authentication: **OAuth**, остальные поля пустые.
4. Отметьте «I understand and want to continue», нажмите **Create as a plugin**.
5. Откройте плагин, нажмите **Install**, войдите в MEDLIB.
6. В новом чате напишите `@`, выберите MEDLIB и назовите источник в вопросе.

Инструкции и схема для создания GPT: [chatgpt/](chatgpt/).

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

- `mcp/`: MCP-коннектор (`.mcp.json`) и слэш-команды `/medlib:*`.
- `skill/skills/medlib/SKILL.md`: скилл, он же в `medlib-skill.zip` для Claude.ai.
- `chatgpt/`: инструкции для MEDLIB GPT в ChatGPT.

MEDLIB не заменяет клиническое суждение. Проверяйте дозировки по первоисточнику.

---

**English.** MEDLIB connects Claude, ChatGPT and other MCP clients to UpToDate, DynaMed, BMJ Best Practice, ClinicalKey, PubMed, Kazakhstan drug registry and MoH protocols, EMA, rare-disease sources and openFDA. Add `https://medlib.kz/api/mcp/medlib` as a custom connector (OAuth) or in Claude Code run `/plugin marketplace add joenaine/medlibkz`, then `/plugin install medlib@medlib` (connector) and `/plugin install medlib-skill@medlib` (skill).
