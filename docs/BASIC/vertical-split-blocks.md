---
title: Vertical Splits & Minitasker
slug: vertical-split-blocks
icon: {"lucideIcon":"Columns2"}
docTags: Revenge
createdAt: Wed Apr 29 2026 12:33:04 GMT+0000 (Coordinated Universal Time)
updatedAt: Wed Apr 29 2026 12:50:32 GMT+0000 (Coordinated Universal Time)
---

## Left Alignment

::::VerticalSplit{layout="left"}
:::VerticalSplitItem
Dummy left content.
:::

:::VerticalSplitItem
Dummy right content.
:::
::::

## Middle Alignment

::::VerticalSplit{layout="middle"}
:::VerticalSplitItem
Dummy left content.
:::

:::VerticalSplitItem
Dummy right content.
:::
::::

## Right Alignment

::::VerticalSplit{layout="right"}
:::VerticalSplitItem
Dummy left content. sadsa
:::

:::VerticalSplitItem
Dummy right content.
:::
::::

## Minitasker

:::DropList
```json
{
  "columns": [
    {
      "id": "todo",
      "name": "Todo",
      "items": [
        {
          "id": "a1",
          "content": "Dummy task A1",
          "justAdded": false
        },
        {
          "id": "a2",
          "content": "Dummy task A2",
          "justAdded": false
        },
        {
          "id": "a3",
          "content": "Dummy task A3",
          "justAdded": false
        }
      ]
    },
    {
      "id": "review",
      "name": "Review",
      "items": [
        {
          "id": "a4",
          "content": "Dummy task A4",
          "justAdded": false
        },
        {
          "id": "a5",
          "content": "Dummy task A5",
          "justAdded": false
        },
        {
          "id": "a6",
          "content": "Dummy task A6",
          "justAdded": false
        }
      ]
    },
    {
      "id": "done",
      "name": "Done",
      "items": [
        {
          "id": "a7",
          "content": "Dummy task A7",
          "justAdded": false
        },
        {
          "id": "a8",
          "content": "Dummy task A8",
          "justAdded": false
        },
        {
          "id": "a9",
          "content": "Dummy task A9",
          "justAdded": false
        }
      ]
    }
  ]
}
```
:::
