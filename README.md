# Autonomous Traders

Autonomous multi-agent equity trading simulation powered by MCP servers. It includes:

- a trader orchestration layer using the OpenAI Agents SDK
- MCP servers for account operations, market data, and push notifications
- optional researcher tools (Fetch, Brave Search, memory graph)
- a Gradio dashboard for monitoring traders

## Project Structure

- `traders.py`: main trader agent implementation
- `trading_floor.py`: scheduler that runs multiple traders
- `reset.py`: initializes trader accounts and strategies
- `mcp_params.py`: MCP server definitions and wiring
- `accounts.py`, `accounts_server.py`, `accounts_client.py`: account domain + MCP API
- `market.py`, `market_server.py`: market price retrieval + MCP API
- `push_server.py`: push notification MCP server
- `app.py`: Gradio dashboard
- `database.py`: SQLite persistence (accounts, logs, market snapshots)
- `memory/`: local memory database files
- `lab4_walkthrough.ipynb`: lab notebook workflow

## Quick Start

1. Install dependencies:

```bash
pip install -r requirements.txt
```

2. Create and edit environment file:

```bash
copy .env.example .env
```

3. Initialize trader accounts:

```bash
python reset.py
```

4. Run the trading floor loop:

```bash
python trading_floor.py
```

5. Optional dashboard:

```bash
python app.py
```

## Environment Variables

See `.env.example` for all options.

Key values:

- `OPENAI_API_KEY` (required for OpenAI models)
- `POLYGON_API_KEY` + `POLYGON_PLAN` (optional market data)
- `BRAVE_API_KEY` (optional researcher web search)
- `PUSHOVER_USER` + `PUSHOVER_TOKEN` (optional push notifications)
- `TRADING_DB_PATH` (default: `trading_sim.db`)

## Notes

- This is a simulation project for educational and portfolio purposes only.
- Do not use outputs for live trading decisions.
