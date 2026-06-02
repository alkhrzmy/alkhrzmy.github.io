---

layout: default
title: End-to-End Spoken Language Understanding for Retail Transaction Recording
--------------------------------------------------------------------------------

# End-to-End Spoken Language Understanding for Retail Transaction Recording

## Overview

This project develops an **End-to-End Spoken Language Understanding (SLU)** system for Indonesian retail transaction recording. The system is designed to extract transaction information directly from speech signals, such as **product**, **quantity**, and **intent**, without relying on a separate speech-to-text transcription pipeline.

The project focuses on applying deep learning to support more efficient and natural transaction recording for small retail businesses and Indonesian SMEs.

---

## Problem

Many retail transaction recording processes in Indonesian SMEs are still performed manually or through text-based input. This can be time-consuming, prone to human error, and less efficient during cashier operations.

A voice-based transaction recording system can provide a more natural input interface, allowing users to record transactions through speech while reducing dependency on manual typing.

---

## Objective

The main objective of this project is to build a deep learning-based SLU model that can understand Indonesian retail transaction speech and predict key semantic information directly from audio.

The model is designed to perform three prediction tasks:

* Product classification
* Quantity classification
* Intent classification

---

## Methodology

The proposed system uses a **CNN-BiLSTM multi-task learning architecture** with **Log-Mel Spectrogram** features as model input.

The workflow consists of several main stages:

1. **Audio Data Collection**
   A hybrid dataset was created by combining synthetic speech and manually recorded speech.

2. **Audio Preprocessing**
   Audio files were resampled, converted to mono format, trimmed to remove silent segments, and transformed into Log-Mel Spectrogram representations.

3. **Data Augmentation**
   Audio augmentation techniques were applied to improve model generalization, including masking-based augmentation, Gaussian noise injection, and time shifting.

4. **Model Architecture**
   The model combines CNN layers for extracting spectral features and BiLSTM layers for modeling temporal dependencies in speech signals.

5. **Multi-Task Learning**
   Separate classification heads were used to predict product, quantity, and intent within a single end-to-end model.

6. **Two-Stage Training**
   The training strategy consisted of mixed training using synthetic and manual data, followed by fine-tuning using manually recorded speech to improve robustness on real speech data.

---

## Model Architecture

The model architecture consists of:

* **CNN Encoder** for extracting local spectral patterns from Log-Mel Spectrogram features.
* **BiLSTM Layer** for capturing sequential and temporal patterns in speech.
* **Multi-task Classification Heads** for predicting product, quantity, and intent.

This architecture enables the system to directly map audio input into semantic transaction labels.

---

## Results

The proposed CNN-BiLSTM model achieved strong performance in understanding Indonesian retail transaction speech.

Key results:

* Achieved high macro-F1 performance on validation data.
* Balanced accuracy remained strong across the main prediction tasks.
* Two-stage training improved model adaptation to manually recorded speech.
* The end-to-end approach reduced dependency on separate ASR and NLU modules.

The best fine-tuning experiment reached a macro-F1 score of approximately **0.98**, showing that the model was able to learn meaningful speech representations for transaction understanding.

---

## Key Learnings

Through this project, I learned how to:

* Build an end-to-end speech understanding pipeline.
* Process audio data into Log-Mel Spectrogram features.
* Design a CNN-BiLSTM model for speech-based classification.
* Apply multi-task learning for semantic information extraction.
* Use two-stage training to combine synthetic and real-world speech data.
* Evaluate model performance using macro-F1 score and balanced accuracy.

---

## Tech Stack

* Python
* PyTorch
* Librosa
* NumPy
* Pandas
* Scikit-learn
* Matplotlib
* CNN-BiLSTM
* Log-Mel Spectrogram
* Multi-task Learning

---

## Repository

[View GitHub Repository](https://github.com/alkhrzmy/SLU-Ritel-CNNBiLSTM)

---

## Project Status

This project was developed as part of a deep learning / MLOps course project. Further improvements may include expanding the dataset, testing the model on more diverse speakers, and deploying the system as a lightweight voice-based retail transaction assistant.
