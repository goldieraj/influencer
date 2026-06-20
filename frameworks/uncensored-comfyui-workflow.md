# Uncensored Local Generation Workflow (Suggestiveness 7-10)

To generate the high-converting, highly suggestive content (7-10 on the suggestiveness scale) required for Fanvue/OnlyFans funnels, you must move off commercial APIs (which have strict NSFW/NSFW-adjacent filters) and run generation locally or via uncensored cloud GPUs.

This document outlines the standard industry workflow for generating "Playful Tease" and explicit-adjacent content using ComfyUI and Stable Diffusion/Flux.

## Infrastructure Requirements

### Option A: Local Hardware (Recommended for Privacy/Cost)
*   **GPU:** NVIDIA RTX 3090, 4080, or 4090 (Minimum 16GB VRAM, 24GB recommended for Flux).
*   **Software:** ComfyUI (node-based, allows for complex face-locking and upscaling workflows).

### Option B: Cloud GPU (Recommended for Mac Users)
*   **Services:** RunPod, Vast.ai, or Tensor.Art (Web-based).
*   **Cost:** ~$0.20 - $0.50 per hour.

## The Model Stack

The current state-of-the-art for hyper-realistic, uncensored influencer content relies on specific models.

1.  **Base Model:** 
    *   *Pony Diffusion V6 XL* (SDXL based) - Excellent for stylized/anime/e-girl aesthetics (perfect for Yuki). Highly responsive to NSFW prompting.
    *   *Juggernaut XL* or *RealVisXL* - Best for photorealistic, Instagram-style content (perfect for Mei Lin, Sasha, Luna).
    *   *Flux.1 [dev]* - The current king of realism, but requires a 24GB GPU and specific uncensored LoRAs to push past its safety training.

2.  **Face Consistency (The "Subject Lock"):**
    *   **IP-Adapter / FaceID:** This is the critical node in ComfyUI. You feed it 1-3 reference images of your character (generated from the safe API), and it locks that exact face onto the new generation.
    *   **Reactor Node:** An alternative/addition to IP-Adapter for perfect face swapping post-generation.

3.  **Pose Control:**
    *   **ControlNet (OpenPose / Depth):** You extract the pose from a viral Instagram photo (e.g., a Joanne Kisses mirror selfie) and force your AI model to replicate that exact pose and camera angle.

## The ComfyUI Workflow (Step-by-Step)

This is the standard node routing for an AI Influencer pipeline:

### 1. The Input Stage
*   **Checkpoint Loader:** Load your base model (e.g., RealVisXL).
*   **Positive Prompt:** Write your uncensored prompt. (e.g., `hyperrealistic, 24yo asian woman, taking mirror selfie in bedroom, wearing tiny black string bikini, heavy cleavage, arched back, seductive bedroom eyes, flawless glowing skin, iPhone photo, high contrast`).
*   **Negative Prompt:** `ugly, deformed, plastic, 3d render, bad anatomy, bad hands, extra fingers, text, watermark`.

### 2. The Control Stage (The Secret Sauce)
*   **Load Image (Reference Pose):** Upload a screenshot of a viral pose.
*   **ControlNet Apply:** Run the reference image through an OpenPose preprocessor and connect it to the ControlNet node. This forces the model to use the viral pose.
*   **Load Image (Character Face):** Upload your base character reference (e.g., Mei Lin's face).
*   **IP-Adapter Apply:** Connect the face reference to the IP-Adapter node. Set the weight to ~0.7-0.8 (high enough to look like her, low enough to allow the new lighting/expression to blend naturally).

### 3. The Generation Stage
*   **KSampler:** This does the actual generation. 
    *   *Steps:* 30-40
    *   *CFG Scale:* 5.0 - 7.0
    *   *Sampler:* DPM++ 2M Karras (standard for realism)

### 4. The Refinement Stage (Crucial for UGC feel)
*   **Face Detailer / Reactor:** Automatically detects the face in the generated image and does a second pass to fix any distortions and ensure it perfectly matches your character.
*   **Film Grain / Noise Node:** Add a slight amount of ISO noise (0.02 - 0.05) to kill the "AI plastic" look and make it feel like a real smartphone photo.

## Prompting for High Suggestiveness (Uncensored)

When you are off the commercial APIs, you can use the exact language that drives clicks.

**The "Caught Changing" Hook:**
> `candid smartphone photo, mirror selfie, 24yo woman, caught changing in bedroom, wearing only unhooked bra and panties, looking at camera with surprised flirty expression, messy hair, glowing skin, flash photography, messy room`

**The "Extreme Arch" Hook:**
> `low angle shot from behind, 24yo woman in gym, wearing tight transparent yoga pants, extreme arched back, looking over shoulder with seductive bedroom eyes, sweaty glowing skin, squat rack background, high contrast lighting`

## Summary of the Dual-Pipeline Strategy

1.  **Safe Pipeline (Manus / OpenAI / Midjourney):** Use this for generating the character concepts, the safe lifestyle grid posts (coffee shops, shopping, casual gym), and building the "real life" narrative.
2.  **Uncensored Pipeline (Local ComfyUI):** Use this for the 30% of content that drives actual funnel conversions — the mirror selfies, the swimwear, the suggestive "accidental" shots, and the explicit-adjacent Fanvue teasers. Use ControlNet to copy poses directly from viral competitors.
