---
name: darkfantasy10
description: Creates 6 Grok Image Dark Fantasy
---

# Dark Fantasy Image Generation Flow

## Overview
Go to the Gemini Dark Fantasy 1.0 gem, generate 6 JSON image prompts, then submit each one to Grok Imagine in its own tab.

---

## Step 1 — Get the prompts from Gemini

1. Navigate to: `https://gemini.google.com/gem/677970b32bbb`
2. Click into the "Ask Gemini" input at the bottom, type `go`, and press Enter.
3. Gemini responds with 6 JSON blocks. Each block looks like this:

```json
{
  "title": "...",
  "prompt": "...",
  "negative_prompt": "...",
  "image_style": {
    "aesthetic": "Dark Fantasy",
    "lighting": "...",
    "rendering": "Old washed-out fantasy illustration"
  },
  "aspect_ratio": "9:16"
}
```

Extract all 6 JSON blocks from Gemini's response using `get_page_text` — you'll need the **entire JSON block** for each one (not just the prompt text). Compact each block to a single line (no line breaks) before submitting to Grok.

---

## Step 2 — Submit each prompt to Grok Imagine

For each of the 6 prompts, open a new tab and run the following steps:

1. Open a new tab and navigate to: `https://grok.com/imagine`
2. Use JavaScript to insert the JSON into the contenteditable input and submit:

```javascript
// Step 1: Insert the JSON text
const ce = document.querySelector('[contenteditable]');
ce.focus();
document.execCommand('insertText', false, YOUR_JSON_STRING_HERE);

// Step 2: Dispatch Enter key events to submit
ce.dispatchEvent(new KeyboardEvent('keydown', {key: 'Enter', code: 'Enter', keyCode: 13, which: 13, bubbles: true}));
ce.dispatchEvent(new KeyboardEvent('keypress', {key: 'Enter', code: 'Enter', keyCode: 13, which: 13, bubbles: true}));
ce.dispatchEvent(new KeyboardEvent('keyup', {key: 'Enter', code: 'Enter', keyCode: 13, which: 13, bubbles: true}));
```

3. Confirm submission: the tab title will update to show the JSON content once the submission registers.

Repeat for all 6 prompts — each in its own tab so they generate in parallel.

---

## Important Notes

- **Do NOT try to click the "Type to imagine" floating bar** — it sits on top of the gallery image grid and clicks will land on gallery images instead. Use the JavaScript method above.
- The `computer.key('Return')` action does **not** work on background tabs. Always use the JS `KeyboardEvent` dispatch method.
- You must paste the **full JSON block** (compacted, no newlines), not just the `prompt` field. Grok reads the whole object.
- Images generate in the background — scroll down on each tab to see them appear.
- The tab title updates to the JSON content once submission registers successfully.
- All 6 tabs can generate simultaneously.

---

## Quick Reference — Grok Imagine Settings

The default settings (Image / Quality / 9:16) are already correct — no need to change them.

| Setting | Value |
|---|---|
| Mode | Image |
| Quality | Quality |
| Aspect Ratio | 9:16 |

---

## URLs

| Service | URL |
|---|---|
| Gemini Dark Fantasy 1.0 Gem | `https://gemini.google.com/gem/677970b32bbb` |
| Grok Imagine | `https://grok.com/imagine` |
