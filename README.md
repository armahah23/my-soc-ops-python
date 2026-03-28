<div align="center">

# 🎯 Soc Ops

### Social Bingo — the ice-breaker game that gets everyone talking

Find people who match the prompts, mark them off your card, and be the first to get **5 in a row!**

[![Python](https://img.shields.io/badge/Python-3.13+-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.115+-009688?logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![HTMX](https://img.shields.io/badge/HTMX-powered-36BCEF?logo=htmx&logoColor=white)](https://htmx.org/)
[![Jinja2](https://img.shields.io/badge/Jinja2-templating-B41717?logo=jinja&logoColor=white)](https://jinja.palletsprojects.com/)
[![uv](https://img.shields.io/badge/uv-package%20manager-DE5FE9?logo=astral&logoColor=white)](https://docs.astral.sh/uv/)
[![Open in Dev Container](https://img.shields.io/badge/Dev%20Container-ready-007ACC?logo=visualstudiocode&logoColor=white)](https://containers.dev/)

</div>

---

## ✨ What is Soc Ops?

**Soc Ops** is a lightweight, browser-based **Social Bingo** game built for in-person mixers, team events, and workshops. Each player gets a randomly generated 5×5 bingo card filled with fun prompts about the people around them — *"has lived in another country"*, *"plays an instrument"*, *"can juggle"* — and races to find real matches in the room.

> 🏆 First to get **5 in a row** wins bragging rights (and maybe a prize)!

This repo also doubles as a **hands-on GitHub Copilot Agent Lab** — a structured workshop where you'll build on this app using VS Code Agent Mode, custom agents, and AI-driven development workflows.

---

## 🚀 Quick Start

> **Fastest path:** open in a GitHub Codespace — zero local setup required.

```bash
# 1. Clone the repo
git clone https://github.com/{your-username}/my-soc-ops-python
cd my-soc-ops-python

# 2. Install dependencies
uv sync

# 3. Run the app
uv run soc-ops
```

Then open **http://localhost:8000** in your browser. 🎉

> 💡 **Tip:** This repo ships with a `.devcontainer` — open it in VS Code or Codespaces for a fully configured environment with one click.

---

## 🎮 Features

| Feature | Details |
|---------|---------|
| 🃏 **Random Bingo Cards** | Every player gets a unique 5×5 card generated from a rich question bank |
| ✅ **Live Square Toggling** | Click to mark squares — powered by HTMX for instant, no-reload updates |
| 🏆 **Win Detection** | Automatic row, column, and diagonal bingo detection with a celebration modal |
| 🔄 **Instant Reset** | Start a fresh game in one click — new card, new round |
| 📱 **Mobile Friendly** | Responsive layout works great on phones at the event |
| 🔒 **Session Isolation** | Each player's card is tracked independently via server-side sessions |

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **Backend** | [FastAPI](https://fastapi.tiangolo.com/) — async Python web framework |
| **Templating** | [Jinja2](https://jinja.palletsprojects.com/) — server-rendered HTML |
| **Interactivity** | [HTMX](https://htmx.org/) — hypermedia-driven UI updates |
| **Styling** | Custom CSS utility classes (no external UI framework) |
| **Package Manager** | [uv](https://docs.astral.sh/uv/) — fast Python package & project manager |
| **Dev Environment** | Dev Container + GitHub Codespaces ready |

---

## 📚 Workshop Lab Guide

This project is also the foundation for a **GitHub Copilot Agent Lab** — an ~1 hour hands-on workshop exploring agentic AI development in VS Code.

| Part | Title | Time | What You'll Do |
|------|-------|------|----------------|
| [**00**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=00-overview) | Overview & Checklist | — | Review prerequisites and what you'll build |
| [**01**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=01-setup) | Setup & Context Engineering | 15 min | Configure the AI with codebase instructions |
| [**02**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=02-design) | Design-First Frontend | 15 min | Redesign the UI with creative AI-driven themes |
| [**03**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=03-quiz-master) | Custom Quiz Master | 10 min | Build a custom agent to generate quiz themes |
| [**04**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=04-multi-agent) | Multi-Agent Development | 20 min | Add new features using TDD and design agents |

> 📝 Offline? All lab guides are available in the [`workshop/`](workshop/) folder.

**➡️ Start here:** [**Part 00 — Overview & Checklist**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=00-overview)

---

## 📁 Project Structure

```
soc-ops/
├── app/
│   ├── main.py           # FastAPI routes and app entrypoint
│   ├── game_logic.py     # Bingo card generation and win detection
│   ├── game_service.py   # Session management
│   ├── models.py         # Game state models
│   ├── data.py           # Question bank
│   ├── templates/        # Jinja2 HTML templates
│   └── static/           # CSS and JS assets
├── tests/                # pytest test suite
├── workshop/             # Lab guide markdown files
├── .devcontainer/        # Dev Container configuration
└── pyproject.toml        # Project metadata and dependencies
```

---

## 🧪 Development

```bash
# Lint
uv run ruff check .

# Test
uv run pytest

# Run with hot reload (default)
uv run soc-ops
```

---

## 🤝 Contributing

Contributions are welcome! Please read our [Contributing Guide](CONTRIBUTING.md) and [Code of Conduct](CODE_OF_CONDUCT.md) before submitting a pull request.

---

## 📄 License

This project is licensed under the terms in [LICENSE](LICENSE).
