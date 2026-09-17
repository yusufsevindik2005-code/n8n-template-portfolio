# AI Video Pipeline: Stock Footage Matching + Auto-Publish

![cover](cover.png)

An n8n workflow that turns an approved script into a rendered, published video: it fetches stock footage candidates per script line (Pexels/Pixabay), re-ranks them with a local CLIP model against the line's actual meaning (not just keyword matching), downloads the winning clip, runs an FFmpeg render pass, uploads the result to Drive, then publishes it straight to TikTok, Instagram, and YouTube — with built-in error handling at every stage so a failed render or a failed publish is never shipped silently.

**Highlights**
- CLIP-based visual re-ranking (ONNX runtime, no GPU required) — picks footage that actually matches the line's subject, not just generic keyword hits
- Cross-line deduplication — avoids reusing the same clip across multiple lines in one video
- One-click distribution: renders, then auto-publishes to TikTok/Instagram/YouTube in the same run (Upload-Post API) with title/description/hashtags pulled straight from your content sheet
- Full error-handling branch at every stage (stock-fetch, render, publish) — a failure writes a distinct status instead of failing the whole run silently

**Get it:** [AutomationWorkflows.io listing](https://automationworkflows.io/product/ai-stock-footage-matcher-video-render-pipeline-n8n)

*(Full template file is delivered on purchase — this repo is a portfolio showcase, not the download.)*
