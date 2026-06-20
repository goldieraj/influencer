# Content Creation Standard Operating Procedure (SOP)

This framework provides the exact step-by-step process for generating hyper-realistic, consistent AI influencer content that drives engagement and converts to paid subscriptions.

## 1. The Realism Hierarchy

Before generating any content, understand the hierarchy of realism. The goal is not just "looking real," but "feeling real."

| Level | Component | Importance | Execution Method |
|-------|-----------|------------|------------------|
| 1 | **Skin Texture** | Critical | Use Flux models with low CFG scale (2.5-3.5) and specific prompt keywords: `raw photo, pores, imperfections, 8k uhd, dslr, soft lighting, high quality`. Avoid terms like `perfect, flawless, smooth`. |
| 2 | **Lighting** | High | Lighting must match the environment. Use keywords like `golden hour lighting, harsh flash, ring light, natural window light`. The shadows must fall correctly across the face and body. |
| 3 | **Pose & Anatomy** | High | Use ControlNet/OpenPose to force natural, relaxed poses. Avoid stiff, straight-on shots. Use keywords like `candid, mid-movement, relaxed posture, asymmetrical pose`. |
| 4 | **Environment Integration** | Medium | The character must interact with the environment. Use keywords like `leaning on counter, holding coffee cup, sitting on edge of bed`. Add depth of field (`bokeh, blurred background`) to separate subject from background. |
| 5 | **Consistency** | Critical | Use a custom LoRA trained on 30-50 high-quality images of the character. Use IP-Adapter for additional facial consistency. Keep prompts consistent regarding hair, eye color, and body type. |

## 2. The Production Pipeline (ComfyUI)

### Step 1: Base Image Generation (Text-to-Image)
1. **Model:** Flux.1 Dev (or a specialized fine-tune like Juggernaut XL if using SDXL).
2. **LoRA:** Load your custom character LoRA (weight 0.7-0.9 to avoid deep-frying).
3. **Prompting Structure:**
   - **Subject:** `[Character Name] woman, 22yo, [ethnicity], [hair style/color], [eye color]`
   - **Action/Pose:** `taking a mirror selfie, holding phone, casual posture`
   - **Outfit:** `wearing oversized grey sweatpants, black crop top`
   - **Environment:** `in a messy bedroom, natural light from window`
   - **Quality/Style:** `raw photo, smartphone photo, candid, flash photography, realistic skin texture, film grain`
4. **Settings:**
   - Steps: 20-30
   - CFG: 3.0-4.0 (lower CFG = more realism with Flux)
   - Sampler: euler
   - Scheduler: simple

### Step 2: Pose Control (Optional but Recommended)
If you need a specific pose (e.g., for a brand deal or specific trend):
1. Find a reference image of a real person in the desired pose.
2. Run it through the OpenPose preprocessor node in ComfyUI.
3. Feed the OpenPose skeleton into a ControlNet node connected to your base model.
4. Set ControlNet strength to 0.6-0.8 (allows some flexibility while maintaining the general pose).

### Step 3: Facial Consistency Enforcement (IP-Adapter)
Even with a LoRA, faces can drift. Use IP-Adapter to lock it in:
1. Load 1-3 "perfect" reference images of your character's face.
2. Connect them to an IP-Adapter FaceID node.
3. Set weight to 0.4-0.6 (too high will make the face look pasted on).

### Step 4: Upscaling and Detailing
1. Run the output through an Ultimate SD Upscale node (or similar).
2. Use a denoise strength of 0.2-0.3 (adds detail without changing the image).
3. Upscale by 1.5x - 2x.
4. Use a realistic upscaler model like `4x-UltraSharp` or `ESRGAN`.

### Step 5: Video Generation (The Growth Engine)
Static images maintain the audience; video (Reels/TikToks) grows the audience.
1. **Tool:** Wan 2.1 or Kling AI (currently the best open-source video models).
2. **Workflow:** Image-to-Video (I2V).
3. **Input:** The upscaled image from Step 4.
4. **Prompt:** Describe the subtle motion. `subtle breathing, slight hair movement in wind, looking at camera, blinking`.
5. **Settings:** Keep motion scale low to avoid morphing/distortion.
6. **Audio:** Add trending audio or AI-generated voiceover in post-production (CapCut/Premiere).

