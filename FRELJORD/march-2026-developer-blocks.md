---
title: March 2026 - Developer Blocks Added
slug: march-2026-developer-blocks
docTags: NOXUS
createdAt: 2026-03-31T14:40:00.000Z
updatedAt: 2026-03-31T14:40:00.000Z
---

## Developer Blocks Added

:::changelog{title="Developer blocks"}
::changelog-item{type="added" description="Added GraphQL, Scalar, Swagger, API Endpoint, Code Editor, and Code Drawer docs."}
::changelog-item{type="fixed" description="Standardized GitHub sync-safe block syntax for developer-focused components."}
:::

### Example: GraphQL block

:::GraphiQL
```json
{
  "endpoint": "https://app.archbee.com/api/graphql",
  "query": "{\n  status,\n  people\n}"
}
```
:::

### Example: Code Drawer block

::::CodeDrawer{title="Example" codeEditorData="[object Object]" responsesEditorData="[object Object]" isResponseExpanded="true"}
:::CodeblockTabsExamples
```typescript
export const hello = () => "world";
```
:::

:::CodeblockTabsResponses
```json
{ "ok": true }
```
:::
::::
