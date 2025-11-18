# Prompt 2 – Few-shot End-to-End Process Mining

## Overview
This prompt demonstrates how the Software System Log Analysis AI Agent performs a complete process mining workflow using a few-shot scenario. Two completed (X,y) examples are provided before generating an output for a new input.

---

## System Role
You are an **AI Agent for Software System Log Analysis and Process Mining**.  
Your task is to process raw system log data (X) and generate a complete process-mining result (y).

The evaluation must include:
1. Preprocessing and trace construction.
2. Export to XES format.
3. Application of **Inductive Miner** and **Heuristic Miner**.
4. Model evaluation with **fitness**, **precision**, **generalization**, **simplicity**.
5. Diagnostic insights (loops, bottlenecks, anomalies).

---

## Example 1 (X,y)
**Input X**
```text
[2024-10-06 12:31:08] INFO Request /checkout user=110
[2024-10-06 12:31:10] INFO Payment gateway init user=110
[2024-10-06 12:31:11] INFO Payment confirmation user=110
```

**Output y**
```json
{
  "constructed_trace": ["Checkout", "PaymentInit", "PaymentConfirmation"],
  "process_model_description": "Strict sequential workflow with no branching.",
  "model_evaluation": {
    "fitness": 0.97,
    "precision": 0.94
  },
  "diagnostic_insights": [
    "Stable flow — no retries or performance bottlenecks observed."
  ]
}
```

---

## Example 2 (X,y)
**Input X**
```text
[2024-10-19 17:11:24] INFO GET /cart id=421
[2024-10-19 17:11:25] WARN Cache miss id=421
[2024-10-19 17:11:27] INFO Cache restored id=421
[2024-10-19 17:11:30] INFO GET /cart id=421
```

**Output y**
```json
{
  "constructed_trace": ["Cart", "CacheMiss", "CacheRestore", "Cart"],
  "process_model_description": "A loop is detected due to repeated cache restoration calls.",
  "model_evaluation": {
    "fitness": 0.90,
    "precision": 0.86
  },
  "diagnostic_insights": [
    "Cache failure loop indicates potential performance degradation under load."
  ]
}
```

---

## NEW REQUEST — Evaluate the Logs

### Input X
```text
[2024-11-22 15:44:03] INFO GET /product?id=221
[2024-11-22 15:44:05] INFO DB lookup id=221
[2024-11-22 15:44:06] WARN Response delay 780ms id=221
[2024-11-22 15:44:09] INFO Product page rendered id=221
```

---

## Expected Behavior
The AI agent should:
- Construct a high-level trace from the log messages.
- Export an XES event log (summary format).
- Discover a process model using both Inductive Miner and Heuristic Miner.
- Compute model quality metrics (fitness, precision, generalization, simplicity).
- Detect and report bottlenecks, loops, or anomalies.

---

## Required Output Format (y)
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

## Notes
- The new output must NOT copy values from previous examples.
- The agent must generalize from the provided few-shot examples.
- All steps of the end-to-end pipeline must be reflected in the output.
