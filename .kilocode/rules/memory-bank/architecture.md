# Architecture: Sequential Thinking MCP Server (Python)

## 1. System Architecture

The project is a Python application that runs as a **Model Context Protocol (MCP) server**. It operates as a standalone executable CLI tool, launched via `python -m src.mcp_fast`. Its primary mode of interaction is through **Standard Input/Output (stdio)**, making it compatible with MCP clients like `cline`.

The architecture is composed of three main layers:

1.  **Server and Transport Layer (`src/mcp_fast/__main__.py`):**
    *   Initializes the MCP server using the `fastmcp` library.
    *   Establishes a transport to listen for and send MCP messages over stdin/stdout.
    *   Registers the core `sequentialthinking` tool and its handlers.

2.  **Core Logic Layer (`src/mcp_fast/__main__.py` - `ToolAwareSequentialThinkingServer` class):**
    *   Manages the state of the thinking process, including history and branches.
    *   Validates incoming `thought` data against a defined schema.
    *   Processes thoughts, formats them for output, and maintains the history.

3.  **Data and Schema Layer (`src/mcp_fast/schema.py`, `src/mcp_fast/types.py`):**
    *   **`schema.py`:** Defines the JSON schema for the `sequentialthinking` tool's inputs.
    *   **`types.py`:** Defines the Python data classes (e.g., `ThoughtData`) that structure the data used throughout the application.

## 2. Source Code Paths

*   **`src/mcp_fast/__main__.py`:** The application's entry point. It contains the main server setup, request handling, and the core `ToolAwareSequentialThinkingServer` class.
*   **`src/mcp_fast/schema.py`:** Defines the strict input schema for the `sequentialthinking` tool.
*   **`src/mcp_fast/types.py`:** Contains all custom Python type definitions.

## 3. Key Technical Decisions

*   **Stdio Communication:** The exclusive use of stdio for communication aligns with MCP standards for local servers.
*   **Single Tool (`sequentialthinking`):** The server exposes its functionality through one comprehensive tool.
*   **Stateful Server Instance:** The `ToolAwareSequentialThinkingServer` class instance is stateful, holding the `thought_history` and `branches` in memory for the duration of the server's process.

## 4. Component Relationships

```mermaid
graph TD
    subgraph "MCP Client (e.g., cline)"
        A[User Input/AI Agent]
    end

    subgraph "mcp-sequentialthinking-tools Server (Python)"
        B(StdioTransport)
        C(MCP Server)
        D(ToolAwareSequentialThinkingServer)
        E[Data Schemas & Types]
    end

    A -- "MCP Request (JSON)" --> B
    B -- "Parsed Request" --> C
    C -- "Call 'sequentialthinking'" --> D
    D -- "Validates against" --> E
    D -- "Processes thought" --> D
    D -- "Returns result" --> C
    C -- "Sends MCP Response (JSON)" --> B
    B -- "stdio" --> A