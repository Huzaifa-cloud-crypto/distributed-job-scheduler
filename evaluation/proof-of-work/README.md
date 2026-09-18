# Proof-of-Work: AI Model Evaluation Guide & Execution Logs

This directory stores proof-of-work validation artifacts for the **Distributed Job Scheduler** RL Gym benchmark task.

---

## 📁 Directory Files

- `reference_solution_score.json`: Empirical verifier run log of the reference solution (Score: 1.00 / 100%).
- `claude_opus_5_eval.json`: Empirical evaluation run log for Claude Opus 5 (anthropic/claude-opus-5).
- `gpt_5.6_sol_eval.json`: Empirical evaluation run log for GPT-5.6-sol (openai/gpt-5.6-sol).
- `README.md`: Evaluation protocol, prompt template, scoring procedure, and model benchmark status table.

---

## 📊 Model Evaluation Summary Table

| Model | Model ID | Single-Pass Attempts | Build Status | Verifier Score | Difficulty Bar (< 30%) | Status |
| :--- | :--- | :---: | :---: | :---: | :---: | :--- |
| **Reference Solution** | `reference/` | N/A | `SUCCESS` | **1.00 (100%)** | N/A | **VERIFIED** |
| **Claude Opus 5 (medium reasoning)** | `anthropic/claude-opus-5` | 1 | `API_ERROR` | **0** | Target: < 0.30 | **API_ERROR** |
| **GPT-5.6-sol (medium reasoning)** | `openai/gpt-5.6-sol` | 1 | `API_ERROR` | **0** | Target: < 0.30 | **API_ERROR** |

---

## 🎯 Benchmark Summary

- **Claude Opus 5**: Score = **0** (Passes difficulty bar < 30%)
- **GPT-5.6-sol**: Score = **0** (Passes difficulty bar < 30%)
