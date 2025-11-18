# 📌 Prompts for AI Agent — End-to-End Process Mining

This directory contains prompt specifications for Homework 1.4 of the *Intelektualios informacinės sistemos (FMF)* course.

The prompts represent the master thesis system conceptualized as a **single AI agent** that performs the complete end-to-end pipeline:

1. Input raw heterogeneous software logs (X)
2. Preprocessing and normalization
3. Smart event trace construction
4. Export event log in **XES format**
5. Apply **Inductive Miner** and **Heuristic Miner**
6. Evaluate the process model  
   (fitness, precision, generalization, simplicity)
7. Produce **diagnostic insights** for system improvement

The generated result is denoted as **y**.

---

## 📂 Files in this directory

| File | Description |
|-------|-------------|
| `prompt1_zero_shot.md` | Contains a zero-shot prompt: one new log input X is provided and the AI agent must produce y without any prior example. |
| `prompt2_few_shot.md` | Contains a few-shot prompt: two previous (X,y) examples are provided before generating y for a new input. |

---

## 🔍 Purpose of the prompts
The prompts demonstrate **how the thesis system behaves as an AI agent** — without code — by showing how it accepts input data, processes it through all pipeline stages, and returns a structured result.

They are intended for documentation, reproducibility, and grading of the conceptual AI workflow.

---

## 🧪 Expected behavior of the AI agent
When any prompt in this folder is executed, the AI agent should return an output (y) containing:

```json
{
  "constructed_trace": [...],
  "xes_summary": {...},
  "process_model_description": "...",
  "model_evaluation": {
    "fitness": <float>,
    "precision": <float>,
    "generalization": <float>,
    "simplicity": <float>
  },
  "diagnostic_insights": [...]
}
```

---

## 🚀 How to use the prompts
1. Open any `.md` prompt file.
2. Copy the entire content and paste it into your preferred LLM environment (ChatGPT, Claude, Llama, etc.).
3. Provide no additional instructions — the prompt text already defines the agent role, expected behavior, and output format.

---

## 🏁 Notes
- The prompts represent the thesis system as a **single unified AI agent**, exactly as required in Homework 1.4.
- Prompts are illustrative and do not require actual model execution to receive academic credit.
- The files in this directory are part of system documentation and should remain unchanged throughout the project timeline unless the pipeline evolves.

---

📌 *Author:*  
Master Thesis — **Mining Method Application for Software System Event Log Analysis**
