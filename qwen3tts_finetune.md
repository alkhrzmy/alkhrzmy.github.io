---
layout: default
title: Fine-Tuning Qwen3-TTS for Indonesian and Sundanese Languages
---

# Fine-Tuning Qwen3-TTS for Indonesian and Sundanese Languages

## Overview

This project fine-tunes the **Qwen3-TTS** text-to-speech model for **Indonesian and Sundanese languages** using Kaggle's free GPU resources. The work explores the voice gap in AI content creation and compares open-source TTS models with commercial solutions like ElevenLabs.

The full article is published on Medium: [The Voice Gap in the AI Content Revolution →](https://medium.com/@gymnastiaralk/the-voice-gap-in-the-ai-content-revolution-1a85c296da6e)

---

## Problem

Most commercial TTS models (ElevenLabs, OpenAI, Google) have limited support for Indonesian regional languages, especially Sundanese. This creates a barrier for local content creators who want to produce voice-based content in their native language.

Key challenges:
- Limited training data for Indonesian regional languages
- Commercial TTS solutions are expensive and lack local language support
- Open-source models need fine-tuning for optimal performance on non-English languages

---

## Objective

Fine-tune Qwen3-TTS to:
- Generate natural-sounding speech in Indonesian
- Support Sundanese language for regional content creation
- Compare performance with commercial TTS solutions
- Democratize TTS access for Indonesian content creators

---

## Approach

### Model
- **Base Model:** Qwen3-TTS (open-source, from Alibaba)
- **Fine-tuning Method:** LoRA (Low-Rank Adaptation) for efficient training
- **Compute:** Kaggle free GPU (NVIDIA T4 x2)

### Dataset
- Indonesian speech data from Common Voice and custom recordings
- Sundanese language samples from community datasets
- Total training hours: ~10 hours of speech data

### Training Configuration
- Learning Rate: 1e-4
- Batch Size: 8
- Epochs: 50
- LoRA Rank: 16
- Optimizer: AdamW with cosine learning rate schedule

---

## Results

The fine-tuned model achieved:
- **Naturalness Score:** 4.2/5 (MOS evaluation)
- **Intelligibility:** 94% word accuracy on test set
- **Language Support:** Indonesian + Sundanese
- **Inference Speed:** ~0.8x real-time on T4 GPU

### Comparison with Commercial Solutions

| Feature | Qwen3-TTS (Fine-tuned) | ElevenLabs | Google Cloud TTS |
|---|---|---|---|
| Indonesian Support | ✅ Native | ⚠️ Limited | ✅ Good |
| Sundanese Support | ✅ Native | ❌ None | ❌ None |
| Cost | Free (open-source) | $5-99/month | Pay-per-use |
| Customization | Full control | Limited | Limited |
| Voice Quality | Good | Excellent | Good |

---

## Key Learnings

Through this project, I learned:
- How to fine-tune large TTS models with limited compute resources
- LoRA efficient fine-tuning for speech models
- Audio data preprocessing and augmentation techniques
- Evaluating TTS quality using both quantitative and qualitative metrics
- The challenges of multilingual TTS for low-resource languages

---

## Tech Stack

- **Python** — Core implementation
- **PyTorch** — Model training
- **Hugging Face Transformers** — Model loading and fine-tuning
- **Qwen3-TTS** — Base TTS model
- **LoRA** — Efficient fine-tuning
- **Kaggle** — Free GPU compute
- **Librosa** — Audio processing
- **Matplotlib** — Training visualization

---

## Article

Read the full article on Medium: [The Voice Gap in the AI Content Revolution →](https://medium.com/@gymnastiaralk/the-voice-gap-in-the-ai-content-revolution-1a85c296da6e)

---

## Project Status

Completed and published on Medium. The fine-tuned model and training code are available upon request.

Future improvements may include:
- Expanding to more Indonesian regional languages (Javanese, Balinese)
- Adding voice cloning capabilities
- Deploying as a web application for content creators
- Integrating with popular content creation tools