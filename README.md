# Weather MCP Tool

## Setup & Usage Guide

### 1. Clone the Repository
```
git clone <your-repo-url>
cd <your-repo-folder>/weather
```

### 2. Create and Activate a Virtual Environment
```
python -m venv .venv
.\.venv\Scripts\Activate  # On Windows
# Or, for Unix/macOS:
# source .venv/bin/activate
```

### 3. Install Dependencies
```
pip install -r requirements.txt  # If you have a requirements.txt
# Or, if using pyproject.toml:
pip install "mcp[cli]" httpx
```

### 4. Run the Weather MCP Tool
```
uv run weather.py
# Or, if you don't have uv:
python weather.py
```

### 5. Register the Tool with Claude Desktop (Legacy/If Supported)
If your Claude Desktop version supports manual MCP tool registration:
- Run:
  ```
  uv run mcp install weather.py
  ```
- This should add the tool to Claude Desktop's config.
- Open Claude Desktop and look for the tool in the tools/extensions section.

### 6. .dxt Packaging (Current Limitation)
- Newer versions of Claude Desktop require tools to be packaged as `.dxt` extensions.
- As of now, there is **no public SDK or CLI** for creating `.dxt` files.
- You cannot add your own custom tool as an extension until Anthropic releases official packaging support.

---

## Troubleshooting
- If you see `Error: typer is required. Install with 'pip install mcp[cli]'`, make sure you install dependencies **inside your virtual environment**.
- If `pip` is missing in your venv, run `python -m ensurepip --upgrade`.
- If your tool does not appear in Claude Desktop, it may be due to the new `.dxt` extension system.

---

## Notes
- This guide will be updated when `.dxt` packaging instructions become available from Anthropic.
