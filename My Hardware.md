# 💻 My Hardware Setup

This document describes my current local machine configuration used for training and running LLMs.

---

## 🖥️ System Overview
- **Operating System:** Windows 11 Pro  
- **CPU:** Intel Core i9-13900K (24 cores / 32 threads, up to 5.8GHz)  
- **GPU:** NVIDIA RTX 4080 SUPER (16GB GDDR6X)  
- **Memory:** 32GB DDR5-5200 MT/s  
- **Motherboard:** ASUS ROG Strix Z690-E Gaming WiFi (PCIe Gen4/Gen5 support)  
- **Cooling:** 360mm AIO Liquid Cooler  
- **Storage:** ~30TB total (mix of NVMe SSD + HDD)  
- **Power Supply:** 1000W Gold (modular)  

---

## 🚀 What This Hardware Can Handle

### Inference
- ✅ **7B and 8B models (Llama 3, Mistral, Phi-3, Gemma)**  
  Runs comfortably in **Q4_K_M** quantization with 4096 context.  
- ⚡ LM Studio / Ollama performance: ~100–160 tokens/sec (7B), ~90–130 tokens/sec (8B).  
- ⚠️ 13B models are possible but limited by 16GB VRAM → requires 4-bit quantization & smaller context length.  

### Fine-tuning (QLoRA)
- ✅ **7B and 8B LoRA fine-tunes** are well supported.  
- ⚠️ **32GB system RAM** is a bottleneck for very large datasets.  
- ⚠️ For 8B + long contexts (4k), gradient accumulation is required to fit training into VRAM.  
- ❌ **70B models** not feasible on this setup without cloud or multi-GPU.  

---
