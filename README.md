# A Topological Proof That the Surface Code Has Distance L

This repository hosts a static, long-form essay that proves the toric/surface code distance is `L`, with embedded mnemonic review prompts after each major section.

Live site: <https://stavan-jain.github.io/DistanceBlog/>

## What is in this repo

- `index.html` - full article, styling, math rendering, and review-card logic
- `distance_proof.md` - markdown source/proof draft used to build the article
- `prompts.md` - section-by-section prompt source
- `implementation_guide.md` - implementation notes and project constraints

## Current implementation

- **Single static page**: no build step required
- **Math rendering**: KaTeX via CDN (`$...$` and `$$...$$`)
- **Mnemonic prompts**: custom review areas with:
  - show/hide answer
  - self-rating buttons (`No`, `Barely`, `Yes`, `Easily`)
  - local due-status labels
- **Scheduling**: localStorage-backed SM-2-style spaced repetition (`sr:<prompt-id>`)

## Article structure

The page contains:

- Introductory motivation + roadmap
- Sections `1` through `8` covering lattice setup, chain complex, homology, invariants, and distance theorem
- A review area after each major technical section
- Conclusion + further reading

## Run locally

From the repository root:

```bash
python3 -m http.server 8080
```

Open <http://localhost:8080>.

## Deploy (GitHub Pages)

This repo is configured for GitHub Pages from branch `main`, folder `/` (root).

- Site URL: <https://stavan-jain.github.io/DistanceBlog/>
- If changes are not visible immediately, wait 1-2 minutes for Pages to rebuild.

## Notes for editing

- Keep prompt IDs stable (`data-id` like `3.2`) so review history in localStorage is preserved.
- Prefer semantic HTML lists (`ul/li`) over manual `<br>` formatting for consistent spacing.
- If you change section text, update `prompts.md` only when prompt content should change too.
