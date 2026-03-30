# Archbee blocks & assets — full reference (this repo)

When content is edited in **GitHub and synced to Archbee**, use the patterns in **GitHub sync — canonical patterns** below. Editor-exported **JSX** (`<Changelog>`, `<Map>`, `<embed>`, `<File>`) often renders **empty** in the portal; prefer the **colon/directive** forms from that section.

For colon-nested blocks (LinkArray, VerticalSplit, etc.), **inner** lines use **fewer** colons than the **outer** wrapper.

**Block taxonomy:** Archbee groups blocks into **BASIC**, **MEDIA**, and **DEVELOPER**. This repo’s markdown mirrors that (`docs/BASIC/`, `docs/MEDIA/`, `docs/DEVELOPER/`). The full product list (including types we do not have sample docs for yet) is in **[SKILL.md](SKILL.md)** → **Block taxonomy**.

---

## GitHub sync — canonical patterns

Use these in `docs/BASIC/`, `docs/MEDIA/`, and `docs/DEVELOPER/` markdown. Showcase paths are noted for copy-paste.

| Content | Correct pattern | Avoid (often blank after sync) |
| ------- | ---------------- | ------------------------------- |
| **TeX** | Fenced code with language `tex` | — |
| **Mermaid** | Fenced code with language `mermaid` | — |
| **Changelog** | `:::changelog{title="..."}` … `::changelog-item{type="..." description="..."}` … `:::` | `<Changelog>` / `<ChangelogItem>` |
| **Map** | `:::::Map` + fenced `json` body + `:::::` | `<Map data="...">` |
| **File** | `::File[]{…}` — attrs in `{}`; use `caption` flag on downloads; `isUploading="false"` for empty slot | `<File>…</File>` |
| **Image** | Standard markdown `![](https://...)` (section **Image**) | — |
| **YouTube Video** | `:::::Embed{url="https://youtu.be/..."}` + `:::::` (or try `:::::Video{url="..."}` / plain URL on its own line) | `<embed url="...">` |

### TeX

````markdown
```tex
your LaTeX here
```
````

See `DEVELOPER/tex-mermaid-blocks.md`.

### Mermaid

````markdown
```mermaid
flowchart LR
  A --> B
```
````

See `DEVELOPER/tex-mermaid-blocks.md`.

### Changelog

```markdown
:::changelog{title="Release name"}
::changelog-item{type="added" description="..."}
::changelog-item{type="fixed" description="..."}
::changelog-item{type="improved" description="..."}
::changelog-item{type="broken" description="..."}
::changelog-item{type="knownIssue" description="..."}
:::
```

