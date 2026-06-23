# Diego Rodriguez — Project Portfolio

A standalone static site implemented from the Claude Design handoff
(`Portfolio.html`). No build step, no framework, no external runtime — just
open it or drop the folder on any static host.

## Files

| File | Purpose |
|------|---------|
| `index.html` | The portfolio (implemented from the design's `Portfolio.html`). |
| `Portfolio-print.html` | Print / PDF-export variant (auto-triggers the print dialog). Linked from the footer "Résumé / Print" button. |
| `assets/` | All 28 project images referenced by the pages. |

## What changed from the design prototype

The prototype used a Claude Design authoring widget (`image-slot.js`) and an
in-page "Design Controls" panel (palette / density / mood / drag-to-edit).
Those are design-tool scaffolding, not part of the real site, so the
implementation:

- Replaces every `<image-slot>` with a plain, accessible `<img>` (real `alt`
  text, lazy loading, no shadow-DOM / 31 KB JS dependency). Visual output is
  identical.
- Removes the `?edit` Design Controls panel and its scripts.
- Keeps the scroll-spy navigation and the print page's auto-print script.

Fonts (Geist, JetBrains Mono) still load from Google Fonts, matching the
design.

## To do / notes

- **Headshot:** the design had an empty "graduation photo" slot — no image was
  included in the handoff. The cover currently shows a labeled placeholder box.
  To add your photo: drop a file at `assets/headshot.jpg`, then in `index.html`
  (and `Portfolio-print.html`) replace the `<div class="hs-empty" …>…</div>`
  inside `.headshot` with
  `<img src="assets/headshot.jpg" alt="Diego Rodriguez" style="width:100%;height:100%;object-fit:cover;display:block">`.
- **Images are web-optimized.** The originals from the handoff totaled ~53 MB;
  they were downscaled to a 1600 px retina-safe cap and re-encoded — photos and
  shaded CAD renders as JPEG, line-art / charts / engineering drawings kept as
  lossless PNG so text and thin lines stay crisp. Result: the whole `assets/`
  folder is now ~2.9 MB with no visible quality loss. Full-resolution originals
  remain in `Portfolio-handoff.zip` if you ever need them.

## Preview locally

From the parent `Resumes` folder:

```
python -m http.server 8137 --directory Portfolio
```

then open <http://localhost:8137>.
