---
name: x-chain-investigation
description: Investigate X/Twitter posts that reference transactions, wallets, token mints, hacks, or chain events. Use when a user gives an X link or quote and wants the real URL, tx hash, wallet addresses, screenshot/OCR extraction, or chain-link analysis. Workflow: use browser if available, then image/vision OCR as fallback, then web mirrors/search, then open block explorers and trace addresses.
---

# X Chain Investigation

Use this skill for **X/Twitter → onchain investigation** tasks.

## Goal
Extract the real artifact behind a post:
- full URL behind truncated links
- tx hash / address / contract / amount / timestamp
- screenshots/images OCR
- explorer follow-through (Etherscan etc.)

## Default workflow
1. **Try browser-native extraction first**
   - Open the X URL in browser tooling when available.
   - Prefer extracting the real anchor `href` from the live page over relying on visible truncated text.
   - If page text is hostile/dynamic, inspect images and screenshots next.

2. **Use image/vision as a first-class fallback**
   - If the post includes screenshots, charts, or explorer images, analyze them.
   - Extract every readable tx hash, wallet address, token amount, timestamp, chain label, and UI tag.
   - Do not stop at “image summary”; explicitly recover structured chain artifacts.

3. **Use mirrors and public fetches**
   - Try `r.jina.ai/http://x.com/...` and search mirrors / reposts / media articles.
   - Treat this as corroboration or fallback, not the only source.

4. **Open the explorer and continue the chain**
   - Once you have a tx hash or address, open the explorer page.
   - Identify:
     - initiator / recipient
     - token transfers / mint events
     - admin/owner changes
     - sell path / LP / router / settlement asset

5. **Report with confidence labels**
   - Separate:
     - directly observed from browser/image
     - inferred from chain structure
     - unconfirmed hypotheses

## Extraction checklist
For every relevant X post, try to recover:
- original post text
- quoted post text
- external URLs
- full tx hash(es)
- address(es)
- token symbol and amount
- chain/network
- timestamps
- screenshots/images containing chain data

## Reporting format
- **What happened**
- **Artifacts recovered**
- **Chain path**
- **Confidence / gaps**

## Important behavior
- Do **not** stop just because the visible X text is truncated.
- Do **not** rely on one path only.
- If browser extraction is flaky, immediately switch to image OCR + mirrors + explorer follow-through.
- For attack events, prioritize the **privilege-change / mint / dump** sequence over price commentary.
