# Working log

Short dated entries: what you ran, what happened, what's next. This becomes the raw material for the write-up and your interview stories.

## YYYY-MM-DD
- Ran:
- Result:
- Confusing / surprising:
- Next:

## 2026-10-15: Environment setup and smoke test
- Ran: installed AgentDojo 0.1.35 in a venv (Python 3.11.4); served Llama 3.1 8B locally with Ollama, context length 16384 (confirmed with `ollama ps`).
- Result: smoke test (banking user_task_0, no attack) passed. This only confirms the pipeline works end to end; it is not a result.
- Confusing / surprising: `--model` takes the uppercase name (`LOCAL`). `python` is aliased to the system Python on this Mac, so use `python3` inside the venv.
- Next: full banking baseline (16 user tasks, no attack). Notes for later: AgentDojo's tool_filter defense only supports OpenAI-client models, so Phase 2 will use spotlighting_with_delimiting. Default benchmark version (v1.2.2) differs from the paper's; record under Limitations.
