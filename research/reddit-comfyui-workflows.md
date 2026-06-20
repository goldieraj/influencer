# Reddit r/comfyui - Key Workflow Posts (Browsed with Browser Control)

## Post 1: "2 days ago I asked for a consistent character posing workflow, nobody delivered. So I made one."
- **Author:** u/gentleman339
- **URL:** https://www.reddit.com/r/comfyui/comments/1m5hc43/
- **Upvotes:** 1.4K | **Comments:** 182
- **Flair:** Workflow Included
- **Age:** ~1 year ago

### What It Does:
Generates a consistent character in multiple poses using Wan 2.1 VACE model. Input a reference character image + OpenPose skeleton → outputs the same character in different poses.

### Required Models/Files:
1. **Main Model:** CivitAI model 1796490 (version 2033042) — Wan2.1 T2V 14B variant
   - Link: https://civitai.com/models/1796490?modelVersionId=2033042
2. **Fastest Wan2.1 model:** QuantStack/Wan2.1_T2V_14B_LightX2V_StepCfgDistill_VACE-GGUF
   - Link: https://huggingface.co/QuantStack/Wan2.1_T2V_14B_LightX2V_StepCfgDistill_VACE-GGUF/tree/main
3. **VAE:** Wan 2.1 ComfyUI repackaged VAE
   - Link: https://huggingface.co/Comfy-Org/Wan_2.1_ComfyUI_repackaged/tree/main/split_files/vae
4. **CLIP Model:** umt5-xxl-enc-fp8_e4m3fn.safetensors
   - Link: https://huggingface.co/Kijai/WanVideo_comfy/blob/main/umt5-xxl-enc-fp8_e4m3fn.safetensors
5. **Poses:** OpenPoses Collection
   - Link: https://civitai.com/models/22214/openposes-collection

### Workflow JSON:
- **Pastebin backup:** https://pastebin.com/4QCLFRwp
- **CivitAI page:** https://civitai.com/models/1796490?modelVersionId=2033042

### Performance:
- A600 with 16GB VRAM: ~40 seconds to generate 3 images
- Increase "image size" node to 700/750 for better quality (default is lower)

### Key Tips from Comments:
- Use umt5_xxl_fp8_e4m3fn_scaled.safetensors (the "scaled" version)
- Can use your own custom poses instead of OpenPoses collection
- Quality can be improved by increasing image size node value

---

## Post 2: "Anime to realistic, or vice-versa, or any to any, with unsampler workflow"
- **Author:** u/afinalsin
- **URL:** https://www.reddit.com/r/comfyui/comments/1iwtyrs/
- **Upvotes:** High (top 3 all-time)
- **Flair:** Workflow Included

### What It Does:
Converts anime-style images to photorealistic, or vice versa, using an "unsampler" technique. Could be used to:
- Take anime character designs and make them photorealistic
- Create stylized versions of realistic characters

---

## Post 3: "Been having too much fun with Wan2.1! Here's the ComfyUI workflows I've been using to make awesome videos locally (free)"
- **Author:** u/blackmixture
- **URL:** https://www.reddit.com/r/comfyui/comments/1jbexmu/
- **Upvotes:** 121 comments
- **Flair:** Workflow Included

### What It Does:
Free local video generation workflows using Wan 2.1 in ComfyUI. Directly relevant for creating Reels content.

---

## Related Posts (Sidebar):
- "Creating Consistent Scenes & Characters with AI" — 529 upvotes, 46 comments (1y ago)
- "my ai model, what do you think??" — 222 upvotes, 131 comments (9mo ago)
- "I fixed up the last workflow I shared you can make lots of n..." — 61 upvotes (4mo ago)
- "Animation Ready Rigged" — (7mo ago)

---

## Post 4: u/pleasuremancer - "It's out! 6+ minutes of AI NSFW video" (r/unstable_diffusion)
- **Author:** u/pleasuremancer
- **URL:** https://www.reddit.com/r/unstable_diffusion/comments/1oun2d3/
- **Upvotes:** High | **Comments:** 114
- **Age:** 7 months ago

### What It Does:
Creates 6+ minute long-form NSFW AI video content using entirely free tools. This is the exact workflow needed for Fanvue/OF-style content.

### Tools Used (ALL FREE):
1. **ComfyUI** — for diffusion models (image generation + video generation)
2. **DaVinci Resolve** — for video editing (free version)
3. **Illustrious (SDXL)** — base model for image generation
4. **Wan 2.2 I2V** — for animating static images into video clips
5. **LoRA** — custom trained for character consistency

### Workflow:
1. Generate base images of character using Illustrious + custom LoRA
2. Select best images (throw away ~80%)
3. Animate selected images using Wan 2.2 Image-to-Video
4. Edit clips together in DaVinci Resolve
5. Add camera movement, music, sound
6. Export final video (6+ minutes)

### Key Insight from pleasuremancer:
- "Everything I use is free"
- Uses ComfyUI locally
- DaVinci Resolve for editing
- The quality shown was enough to get significant engagement on Reddit
- Posts full videos on X/Twitter (only platform that allows long NSFW video)
- HD downloads on Patreon (monetization)

### Monetization Model:
- Free previews on Reddit/X → drive to Patreon for HD downloads
- Same model works for Fanvue (replace Patreon with Fanvue subscription)

---

## Post 5: "Creating Consistent Scenes & Characters with AI" (r/comfyui)
- **Upvotes:** 529 | **Comments:** 46
- **Age:** ~1 year ago
- **URL:** https://www.reddit.com/r/comfyui/comments/[check sidebar]

### Relevance:
529 upvotes makes this one of the most popular posts ever on r/comfyui. Directly addresses the #1 challenge for AI influencers: keeping the same character consistent across different scenes and poses.

---

## Key Workflow Links Summary (All Verified via Browser):

| Resource | URL | Purpose |
|----------|-----|---------|
| Consistent Character Posing Workflow | https://pastebin.com/4QCLFRwp | ComfyUI workflow JSON |
| Wan 2.1 VACE Model (Fast) | https://huggingface.co/QuantStack/Wan2.1_T2V_14B_LightX2V_StepCfgDistill_VACE-GGUF/tree/main | Fastest video model |
| Wan 2.1 VAE | https://huggingface.co/Comfy-Org/Wan_2.1_ComfyUI_repackaged/tree/main/split_files/vae | Required VAE |
| Text Encoder (CLIP) | https://huggingface.co/Comfy-Org/Wan_2.1_ComfyUI_repackaged/resolve/main/split_files/text_encoders/umt5_xxl_fp8_e4m3fn_scaled.safetensors | Required text encoder |
| OpenPoses Collection | https://civitai.com/models/22214/openposes-collection | Pose references |
| CivitAI Workflow Page | https://civitai.com/models/1796490?modelVersionId=2033042 | Full workflow + model |
