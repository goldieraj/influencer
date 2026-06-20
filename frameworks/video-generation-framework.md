# Video Generation Framework: The Growth Engine

Static images maintain your audience; video (Reels, TikToks, Shorts) is what actually grows your audience in 2026. This framework outlines the exact process for turning static AI images into viral, highly engaging video content.

## 1. The Core Strategy: "Subtle Motion"

The biggest mistake new AI creators make is trying to generate complex, full-body motion (like walking or dancing) entirely with AI. Current models still struggle with temporal consistency over long periods, leading to morphing, extra limbs, or "uncanny valley" movements.

The winning strategy (used by accounts like @lilithhberry and @joanne.kisses) is **Subtle Motion applied to High-Action Contexts**.

### How it works:
1. Generate a static image of the character in a dynamic pose (e.g., mid-jump, holding a basketball, leaning over a counter).
2. Animate ONLY the subtle elements: hair blowing, eyes blinking, chest breathing, camera panning.
3. The brain fills in the rest of the action because the context implies it.

## 2. The Tool Stack (2026)

| Tool | Primary Use Case | Pros | Cons |
|------|------------------|------|------|
| **Wan 2.1 (ComfyUI)** | Local, free generation | Ultimate control, no censorship, free | Requires heavy GPU (24GB+ VRAM) |
| **Kling AI** | Cloud generation | Best-in-class temporal consistency, easy to use | Paid, strict NSFW filters |
| **Luma Dream Machine**| Cloud generation | Excellent for camera movements and cinematic shots | Can struggle with facial consistency |
| **CapCut/Premiere** | Post-production | Essential for audio syncing, color grading, and adding grain | Requires manual editing |

## 3. The Step-by-Step Workflow (Image-to-Video)

This is the standard operating procedure for creating a daily Reel.

### Phase 1: The Perfect Base Image
Your video will only be as good as the image you start with.
1. Generate your base image using Flux + your character LoRA (see Content Creation SOP).
2. **Crucial:** The image MUST be high resolution (at least 1080x1920 for vertical video). Upscale it if necessary.
3. **Crucial:** Ensure there are no AI artifacts (weird hands, fused background objects). Any artifact in the static image will become a glaring, morphing nightmare in the video. Inpaint to fix before animating.

### Phase 2: Animation (Using Wan 2.1 in ComfyUI)
1. Load the Wan 2.1 Image-to-Video workflow in ComfyUI.
2. **Reference Order Discipline:** If using multiple references (e.g., face ref + outfit ref + pose ref), upload them in a strict numbered sequence and use `@image1`, `@image2` tags in your prompt to explicitly lock traits to specific images.
3. **The Motion Prompt (Positive Locks Only):** Describe the motion using positive locks. Do not use negative prohibitions.
   - *Good Prompt (Positive Lock):* `@image1 keeps the same face, hair, and wardrobe throughout. Subtle breathing, slight hair movement in the wind, camera slowly panning right, soft blinking. Boots stay planted on the same ground marks.`
   - *Bad Prompt (Negative Prohibition):* `Don't change the face, don't move the feet, don't morph the background.`
4. **Motion Scale/CFG:** Keep motion scale low (usually around 3.0-5.0). You want subtle, realistic movement, not chaotic morphing.
5. Generate a 3-5 second clip. (Most viral reels are under 7 seconds anyway).

### Phase 2.5: The VACE Protocol (Fixing Facial Morphing)
**CRITICAL:** Wan 2.1 and Kling often cause the character's face to morph or lose consistency during movement. You MUST fix this before posting.
1. **Extract Frames:** Extract the generated video into individual PNG frames.
2. **Batch FaceDetailer:** Run the image sequence through a ComfyUI batch `FaceDetailer` workflow.
3. **Re-apply LoRA:** The FaceDetailer will detect the face in every frame, re-apply your specific Flux Character LoRA, and paste it back.
4. **Recompile:** Recombine the frames into a video. This guarantees 100% facial consistency throughout the motion.

### Phase 3: Post-Production (The 70/30 Rule)
**CRITICAL MINDSET:** AI only gets video to 70% realism. The remaining 30% of realism comes from traditional post-production. Raw AI video often looks "too smooth" or plastic. The edit bay is where you sell the illusion.
1. Import the clip into CapCut or Premiere.
2. **Add Film Grain:** Add 10-15% film grain. This hides AI smoothing artifacts and makes it look like it was shot on a phone.
3. **Add Camera Shake:** Add a very subtle "handheld camera" effect. Perfect tripod stability screams "AI."
4. **Color Grading:** Apply a slight filter (e.g., VSCO-style) to unify the colors and shift away from the default AI color science.
5. **Speed Ramping:** If the AI motion is slightly unnatural, speed it up by 1.2x or slow it down by 0.8x to hide the imperfections.
6. **Cut Bad Frames:** Ruthlessly cut any frames where the face morphs or fingers blend. A 2-second perfect clip is infinitely better than a 4-second clip that breaks the illusion at the end.

## 4. The Audio Strategy

Audio is 50% of the video. Without good audio, the illusion breaks.

1. **Trending Audio:** For growth, always use trending Instagram audio.
2. **Environmental Sound Design:** If the video is in a gym, add faint gym background noise (weights clanking, distant talking). If outside, add wind and traffic. This anchors the character in reality.
3. **Voice (Advanced):** If the character speaks, use ElevenLabs to clone a consistent voice. Sync the lip movement using a tool like SyncLabs or Wav2Lip (though this is advanced and often looks uncanny—use sparingly).

## 5. Proven Reel Formats to Replicate

Based on the top 100 accounts analyzed, here are the formats you should rotate:

### Format A: The "Accidental" Loop (High Retention)
- **Visual:** A 3-second loop of the character doing something mundane (e.g., looking at phone, then looking up at camera, then looking back down).
- **Audio:** Trending song.
- **Caption:** A relatable, slightly controversial opinion or question.
- **Why it works:** The video is so short it loops multiple times while the user reads the caption, skyrocketing retention metrics.

### Format B: The "Action Tease"
- **Visual:** Character in gym clothes holding a weight, or in a swimsuit adjusting the strap. Subtle breathing motion.
- **Audio:** Upbeat/workout music.
- **Caption:** "Day 45 of the new routine 💪"
- **Why it works:** Sells the lifestyle without requiring complex workout animation.

### Format C: The "Mirror Check"
- **Visual:** Character holding phone to a mirror. Flash glare visible. Subtle shifting of weight from one hip to the other.
- **Audio:** Muffled music (like it's playing in the next room).
- **Caption:** "Fit check before heading out ✨"
- **Why it works:** The phone obscures the mouth (no lip-sync needed), and mirror selfies are inherently intimate and realistic.
