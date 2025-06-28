# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a study project for learning HuggingFace MCP (Model Context Protocol). The repository contains a simple MCP server implementation that provides weather-related services.

## Architecture

- `server.py` - Main MCP server implementation with weather services
  - Implements MCP server with tool, resource, and prompt capabilities
  - Uses stdio transport for communication
  - Provides weather data through three interfaces:
    - Tool: `get_weather(location)` function
    - Resource: `weather://{location}` URI scheme
    - Prompt: Weather report template generation

- `main.py` - Simple hello world entry point
- `pyproject.toml` - Project configuration with MCP server registration

## Running the Code

The MCP server is registered in pyproject.toml as:
```
[tool.mcp]
servers = { weather = "server:main" }
```

To run the server:
```bash
python server.py
```

To run the main entry point:
```bash
python main.py
```

## Development Environment

- Requires Python >=3.13
- Uses the `mcp` package for Model Context Protocol implementation
- No additional dependencies currently defined

## MCP Server Structure

The server implements the three core MCP capabilities:
1. **Tools** - Callable functions that can be invoked by clients
2. **Resources** - URI-addressable data sources
3. **Prompts** - Template generation for language model interactions

All implementations currently return mock weather data for demonstration purposes.