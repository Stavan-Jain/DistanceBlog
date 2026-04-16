# Orbit-based Mnemonic Medium Starter

This folder contains a minimal static page using Orbit's web component to embed spaced-repetition prompts in prose.

## What this gives you

- A local starter page at `index.html`
- Embedded `<orbit-reviewarea>` blocks and `<orbit-prompt>` cards
- A direct path to building a QCVC-style essay with memory prompts

## Run locally

From this directory:

```bash
python3 -m http.server 8080
```

Then open:

`http://localhost:8080`

## Authoring pattern

1. Write a short section of prose.
2. Add a nearby `<orbit-reviewarea>` with 2-5 prompts.
3. Keep each prompt focused on one retrievable fact or idea.
4. Repeat section-by-section.

## Prompt-writing heuristics

- Prefer short questions with one clear target answer.
- Avoid broad or essay-style prompts.
- Use multiple prompts for the same concept from different angles.
- Add notation prompts (e.g., "$|0\\rangle$") for technical fluency.

## Useful references

- Orbit repository: <https://github.com/andymatuschak/orbit>
- Orbit docs: <https://docs.withorbit.com/>
- QCVC inspiration: <https://quantum.country/qcvc>

## Getting the surface-code visualization

Use the hosted Quantum Code Visualizer:

- Main page: <https://gui.quantumcodes.io/>
- 2D surface/toric view: <https://gui.quantumcodes.io/2d>

To embed it in your page, use:

```html
<iframe
  src="https://gui.quantumcodes.io/2d"
  title="Surface Code Visualizer"
  style="width: 100%; height: 640px; border: 1px solid #8884"
  loading="lazy"
  referrerpolicy="no-referrer-when-downgrade"
  allowfullscreen
></iframe>
```
