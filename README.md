# Agentlys Dev

An AI development agent built with [agentlys](https://github.com/BenderV/agentlys).

Give it a task and it will autonomously code, test, and deploy using real development tools.

Think about it as a simple Claude Code but for any LLM provider.

## What it does

- **Code Editor**: Read, write, edit files with syntax awareness
- **Terminal**: Run commands, scripts, build tools, tests
- **Git Operations**: Branch, commit, push, create PRs
- **Web Rendering**: Take screenshots of web apps for testing
- **Multi-Agent**: Coordinate multiple specialized agents

## Installation

```bash
pip install -e .
```

Requires:

- Python 3.9+
- OpenAI or Anthropic API key

## Usage

### Interactive Development Agent

```bash
# Start with a task
agentlys-dev "Create a FastAPI app with user authentication"

# Or start interactive mode
agentlys-dev
> Create a React component for file upload
> Add unit tests
> Deploy to Vercel
```

### Available Commands

The project exposes a few other convenience commands:

```bash
agentlys-dev                    # Interactive agent
agentlys-dev-dual              # Dual-agent collaboration demo
agentlys-dev-export            # Export conversation history
agentlys-dev-github-issue-server  # GitHub webhook server
```

## How it Works

Built on [agentlys](https://github.com/myriade-ai/agentlys), agentlys-dev gives AI agents access to real development tools:

```python
from agentlys import Agentlys
from agentlys_tools.code_editor import CodeEditor
from agentlys_tools.terminal import Terminal

agent = Agentlys(
    instruction="You are a senior developer...",
    provider="anthropic",
    model="claude-sonnet-4-20250514"
)

# Add development tools as classes
agent.add_tool(CodeEditor(), "CodeEditor")
agent.add_tool(Terminal(), "Terminal")

# Agent now has full development capabilities
for message in agent.run_conversation("Build a web scraper with tests"):
    print(message.to_markdown())
```

## Configuration your api keys

Choose your provider and set your api key:

```bash
export ANTHROPIC_API_KEY="your-key"
```

```bash
export OPENAI_API_KEY="your-key"
```
