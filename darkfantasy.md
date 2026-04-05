# Dark Fantasy Image Generator — Project Instructions

## Overview

Get 6 dark fantasy image prompts from the Gemini gem, then submit each to a separate Grok Imagine tab for parallel rendering. All 6 tabs generate simultaneously.

---

## Step 1: Get Prompts from Gemini

1. Navigate to `https://gemini.google.com/gem/677970b32bbb`
2. Type `go` and submit
3. Use `get_page_text` to extract the 6 JSON prompt blocks from the response

---

## Step 2: Submit Each Prompt to Grok Imagine

Repeat the following for each of the 6 prompts:

### a. Open tab and navigate
```
tabs_create_mcp → navigate to https://grok.com/imagine → wait 3 seconds
```

### b. Make the tab the active Chrome foreground tab
```
computer.screenshot(tabId)
```
**This step is required before typing.** `computer.type` sends keystrokes to whichever Chrome tab is currently the active foreground window — taking a screenshot forces this tab to be it.

### c. Focus the TipTap editor via JavaScript
Direct coordinate clicks don't work — the outer container has `pointer-events: none`, so clicks pass through to gallery images underneath. Use JS to dispatch events directly on the editor element:

```javascript
const editor = document.querySelector('.tiptap.ProseMirror');
const rect = editor.getBoundingClientRect();
['mousedown', 'mouseup', 'click'].forEach(type => {
  editor.dispatchEvent(new MouseEvent(type, {
    bubbles: true, cancelable: true,
    clientX: rect.left + 200, clientY: rect.top + 10
  }));
});
editor.focus();
```

Verify: `document.activeElement.className` should contain `tiptap ProseMirror`

### d. Type the JSON prompt
```
computer.type(tabId, <JSON string>)
```

Verify: `document.querySelector('.tiptap.ProseMirror').textContent.substring(0, 50)` should show the start of the JSON.

### e. Submit
```
find(tabId, "Submit button") → left_click(tabId, ref)
```

**Confirmation signal:** the tab title changes from `Imagine - Grok` to the full JSON string. If it navigates to the Discover page instead, the editor content was empty — retry from step c.

### f. Wait 2 seconds
The tab is already in the foreground, so Grok starts rendering immediately. Wait 2 seconds before opening the next tab.

---

## Key Technical Notes

| Issue | Cause | Fix |
|-------|-------|-----|
| Clicking input by coordinate focuses a background element | Outer container has `pointer-events: none` | Use JS MouseEvent dispatch on the editor element directly |
| `document.execCommand('insertText')` doesn't work | Does not update React/TipTap state | Use `computer.type` after JS focus |
| Typing goes to wrong tab | `computer.type` targets the active Chrome foreground window, not the tabId | Take a screenshot of the target tab first to make it foreground |
| Submit navigates to Discover page | Editor content was empty when submitted | Always verify textContent before clicking Submit |
| Grok doesn't render images | Tab is in the background when submitted | The tab must be the active foreground tab — the screenshot step handles this |

---

## The 6 Prompts

All prompts use `"aspect_ratio": "9:16"` and the `"rendering": "Old washed-out fantasy illustration"` style.

| # | Title | Lighting |
|---|-------|---------|
| 1 | The Last Sentinel | Pale moonlit silver |
| 2 | Ritual of the Ash Grove | Cold teal haze and ember glow |
| 3 | Monarch of the Ruined Peak | Smoky crimson storm light |
| 4 | The Silent Cathedral | Dusty blue shafts and murky shadows |
| 5 | Wanderer of the Ash Plains | Muted violet haze |
| 6 | Grave of the First King | Blood-red moonlight and smoky shadows |

Prompts are regenerated fresh each run by the Gemini gem — the titles and themes above are the expected output but may vary slightly run to run.
