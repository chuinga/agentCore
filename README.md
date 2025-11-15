# AgentCore Training Materials

Training materials demonstrating AWS Bedrock AgentCore integration with OpenAI Agents SDK, featuring a Star Trek: TNG "Lt. Commander Data" agent.

## Overview

This repository contains progressive examples of building AI agents using OpenAI's Agents SDK integrated with AWS Bedrock AgentCore runtime. Each module demonstrates different capabilities:

- **AgentCoreAuth**: Basic authentication setup with Cognito
- **AgentCoreRuntime**: Core agent with web search, file search, and guardrails
- **AgentCoreMemory**: Adds session memory management
- **AgentCoreCodeInterpreter**: Adds Python code execution capabilities
- **OpenAI-Agents**: Standalone OpenAI SDK implementation

## Prerequisites

- Python 3.8+
- OpenAI API key
- AWS account with Bedrock AgentCore access
- AWS credentials configured

## Installation

```bash
# Install dependencies for each module
cd AgentCoreRuntime
pip install -r requirements.txt
```

## Modules

### AgentCoreAuth
Authentication setup using AWS Cognito for AgentCore.

**Files:**
- `SetupCognito.py` - Cognito configuration
- `GetBearerToken.py` - Token retrieval
- `agentcore-auth/data_agent_agentcore.py` - Agent with auth

### AgentCoreRuntime
Basic Data agent with tools and guardrails.

**Features:**
- Web search via WebSearchTool
- File search using OpenAI vector stores
- Calculator agent handoff
- Tasha Yar guardrail (blocks specific topics)

**Run:**
```bash
cd AgentCoreRuntime
export OPENAI_API_KEY=your_key
python data_agent_agentcore.py
```

### AgentCoreMemory
Extends runtime with session memory.

**Features:**
- All AgentCoreRuntime features
- Session-based memory via AgentCoreSession
- Conversation persistence

**Run:**
```bash
cd AgentCoreMemory
export OPENAI_API_KEY=your_key
python data_agent_agentcore_memory.py
```

### AgentCoreCodeInterpreter
Full-featured agent with code execution.

**Features:**
- All AgentCoreMemory features
- Python code execution via AgentCore Code Interpreter
- Secure sandboxed environment

**Run:**
```bash
cd AgentCoreCodeInterpreter
export OPENAI_API_KEY=your_key
python data_agent_agentcore_memory_interpreter.py
```

## Agent Capabilities

### Tools
- **WebSearchTool**: Current web information
- **FileSearchTool**: RAG from vector stores
- **Calculator**: Safe arithmetic evaluation
- **Code Interpreter**: Python execution (CodeInterpreter module only)

### Guardrails
Input guardrail blocks mentions of "Tasha Yar" using agent-based classification.

### Handoffs
Main agent can hand off arithmetic tasks to specialized Calculator agent.

## Configuration

### Environment Variables
```bash
export OPENAI_API_KEY=your_openai_key
export AWS_REGION=us-east-1  # Optional, defaults to us-east-1
```

### Vector Store Setup
Create an OpenAI vector store named "Data Lines Vector Store" with relevant content before running agents.

## Usage Example

```python
# Payload structure
payload = {
    "prompt": "What is 25 * 4?"
}

# Response
{
    "result": "100"
}
```

## Architecture

Each agent follows this pattern:
1. User input → Input guardrails
2. Agent processes with available tools
3. Handoff to specialized agents if needed
4. Return structured output

## License

Training materials for internal use.
