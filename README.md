# Token Cost Estimator

A small **React + TypeScript + Vite** web app that estimates how much a single LLM call might cost. You enter **input and output token counts** and your provider’s **price per 1 million tokens** (separate rates for prompt vs completion). The app shows input subtotal, output subtotal, and **total USD**.

This is for **planning and comparison only** — always confirm pricing on your vendor’s current price list.

## What you need on your machine

- **Node.js** (LTS recommended, e.g. 20.x or 22.x). [nodejs.org](https://nodejs.org/)
- **npm** (bundled with Node)

Check versions:

```bash
node -v
npm -v
```

## Install

From the project folder:

```bash
npm install
```

## Run locally (development)

```bash
npm run dev
```

Vite prints a local URL (usually `http://localhost:5173`). Open it in your browser. The page updates as you type; there is **no server-side API** and **no `.env` file** — everything runs in the browser.

## How to use the app

1. **Input tokens** — tokens you send in the prompt (context + user message, etc.).
2. **Input price / 1M (USD)** — your provider’s cost per **one million** input tokens.
3. **Output tokens** — tokens the model generates.
4. **Output price / 1M (USD)** — cost per **one million** output tokens.

**Formula:**

`(input tokens ÷ 1,000,000 × input $/M) + (output tokens ÷ 1,000,000 × output $/M)`

You can paste numbers with commas; invalid text is treated as zero for the calculation. Currency is formatted as **USD** in the UI.

## Build for production

```bash
npm run build
```

Output goes to the `dist/` folder. You can preview that build locally:

```bash
npm run preview
```

Deploy `dist/` to any static host (Netlify, Vercel, S3 + CloudFront, etc.) — no special server configuration is required.

## Lint

```bash
npm run lint
```

## Project layout (short)

| Path        | Role                                      |
| ----------- | ----------------------------------------- |
| `src/App.tsx` | Main calculator UI and logic            |
| `src/App.css` | Layout and styling                        |
| `vite.config.ts` | Vite + React plugin                   |

There is **no backend** and **no environment-based configuration** in this repo; “configuration” is whatever rates you type into the form for the model you are pricing.
