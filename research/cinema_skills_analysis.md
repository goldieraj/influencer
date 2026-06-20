# Cinema Skills Analysis — What to Extract for UGC AI Influencer Pipeline

## Source
- YouTube: https://www.youtube.com/watch?v=4TXaAnittHs
- Notion: https://pyrite-mallow-3b0.notion.site/The-Claude-skills-that-run-my-AI-Cinema-workflow-got-an-UPGRADE-Here-s-Why-36d49da027d780ff928ef70a16148369
- Skills: banana-pro-director-2.0, cinema-worldbuilder-pro-2.0

## Key Techniques to ADAPT (Not Copy) for UGC Influencer Content

### 1. Gray Background Character Builds (CRITICAL)
- Build character on **mid-gray seamless** background, NOT white
- White = plastic, over-lit, AI-portrait look
- Gray gives model a value to read skin tones against, lets shadows work naturally
- Result: actual dimensionality instead of render look
- **UGC adaptation:** Use this for ALL LoRA training reference images and character sheets

### 2. Camera Described by Behavior, Not Brand Names
- Old way: "ARRI Alexa 35, Panavision Ultra Vintage 75mm"
- New way: "wide-latitude cinema capture, vintage 75mm 2x anamorphic character at a wide aperture"
- The model pattern-matches on vibe, not actual gear rendering
- **UGC adaptation:** For our content, describe as "smartphone camera, natural daylight, slight overexposure, casual framing" — same principle, different target aesthetic

### 3. Anti-Plastic Skin Language (CRITICAL FOR REALISM)
- Per-zone specular kill: zero shine on forehead, nose bridge, cheekbones, temples, chin
- Real peach fuzz at jaw and hairline
- Subsurface scattering
- Skin reads matte without going harsh
- **UGC adaptation:** MUST include in all prompts. This is what separates "obviously AI" from "wait, is she real?"

### 4. Volumetric Depth / Atmospheric Language
- Real cinematography has atmosphere — light cutting through haze
- Particulate in air, light shafts, atmospheric falloff between subject and background
- Flat air = AI giveaway
- **UGC adaptation:** For UGC, translate to "natural room haze from cooking/shower steam, dust particles in window light, morning fog on beach" — organic reasons for atmosphere

### 5. Subject Lock System (CRITICAL FOR CONSISTENCY)
- Each character gets dedicated reference image slot + Subject Lock block
- Pins: pose, gaze, contact points, state
- Does NOT re-describe what reference sheet already carries
- Only describes what CHANGES shot to shot
- **UGC adaptation:** When generating multiple images of same character, always use this discipline — reference carries identity, prompt only carries the new context

### 6. Frame Map First, Identity Second
- Anchor subjects to screen positions, depth layers, contact points BEFORE describing who they are
- Model can't drift character to wrong side if frame is locked first
- **UGC adaptation:** Even for simple selfies, specify "subject centered, phone held at chest height, mirror reflection showing full body, bathroom tiles visible in background" — spatial anchoring

### 7. 6-Panel Reference Sheet Method
- Generate base character → Create 6-panel sheet (front, 3/4, side, full body, hands, details)
- Use this as LoRA training data AND as generation reference
- **UGC adaptation:** This IS our LoRA training dataset method. Generate 30-50 images of character in different angles on gray background.

### 8. Outfit Swap Technique
- Generate outfit on generic model (gray background)
- Then swap face/body of your character onto the outfit
- Keeps outfit accuracy while maintaining character consistency
- **UGC adaptation:** Perfect for "outfit of the day" content — generate 10 outfits on mannequin, then swap character in

### 9. The 70/30 Rule
- AI gets video to 70% realism
- Remaining 30% = post-production (color grading, pacing, cutting bad frames, sound design)
- **UGC adaptation:** For UGC the bar is lower, but still: add grain, slight color shift, audio (ambient room sound, music playing from speaker), crop to 9:16, add slight shake in post

### 10. Positive Locks Over Negative Prohibitions
- "Don't change face" → "@image1 keeps the same face, hair, wardrobe throughout"
- "Don't drift" → "Boots stay planted on the same ground marks across the full runtime"
- Seedance/video models respond far better to positive instructions
- **UGC adaptation:** Same principle applies to ALL image generation. Never say "no artifacts" — say "clean natural skin texture, consistent lighting"

---

## What NOT to Use for UGC (Too Cinematic)

1. ❌ 2x anamorphic character, oval bokeh — screams "production"
2. ❌ Color-negative film rendition with fine 35mm grain — too stylized for UGC
3. ❌ Vintage lens falloff — UGC uses modern smartphone lenses (sharp edge to edge)
4. ❌ Diegetic audio only rule — UGC uses trending audio/music
5. ❌ 24fps 180° shutter — UGC is 30fps or 60fps smartphone
6. ❌ Complex multi-shot sequences — UGC is single continuous take or simple cuts
7. ❌ Elaborate Scene & Mood blocks — UGC is casual, not dramatic

---

## The UGC Translation Layer

| Cinema Skill Technique | UGC Equivalent |
|---|---|
| Gray background character build | Same — use for LoRA training |
| Anti-plastic skin language | Same — CRITICAL for all content |
| Subject Lock system | Same — use for consistency |
| 6-panel reference sheet | Same — LoRA training dataset |
| Outfit swap technique | Same — OOTD content |
| Volumetric depth | "Natural room haze, dust in sunlight, steam from shower" |
| Camera behavior description | "iPhone 15 Pro, natural daylight, slightly overexposed, casual angle" |
| Frame Map anchoring | "Subject centered in mirror, phone visible at chest, bathroom tiles behind" |
| 70/30 post-production | Add grain, color shift, ambient audio, slight shake |
| Positive locks | Same — always positive framing in prompts |

---

## Recommendation: Build a UGC-Adapted Skill

Create a simplified version of these skills specifically for AI influencer UGC content:
- Strip all cinematic language
- Replace with smartphone/casual equivalents
- Keep the STRUCTURAL discipline (Subject Lock, Frame Map, positive locks, gray backgrounds)
- Add UGC-specific elements (trending audio, caption overlays, story-style framing)
- Include the anti-plastic skin language as mandatory
- Include metadata stripping as final step
