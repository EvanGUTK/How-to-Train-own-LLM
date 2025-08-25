# 🧠 Model Guide

This document covers recommended base models for fine-tuning and how to install them for use in **LM Studio**, **Ollama**, or in your training environment.

---

## 🔹 Recommended Base Models

| Model | Size(s) | Strengths | License |
|-------|---------|-----------|---------|
| [Meta Llama-3.1 Instruct](https://huggingface.co/meta-llama/Meta-Llama-3.1-8B-Instruct) | 8B, 70B | General-purpose, strong reasoning, state-of-the-art | Meta license (non-commercial unless approved) |
| [Mistral Instruct](https://huggingface.co/mistralai/Mistral-7B-Instruct-v0.3) | 7B | Small but powerful, efficient, fast | Apache 2.0 |
| [Phi-3 Mini](https://huggingface.co/microsoft/Phi-3-mini-4k-instruct) | 3.8B | Lightweight, great for small GPUs, solid reasoning | MIT |
| [Gemma Instruct](https://huggingface.co/google/gemma-7b) | 2B, 7B | Google’s open models, good balance, permissive | Gemma License |
| [OpenHermes](https://huggingface.co/teknium/OpenHermes-2.5-Mistral-7B) | 7B | Fine-tuned on diverse instructions, very chatty | Apache 2.0 |
| [WizardLM](https://huggingface.co/WizardLM/WizardLM-7B-V1.0) | 7B, 13B | Instruction-following, reasoning-focused | GPL-like |

---

## 🔹 Installation Options

### 1. Using Hugging Face (for training/fine-tuning)
Install [transformers](https://huggingface.co/docs/transformers/index) and [datasets]:
```bash
pip install transformers accelerate bitsandbytes datasets
```

## Example: download Llama-3.1-8B-Instruct:

```bash
from transformers import AutoModelForCausalLM, AutoTokenizer

model = AutoModelForCausalLM.from_pretrained(
    "meta-llama/Meta-Llama-3.1-8B-Instruct",
    device_map="auto",
    torch_dtype="auto"
)

tokenizer = AutoTokenizer.from_pretrained("meta-llama/Meta-Llama-3.1-8B-Instruct")
```

## Using LM Studio (easy GUI)
- Open LM Studio → Discover tab
- Search for the model name (e.g. Mistral-7B-Instruct).
- Click Download (choose GGUF quantization, like Q4_K_M).
- Once downloaded, the model appears in Local Models → ready to chat.

## Using Ollama (CLI)
- Ollama uses Modelfiles to build and run models.

## Example: install Mistral 7B Instruct:
```bash
ollama pull mistral:7b-instruct
```

## Which Model Should I Start With?
Small GPU (≤8GB VRAM): Phi-3 Mini (3.8B)
 or Gemma 2B

Mid GPU (12–16GB VRAM like RTX 4080): Mistral-7B-Instruct
 or Llama-3.1-8B

High-end (48GB+ VRAM or multi-GPU): Llama-3.1-70B
