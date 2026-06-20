# Audit Research Notes

## Critical Gaps Identified

### 1. METADATA STRIPPING (COMPLETELY MISSING)
- Instagram, TikTok, Pinterest ALL scan for C2PA, XMP, EXIF metadata
- ComfyUI embeds workflow metadata in PNG text chunks
- Stable Diffusion embeds generation parameters
- Tools: removeailabel.com, aimetadatacleaner.com (browser-based, free)
- MUST strip before every upload or get auto-labeled "Made with AI"
- This alone can kill engagement by 15-80%

### 2. INSTAGRAM BAN WAVE 2026 (UNDERESTIMATED)
- June 2026: Massive ban wave hitting AI accounts
- CSE (Child Sexual Exploitation) false positives
- Triggers: overly perfect content, repetitive posts, NSFW-adjacent, growth spikes, device/IP linking
- Meta requiring biometric video verification for appeals
- YouTube video "Why Every AI OFM Operator Is Getting Banned on Instagram in 2026" (May 2026)
- Need: device fingerprint isolation, residential proxies, phone verification strategy

### 3. CHAT AUTOMATION (BARELY COVERED)
- Reddit SaaS post: "$556K in 3 months" from AI-powered OF chatting
- Chat/PPV is 80% of revenue but framework only mentions it briefly
- Need: specific LLM setup, persona training, PPV timing, escalation scripts
- Tools: Custom GPT wrappers, dedicated OF chat SaaS platforms
- Vice article confirms this is industry standard now

### 4. FLUX + IP-ADAPTER COMPATIBILITY (TECHNICAL GAP)
- Reddit: "Do Flux IP adapters even work?" - community says they're weak
- Best OpenPose ControlNet was for SD1.5, Flux versions are "much weaker"
- Flux Union ControlNet exists but is less precise
- Shakker-Labs/ComfyUI-IPAdapter-Flux exists on GitHub
- XLabs-AI/flux-ip-adapter on HuggingFace
- The technical guide says "use IP-Adapter" but doesn't acknowledge Flux compatibility issues
- Real workflow: Generate base with Flux LoRA → Use SDXL IP-Adapter for pose variants → Upscale back

### 5. WAN 2.1 CHARACTER CONSISTENCY (VIDEO GAP)
- Reddit: "WAN is useless with characters if you want consistency"
- Face morphing is a known issue
- Wan 2.1 VACE exists for consistent character but requires specific workflow
- extra-ordinary.tv has a full blog series on this
- Video framework doesn't address the face morphing problem or solutions

### 6. PLATFORM RISK DIVERSIFICATION (WEAK)
- OnlyFans BANNED AI completely - framework mentions Fanvue but doesn't emphasize enough
- Fanvue has AI content verification (age verification for AI characters)
- Fansly also allows AI content
- Need: multi-platform strategy from day 1, not just "backup"

### 7. FINANCIAL REALITY CHECK (MISSING)
- Reddit consensus: "If AI influencer pages were consistently making serious money, people would scale more pages instead of selling guides"
- Market is getting saturated
- Startup costs: ~$1K minimum (GPU rental, tools, time)
- Most people fail because they treat it as passive income, not a business
- Need: realistic timeline, budget, and failure rate data

### 8. LEGAL/COMPLIANCE (COMPLETELY MISSING)
- EU AI Act requires AI disclosure
- Platform ToS violations can lead to permanent bans
- Tax implications of AI-generated content revenue
- Fanvue requires age verification for AI characters
- Some jurisdictions have deepfake laws

### 9. DEVICE/ACCOUNT ISOLATION (MISSING)
- IP linking multiple accounts = instant network ban
- Need: separate devices OR antidetect browsers (GoLogin, Multilogin)
- Residential proxies per account
- Separate phone numbers for verification
- Separate email addresses per account

### 10. CONTENT VARIETY & ANTI-DETECTION (WEAK)
- "5 near-identical bikini shots a day with generic captions screams bot/fake"
- Need: content calendar with variety built in
- Mix of content types (stories, polls, Q&A, behind-scenes)
- Manual engagement patterns (not robotic timing)
- Caption variety framework (not templates that repeat)
