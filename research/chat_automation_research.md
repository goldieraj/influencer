# Chat Automation Research

## Recommended Stack (Easiest Path)

### The Minimum Viable Stack: ~$80/month
1. **Inrō** (€12.99/mo) — Instagram comment-to-DM automation, CRM tagging, Meta-approved
2. **Supercreator / Izzy AI** ($15/mo+) — AI chatting inside OnlyFans/Fanvue, handles 90-95% of conversations
3. **Beacons.ai** (free+) — Link-in-bio + email capture

### Why Supercreator is the Easiest:
- Trained specifically for OF/Fanvue fan conversation context
- Handles PPV upsells, tip requests, retention messaging in creator's voice
- 90-95% automation rate without human input
- Human handover triggered for high-value or sensitive interactions
- From $15/month

### Fanvue Has Its Own API for Custom Chatbots:
- Official API at api.fanvue.com
- Endpoints: GET /chats?filter=unread, GET /chats/{userUuid}/messages, POST /chats/{userUuid}/message
- Can build custom chatbot with Claude/GPT-4 as the brain
- Python or Node.js implementation
- Schedule via cron job to run every 5-15 minutes

### The DIY Route (More Control, More Work):
1. Get Fanvue API access token
2. Build Python script that:
   - Polls for unread messages
   - Feeds conversation history to Claude/GPT-4 with character persona prompt
   - Sends generated reply back via API
3. Run on a cron schedule (every 5-15 min)
4. Cost: Just the LLM API costs (~$20-50/month at scale)

## ComfyUI Workflow Sources

### Official Comfy.org Templates (FREE):
- https://www.comfy.org/workflows/model/wan2-1/ (20 Wan2.1 workflows)
  - Wan 2.1 Image to Video
  - Wan2.1 VACE Control Video
  - Wan2.1 VACE First-Last Frame
  - Wan2.1 VACE Inpainting
  - WanMove: Motion-Control Image to Video
  - Wan 2.1 Fun Camera 14B

### RunComfy Consistent Character Creator 3.8:
- https://www.runcomfy.com/comfyui-workflows/consistent-character-creator-3-8-in-comfyui-hyperrealistic-consistent-ai-characters
- Uses Qwen-Image-Edit-2511 (GGUF) as the core model
- Single reference image → full character pack (turnarounds, scenes, close-ups, poses, dataset export)
- Key models needed:
  - unsloth/Qwen-Image-Edit-2511-GGUF
  - Comfy-Org/Qwen-Image_ComfyUI
  - lightx2v/Qwen-Image-Edit-2511-Lightning (LoRA)
  - Comfy-Org/flux1-dev
  - gokaygokay/Florence-2-Flux-Large (auto-captioning)
  - 4x-UltraSharp upscaler

### GitHub Workflow Repos:
- https://github.com/comfyanonymous/ComfyUI_examples (official examples with metadata)
- https://github.com/loscrossos/comfy_workflows (GGUF-focused workflows)
- https://github.com/ComfyUI-Workflow/awesome-comfyui (curated custom nodes list)

### Key Reddit Workflow Posts:
- r/comfyui "Been having too much fun with Wan2.1! Here's the ComfyUI workflow" (March 2025)
- r/comfyui "2 days ago I asked for consistent character posing" (May 2025)
- r/StableDiffusion "ComfyUI Wan2.1 14B Image to Video example workflow" (March 2025)
