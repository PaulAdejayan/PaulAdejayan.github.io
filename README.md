# PaulAdejayan.github.io

My personal site and portfolio — computer science and cybersecurity at UMBC, building automation where security meets AI.

**Live at [pauladejayan.github.io](https://pauladejayan.github.io/)**

---

## What this is

One hand-written `index.html`. No framework, no build step, no bundler, no npm. Open the file in a browser and you have the whole site. The only network dependency is the Google Fonts stylesheet for Instrument Serif and Hanken Grotesk; everything else — styles, scripts, SVG artwork, the favicon — is inline or local.

GitHub Pages serves it straight from `main`.

## Running it locally

```bash
python -m http.server 8000
```

Then open <http://localhost:8000>. Opening `index.html` directly from the filesystem also works; the local server only matters if you want the paths to behave exactly as they do in production.

## Layout

```
index.html                 the entire site: markup, styles, scripts
Paul_Adejayan_Resume.pdf   linked from the hero, the contact rows and the footer
img/
  architecture.svg         phi-scrubber pipeline diagram
  demo.svg                 phi-scrubber CLI terminal figure
  *.jpg                    photographs (credited in the page footer)
```

## The PHI Scrubber demo

The page embeds a live demo of [phi-scrubber](https://github.com/PaulAdejayan/phi-scrubber), my open-source tool for de-identifying clinical notes under HIPAA Safe Harbor. Type into the sample note and the identifiers are replaced as you go.

Two things worth being clear about:

- **The sample note is fictional.** No real patient data is in this repository, and none should ever be pasted into the demo.
- **The demo is pattern-matching only** — a self-contained regex pass running in your browser, with nothing sent anywhere. The real tool adds spaCy named-entity recognition, keyed date shifting that preserves intervals, and an audit log. Neither the demo nor the tool is sufficient as a sole de-identification control; a human reviewer is still required.

The pipeline diagram and the CLI figure on the page are the same artwork that documents the tool in its own repository.

## Notes on the build

A few decisions that are easy to undo by accident:

- Hover effects are gated behind `@media (hover:hover) and (pointer:fine)`. Touch browsers apply `:hover` on first tap and leave it stuck otherwise.
- Viewport heights use `svh`, not `vh`, so mobile browser chrome doesn't crop the hero.
- `prefers-reduced-motion: reduce` disables every reveal, parallax and transition.
- The wide SVG figures scroll inside their own panel rather than widening the page — that is what the `min-width: 0` on `.art` is holding in place.

## Credits

Photographs are credited in the page footer, each via Wikimedia Commons under its own licence. The pipeline diagram and CLI figure are mine.
