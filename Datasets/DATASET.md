# 📚 Dataset Guide

This document explains how to get and prepare datasets for fine-tuning your own LLM.

---

## 🔹 Dataset Format
All datasets must follow the **Alpaca format** (instruction → input → output).  

Example:
```json
[
  {
    "instruction": "Explain QLoRA in one paragraph.",
    "input": "",
    "output": "QLoRA is a parameter-efficient fine-tuning method..."
  },
  {
    "instruction": "Turn these bullet points into an email.",
    "input": "- Meeting Tue 2pm\n- Bring demo\n- Ask about dataset",
    "output": "Subject: Tuesday Meeting\n\nHi team, ..."
  }
]

```
| Dataset                                                                                 | Size     | Notes                                     |
| --------------------------------------------------------------------------------------- | -------- | ----------------------------------------- |
| [Databricks Dolly 15k](https://huggingface.co/datasets/databricks/databricks-dolly-15k) | 15k      | Small, human-written, great for beginners |
| [Stanford Alpaca](https://huggingface.co/datasets/tatsu-lab/alpaca)                     | 52k      | Classic dataset, GPT-3 generated          |
| [OpenOrca](https://huggingface.co/datasets/Open-Orca/OpenOrca)                          | Millions | High quality, GPT-4 style                 |
| [OASST1](https://huggingface.co/datasets/OpenAssistant/oasst1)                          | 600k+    | OpenAssistant, dialogue style             |
| [CodeAlpaca](https://huggingface.co/datasets/sahil2801/CodeAlpaca-20k)                  | 20k      | Programming / code-focused                |

# Installing Datasets

```bash
pip install datasets
```
