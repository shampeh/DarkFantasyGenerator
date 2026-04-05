
```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║    ██████╗  █████╗ ██████╗ ██╗  ██╗    ███████╗ █████╗ ███╗   ██╗          ║
║    ██╔══██╗██╔══██╗██╔══██╗██║ ██╔╝    ██╔════╝██╔══██╗████╗  ██║          ║
║    ██║  ██║███████║██████╔╝█████╔╝     █████╗  ███████║██╔██╗ ██║          ║
║    ██║  ██║██╔══██║██╔══██╗██╔═██╗     ██╔══╝  ██╔══██║██║╚██╗██║          ║
║    ██████╔╝██║  ██║██║  ██║██║  ██╗    ██║     ██║  ██║██║ ╚████║          ║
║    ╚═════╝ ╚═╝  ╚═╝╚═╝  ╚═╝╚═╝  ╚═╝   ╚═╝     ╚═╝  ╚═╝╚═╝  ╚═══╝          ║
║                                                                              ║
║             F A N T A S Y   I M A G E   G E N E R A T O R                  ║
║                          v1.0 - PROPER                                       ║
║                                                                              ║
╠══════════════════════════════════════════════════════════════════════════════╣
║  RELEASE . . : DarkFan.v1.0-WRAITH          SIZE . . . : 1 x claude        ║
║  DATE  . . . : 2026-04-04                   TYPE . . . : automation        ║
║  FORMAT  . . : browser / grok.com           OS   . . . : win / mac / lin   ║
║  LANGUAGE  . : english                      REQS . . . : chrome + claude   ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

## RELEASE NOTES

After weeks of failed attempts, pointer-events-none nightmares, and more
empty form submissions than we care to count, WRAITH is proud to drop the
first working release of the Dark Fantasy Image Generator automation flow.

This is the real deal. No cracks, no trainers. Just 6 cinematic dark fantasy
images generating in parallel tabs while you go touch grass.

---

## WHAT IS THIS

An automated workflow that:

1. Hits the Gemini Dark Fantasy gem and pulls 6 JSON image prompts
2. Opens 6 Grok Imagine tabs
3. Submits each prompt using a cursed-but-working TipTap focus method
4. Leaves all 6 tabs rendering simultaneously in the foreground

All images render at **9:16 vertical** in an **old washed-out fantasy
illustration** aesthetic. Think faded pigments, matte surfaces, dusty
desaturated vibes. No glossy CGI slop.

---

## THE SIX SCENES

```
  01. The Last Sentinel       [ moonlit knight on crumbling citadel cliff  ]
  02. Ritual of the Ash Grove [ hooded pilgrim, teal mist, stone arch      ]
  03. Monarch of the Ruined   [ antler-crowned throne, crimson storm sky   ]
  04. The Silent Cathedral    [ skeletal priest, shattered stained glass   ]
  05. Wanderer of the Ash     [ colossal stone beast, violet haze, mist   ]
  06. Grave of the First King [ blood-red moon, grave mystic, wasteland   ]
```

---

## INSTALL NOTES

```
  1. open chrome
  2. have claude running in cowork mode
  3. run the flow (see darkfantasygenerator.md for full technical notes)
  4. wait
  5. collect images
```

Requires an active Grok account with Imagine access.
Gemini gem URL: `https://gemini.google.com/gem/677970b32bbb`

---

## KNOWN ISSUES

- `pointer-events: none` on the input container means you cannot click into
  the prompt field by coordinate. fixed in this release via JS event dispatch.

- Background tab throttling means Grok will not render unless the tab is
  active. this release handles it. earlier releases did not.

- `document.execCommand('insertText')` does not update React state and will
  cause an empty form submission. do not use it. we learned this the hard way.

---

## GREETS

```
  shouts to everyone who said "this should not be hard" and was correct
  shouts to TipTap for being simultaneously the right tool and a nightmare
  shouts to the pale moonlit knight, still standing on that cliff
  no shouts to pointer-events: none
```

---

## NFO

```
  ┌──────────────────────────────────────────────────────────────────────┐
  │  WRAITH  2026  │  do not re-encode  │  keep the nfo  │  stay grim   │
  └──────────────────────────────────────────────────────────────────────┘
```
