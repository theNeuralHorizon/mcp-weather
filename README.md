# Weather MCP Tool

## Setup & Usage Guide (Legacy/Manual)

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

---

## Troubleshooting
- If you see `Error: typer is required. Install with 'pip install mcp[cli]'`, make sure you install dependencies **inside your virtual environment**.
- If `pip` is missing in your venv, run `python -m ensurepip --upgrade`.
- If your tool does not appear in Claude Desktop, ensure you installed the `.dxt` file correctly and that your manifest is valid.

---

## Notes
- This guide will be updated as the Claude Desktop tool ecosystem evolves.
- For the latest `.dxt` packaging instructions, refer to the official Anthropic documentation or CLI help.

---

## 🚀 Claude Desktop .dxt Extensions: Packaging & Installation (2024+)

Anthropic now provides official support and tooling for packaging Claude Desktop extensions as `.dxt` files, including Python-based MCP servers. This enables one-click installation, bundled dependencies, user-friendly configuration, and automatic updates. Here’s how to package and install your Python MCP tool as a Claude Desktop extension:

### 1. Install the DXT CLI
```bash
npm install -g @anthropic-ai/dxt
```

### 2. Initialize Your Extension
Navigate to your MCP server directory and run:
```bash
dxt init
```
This will guide you through creating a `manifest.json` (set `"type": "python"` and specify your entry point script).

### 3. Bundle Python Dependencies
- Include dependencies in `server/lib/` or a full virtual environment in `server/venv/`.
- Or use `pip-tools`, `poetry`, or `pipenv` for reproducible environments.
- Set `PYTHONPATH` in `mcp_config.env` if needed.

### 4. Package Your Extension
```bash
dxt pack
```
This creates a `.dxt` file in your project directory.

### 5. Install in Claude Desktop
- Open Claude Desktop.
- Go to **Settings > Extensions**.
- Click **Install Extension...** and select your `.dxt` file.

### 6. Test and Iterate
- Your Python MCP tool is now available as a Claude Desktop extension!

**Benefits:**
- One-click install, no manual setup
- All dependencies bundled
- User-configurable settings via manifest
- Automatic updates and extension directory support
