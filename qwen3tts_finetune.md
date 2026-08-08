---
layout: default
title: Fine-Tuning Qwen3-TTS for Indonesian and Sundanese Languages
---

# Fine-Tuning Qwen3-TTS for Indonesian Voice

## Overview

This project fine-tunes the **Qwen3-TTS** text-to-speech model for **Bahasa Indonesia** using Google Colab T4 free tier. The work explores the voice gap in AI content creation and compares open-source TTS models with commercial solutions like ElevenLabs.

The full article is published on Medium: [The Voice Gap in the AI Content Revolution →](https://medium.com/@gymnastiaralk/the-voice-gap-in-the-ai-content-revolution-1a85c296da6e)

---

## Problem

ElevenLabs costs $5-22/month. Qwen3-TTS is free and Apache 2.0 licensed. But there is a catch: Indonesian is not supported natively. You need to fine-tune.

Key challenges:
- Qwen3-TTS supports 10 languages -- Indonesian is NOT included
- Accent bias issue for non-supported languages (GitHub issue #323)
- Known bugs in official training script (sft_12hz.py)
- No public Indonesian LoRA adapter exists yet

---

## Objective

Fine-tune Qwen3-TTS to:
- Generate natural-sounding speech in Bahasa Indonesia
- Compare performance with commercial TTS solutions (ElevenLabs)
- Democratize TTS access for Indonesian content creators
- Provide first complete tutorial for Indonesian fine-tuning

---

## Approach

### Model
- **Base Model:** Qwen3-TTS (Alibaba, Apache 2.0)
- **Variant:** 0.6B-Base (lightweight, 4GB VRAM) or 1.7B-Base
- **Fine-tuning Method:** LoRA (Low-Rank Adaptation)
- **Compute:** Google Colab T4 (free tier)

### Pipeline
```
1. Prepare JSONL: {audio, text, ref_audio}
2. Resample audio to 24kHz (mandatory)
3. Run prepare_data.py (extract audio_codes)
4. Run sft_12hz.py (training)
5. Test inference from checkpoint
```

### Dataset
- Indonesian speech data from community datasets
- Single-speaker fine-tuning (multi-speaker coming in future releases)

---

## Results

The fine-tuned model achieved:
- **Indonesian voice generation** from base model (previously unsupported)
- **Cost savings:** $22/month (ElevenLabs) → $0 (self-hosted)
- **Community contribution:** First Indonesian TTS fine-tune tutorial

### Comparison with ElevenLabs

| Feature | Qwen3-TTS (Fine-tuned) | ElevenLabs |
|---|---|---|
| Indonesian Support | ✅ Fine-tuned | ⚠️ Limited |
| Cost | Free (Apache 2.0) | $5-22/month |
| Customization | Full control | Limited |
| Known Bugs | Documented | N/A |

### Known Bugs Documented
- Missing text_projection (issue #39)
- Double label-shift causing speech acceleration
- 24kHz resampling requirement (PR #233 unmerged)
- Accent bias for non-supported languages (issue #323)

---

## Key Learnings

Through this project, I learned:
- How to fine-tune large TTS models with limited compute resources
- LoRA efficient fine-tuning for speech models
- Audio data preprocessing (24kHz resampling, normalization)
- Documenting and working around open-source bugs
- The challenges of multilingual TTS for low-resource languages

---

## Tech Stack

- **Python** -- Core implementation
- **PyTorch** -- Model training
- **Hugging Face Transformers** -- Model loading
- **Qwen3-TTS** -- Base TTS model (Alibaba)
- **LoRA** -- Efficient fine-tuning
- **Google Colab T4** -- Free GPU compute
- **Librosa** -- Audio processing

---

## Article

Read the full article on Medium: [The Voice Gap in the AI Content Revolution →](https://medium.com/@gymnastiaralk/the-voice-gap-in-the-ai-content-revolution-1a85c296da6e)

---

## Project Status

Completed and published on Medium. The fine-tuned model and training code are available in the repository.

Future improvements may include:
- Expanding to multi-speaker support
- Adding more Indonesian regional languages
- Deploying as a web application
- Contributing bug fixes upstream to Qwen3-TTS repo