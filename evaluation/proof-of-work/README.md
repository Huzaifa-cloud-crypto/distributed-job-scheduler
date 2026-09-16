# Proof-of-Work: AI Model Evaluation Guide & Execution Logs

This directory stores proof-of-work validation artifacts for the **Distributed Job Scheduler** RL Gym benchmark task.

---

## 📁 Directory Files

- `reference_solution_score.json`: **EMPIRICAL LOG** of the reference solution achieving 1.00 (100%) score on the verifier suite.
- `claude_opus_5_eval.json`: **PENDING MODEL BENCHMARK** — Raw log template for Claude Opus 5 (medium reasoning) evaluation.
- `gpt_5.6_sol_eval.json`: **PENDING MODEL BENCHMARK** — Raw log template for GPT-5.6-sol (medium reasoning) evaluation.
- `README.md`: Evaluation protocol, exact prompt template, scoring procedure, and model benchmark status table.

---

## 📊 Model Evaluation Summary Table

| Model | Single-Pass Attempts | Build Status | Verifier Score | Difficulty Bar (< 30%) | Status |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **Reference Solution** | N/A | `SUCCESS` | **1.00 (100%)** | N/A | **VERIFIED** |
| **Claude Opus 5 (medium reasoning)** | 1 | `PENDING` | `PENDING` | Target: < 0.30 | **PENDING EXECUTION** |
| **GPT-5.6-sol (medium reasoning)** | 1 | `PENDING` | `PENDING` | Target: < 0.30 | **PENDING EXECUTION** |

---

## 🎯 Model Evaluation Protocol

### 1. Model Input Guidelines
- Models must be evaluated in **single-pass mode** (one single attempt per model).
- Provide **ONLY** the model-facing instruction file (`task/instruction.md`). Do **NOT** include tests, reference solutions, or internal scoring criteria.

### 2. Prompt Template (Paste-Ready)

```markdown
You are an expert software engineer. Implement a complete Node.js / TypeScript solution for the following software specification.
Place your code in a standard repository structure with a package.json and build script.
Do not ask clarifying questions; strictly satisfy all observable CLI specifications and state persistence requirements.

--- BEGIN SPECIFICATION ---
[Insert full contents of task/instruction.md here]
--- END SPECIFICATION ---
```

---

## 🛠️ Step-by-Step Scoring Procedure

1. **Run Model**: Pass the prompt template to the model (Claude Opus 5 / GPT-5.6-sol) in a fresh session.
2. **Collect Code**: Extract the generated TypeScript/Node project code into a temporary folder (e.g., `temp_model_run/`).
3. **Build Code**: Run `npm install` and `npm run build` inside `temp_model_run/`. Note whether build succeeds or fails.
4. **Evaluate Code**: Run the verifier suite against the compiled entrypoint:
   ```bash
   node ./evaluation/dist/test_runner.js ./temp_model_run/dist/cli.js
   ```
5. **Record Results**: Save the raw output log, exit code, score, and failed test check IDs in `evaluation/proof-of-work/<model_name>_eval.json`.
6. **Difficulty Assertion**: Confirm that both model scores are **< 0.30 (30%)**.
