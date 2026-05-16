# APP-Builder

An AI-powered application builder using a multi-agent LangGraph pipeline.

## How It Works
1. **Planner** — converts your prompt into a structured project plan
2. **Architect** — breaks the plan into detailed file-level tasks
3. **Coder** — implements each task using file read/write tools

## Setup
1. Clone the repo
2. Create a virtual environment: `python -m venv .venv`
3. Activate it: `.venv\Scripts\activate` (Windows)
4. Install dependencies: `pip install -r requirements.txt`
5. Copy `.env.example` to `.env` and add your Groq API key

## Usage
```python
from Agent.graph import agent

result = agent.invoke(
    {"user_prompt": "Build a todo app with Flask"},
    {"recursion_limit": 100}
)
```