Types: `added`, `improved`, `fixed`, `broken`, `knownIssue`. [Archbee Changelog block](https://www.archbee.com/docs/changelog-block). See `DEVELOPER/changelog-blocks.md`.

### Map

````markdown
:::::Map
```json
{"center":[lat,lng],"zoom":10,"markerPositions":[]}
```
:::::
````

See `MEDIA/map-blocks.md`. If blank, insert with `(map)` in Archbee and match exported markdown.

### File

**Two colons**, `File`, **empty `[]`**, then **`{…}`** attributes (works on GitHub sync; JSX `<File>` often does not).

```markdown
::File[]{isUploading="false"}

::File[]{src="https://…" label="filename.ext" caption}
```

- **`src`**: presigned or hosted file URL.
- **`label`**: display name.
- **`caption`**: trailing flag (no `=`) for caption UI, matching editor export from another project.

See `MEDIA/file-blocks.md`.

### Image

```markdown
![](https://example.com/image.png)
```

See **Images & YouTube Videos** (`MEDIA/images-embeds.md`). Link grid cards may use Imgur URLs listed below.

### YouTube Video

````markdown
:::::Embed{url="https://youtu.be/VIDEO_ID"}
:::::
````

See **Images & YouTube Videos** (`MEDIA/images-embeds.md`). Fallbacks: `:::::Video{url="..."}` or a **plain YouTube URL** on its own line; compare export from `(video)` in the editor.

---

## Link grid header images (Imgur)

Rotate these for `LinkArrayItem` with `headerType="IMAGE"`. All are `.jpeg` on `i.imgur.com`.

| Label | URL |
| ----- | --- |
| Image 1 | `https://i.imgur.com/egDw6na.jpeg` |
| Image 2 | `https://i.imgur.com/paHSk6w.jpeg` |
| Image 3 | `https://i.imgur.com/S9lPyzp.jpeg` |

Copy-paste line:

```text
https://i.imgur.com/egDw6na.jpeg
https://i.imgur.com/paHSk6w.jpeg
https://i.imgur.com/S9lPyzp.jpeg
```

---

## Link grid color headers (examples in repo)

| Card | `headerColor` |
| ---- | ------------- |
| Amber | `#CA8A04` |
| Red | `#DC2626` |
| Cyan | `#0891B2` |

---

## Doc pages by category (paths and slugs for `docId` / `externalHref`)

**Internal href pattern:** `/docs/<Category>/<slug>` — no `.md` in the URL. **Category** is `BASIC`, `MEDIA`, or `DEVELOPER` (matches folders under `docs/`).

### BASIC

| Path | `slug` |
| ---- | ------ |
| `BASIC/heading-expandable-blocks.md` | `heading-expandable-blocks` |
| `BASIC/checklist-list-blocks.md` | `checklist-list-blocks` |
| `BASIC/table-divider-blocks.md` | `table-divider-blocks` |
| `BASIC/buttons-callouts.md` | `buttons-callouts` |
| `BASIC/vertical-split-blocks.md` | `vertical-split-blocks` |
| `BASIC/minitasker.md` | `minitasker` |
| `BASIC/link-grids-blocks.md` | `link-grids-blocks` |
| `BASIC/workflow-tabs-blocks.md` | `workflow-tabs-blocks` |

### MEDIA

| Path | `slug` |
| ---- | ------ |
| `MEDIA/file-blocks.md` | `file-blocks` (page title: **Files**) |
| `MEDIA/images-embeds.md` | `images-embeds` (page title: **Images & YouTube Videos**) |
| `MEDIA/map-blocks.md` | `map-blocks` |

### DEVELOPER

| Path | `slug` |
| ---- | ------ |
| `DEVELOPER/tex-mermaid-blocks.md` | `tex-mermaid-blocks` |
| `DEVELOPER/changelog-blocks.md` | `changelog-blocks` |

---

## archbee.json (quick)

- `docsPath`: `"docs/"`.
- `structure.summary`: e.g. `BASIC/heading-expandable-blocks.md`.
- Nav: `structure.docsTree` → categories **BASIC**, **MEDIA**, **DEVELOPER** → each child `path`: `BASIC/...`, `MEDIA/...`, or `DEVELOPER/...`.
- Optional **`name`** on a child (e.g. `"name": "Files"`) sets the **sidebar label** if Archbee still shows an old title after you change YAML `title` (cached metadata). Match `name` to `title` when renaming pages.
- Logos: `faviconURL`, `publicLogoURL`, `darkPublicLogoURL` under `/public/`.

Validate after edits:

```bash
python3 -m json.tool archbee.json >/dev/null && echo OK
```

---

## Block inventory

| Kind | Component / pattern | Showcase file |
| ---- | ------------------- | --------------- |
| CTA | `CtaButton` | `BASIC/buttons-callouts.md` |
| Callout | `hint` | `BASIC/buttons-callouts.md` |
| Expandable | `ExpandableHeading` | `BASIC/heading-expandable-blocks.md` |
| Columns | `VerticalSplit` + `VerticalSplitItem` | `BASIC/vertical-split-blocks.md` |
| Board | `DropList` + JSON | `BASIC/minitasker.md` |
| Link grid | `LinkArray` + `LinkArrayItem` | `BASIC/link-grids-blocks.md` |
| Workflow | `WorkflowBlock` + `WorkflowBlockItem` | `BASIC/workflow-tabs-blocks.md` |
| Tabs | `Tabs` + `Tab` | `BASIC/workflow-tabs-blocks.md` |
| Table | Markdown pipe table | `BASIC/table-divider-blocks.md` |
| Table | Raw HTML `<table>` | `BASIC/table-divider-blocks.md` |
| Divider | Markdown `***` | `BASIC/table-divider-blocks.md` |
| Lists | `- [ ]`, `-`, `1.` | `BASIC/checklist-list-blocks.md` |
| File | `::File[]{…}` (`src`, `label`, `caption`, `isUploading`) | `MEDIA/file-blocks.md` |
| Image | `![](url)` | `MEDIA/images-embeds.md` |
| YouTube Video | `:::::Embed{url="..."}` (or `:::::Video{url="..."}`) | `MEDIA/images-embeds.md` |
| Map | `:::::Map` + fenced `json` body | `MEDIA/map-blocks.md` |
| Mermaid | Fenced code block with language `mermaid` | `DEVELOPER/tex-mermaid-blocks.md` |
| TeX | Fenced code block with language `tex` | `DEVELOPER/tex-mermaid-blocks.md` |
| Changelog | `:::changelog` + `::changelog-item` (lowercase) | `DEVELOPER/changelog-blocks.md` |

---

## Changelog (colon fences) — detail

Same as **GitHub sync — canonical patterns** → Changelog. Full example:

```markdown
:::changelog{title="v1.0"}
::changelog-item{type="added" description="New feature"}
::changelog-item{type="fixed" description="Bug fix"}
::changelog-item{type="knownIssue" description="Known limitation"}
:::
```

---

## Map (colon fences + JSON) — detail

Same as **GitHub sync — canonical patterns** → Map.

---

## Video / YouTube (colon fences) — detail

Same as **GitHub sync — canonical patterns** → **YouTube Video**.

---

## Frontmatter template (new doc)

```yaml
---
title: Page Title
slug: kebab-slug
icon: {"lucideIcon":"IconName"}
# OR: icon: {"faIcon":"fa-solid fa-name"}
# OR: icon: "emoji"
docTags: Revenge
createdAt: 2026-03-30T10:00:00.000Z
updatedAt: 2026-03-30T10:00:00.000Z
---
```

Add the file to `archbee.json` `docsTree` and set `structure.summary` if this should be the landing doc.

---

## CtaButton

Uses **five** colons open and close; body is empty.

```md
:::::CtaButton{label="LABEL" docId docAnchorId externalHref openInNewTab="true" noFollow="false"}
:::::

:::::CtaButton{label="GO TO PAGE" docId="target-slug" docAnchorId="anchor-id" externalHref="/docs/BASIC/target-slug" openInNewTab="false" noFollow="false"}
:::::

:::::CtaButton{label="EXTERNAL" docId docAnchorId externalHref="https://example.com" openInNewTab="true" noFollow="false"}
:::::
```

---

## hint (callouts)

Types: `info`, `success`, `warning`, `danger`.

```md
:::::hint{type="info"}
Content.
:::::

:::::hint{type="success"}
Content.
:::::

:::::hint{type="warning"}
Content.
:::::

:::::hint{type="danger"}
Content.
:::::
```

---

## ExpandableHeading

Put markdown headings (e.g. `#` through `###`) inside the block.

```md
:::::ExpandableHeading
# Expandable title

Body text.
:::::
```

---

## VerticalSplit

`layout`: `"left"` | `"middle"` | `"right"`.

```md
:::::VerticalSplit{layout="left"}
::::VerticalSplitItem
Left column.
::::

::::VerticalSplitItem
Right column.
::::
:::::
```

---

## DropList (Minitasker)

JSON inside a fenced `json` block; `:::::DropList` wraps it.

````md
:::::DropList
```json
{
  "columns": [
    {
      "id": "col",
      "name": "Column name",
      "items": [
        { "id": "i1", "content": "Task text", "justAdded": false }
      ]
    }
  ]
}
```
:::::
````

---

## LinkArray + LinkArrayItem

Outer: `:::::LinkArray` … `:::::`. Inner items: `::::LinkArrayItem` … `::::`.

`contentSource="CUSTOM"`. `itemsPerRow`: often `"3"`.

**Content only (no header):**

```md
:::::LinkArray{contentSource="CUSTOM" itemsPerRow="3"}
::::LinkArrayItem
Body.
::::

::::LinkArrayItem
Body.
::::
:::::
```

**Color header:**

```md
:::::LinkArray{contentSource="CUSTOM" itemsPerRow="3"}
::::LinkArrayItem{headerType="COLOR" headerColor="#CA8A04"}
Body.
::::
:::::
```

**Image header (use URLs from the table at top):**

```md
:::::LinkArray{contentSource="CUSTOM" itemsPerRow="3"}
::::LinkArrayItem{headerType="IMAGE" headerImage="https://i.imgur.com/egDw6na.jpeg"}
Body.
::::
:::::
```

---

## WorkflowBlock + WorkflowBlockItem

First line of each item is the step title; blank line then body.

```md
:::::WorkflowBlock
::::WorkflowBlockItem
Step title

Step body.
::::

::::WorkflowBlockItem
Another step

More text.
::::
:::::
```

---

## Tabs + Tab

```md
:::::Tabs
::::Tab{title="TAB A"}
Tab A content.
::::

::::Tab{title="TAB B"}
Tab B content.
::::
:::::
```

---

## Markdown table

```md
| Col A | Col B |
| ----- | ----- |
| A1    | B1    |
```

---

## Horizontal rule (divider)

```md
***
```

---

## HTML table (Archbee attributes)

- `<table>`: `isTableHeaderOn="true|false"`, `columnWidths="220,220,220"` (comma-separated numbers).
- `<td>`: `align="left|center|right"`, `lightBackgroundColor="#HEX"`, `darkBackgroundColor="#HEX"`, `colSpan="N"`, `rowSpan="N"`.
- Put content in `<p>` inside cells when needed.

Minimal example:

```html
<table isTableHeaderOn="true" columnWidths="200,200">
  <tr>
    <td lightBackgroundColor="#E5E7EB" darkBackgroundColor="#1F2937" align="center">
      <p><strong>Header</strong></p>
    </td>
  </tr>
</table>
```

---

## Plain markdown lists (no custom component)

```md
- [ ] Checklist item
- Bullet
1. Numbered
```

---

## Pitfalls

- **Sync duplication:** external sync can append the same file twice; if you see repeated YAML frontmatter, keep one clean copy.
- **Fences:** mismatching colon counts breaks parsing — copy from this file or from the matching page under `docs/BASIC/`, `docs/MEDIA/`, or `docs/DEVELOPER/`.
