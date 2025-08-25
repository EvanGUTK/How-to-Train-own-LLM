# How to Train Your Own LLM

This guide walks you through **fine-tuning your own Large Language Model (LLM)** at home using **QLoRA**.  
You’ll start with an open-source base model (e.g. Llama-3.1-8B-Instruct), fine-tune it on your dataset, and export a quantized version that runs locally in **LM Studio** and **Ollama**.

---

## 🚀 What You’ll Build
- Fine-tune a base model on your own instructions.
- Merge + quantize it into a `.gguf` file.
- Run it in **LM Studio** (GUI) and **Ollama** (CLI).
- Share results in this repo.

---

## 📦 Requirements
- **Windows 10/11 with WSL2 (Ubuntu 22.04)**
- **NVIDIA GPU (16GB+ VRAM recommended)**
- **Conda (Miniconda or Anaconda)**
- **LM Studio** (for local inference)
- **Ollama** (for CLI inference)
- Optional: **Jenkins (CI/CD)** to automate dataset checks & training

---

## 🛠️ Setup
1. Install [WSL2](https://learn.microsoft.com/en-us/windows/wsl/install) and open Ubuntu 22.04.
2. Install [Miniconda](https://docs.conda.io/en/latest/miniconda.html).
3. Install PyTorch (CUDA 12.1 for NVIDIA GPUs):
   ```bash
   pip install torch --index-url https://download.pytorch.org/whl/cu121
