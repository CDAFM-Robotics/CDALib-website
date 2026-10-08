# Importing the CDALib docs into Wix

This site is built as **self-contained HTML pages** on purpose. Every page
(`index.html`, `overview.html`, `subsystems.html`, …) is a complete document with **all of its CSS
inlined** and **no external files** (no linked stylesheets, scripts, fonts, or images). That is
exactly the shape Wix's HTML-embed element expects, so each page can be dropped into your existing
Wix team site with no build step.

Because Wix has no "import a whole website" button, you embed the pages one at a time. There are two
supported ways, depending on how much of the page you want.

---

## Option A — Embed each page as a full HTML widget (recommended)

Best when you want the page to look exactly like it does here (dark theme, nav bar, cards, code
blocks) inside a panel on your Wix page.

1. In the Wix Editor, open the page where the docs should live.
2. Click **Add (+) → Embed Code → Embed HTML** (older editors: **More → HTML iframe**).
3. Select the element, click **Enter Code**, and choose **Code** (not "Website address").
4. Open the corresponding `.html` file from this folder in a text editor, **copy the entire file**
   (from `<!DOCTYPE html>` to `</html>`), and paste it into the box.
5. Resize the element and set it to stretch full-width. Because the content scrolls inside the
   iframe, give it a tall height (e.g. 1600–3000px depending on the page) or enable scrolling.
6. Repeat for each page you want (create one Wix page per doc page, or stack a few embeds).

> Tip: the left **sidebar** and the **Prev/Next** pager inside each page link to sibling files by
> bare filename (`subsystems.html`, etc.). Inside a Wix iframe those links won't resolve to your Wix
> URLs, so either (a) ignore the in-page nav and use your normal Wix menu to move between pages, or
> (b) after pasting, edit the `<nav class="side">` (sidebar) and `<nav class="pager">` (prev/next)
> links in each embed to point at the matching Wix page URLs.

---

## Option B — Paste just the content into a Wix page (native styling)

Best when you want the docs to inherit **your Wix site's fonts and theme** instead of this dark
theme, and to be indexed by Wix's search.

1. In each `.html` file, copy only what's **inside** `<main> … </main>` (the article content —
   headings, paragraphs, code blocks, tables). Skip the `<head>`, the `<style>`, the header nav, and
   the footer.
2. In Wix, use **Add → Embed HTML** for that fragment, **or** rebuild the content with native Wix
   text/table elements and paste the text in.
3. For code blocks, keep them inside `<pre><code>…</code></pre>` so indentation and monospacing
   survive, or use a Wix code-block/embed element.

Option B loses the custom dark theme and the syntax styling but blends into your site and is fully
editable in Wix.

---

## The API reference (Javadoc)

The `javadoc/` folder is a standard multi-file Javadoc site (it has its own `index.html`, frames,
search, and stylesheet), so it is **not** a single self-contained page and is **not** meant to be
pasted into a Wix HTML box. Publish it one of these ways and link to it from the docs:

- Upload the whole `javadoc/` folder to any static host (GitHub Pages, Netlify, Cloudflare Pages,
  S3, etc.) and link your Wix "API" menu item to that URL, **or**
- Host `javadoc/` under your own domain and point the `<a href="javadoc/index.html">API</a>` links
  at it.

Keep the docs pages and the Javadoc under the same site root if you want the relative
`javadoc/index.html` links in the pages to keep working.

---

## Page inventory

| File | Nav label | Purpose |
|------|-----------|---------|
| `index.html` | Home | Landing page with feature grid + quick start |
| `overview.html` | Overview | What CDALib is and how the pieces fit |
| `installation.html` | Install | JitPack + Gradle setup, repositories, requirements |
| `getting-started.html` | Get Started | First `ModularOpMode`, registration, lifecycle |
| `modular-opmode.html` | OpMode | `ModularOpMode` deep dive, lifecycle, bulk caching |
| `subsystems.html` | Subsystems | `Subsystem` lifecycle and provided subsystems |
| `devices.html` | Devices | Hardware device wrappers (actuators + sensors) |
| `controllers.html` | Controllers | PID / feedforward / compound controllers |
| `bindings.html` | Bindings | Named gamepad button/analog bindings |
| `tasks.html` | Tasks | Task framework and composition |
| `modules.html` | Modules | OpMode-shaped modules incl. PedroPathing TeleOp |
| `telemetry.html` | Telemetry | `TelemetryManager` and tagged entries |
| `javadoc/` | API | Generated Javadoc API reference |

To preview the whole site locally before importing, open `index.html` in a browser, or run a static
server from this folder (`python3 -m http.server`) and visit `http://localhost:8000/`.
