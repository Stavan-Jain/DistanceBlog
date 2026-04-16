# Implementation Guide: Mnemonic Medium Blog Post

## Overview

You are building a web-based blog post that uses the **mnemonic medium** — a format pioneered by Andy Matuschak and Michael Nielsen in [Quantum Country](https://quantum.country/qcvc). The post presents a rigorous proof that the surface code has distance L, with embedded spaced repetition prompts that help readers retain the key concepts.

The source material is in `distance_proof.md`. Your job is to turn it into a working web page with Orbit spaced repetition prompts embedded at appropriate points.

## Technical Stack

### Orbit

Use [Orbit](https://github.com/andymatuschak/orbit) by Andy Matuschak. Orbit provides web components for embedding spaced repetition prompts in articles. The official documentation is at [docs.withorbit.com](https://docs.withorbit.com/).

**Current status (as of April 2026):** Orbit's repo has been largely inactive since ~2022. The embedded web component (the author-facing API) is the most stable part and is still used by [Quantum Country](https://quantum.country). However, the backend cloud service (which syncs review schedules across devices and sessions) may be unreliable or down. The Business Source License converted to Apache 2.0 in December 2025, so there are no licensing concerns for production use.

**Strategy: try Orbit first, fall back to local-only.**

1. **First, try the Orbit web component.** The setup is simple: add one `<script>` tag to the page, then use `<orbit-reviewarea>` and `<orbit-prompt>` tags. Test whether the prompts render and the cloud service responds. See the docs at https://docs.withorbit.com/ for the exact script tag URL and API.

2. **If Orbit's service is down or unreliable, build a local-only fallback.** Implement a custom review area component that:
   - Visually matches the Orbit design (subtle background, card-style prompts with a "Show answer" button, self-rating buttons)
   - Stores review state in `localStorage` (prompt ID → {last reviewed, interval, next due})
   - Implements a basic spaced repetition scheduler (e.g., Leitner boxes or SM-2)
   - Uses the same prompt data format (question/answer pairs grouped by section)
   - Looks and feels like the Quantum Country experience even without cloud sync

The fallback should be a drop-in replacement: same prompt content, same placement in the article, same visual rhythm. The only thing lost is cross-device sync.

The basic Orbit pattern for embedding prompts looks like this:

```html
<!-- Add this script tag once in the <head> -->
<script type="module" src="https://js.withorbit.com/orbit-web-component.js"></script>

<orbit-reviewarea color="violet">
  <orbit-prompt
    question="What is a 1-cycle on the toric code lattice?"
    answer="An edge-set where every vertex has even degree (0, 2, or 4 edges of the set meet at each vertex)."
  />
  <orbit-prompt
    question="..."
    answer="..."
  />
</orbit-reviewarea>
```

If building the fallback, use the same data structure but render with custom HTML/CSS/JS instead of the Orbit web component.

Review areas are placed inline in the article, typically at the end of a section, after the reader has encountered all the concepts being tested.

### Rendering

- The post should be a single HTML page (or a simple static site).
- Mathematical notation must be rendered properly. Use **KaTeX** or **MathJax** for LaTeX rendering.
- The page should be readable and well-styled. Use clean typography (serif font for body, good line spacing, reasonable max-width). Reference the visual style of https://quantum.country/qcvc for inspiration.
- The markdown source uses `$...$` for inline math and `$$...$$` for display math. These need to be converted to whatever format your math renderer expects.

### Build

Keep the build simple. A static HTML file with linked CSS/JS is fine. If you need a build step (e.g., for markdown-to-HTML conversion), keep it minimal.

## Content Structure

The blog post has the following sections. The source material is in `distance_proof.md`.

1. **Introduction** (Why this post?, The standard argument and its gap, The topological approach, Prerequisites, Roadmap)
2. **Section 1: The Lattice** — coordinates, edges, faces, toric code definition
3. **Section 2: The Chain Complex** — k-cells, chains, boundary maps
4. **Section 3: Cycles, Boundaries, and Homology** — Z₁, B₁, H₁
5. **Section 4: Connection to the Toric Code** — logicals as cycles, dual lattice
6. **Section 5: Dimension of H₁** — rank-nullity computation
7. **Section 6: The Invariants h and v** — definitions, independence, boundary-invariance
8. **Section 7: The Isomorphism** — φ is an isomorphism
9. **Section 8: The Distance Theorem** — upper bound, lower bound, Z-type and full distance
10. **Conclusion** — recap, generalizations, further reading

## Prompts

The exact prompts to embed are specified in `prompts.md`. Do not add, remove, or reword them.

Place an `<orbit-reviewarea>` block at the end of each major section (after Sections 1, 2, 3, 4, 5, 6, 7, and 8), containing exactly the prompts listed for that section in `prompts.md`. Do NOT place prompts inside the introduction or conclusion.

Prompts contain LaTeX math notation. Ensure it renders correctly in both question and answer fields (e.g., with KaTeX).

## Style and Design Notes

- Keep the visual design clean and focused on readability. The content is dense; don't add visual clutter.
- Use a serif font for body text and a clear monospace or sans-serif for math.
- Aim for ~65-75 characters per line (max-width around 700px).
- Use generous vertical spacing between sections.
- Section headings should be clearly visible but not overpowering.
- The Orbit review areas should be visually distinct (e.g., a subtle background color) but not distracting.
- Make sure the page is responsive and readable on mobile.
- Look at https://quantum.country/qcvc as the reference for overall feel.

## Files

- `distance_proof.md` — the source content for the blog post
- `prompts.md` — the exact spaced repetition prompts to embed (do not modify)
- This file — implementation guide

## Summary

1. Check the current state of the Orbit repo; if the service is down, build the local-only fallback.
2. Convert `distance_proof.md` to a styled HTML page with KaTeX/MathJax for math.
3. Embed the prompts from `prompts.md` at the end of each section using `<orbit-reviewarea>` blocks (or the fallback component). Do not add, remove, or reword prompts.
4. Ensure the page looks clean, is readable, and renders math correctly in both prose and prompts.
5. Test that prompts are interactive (reveal answer, self-rate recall).
