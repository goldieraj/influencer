# Technical Guides: ComfyUI Setup & LoRA Training

This document provides the exact technical setup required to execute the Content Creation SOP. It assumes you are setting up a local machine or a cloud GPU instance (RunPod, Vast.ai) with at least 24GB VRAM (RTX 3090/4090 or A5000).

---

## Part 1: ComfyUI Master Setup

### 1. Installation
1. Clone the official repository:
   `git clone https://github.com/comfyanonymous/ComfyUI.git`
2. Install dependencies:
   `pip install -r requirements.txt`
3. Install the ComfyUI Manager (CRITICAL for downloading custom nodes):
   `cd custom_nodes`
   `git clone https://github.com/ltdrdata/ComfyUI-Manager.git`
4. Restart ComfyUI.

### 2. Essential Custom Nodes to Install (via Manager)
Open the ComfyUI Manager and install the following:
- **ComfyUI-Custom-Scripts (pysssss):** Adds QoL features like snapping nodes and saving text.
- **ComfyUI-Advanced-ControlNet:** Required for precise pose control.
- **ComfyUI_IPAdapter_plus:** Required for facial consistency across generations.
- **ComfyUI-Impact-Pack:** Essential for detailing, upscaling, and face-fixing.
- **ComfyUI-UltimateSDUpscale:** The best node for high-res upscaling without changing the image.
- **ComfyUI-VideoHelperSuite:** Required if you plan to do Image-to-Video locally.

### 3. Required Models (Download to `/models/checkpoints/`)
For the highest realism in 2026, you must use Flux.
1. **Base Model:** Flux.1 [dev] (Requires 24GB VRAM) or Flux.1 [schnell] (Faster, less VRAM).
2. **Alternative (SDXL):** Juggernaut XL v9 or RealVisXL V4.0 (If you only have 12-16GB VRAM).

### 4. Required ControlNet Models (Download to `/models/controlnet/`)
- `control_v11p_sd15_openpose.pth` (For SD1.5)
- `thibaud_xl_openpose.safetensors` (For SDXL)
- *Note: Flux ControlNets are currently in active development; check Civitai for the latest Flux-compatible pose models.*

---

## Part 2: Character LoRA Training Guide

A LoRA (Low-Rank Adaptation) is how you teach the AI what your specific character looks like. Without a good LoRA, your character will look like a different person in every photo.

### 1. Dataset Preparation (The Most Important Step)
The AI is only as good as the data you feed it.
- **Quantity:** Gather 30-50 images of your character.
- **Quality:** High resolution, clear lighting, no blurry or heavily filtered photos.
- **Variety:** 
  - 10 Close-up face shots (different angles)
  - 15 Half-body shots (different outfits)
  - 15 Full-body shots (different environments/poses)
- **Consistency:** Ensure the hair color, eye color, and facial structure are identical across all images.

### 2. Image Cropping & Sizing
- Crop all images to 1024x1024 (for SDXL/Flux training).
- Use a tool like Birme (birme.net) for bulk cropping.

### 3. Captioning (Tagging)
You must tell the AI what is in the image so it knows what to associate with your character.
- Use an auto-tagger (like WD14 Tagger).
- **CRITICAL:** Use a unique trigger word that the AI doesn't already know (e.g., `zxcvbn_woman`).
- Remove tags that describe the character's permanent features (e.g., if she always has brown hair, remove "brown hair" from the tags so the AI learns that "brown hair" is part of the `zxcvbn_woman` concept).
- Keep tags that describe the outfit, pose, and background.

### 4. Training using FluxGym or Kohya_ss
For local training, Kohya_ss is the standard.
1. Install Kohya_ss: `git clone https://github.com/bmaltais/kohya_ss.git`
2. Run the GUI.
3. **Recommended Settings for Flux/SDXL:**
   - Optimizer: AdamW8bit
   - Learning Rate: 0.0001
   - Text Encoder LR: 0.00005
   - Network Rank (Dim): 32 or 64
   - Network Alpha: 16 or 32
   - Epochs: 10
   - Batch Size: 1-4 (depending on VRAM)
4. Start training. It will take a few hours depending on your GPU.

### 5. Testing the LoRA
1. Move the generated `.safetensors` file to your ComfyUI `/models/loras/` folder.
2. Generate a simple prompt: `zxcvbn_woman, simple portrait, white background`.
3. Test it at different weights (0.5, 0.7, 1.0).
4. If the face looks "deep-fried" or distorted at 1.0, the LoRA is overtrained. Use it at a lower weight (0.6-0.8).

---

## Part 3: The "Pleasuremancer" Workflow (Advanced NSFW)

Based on the leaked r/unstable_diffusion workflow used by top creators:

1. **Base Generation:** Flux Dev + Character LoRA (Weight 0.8).
2. **Pose Control:** OpenPose fed into Flux ControlNet.
3. **Face Fixing (The Secret):**
   - The initial generation often messes up the face if the body is doing a complex pose.
   - Use the `FaceDetailer` node (from Impact Pack).
   - It automatically detects the face using a YOLO model, crops it, runs it through the base model again at a higher resolution with a specific "beautiful face" prompt, and pastes it seamlessly back onto the body.
4. **Anatomy Fixing:**
   - Use `MeshGraphormer` for hands. If hands are mangled, mask them and use an inpainting node specifically prompted for "perfect hands, 5 fingers."
5. **Upscaling:** Ultimate SD Upscale (Tile size 512, Denoise 0.25) to bring the final image to 4K resolution before posting to Fanvue.
