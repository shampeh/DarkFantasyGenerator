```
////////////////////////////////////////////////////////////////////////////////
//                                                                            //
//  ██████╗  █████╗ ██████╗ ██╗  ██╗    ███████╗ █████╗ ███╗  ██╗████████╗  //
//  ██╔══██╗██╔══██╗██╔══██╗██║ ██╔╝    ██╔════╝██╔══██╗████╗ ██║╚══██╔══╝  //
//  ██║  ██║███████║██████╔╝█████╔╝     █████╗  ███████║██╔██╗██║   ██║     //
//  ██║  ██║██╔══██║██╔══██╗██╔═██╗     ██╔══╝  ██╔══██║██║╚████║   ██║     //
//  ██████╔╝██║  ██║██║  ██║██║  ██╗    ██║     ██║  ██║██║  ███║   ██║     //
//  ╚═════╝ ╚═╝  ╚═╝╚═╝  ╚═╝╚═╝  ╚═╝   ╚═╝     ╚═╝  ╚═╝╚═╝  ╚══╝   ╚═╝    //
//                                                                            //
//              [ Gemini -> Grok Dark Fantasy Image Pipeline v1.0 ]          //
//                                                                            //
////////////////////////////////////////////////////////////////////////////////

 ╔══════════════════════════════════════════════════════════════════════════╗
 ║  RLS  DATE  :  2026                                                      ║
 ║  RLS  TYPE  :  Browser Automation / AI Image Generation Workflow         ║
 ║  SERVICES   :  Gemini (prompt gen) -> Grok Imagine (image gen)           ║
 ║  OUTPUT     :  6 x Dark Fantasy images, 9:16 aspect ratio                ║
 ║  METHOD     :  Claude in Chrome / JavaScript injection                   ║
 ╚══════════════════════════════════════════════════════════════════════════╝

 ┌──────────────────────────────────────────────────────────────────────────┐
 │  :: RELEASE NOTES                                                        │
 └──────────────────────────────────────────────────────────────────────────┘

   Two-stage AI image pipeline. Stage one hits a custom Gemini gem to
   generate 6 structured JSON image prompts in the dark fantasy aesthetic.
   Stage two submits each prompt to Grok Imagine in its own tab via JS
   injection — all 6 generate in parallel.

   Do not deviate from the JavaScript submission method. Clicking the
   Grok input directly does not work reliably. See nukes section.

 ┌──────────────────────────────────────────────────────────────────────────┐
 │  :: URLS                                                                 │
 └──────────────────────────────────────────────────────────────────────────┘

   Gemini Dark Fantasy 1.0 Gem   https://gemini.google.com/gem/677970b32bbb
   Grok Imagine                  https://grok.com/imagine

 ┌──────────────────────────────────────────────────────────────────────────┐
 │  :: STEP 1 — GENERATE PROMPTS VIA GEMINI                                 │
 └──────────────────────────────────────────────────────────────────────────┘

   01.  Navigate to the Gemini gem URL above
   02.  Click into the "Ask Gemini" input at the bottom
   03.  Type  go  and press Enter
   04.  Gemini responds with 6 JSON blocks in this format:

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

   05.  Extract all 6 blocks using  get_page_text
        Compact each block to a single line — no line breaks

 ┌──────────────────────────────────────────────────────────────────────────┐
 │  :: STEP 2 — SUBMIT TO GROK IMAGINE                                      │
 └──────────────────────────────────────────────────────────────────────────┘

   For each of the 6 prompts:

   01.  Open a new tab and navigate to  https://grok.com/imagine
   02.  Inject the compacted JSON and submit via JavaScript:

          const ce = document.querySelector('[contenteditable]');
          ce.focus();
          document.execCommand('insertText', false, YOUR_JSON_STRING_HERE);

          ce.dispatchEvent(new KeyboardEvent('keydown',  {key:'Enter',code:'Enter',keyCode:13,which:13,bubbles:true}));
          ce.dispatchEvent(new KeyboardEvent('keypress', {key:'Enter',code:'Enter',keyCode:13,which:13,bubbles:true}));
          ce.dispatchEvent(new KeyboardEvent('keyup',    {key:'Enter',code:'Enter',keyCode:13,which:13,bubbles:true}));

   03.  Confirm: tab title will update to the JSON content once registered
   04.  Repeat for all 6 prompts — each in its own tab

   All 6 tabs generate simultaneously. Scroll down on each tab to see output.

 ┌──────────────────────────────────────────────────────────────────────────┐
 │  :: GROK SETTINGS                                                        │
 └──────────────────────────────────────────────────────────────────────────┘

   Default settings are correct — do not change them.

   Mode           Image
   Quality        Quality
   Aspect Ratio   9:16

 ┌──────────────────────────────────────────────────────────────────────────┐
 │  :: KNOWN ISSUES / NUKES                                                 │
 └──────────────────────────────────────────────────────────────────────────┘

   [!]  Do NOT click the "Type to imagine" floating bar directly
        It sits over the image gallery — clicks land on gallery images
        Always use the JavaScript injection method above

   [!]  computer.key('Return') does NOT work on background tabs
        Always use the JS KeyboardEvent dispatch method

   [!]  Submit the FULL compacted JSON block — not just the prompt field
        Grok reads the entire object

   [i]  Images generate in the background
        Scroll down on each tab to see them appear

   [i]  Tab title updates to the JSON content on successful submission

////////////////////////////////////////////////////////////////////////////////
//  Provided as-is for personal use. Use responsibly.                        //
////////////////////////////////////////////////////////////////////////////////
```
