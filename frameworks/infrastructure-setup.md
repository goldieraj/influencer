# Infrastructure & Security Setup Framework

This document outlines the exact technical infrastructure required to run a multi-character AI influencer network without triggering platform bans, shadowbans, or algorithmic suppression.

## The Core Problem: Device Fingerprinting

Instagram, TikTok, and Twitter do not ban AI accounts simply for being AI (unless they violate explicit content policies). They ban them when multiple accounts are detected operating from the same device, IP address, and browser fingerprint, which triggers "bot farm" or "spam network" flags.

If you log into 5 different AI influencer accounts from your personal iPhone or standard Chrome browser, they will all be shadowbanned within 48 hours.

## 1. Antidetect Browser Setup

To run multiple accounts safely, you must isolate their digital footprints. An antidetect browser creates unique, spoofed browser fingerprints (Canvas, WebGL, AudioContext, fonts, OS, screen resolution) for each profile.

**Recommended Tool:** AdsPower or GoLogin (AdsPower is preferred for social media farming).

### Configuration Protocol:
1. Create a new profile in AdsPower for each character (e.g., "Profile 1: Mei Lin").
2. Set OS to match the target device (Mobile/iOS is best for Instagram, but MacOS/Windows works for desktop management).
3. **CRITICAL:** Set WebRTC, Canvas, and WebGL to "Noise" or "Spoof" — do not disable them entirely, as that is a massive red flag to Meta.
4. Enable "Do Not Track" and set Language/Timezone to match the character's stated location (e.g., Tokyo timezone for Yuki Tanaka).

## 2. Proxy Procurement & Configuration

A unique browser fingerprint is useless if all 5 accounts share your home IP address. You must assign a dedicated proxy to each antidetect profile.

**Proxy Type:** 4G/5G Mobile Proxies or high-quality Residential Proxies. **NEVER use Datacenter proxies.** Meta flags datacenter IPs (AWS, DigitalOcean, etc.) instantly.

**Providers:** Proxy-Seller, IPRoyal, or Soax.
**Cost:** ~$30-50/month per dedicated mobile proxy.

### Configuration Protocol:
1. Purchase one dedicated proxy per character.
2. Input the proxy credentials (IP:Port:User:Pass) into the corresponding AdsPower profile.
3. Use the "Check Proxy" tool in AdsPower before launching the browser.
4. Go to `whoer.net` or `browserleaks.com` within the profile to verify the IP and ensure the anonymity score is 100%.

## 3. SIM Cards & Phone Verification

Social platforms require phone number verification. VoIP numbers (Google Voice, Twilio, TextNow) are heavily flagged by Meta and Twitter and will often result in instant bans.

**Protocol:**
1. Purchase physical, prepaid SIM cards (e.g., Mint Mobile, Lycamobile, or local equivalents).
2. You need one physical SIM card per character.
3. Keep an old, unlocked smartphone (an old iPhone or cheap Android) to receive SMS verification codes.
4. Label each SIM card with the character's name. Swap them into the phone only when verification is required.

## 4. Account Creation & Warming Protocol

Creating an account and immediately posting 5 times with links to an OnlyFans/Fanvue is the fastest way to get banned. Accounts must be "warmed up" to mimic real human behavior.

### The 14-Day Warming Schedule:

| Day | Actions to Take | What NOT to do |
|-----|-----------------|----------------|
| **Day 1** | Create account via AdsPower using the proxy. Add profile picture and bio. | Do not post. Do not add link in bio. |
| **Day 2** | Scroll feed for 10 minutes. Follow 5-10 large accounts in the niche (e.g., Gymshark, FashionNova). | Do not follow small accounts. Do not comment. |
| **Day 3** | Post 1 static image (SFW, casual). Like 3-5 posts on the timeline. | Do not use hashtags yet. |
| **Day 4** | Scroll feed. Watch 5 Reels all the way through. Follow 3 more accounts. | Do not post. |
| **Day 5** | Post 1 Reel (SFW, subtle motion). Add 2-3 broad hashtags. | Do not add link in bio. |
| **Day 6** | Post 1 Story. Reply to 1 comment on your own post. | Do not DM anyone. |
| **Day 7** | Post 1 static image. Follow 5 mid-sized creators in the niche. | Do not add link in bio. |
| **Days 8-13** | Post daily (alternating Reel/Static). Engage organically for 15 mins/day. | Do not spam comments. |
| **Day 14** | Add Fanvue/Linktree link to bio. Begin normal posting schedule. | Do not use explicit language in bio. |

## 5. Fanvue / Monetization Setup

Fanvue is preferred over OnlyFans for AI creators because Fanvue explicitly allows and supports AI-generated content, whereas OnlyFans has a history of suddenly banning AI accounts during identity verification sweeps.

### Setup Protocol:
1. Create the Fanvue account using the same AdsPower profile and proxy as the Instagram account.
2. **Identity Verification:** Fanvue requires KYC (Know Your Customer) for payouts. You must verify using your real identity/ID. Fanvue allows creators to operate under pseudonyms/AI personas while keeping the financial backend tied to a real human.
3. Ensure the AI disclosure toggle is checked in Fanvue settings (required by their TOS).

## 6. Payment Processing & Anonymity

If you are running multiple characters, you need to manage payouts without crossing streams or exposing your real identity to subscribers.

1. **Payouts:** Route Fanvue payouts to a dedicated business bank account (e.g., Mercury, Wise, or a local LLC account) rather than your personal checking account.
2. **Anonymity:** Subscribers on Fanvue only see the creator's display name. They do not see the legal name attached to the bank account.
3. **Taxes:** Track income per character for ROI analysis, but consolidate it under one LLC for tax reporting purposes.

## 7. Cost Breakdown (Per Character)

| Item | Monthly Cost | Notes |
|------|--------------|-------|
| AdsPower Profile | ~$5 | Scales down with bulk plans |
| 4G Mobile Proxy | ~$40 | Essential for avoiding shadowbans |
| Physical SIM Card | ~$15 | Prepaid plan for SMS verification |
| Fanvue Hosting | $0 | Platform takes 15-20% cut |
| AI Generation Compute | ~$30 | API credits (RunPod, Banana, etc.) |
| **Total Baseline** | **~$90/mo** | You must generate >$90/mo per character to break even. |

## 8. Limitations & Failure Modes

1. **The "Cross-Contamination" Ban:** If you accidentally open Character A's Instagram in Character B's AdsPower profile, Meta will link the accounts. If one gets banned, the other will fall like dominos.
2. **The Metadata Flag:** Forgetting to strip C2PA/XMP metadata before uploading (see Content Creation SOP) will result in algorithmic suppression.
3. **The Proxy Drop:** If your proxy disconnects and AdsPower falls back to your real IP, the account is compromised. Ensure "Block access if proxy fails" is enabled in AdsPower settings.
