# agent-eval-harness

<div align="center">
  <img src="assets/eval-harness-architecture.svg" alt="Eval Harness Architecture" width="800" />
</div>

<div align="center">

[![CI](https://github.com/hummbl-dev/agent-eval-harness/actions/workflows/ci.yml/badge.svg)](https://github.com/hummbl-dev/agent-eval-harness/actions/workflows/ci.yml)
[![License: MIT OR Apache-2.0](https://img.shields.io/badge/License-MIT%20OR%20Apache--2.0-blue.svg)](LICENSE-APACHE)
[![Python: 3.10+](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://python.org)
[![Zero Dependencies](https://img.shields.io/badge/Dependencies-0%20(Pure%20Stdlib)-brightgreen.svg)](pyproject.toml)

**Deterministic Rule-Adherence & Constraint Satisfaction Benchmark for LLM Agents.**

*Evaluates autonomous agent responses against rigid positive and negative constraints to detect model drift.*

</div>

---

## Features

- 🎯 **Deterministic Grading**: Exact regex and AST-backed constraint satisfaction.
- ⚡ **Zero Dependencies**: Pure Python standard library (`re`, `dataclasses`).
- 🤖 **CI/CD Regression Suite**: Easily pluggable into GitHub Actions to gate model updates.

---

## Usage

```python
from agent_eval_harness import AgentEvalHarness

harness = AgentEvalHarness()
harness.add_regex_constraint("R1", r"\bPASS\b", "Must include status keyword")
harness.add_regex_constraint("R2", r"\bSECRET_KEY\b", "Must not leak secret keys", must_not_match=True)

result = harness.evaluate("System Status: PASS. Verification complete.")
assert result.score == 100.0
```

---

<div align="center">
  <sub>Part of the <a href="https://github.com/hummbl-dev">HUMMBL Developer Ecosystem</a>.</sub>
</div>
