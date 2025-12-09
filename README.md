# MyDemo - Interactive MCP Chat Agent

An interactive chat application powered by LangChain, Groq LLM, and Model Context Protocol (MCP) servers. This project demonstrates how to build an AI agent with conversation memory that can interact with multiple MCP servers for web browsing, search, and other capabilities.

## Features

- 🤖 **Interactive Chat Interface**: Command-line chat interface with conversation memory
- 🧠 **Conversation Memory**: Built-in memory system that maintains context across conversations
- 🌐 **MCP Server Integration**: Connects to multiple MCP servers for extended capabilities:
  - **Playwright**: Browser automation and web interaction
  - **Airbnb**: Search and browse Airbnb listings
  - **DuckDuckGo Search**: Web search capabilities
- 🔄 **Async Support**: Fully asynchronous implementation for better performance
- ⚙️ **Configurable**: Easy configuration via JSON files

## Prerequisites

- Python 3.11 or higher
- Node.js and npm (for MCP servers)
- Groq API key ([Get one here](https://console.groq.com/))

## Installation

### 1. Clone the repository

```bash
git clone <your-repo-url>
cd mydemo
```

### 2. Install Python dependencies

Using `uv` (recommended):
```bash
uv sync
```

Or using `pip`:
```bash
pip install -r requirements.txt
```

### 3. Install Node.js dependencies

```bash
npm install
```

### 4. Set up environment variables

Create a `.env` file in the project root:

```bash
GROQ_API_KEY=your_groq_api_key_here
```

## Configuration

The project uses `browser_mcp.json` to configure MCP servers. The default configuration includes:

- **Playwright MCP Server**: For browser automation
- **Airbnb MCP Server**: For Airbnb search functionality
- **DuckDuckGo Search MCP Server**: For web search (with rate limiting)

You can modify `browser_mcp.json` to add or remove MCP servers as needed.

## Usage

### Running the Application

```bash
python app.py
```

### Interactive Commands

Once the application starts, you can:

- **Chat normally**: Type your message and press Enter
- **Clear history**: Type `clear` to clear conversation history
- **Exit**: Type `exit` or `quit` to end the conversation

### Example Interactions

```
You: Search for hotels in Paris on Airbnb
Assistant: [Agent searches Airbnb and provides results]

You: What's the weather like today?
Assistant: [Agent uses browser to check weather]

You: Search for latest Python news
Assistant: [Agent uses DuckDuckGo to search and summarize results]
```

## Project Structure

```
mydemo/
├── app.py                 # Main application with interactive chat
├── main.py                # Simple entry point
├── browser_mcp.json       # MCP server configuration
├── pyproject.toml         # Python project configuration
├── package.json           # Node.js dependencies
├── uv.lock               # Dependency lock file
└── README.md             # This file
```

## MCP Servers

This project integrates with the following MCP servers:

1. **@playwright/mcp**: Browser automation and web scraping
2. **@openbnb/mcp-server-airbnb**: Airbnb listing search and details
3. **duckduckgo-mcp-server**: Web search functionality

## Dependencies

### Python Dependencies
- `langchain-groq>=1.1.0`: Groq LLM integration for LangChain
- `langchain-openai>=1.1.0`: OpenAI integration (if needed)
- `mcp-use>=1.5.0`: MCP client and agent utilities
- `python-dotenv`: Environment variable management

### Node.js Dependencies
- `@playwright/mcp`: Playwright MCP server
- `@openbnb/mcp-server-airbnb`: Airbnb MCP server
- `duckduckgo-mcp-server`: DuckDuckGo search MCP server
- `playwright`: Browser automation library

## How It Works

1. **Initialization**: The application loads environment variables and MCP server configuration
2. **MCP Client**: Creates an MCP client that connects to configured servers
3. **Agent Creation**: Initializes an MCPAgent with:
   - Groq LLM (qwen/qwen3-32b model)
   - MCP client for tool access
   - Conversation memory enabled
4. **Interactive Loop**: Processes user input and generates responses using available MCP tools
5. **Memory Management**: Automatically maintains conversation context across interactions

## Troubleshooting

### Common Issues

1. **MCP Server Connection Errors**
   - Ensure Node.js dependencies are installed: `npm install`
   - Check that MCP servers are properly configured in `browser_mcp.json`

2. **API Key Errors**
   - Verify your `.env` file exists and contains `GROQ_API_KEY`
   - Ensure the API key is valid and has sufficient credits

3. **Import Errors**
   - Make sure all Python dependencies are installed: `uv sync` or `pip install -r requirements.txt`



