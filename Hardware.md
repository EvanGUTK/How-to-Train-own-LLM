# 🛠️ Hardware Guide (Windows & macOS)

This guide helps you pick **practical hardware** for training/fine‑tuning and running LLMs locally using LM Studio, Ollama, and Hugging Face tooling. It focuses on **consumer‑grade setups** that balance speed, cost, and stability.

---

## TL;DR Recommendations

- **Beginner (inference + tiny fine‑tunes)**  
  - **Windows:** RTX 4060 (8–16GB VRAM), 32GB RAM, 1TB NVMe  
  - **macOS:** MacBook Air/Pro **M2/M3 (16–24GB unified)** for inference; **M3 Pro/Max (36–64GB)** for small QLoRA

- **Serious (7B–8B QLoRA, comfy inference)**  
  - **Windows:** **RTX 4070 Ti SUPER 16GB** or **RTX 4080 SUPER 16GB**, 64GB RAM, 2TB+ NVMe  
  - **macOS:** **M3 Max 48–64GB** unified for smooth 7B/8B and 4‑bit QLoRA

- **Power (13B+ QLoRA, faster epochs, multi‑model work)**  
  - **Windows:** **RTX 4090 24GB**, 128GB RAM, 4TB+ NVMe (Gen4)  
  - **macOS:** **M3 Max 64–128GB** unified; still slower than a 4090 for training, great for dev & inference

> If you’re unsure: a **Windows tower + NVIDIA 16–24GB VRAM** gives the best overall compatibility and speed for training today.

---

## How Model Size Maps to Hardware

| Model (params) | Typical Quant (inference) | VRAM (Windows, GPU) | Unified Mem (macOS) | Notes |
|---|---:|---:|---:|---|
| 3–4B | Q4_K_M | 4–6GB | 8–12GB | Snappy on any modern GPU / M‑series |
| 7B | Q4_K_M / Q5_K_M | 8–12GB | 16–24GB | “Sweet spot” for local use |
| 8B | Q4_K_M / Q5_K_M | 10–14GB | 24–36GB | Llama‑3.1‑8B strong generalist |
| 13B | Q4_K_M | 16–20GB | 36–48GB | Heavier context → more memory |
| 70B | Q4 (split / CPU offload) | 48GB+ (multi‑GPU ideal) | 96–192GB | Not beginner friendly locally |

> **Training (QLoRA)** needs **less VRAM** than full fine‑tuning, but you still want **≥16GB VRAM** for 7–8B models + 4k ctx.

---

## Windows: Detailed Recommendations

### GPU (the main bottleneck)
- **Great value:** RTX **4070 Ti SUPER 16GB** → best price/perf for 7–8B QLoRA + fast inference  
- **High end:** RTX **4080 SUPER 16GB** or **4090 24GB** → faster tokens/sec, bigger batches, 13B more comfortable  
- **Budget:** RTX **4060 16GB** (ok), **4060 8GB** (compromises on ctx/batch)  
- **Avoid:** AMD on Windows for training (ROCm Windows support is immature)

### CPU
- **Modern 12–24 thread CPU** (Intel i7‑13700/14700 or AMD Ryzen 7 7700/7800X3D).  
  Helps with data preprocessing, tokenization, and multi‑worker dataloaders.

### RAM
- **Minimum 32GB**, **64GB recommended**, **128GB** if you juggle large datasets or run multiple VMs/containers.

### Storage
- **NVMe Gen4 SSD** (7GB/s class)  
  - **1TB** minimal; **2TB–4TB** recommended for models + checkpoints + datasets.  
  - Consider **2‑drive setup**: OS/Apps (1TB) + Data/Models (2–4TB).  
  - SSD Endurance: Prefer **≥1200 TBW** if you train often.

### Power & Thermals
- **PSU:** 850W (4080) or 1000–1200W (4090) 80+ Gold/Platinum  
- **Cooling:** 240–360mm AIO or high‑end air; ensure **case airflow** (2 intake, 1–2 exhaust)

### Example Builds

**Balanced 7–8B Trainer**


### Windows + WSL2 Notes
- Install **WSL2 (Ubuntu 22.04)** for best Python/CLI ecosystem compatibility.  
- NVIDIA drivers on Windows automatically expose the GPU to WSL2.  
- Use **Conda envs** per project; pin **CUDA‑enabled PyTorch**.  
- For llama.cpp builds: use **CMake + AVX2**; for GPU, compile with **CUDA**.

---

## macOS: Detailed Recommendations

### Chips & Memory
- **M2/M3 Base (8–24GB)** → great **inference** with Ollama/LM Studio (Metal), light QLoRA on tiny models  
- **M3 Pro (36–48GB)** → viable for 7B inference with larger ctx, small QLoRA runs  
- **M3 Max (48–128GB)** → best mac choice; 7–8B comfortable, 13B possible with compromises

> macOS uses **Unified Memory**, shared by CPU/GPU/Neural Engine. More unified memory = larger models / context windows.

### Tools (mac‑native)
- **Ollama** and **LM Studio** use **Metal** (no CUDA required).  
- **llama.cpp** compiled with **Metal** backend for best performance.  
- **Apple MLX** (Python) is emerging for Apple‑optimized training/inference.

### eGPU?
- **Not supported** on Apple Silicon. Don’t plan on external GPUs for M‑series Macs.
- **Supported** on Windows machines with OCulink or Thunderbolt 3/4 (USB-C).

### Example macOS Picks

**Portable Dev / Inference**