## 3. Content Strategy & Formats

Based on analysis of 100+ top accounts, these formats drive the highest engagement:

### Format 1: The "Activity" Reel (Highest Growth)
- **Concept:** The character doing something normal, not just posing.
- **Examples:** Shooting a basketball, cooking, doing yoga, walking a dog.
- **Why it works:** Bypasses the "AI radar" because people focus on the action, not just the face. Feels authentic.
- **Execution:** Generate an image of the action, use I2V to add subtle motion, add environmental sound design.

### Format 2: The "Mirror Selfie" (Highest Conversion)
- **Concept:** A classic bathroom/bedroom mirror selfie.
- **Why it works:** Inherently intimate and realistic. The smartphone obscures part of the face, making it easier to generate flawlessly.
- **Execution:** Prompt for `mirror selfie, holding phone, flash glare`. Ensure the phone looks realistic (AI often messes up hands holding phones, so use ControlNet or inpainting to fix).

### Format 3: The "Engagement Bait" Question
- **Concept:** A simple lifestyle shot with a caption that demands an answer.
- **Why it works:** Comments drive the Instagram algorithm.
- **Execution:** Image of character looking slightly confused or thoughtful. Caption: "Do you guys actually read captions or just look at the pictures? Be honest 🤭"

### Format 4: The "Accidental/Candid" Shot
- **Concept:** Looks like someone else took the photo when she wasn't ready.
- **Why it works:** Breaks the "perfect Instagram model" mold. Builds parasocial connection.
- **Execution:** Prompt for `candid, blurry background, motion blur, looking away from camera, laughing`.

## 4. Quality Control & Metadata Stripping (CRITICAL)

Before any image touches a social platform, it must pass this checklist and be stripped of AI metadata.

### The Metadata Vulnerability
Instagram, TikTok, and Pinterest actively scan uploads for C2PA, XMP, and EXIF metadata embedded by ComfyUI, Stable Diffusion, and Photoshop. If found, your post is automatically labeled "Made with AI," which suppresses reach and destroys the illusion.

**Mandatory Upload Prep:**
1. Generate final image.
2. Go to [removeailabel.com](https://removeailabel.com/) or [aimetadatacleaner.com](https://aimetadatacleaner.com/).
3. Upload image and strip all C2PA, XMP, and PNG text chunks.
4. Download the cleaned image. *This is the only file you upload.*

### Visual QC Checklist

Before posting ANY piece of content, verify:

- [ ] **Hands:** Do they have 5 fingers? Are they blending into objects? (Inpaint to fix).
- [ ] **Eyes:** Are the pupils round and looking in the correct direction? Do they match the character's eye color?
- [ ] **Skin:** Is there texture? Does it look too smooth/plastic? (Add noise/grain in post if needed).
- [ ] **Lighting:** Do the shadows on the face match the shadows in the background?
- [ ] **Teeth:** If smiling, do the teeth look human (not too many, not perfectly straight white blocks)?
- [ ] **Background:** Are there weird AI artifacts in the background (fused objects, floating items)? (Crop them out or blur them).
- [ ] **Consistency:** Does this look exactly like the character from yesterday's post?

## 5. Posting Schedule & Ratios

- **Frequency:** 1 Reel daily + 1 Static Post/Carousel every 2 days.
- **Stories:** 3-5 Stories daily (mix of lifestyle, Q&A, and subtle funnel links).
- **Content Mix:**
  - 60% SFW Lifestyle/Activity (Growth content)
  - 30% Suggestive/Thirst Traps (Conversion content)
  - 10% Direct Funnel/Promo (Sales content)

*Note: Never post explicit content on Instagram. Keep it PG-13 to avoid shadowbans. Save the explicit content for the paid platforms.*
