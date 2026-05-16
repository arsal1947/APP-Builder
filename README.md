# APP-Builder 🤖

> An AI-powered application generator — a Lovable.ai-inspired clone that takes a plain English prompt and autonomously builds a complete, working application with all files and folders.

## What It Does

You give it a prompt like *"Build a calculator app"* and it:
1. Plans the entire project structure
2. Breaks it down into engineering tasks
3. Writes every file — fully implemented, ready to run

No templates. No boilerplate. Just working code, generated from scratch.

## How the Agent Pipeline Works

APP-Builder uses a **3-agent LangGraph pipeline**, each agent with a specific role:


User Prompt → [Planner] → [Architect] → [Coder] → Generated Project

- **Planner Agent** — Reads your prompt and produces a structured project plan: app name, tech stack, features, and a list of files to create.
- **Architect Agent** — Takes the plan and breaks it into ordered, detailed implementation tasks — one per file — with exact function names, dependencies, and integration details.
- **Coder Agent** — Loops through each task using a ReAct agent loop, reads existing files for context, and writes the full implementation using file tools.

All generated files are saved inside a `generated_project/` folder.

## Tech Stack

| Layer | Technology |
|---|---|
| Agent Framework | LangGraph |
| LLM Provider | Groq (LLaMA 3.3 70B) |
| LLM Abstraction | LangChain |
| Data Validation | Pydantic |
| Environment | python-dotenv |

## Tested On

- ✅ Simple Calculator App (Python)
- ✅ Time Scheduling App (Python)

## Project Structure
##
APP-Builder/
├── Agent/
│   ├── graph.py        # LangGraph pipeline definition
│   ├── prompts.py      # System prompts for each agent
│   ├── states.py       # Pydantic state models (Plan, TaskPlan, CoderState)
│   └── tools.py        # File I/O tools (read, write, list)
├── generated_project/  # Output folder — your app gets built here
├── main.py
├── .env.example
├── requirements.txt
└── README.md
##
## Setup

**1. Clone the repository**
```bash
git clone https://github.com/arsal1947/APP-Builder.git
cd APP-Builder
```

**2. Create and activate virtual environment**
```bash
python -m venv .venv
.venv\Scripts\activate        # Windows
source .venv/bin/activate     # Mac/Linux
```

**3. Install dependencies**
```bash
pip install -r requirements.txt
```

**4. Add your Groq API key**
```bash
cp .env.example .env
```
Then open `.env` and replace with your actual key from [console.groq.com](https://console.groq.com).

## Usage

Edit `Agent/graph.py` and change the prompt:

```python
result = agent.invoke(
    {"user_prompt": "Build a todo app with Flask"},
    {"recursion_limit": 100}
)
```

Then run:
```bash
python main.py
```

Your generated app will appear in the `generated_project/` folder.

## Inspiration

Inspired by [Lovable.dev](https://lovable.dev) — the idea that anyone should be able to describe an app in plain English and have it built automatically by AI.

---

Built with ❤️ by [Arsal Riaz](https://github.com/arsal1947)
