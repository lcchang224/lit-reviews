# lit-reviews

Published literature-review HTMLs, served at `lit.lcchema.cc` behind CF Access.

## How content gets here

Run the builder with `-Publish`:

```powershell
& "C:\Users\lccha\OneDrive\文件\Claude\Projects\litreview-html\Build-LitReviewHtml.ps1" -InputPath review.md -Publish
```

The builder will:
1. Build the HTML (embedded CSS, single file)
2. Copy it into `public/`
3. Update `manifests/latest.json` (title + date pulled from front matter)
4. Show a diff and prompt for confirm
5. `git push` to master → CF Pages auto-deploys

## Manifest schema

```json
{
  "generated": "ISO timestamp",
  "items": [
    { "date": "YYYY-MM-DD", "title": "...", "url": "https://lit.lcchema.cc/<slug>.html" }
  ]
}
```

Items sorted newest first. Consumed by the hub at `lcchema.cc`.

## Scope

Lit-reviews only — no patient information. TBMT debate prep stays local.
