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
