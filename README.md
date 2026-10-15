# AgentDojo Replication: Prompt-Injection Robustness of Current LLM Agents

**Status:** In progress

## What this project is
A replication and extension of **AgentDojo** (Debenedetti et al., NeurIPS 2024 Datasets & Benchmarks), a benchmark for **indirect prompt injection**: malicious instructions hidden in data that an AI agent reads through its tools (emails, web pages, files) and that try to hijack the agent into doing something the user never asked for.

The original paper evaluated 2024-era models (GPT-4o, Claude 3.5 Sonnet, Gemini 1.5, Llama 3). This project asks: **how robust are current models, and do the paper's defenses still hold?**

- Paper: https://arxiv.org/abs/2406.13352
- Framework: https://github.com/ethz-spylab/agentdojo

## Metrics (from the paper)
| Metric | Meaning |
|---|---|
| Benign utility | Share of user tasks solved with no attack present |
| Utility under attack | Share of attacked cases where the user task is still solved, with no malicious side effects |
| Targeted attack success rate (ASR) | Share of attacked cases where the attacker's goal is carried out |

## Plan
- [ ] **Phase 1:** Install AgentDojo, run one suite (Banking or Workspace) on one current model: benign baseline, then with the "important message" attack
- [ ] **Phase 2:** Rerun with built-in defenses (tool filter, data delimiting) and compare against the paper's results
- [ ] **Phase 3:** Write up findings: results table, chart, observations, limitations
- [ ] **Phase 4 (extension):** Add one new injection task or defense, and/or apply the same tests to my own RAG pipeline

## Setup
- Hardware: Apple M1 Pro, 16 GB RAM
- Python 3.11.4, AgentDojo 0.1.35 (benchmark version v1.2.2, the package default)
- Model: Llama 3.1 8B (`llama3.1:8b`), run locally with Ollama 0.40.4, context length 16384

```bash
# Terminal 1: start the model server (leave running)
OLLAMA_CONTEXT_LENGTH=16384 ollama serve

# Terminal 2: install and run
ollama pull llama3.1:8b
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
python3 -m agentdojo.scripts.benchmark -s banking -ut user_task_0 --model LOCAL --model-id llama3.1:8b
```

## Results
_Table goes here after Phase 1–2._

| Model | Suite | Defense | Benign utility | Utility under attack | Targeted ASR |
|---|---|---|---|---|---|
| | | none | | | |

## Observations
_What surprised you, how results compare with the paper, failure modes worth noting._

## Limitations
_Sample size, single suite, cost limits, model versions, etc._

## Responsible use
This project only runs attacks inside AgentDojo's simulated environments with dummy data, against a model running locally on my own machine. It does not target real systems or users.

## Credits
AgentDojo © 2024 Debenedetti, Zhang, Balunovic, Beurer-Kellner, Fischer, and Tramèr (MIT License).
