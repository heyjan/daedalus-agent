# Daedalus Agent

[![Python](https://img.shields.io/badge/python-3.14+-3776AB?style=flat&logo=python&logoColor=white)](https://www.python.org/downloads/)
[![uv](https://img.shields.io/badge/uv-managed-DE5FE9?style=flat)](https://docs.astral.sh/uv/)
[![Pydantic AI](https://img.shields.io/badge/Pydantic%20AI-2.0%20beta-e92063?style=flat)](https://ai.pydantic.dev/)
[![License](https://img.shields.io/badge/license-unlicensed-lightgrey?style=flat)](LICENSE)

Autonomous agent framework built on [Pydantic AI](https://ai.pydantic.dev/) 2.0 beta. Daedalus evaluates and refines its own execution strategies over time combining type safe structured generation with a harness oriented architecture so tasks improve with each run, not only on the first attempt.

## Overview

In Greek mythology, Daedalus was a master craftsman and inventor who built complex systems and pushed the limits of his own designs. This project applies that idea to agentic workflows: strict schemas, observable runs, and iterative refinement instead of one-shot prompts.

## Architecture

<p align="center">
  <a href="https://excalidraw.com/#json=FrnXj32-3xJTRiuZkCSL7,mNXcZ_aoDaeU_ZOBnjHFYw">
    <img src="docs/architecture.png" alt="Daedalus agent architecture diagram" width="720"/>
  </a>
</p>

<p align="center">
  <a href="https://excalidraw.com/#json=FrnXj32-3xJTRiuZkCSL7,mNXcZ_aoDaeU_ZOBnjHFYw"><strong>Open diagram in Excalidraw</strong></a>
  · edit live, then export to refresh the preview below
</p>

The diagram shows the **Model** at the center, with **runtime** (harness, REPL loop, orchestrator) and **memory** (file-, DB-, or hybrid-backed) on one side, and an **Evals** loop (LLM-as-judge) feeding back into the model.

To update the image in the repo: in [Excalidraw](https://excalidraw.com/#json=FrnXj32-3xJTRiuZkCSL7,mNXcZ_aoDaeU_ZOBnjHFYw), choose **Export image → Embed scene**, save as `docs/architecture.excalidraw.png`, and point the `<img>` `src` at that file so the PNG stays editable in Excalidraw ([embedded scene](https://kevinjalbert.com/using-excalidraws-embedded-scene-feature-for-collaborative-diagramming/)).

## Features

- **Pydantic AI 2** — Structured outputs, tool use, and provider integrations via `pydantic-ai-slim`
- **Multi-provider** — Anthropic and Hugging Face (extensible through optional extras)
- **Web tools** — HTTP fetch and DuckDuckGo search for grounded, up-to-date context
- **uv-native** — Reproducible installs from `pyproject.toml` and `uv.lock`

## Requirements

- Python **3.14+**
- [uv](https://docs.astral.sh/uv/getting-started/installation/)

## Installation

```bash
git clone https://github.com/<owner>/daedalus-agent.git
cd daedalus-agent
uv sync --prerelease=allow
```

## Usage

```bash
uv run daedalus-agent
```

## Configuration

Create a `.env` file in the project root for provider credentials (for example `ANTHROPIC_API_KEY`, `HF_TOKEN`). See [Pydantic AI model configuration](https://ai.pydantic.dev/models/) for provider-specific variables.

```bash
cp .env.example .env   # when .env.example is available
# edit .env with your keys
```

## Development

```bash
uv sync --prerelease=allow
uv run daedalus-agent
```

CI is defined under [`.github/workflows/ci.yml`](.github/workflows/ci.yml). After pushing to GitHub, add a workflow badge by replacing `<owner>` and `<repo>`:

```markdown
[![CI](https://github.com/<owner>/<repo>/actions/workflows/ci.yml/badge.svg)](https://github.com/<owner>/<repo>/actions/workflows/ci.yml)
```

## License

No license file is included yet. Add a `LICENSE` and update the badge above when you choose one.
