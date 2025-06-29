# AI Assistant with Planning Framework

An AI assistant that uses OpenAI's GPT model to execute tasks through a structured **Plan → Action → Observe** cycle.

## Features

- Structured planning and execution
- Linux command execution via `run_command` tool
- Interactive conversation loop
- JSON-based communication

## Installation

```bash
pip install openai python-dotenv requests
```

Create `.env` file:
```env
OPENAI_API_KEY=your_api_key_here
```

## Usage

```bash
python main.py
```

Example interaction:
```
> List files in current directory
🧠: User wants to see files in current directory
🧠: I should use run_command with 'ls' command
🛠️: Calling Tool:run_command with input ls
🤖: Here are the files: file1.py, file2.txt, README.md
```

## Available Tools

- `run_command`: Executes Linux/Unix commands

## Adding Tools

```python
def new_tool(input_param):
    return result

available_tools["new_tool"] = new_tool
```

## Security Warning

⚠️ The `run_command` tool can execute any system command. Use with caution and consider sandboxing for production.

## Output Format

```json
{
    "step": "plan|action|observe|output",
    "content": "description",
    "function": "tool_name",
    "input": "tool_input"
}
```