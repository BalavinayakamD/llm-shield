# 🛡️ LLM Shield: AI Security & Prompt Injection Detector

An intelligent API middleware that protects Large Language Models (LLMs) from prompt injection attacks, jailbreaks, and malicious overriding instructions. 

This project demonstrates a defense-in-depth architecture by routing incoming user prompts through a locally fine-tuned Machine Learning classifier (DistilBERT) before allowing the prompt to reach the target generative model.

## 🧠 Core Architecture

This API sits between the end-user and your target LLM (e.g., OpenAI, Gemini, Claude). It operates in two stages:

1. **Layer 1 (The AI Shield):** Incoming prompts are analyzed by a lightweight, fine-tuned `distilbert-base-uncased` model. This model was trained on the `deepset/prompt-injections` dataset to act as a binary classifier (`Safe` vs `Malicious`). It runs locally and evaluates prompts in milliseconds.
2. **Layer 2 (The Target LLM):** If Layer 1 detects an attack with high confidence, the request is immediately blocked (HTTP 403). If the prompt is clean, it is forwarded to the main generative AI model to generate a response.

## 🚀 Features

* **Real-time Threat Detection:** Intercepts and blocks malicious prompts before they reach expensive LLM endpoints.
* **Cost-Efficient Local ML:** Uses a small Transformer model (DistilBERT) for fast, CPU-friendly inference, saving token costs.
* **FastAPI Backend:** Asynchronous, lightning-fast Python API.

---

## 🛠️ Tech Stack

* **Machine Learning:** Hugging Face `transformers`, `datasets`, PyTorch
* **Backend:** Python, FastAPI, Uvicorn
* **Base Model:** `distilbert-base-uncased`

--- 